---
name: ship
description: "Takes a feature from a rough description to an open PR — orchestrates design → plan → implement → test → verify → simplify → PR. Trigger on \"/ship\", \"ship this feature\", \"run the feature workflow\", \"build and PR this\". Autonomous after plan approval by default; --step pauses at each stage; --micro/--big force design depth."
argument-hint: "<feature description> [--step] [--auto] [--micro|--big]"
allowed-tools: Read, Write, Edit, Bash, Grep, Glob, Task, Skill, AskUserQuestion, TaskCreate, TaskUpdate, TaskList, TaskGet
---

# /ship — end-to-end feature delivery

Orchestrate one feature from a rough description to an open PR. You reuse native capabilities and other skills; your job is to **sequence them, enforce the gates, and honor the repo config** — not to reimplement them.

Create a task list (TaskCreate) with one item per stage below, and keep it current — mark each stage `in_progress` when you start it and `completed` when it's done (TaskUpdate), and use TaskList to report progress.

## Stage 0 — Load config and parse flags

1. Read `.claude/feature-flow.local.md` (YAML frontmatter = settings). If it is **missing**, offer to create it from `${CLAUDE_PLUGIN_ROOT}/config/feature-flow.config.example.md` and add `.claude/*.local.md` to `.gitignore`. If the user declines, proceed with the example's defaults in memory — **but the example's verify defaults assume a Node/npm/Jest toolchain.** If the repo isn't obviously Node (no `package.json`), do **not** fall back to `npm run …` blindly: ask the user for this repo's verify commands (typecheck/lint/test/build) up front, or strongly recommend creating the config first. Guessing the wrong toolchain makes the Stage-6 gate fail on the first command.
2. From the frontmatter read: `autonomy` (default `auto`), `models` (plan / implement / review tiers — `implement` may be a scalar OR a per-complexity map `{simple, standard, hard}`, see Stage 5), `execution.mode` (`subagent` (default) | `inline` — see Stage 5), `design_doc_dir`, `verify`, `test_policy`, `review` (optional Stage-7 override: `command`/`scope`/`never`/`simplify`), `stop_conditions`, `pr`, `retry_budget` (default 3).
3. Parse `$ARGUMENTS` flags: `--step`/`--auto` override `autonomy`; `--micro`/`--big` force design depth. The remaining text is the feature description.

## Stage 1 — Branch / isolation (do this BEFORE any edit)

- If the working tree is **dirty**, STOP and surface it — never fold unrelated changes into this feature (preserve pre-existing work).
- If on the base branch (`pr.base`, default `main`), create a feature branch: `feature/<kebab-of-description>`.
- If the plan is likely to **fan out parallel implementers on disjoint files**, prefer a git worktree so concurrent edits don't collide. Otherwise a branch is enough.

## Stage 2 — Design (invoke `storm`)

Invoke the **storm** skill (Skill tool) with the description + any `--micro`/`--big` hint. It returns a short agreed design (and a doc path for big features). Do not proceed to planning until storm reports the design is agreed.

## Stage 3 — Plan (strong model)

Decompose the design into an ordered task list. Author this on the **`models.plan`** tier (strong model) — the plan is the contract a cheaper subagent implements. For each task record:

- **files** it touches,
- **test policy** — classify via `${CLAUDE_PLUGIN_ROOT}/references/test-policy.md` and the config `test_policy` map (`test-first` | `test-after` | `none`),
- **coupling** — `coupled` (edits interact with other tasks / shared state) or `independent` (disjoint files, no shared state),
- **complexity** — `simple` (mechanical: boilerplate, well-patterned, single-file, obvious edits), `standard` (normal feature work — the default), or `hard` (tricky logic, subtle invariants, many-file coordination). This selects the implementer model in Stage 5, so tag honestly: over-tagging burns the strong model, under-tagging risks a weak one on a subtle task.
- **risk / stop-condition flags** — see Stage 4.

**Prefer independent, disjoint-file tasks.** The plan is where cost is won: tasks that own disjoint files with no shared state fan out to cheap parallel implementers (Stage 5), while `coupled` tasks serialize onto one subagent. So when the work genuinely separates, carve it that way (e.g. per-route, per-component, per-module) and name the exact files each task owns. Do **not** force artificial splits that fragment one coherent change across files that must move together — those stay `coupled`. A good plan is mostly `independent` tasks with a small `coupled` core.

Write the plan into the design doc (or `design_doc_dir`) for non-trivial features — it is the durable contract each implementer subagent re-reads, not just in-context memory. Skip the written plan only for genuinely micro changes.

## Stage 4 — Approval gate (ALWAYS, both modes)

Present the design + task plan and get **explicit approval**. This is the single mandatory checkpoint in both autonomy modes — you never implement an unapproved plan. If planning surfaced any **stop-condition** (`${CLAUDE_PLUGIN_ROOT}/references/stop-conditions.md`), raise it here before asking to proceed.

## Stage 5 — Implement

**Subagent-driven (`execution.mode: subagent`, the default and preferred mode).** The plan is approved, so hand the *writing* to implementer subagents (**Task tool**) on the `models.implement` tier and keep the strong orchestrator model for sequencing, gating, and debugging. **The orchestrator's context is a scarce resource** — reading large files, exploring the codebase, and writing code all bloat it and degrade the gating and debugging you exist to do. So push implementation *out of the main session* by default. Route by the plan's coupling tags:

- **≥2 genuinely independent tasks on disjoint files** → dispatch them **in parallel**: emit **multiple Task calls in a single message** so the subagents run concurrently — one per task, each on the model its `complexity` resolves to (see *Model selection* below). Because each owns disjoint files, concurrent edits can't collide. Give each subagent the plan-doc path, its one task, the exact files it owns, and its test policy; tell it to stay strictly within that scope.
- **Coupled / must-be-sequential tasks** → dispatch **one** implementer subagent (Task tool) with the approved plan path and the ordered coupled tasks; it implements them in a single coherent thread. Run it on the tier the group's **highest** `complexity` resolves to (a coupled group containing one hard task runs hard). One sequential subagent is safe for coupled work — the race risk is *parallel* subagents on shared state, not a single one.
- **Trivial change** (a few lines / pure copy / one small view) → **still prefer a single subagent.** Implement inline in the orchestrator only when the edit is so small that cold-start overhead clearly outweighs it **and** doing it inline won't meaningfully bloat your context (no large file reads, no exploration to get there). When in doubt, dispatch a subagent. "One subagent does the whole implementation" is the right default even for a single coherent task — it keeps the main session clean for gating and debugging.

**Prefer subagent over inline, always** — the question is never "can I just do this inline?" but "does this genuinely need to be inline, or can one subagent own it?" Default to the subagent; reserve inline for the rare truly-trivial edit.

After a subagent returns, verify its diff matches its task and scope before moving on — for non-trivial work, have the implementer self-check its own diff (or dispatch a cheap check subagent) rather than pulling the whole diff into the orchestrator.

**Model selection (per task `complexity`).** Resolve each task's implementer model from `models.implement`:
- if `models.implement` is a **map**, look up the task's `complexity` key (`simple` / `standard` / `hard`), defaulting untagged tasks to `standard`;
- if it is a **scalar**, use it for every task.
Pass the resolved model as the Task `model` (and match `effort` to complexity — `low` for simple, `high` for hard). A task the implementer finds harder than tagged should be escalated, not forced through on a weak model — surface it and bump the tier.

`execution.mode: inline` (opt-in, legacy) overrides the above: the orchestrator writes coupled/small work itself. Use only when you deliberately want the strong model writing everything and accept the context cost — `subagent` is preferred.

Whichever path: dispatched implementers must **stay within their task's files and scope** and re-read the plan doc for context (they cold-start). For every task, honor its **test policy**: `test-first` → write the failing test before the code; `test-after` → cover meaningful paths after; `none` → no new tests (trivial view/copy).

On a test failure or bug, invoke the **debug** skill (Skill tool) yourself — confirm intended behavior, then root cause before fixes. Debugging stays on the orchestrator (strong) tier by design. Respect `retry_budget`; if exhausted, treat it as a stop-condition and escalate.

## Stage 6 — Verify (invoke `verify`)

Invoke the **verify** skill (Skill tool). It runs the right subset of gates by what changed and **pastes real output**. It is read-only — if it reports a failure, you (the orchestrator) invoke the **debug** skill. Must be green to continue. In `--step` mode, pause here for the user.

## Stage 7 — Review + simplify (size-gated)

Run the review + simplify pass on the **`models.review`** tier: dispatch it as a single review subagent (Task tool) at that tier rather than inline, so the strong orchestrator model isn't spent on it. If the config has a `review:` block, honor it (`command`, `scope`, `never`, `simplify`) — it wins over the defaults below.

- **Substantial feature** → run `/code-review` (correctness) then `/simplify` (quality). Keep `scope` to the working diff unless the config says otherwise; escalate to the cloud `codebase-review` board only if the config allows it (respect any `review.never` list). Apply findings with rigor — verify each before implementing, don't agree performatively. Apply/fix findings on the `models.implement` tier.
  - **If `/code-review` or `/simplify` isn't available** (they are separate skills a user may not have installed), don't fail — have the review subagent do the equivalent inline on the working diff: first a correctness pass (bugs, missed cases, broken invariants), then a quality pass (reuse, simplification, dead code). Same rigor, same tier.
- **Trivial change (a few divs/copy)** → skip both.

## Stage 8 — PR

Commit (branch-first; include `pr.trailers`), push, open the PR against `pr.base`. Reuse the `commit-commands:commit-push-pr` pattern if available. Do not merge unless the user asked.

- **`gh` required for opening the PR.** Before relying on it, confirm it's usable (`gh auth status`). If `gh` is missing or unauthenticated, don't fail the run: commit and **push the branch**, then print the PR-compare URL (`https://<host>/<owner>/<repo>/compare/<base>...<branch>?expand=1`) for the user to open the PR manually, and note that the finish stage can't auto-confirm the merge without `gh`.

## Stage 9 — Finish

Follow `${CLAUDE_PLUGIN_ROOT}/references/squash-safe-finish.md`. Key rule: after any merge, confirm it via `gh pr view <branch> --json state,mergedAt` (the PR state) — **never** infer "not merged" from commit SHAs (squash rewrites them). Then prune the branch.

## Autonomy behavior

- **auto** (default): after the Stage-4 approval, run Stages 5–8 **without pausing**, UNLESS a stop-condition fires — then STOP and ask. Report progress via the task list; summarize at the end.
- **step**: pause for confirmation after design, implement, verify, review, and PR (Stage 4 is always a gate).

## Non-negotiables

- Never skip Stage 4 (plan approval) or Stage 6 (verify green with evidence).
- Never expand scope mid-run; a scope change is a stop-condition.
- Report faithfully — if a gate failed or a step was skipped, say so with the output.
