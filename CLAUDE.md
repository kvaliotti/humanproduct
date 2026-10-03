# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A Claude Code plugin marketplace (not an application). No build, lint, or test step — it ships content (skills, slash commands, and sub-agents) consumed by Claude Code when a user installs a plugin from it. Published at `kvaliotti/humanproduct` and installed via `/plugin marketplace add kvaliotti/humanproduct`.

## Structure

```
.claude-plugin/marketplace.json   # marketplace manifest — lists every plugin in the repo
prd-workflow/                     # plugin (directory referenced by marketplace.json)
  .claude-plugin/plugin.json      # plugin manifest (name, version, description, keywords)
  skills/<skill-name>/SKILL.md    # each skill: YAML frontmatter + markdown body
  skills/<skill-name>/references/ # optional supporting docs the skill reads at runtime
strategic-research/               # plugin — five short skills + the /strategic-research command
  .claude-plugin/plugin.json
  commands/strategic-research.md  # slash command (description, argument-hint)
  skills/<skill-name>/SKILL.md    # no per-skill references, assets, or templates
  references/plain-writing.md     # the one shared file: writing rules every skill follows
pmm-define-and-review-positioning/ # plugin — six skills, no slash commands
  .claude-plugin/plugin.json
  skills/<skill-name>/SKILL.md
  skills/<skill-name>/references/
user-research/                    # plugin — three skills + one agent (modelled on sales-call-analysis)
  .claude-plugin/plugin.json
  skills/<skill-name>/SKILL.md    # plan-research, analyze-interviews, synthesize-research
  agents/interview-analyst.md     # one per participant, spawned by analyze-interviews
sales-call-analysis/              # plugin — two skills + one agent; the reference for "simple"
  .claude-plugin/plugin.json
  skills/<skill-name>/SKILL.md    # analyze-sales-call, aggregate-call-analyses
  agents/call-analyst.md          # one per client, spawned by analyze-sales-call
plg-growth/                       # plugin — fourteen short skills (~50–100 lines each), no slash commands
  .claude-plugin/plugin.json
  skills/<skill-name>/SKILL.md    # only plg-readiness and acquisition-model-selector keep one reference each
  references/                     # problem-solving-backbone, work-plan-template, team-structuring (shared)
event-tracking/                   # plugin — three skills, no slash commands
  .claude-plugin/plugin.json
  skills/<skill-name>/SKILL.md    # analytics-use-cases, event-definition, tracking-plan-review
  skills/event-definition/references/platform-formats.md
  references/                     # platform-constraints, naming-conventions, decision-framework (shared)
cro-engine/                       # plugin — one skill, no references; conversion-rate-optimization reviewer
  .claude-plugin/plugin.json
  skills/cro-engine/SKILL.md
design-system-master/             # plugin — orchestrator + three skills (review/optimize/create design systems)
  .claude-plugin/plugin.json
  skills/<skill-name>/SKILL.md    # design-system-master (router), review-/optimize-/create-design-system
  skills/create-design-system/assets/DESIGN.template.md  # scaffold the create skill writes out
  references/                     # plugin-root shared refs (format, a11y, patterns, archetypes, codebase-bridge)
  references/exemplars/           # 2 curated real DESIGN.md specs (Linear, Binance) at the two ends of the archetype range
designing-for-behaviour/          # plugin — orchestrator skill + FOUR analyst AGENTS
  .claude-plugin/plugin.json
  skills/designing-for-behaviour/SKILL.md   # orchestrator + /designing-for-behaviour entry point
  agents/<lens>-analyst.md        # behavioural-loop / cognitive-ease / capability-results / control-autonomy (read-only inspection)
  references/                     # plugin-root shared refs (foundations, 4 lens-*.md, ethics, coherence-and-anti-bloat, report-template)
user-story-review/                # plugin — one skill; user-story reviewer with a hard one-page output budget
  .claude-plugin/plugin.json
  skills/user-story-review/SKILL.md
  skills/user-story-review/references/   # review-rubric, output-contract, splitting-patterns (single-skill → per-skill, not plugin-root)
writing-review/                   # plugin — one skill + one agent (sales-call-analysis shape); five parallel reviewers + merge
  .claude-plugin/plugin.json
  skills/review-writing/SKILL.md  # orchestration, the five reviewer specs, findings format, merge rules
  skills/review-writing/references/writing-rules.md  # Zinsser-style clutter + AI-writing tells (the only reference)
  agents/writing-reviewer.md      # spawned once per reviewer (reader/structure/argument/evidence/prose)
```

Note: `design-md-corpus/` at the repo root (74 product `DESIGN.md` files) is **grounding data, not a plugin** — it is untracked and must not be registered in `marketplace.json` or shipped. The `design-system-master` plugin distills it into `references/` + 2 curated `references/exemplars/`; it does not ship the full corpus.

Adding a plugin: create `<plugin>/.claude-plugin/plugin.json` and `<plugin>/skills/...` (plus `<plugin>/commands/...` for slash commands and `<plugin>/agents/<name>.md` for sub-agents, spawned as `<plugin>:<name>`), then register it in the root `marketplace.json` `plugins` array with `name`, `source` (relative path), `description`, `version`.

## Skill contract

Every `SKILL.md` starts with YAML frontmatter:

- `name` — must match the directory name
- `description` — trigger phrases; this is what Claude Code matches against user intent to decide when to activate the skill. Be generous with phrasings.
- `user-invocable: true` — exposes the skill as `/skill-name` (optional — skills can also activate purely from description matching)
- `argument-hint` — shown in the slash-command picker

Skill bodies are prose instructions the model follows at activation time. They can reference sibling files via relative paths (e.g., `references/prd-template.md`, `assets/html-template.html`).

**Shared references (cross-skill).** When a reference is used by more than one skill in a plugin, it lives once at the plugin root (`<plugin>/references/…`) and skills point to it with the absolute plugin variable `${CLAUDE_PLUGIN_ROOT}/references/<file>.md` — not a per-skill copy. This is the standard for de-duplicated content across the marketplace (e.g. `plg-growth/references/problem-solving-backbone.md`, `strategic-research/references/plain-writing.md`, `event-tracking/references/platform-constraints.md`). Keep single-skill references under that skill's own `references/`. When you delete or move a reference, grep the whole plugin for its path (both `references/…` and `${CLAUDE_PLUGIN_ROOT}/…` forms) and fix every pointer.

## Quality bar (every plugin)

The marketplace was slimmed in Oct 2026 (plg-growth 14.8k → 1.1k lines, cro-engine 2.7k → 62, event-tracking 1.9k → 0.5k, design-system-master 4.9k → 2.3k). Don't let these come back:

- **No invented scores.** No 0–100 / percentage / 1–5 maturity scorecards, no confidence percentages, no "iterate until the average is 90". Measured ratios and rubric-defined pass/weak/fail with stated criteria are fine.
- **No role-played panels of real named experts.** Fold any useful check into a one-line rule.
- **No benchmark without a named source.** Otherwise "measure your own baseline".
- **No textbook.** Name a framework in one line; don't teach it. Keep what the model wouldn't do unprompted: decision rules, practitioner opinions, gates, output contracts.
- **Short output, top fixes first, depth on request.** Short answer by default where a skill has a full-analysis mode.

## Command contract

Slash commands live in `<plugin>/commands/<name>.md` with frontmatter:

- `description` — shown in the command picker and used for matching
- `argument-hint` — placeholder text for the argument field

The body is the prompt the command runs. `strategic-research/commands/strategic-research.md` is the working example.

## prd-workflow architecture

The three skills form a sequential pipeline that enriches a single `PRD-[feature-name].md` file in the user's working directory:

1. `prd-draft` — writes the initial PRD from messy input, using `references/prd-template.md`
2. `prd-evaluate` — runs gap analysis against `references/evaluation-checklist.md`; the user accepts/rejects findings, PRD is updated
3. `sit-beh` — runs Situation/Behaviour analysis on the PRD's situations section, adds new user stories and acceptance criteria; also writes to `.sitbeh/` in the user's working directory

Each skill's SKILL.md describes the handoff to the next. When editing one, keep the chaining instructions at the end of the file consistent with the others.

## strategic-research architecture

Five short skills run in order by `/strategic-research` (resume with `--from=N`). Each writes one markdown file to a `strategic-research/` subfolder of the user's working directory under a **fixed step-numbered name** and reads whichever earlier files exist:

1. `industry-process-map` → `01-industry-process-map.md` — workflow steps and how each gets done today
2. `audience-segment-research` → `02-audience-segments.md` — segments, how to spot them, who to target first
3. `willingness-to-pay-research` → `03-willingness-to-pay.md` — current spend, price range to test, arithmetic shown
4. `competitor-evaluation` → `04-competitor-evaluation.md` — competitor table, why people pick/leave, gaps
5. `strategic-synthesis-report` → `05-summary.md` — one page: answer, where to play, how to win, risks, next steps

- **Plain output is the load-bearing idea.** v1 produced incomprehensible output (YAML handoffs, confidence percentages, tension taxonomies, 7 Powers grids, a Chart.js HTML report). v2 deleted all of that. Every skill follows `references/plain-writing.md`: short sentences, no framework jargon in the output, real names and numbers, a source for every fact or an explicit **(assumption)**, no made-up scores, ≤2 pages per file, and a closing **What we don't know**. Do not reintroduce YAML handoffs, numeric confidence, scoring rubrics, per-skill reference libraries, or an HTML report.
- Each SKILL.md is a numbered list of output sections plus a few rules (the sales-call-analysis shape). Keep them that short.
- Chaining is by the fixed filenames only. Don't switch to slug-derived filenames or absolute paths — that broke `--from` resume historically.

## pmm-define-and-review-positioning architecture

Six skills forming a positioning toolkit based on the 5+1 framework (Competitive Alternatives → Unique Attributes → Value Themes → Target Market → Market Category → optional Trends). Re-reviewed in Oct 2026 and deliberately **kept at six**: each standalone skill is a real entry point ("should we create a category?", "find our differentiators", "turn our positioning into a pitch"), and the apparent duplication is standalone vs orchestrated modes.

1. `positioning-workshop` — full guided 10-step process producing a filled 5+1 canvas, narrative, and pressure test results
2. `positioning-review` — audits existing positioning against the 9-question pressure test (pass/weak/fail with defined criteria in `pressure-test-scoring.md`; tests that can't be judged from a document are marked ❓ Ask; stated mapping to Pass / Needs Work / Major Rework)
3. `competitive-alternatives` — deep dive into Steps 4-6 (alternatives → attributes → value themes)
4. `market-frame-selector` — Step 8 decision tool: Head to Head vs Big Fish Small Pond vs Create a New Game
5. `sales-story-builder` — translates a completed canvas into a 7-stage sales narrative plus story-on-a-page
6. `positioning-orchestrator` — runs the skills in sequence (workshop → market frame → trend → capture → sales story) with phase-boundary confirmations

YAML blocks are emitted **only under the orchestrator** (`phase_1_output` … `phase_4_output`) as in-conversation checkpoints; standalone runs never print them. Shared content lives once in plugin-root `references/` (`three-styles.md`, `case-studies.md`, `pressure-test.md` — the canonical 9 tests plus the workshop loop-back procedure).

## user-research architecture

Three skills and one agent, deliberately built in the same shape as `sales-call-analysis` (v0.x had six build/evaluate skills and ~6,000 lines of methodology references; v1 replaced them):

1. `plan-research` — decision, riskiest assumptions, research questions (≤5), optional target behaviour, screening by past behaviour, and a Mom-Test interview guide, in one file: `research/plan-<topic>.md`.
2. `analyze-interviews` — confirms the setup with the user, then spawns one `user-research:interview-analyst` (Opus) per participant. The skill's **Analysis** section is the spec the agent follows; the orchestrator passes the agent `${CLAUDE_PLUGIN_ROOT}/skills/analyze-interviews/SKILL.md`. Writes `research/analyses/<participant>.md`: numbered sections alternating analysis and verbatim quotes, with barriers tagged don't know / can't / don't want (the same lens as `prd-workflow`'s `sit-beh`) and hypotheticals marked **(said, not done)**.
3. `synthesize-research` — one sub-agent per dimension (pains, goals, barriers, workarounds) builds theme → finding tables with participants, quotes, and counts (count = participants, not quotes), then the skill writes answers to the plan's research questions and marks each assumption confirmed / killed / open: `research/YYYY-MM-DD-synthesis.md`.

Contract: the `research/` folder layout and the analysis section numbers (synthesize-research maps dimensions to them). Change one, change the other.

## sales-call-analysis architecture

Two skills and one agent. The marketplace's model of a simple, effective plugin — no references, each SKILL.md under 50 lines.

1. `analyze-sales-call` — groups transcripts (default `transcripts/`) by client, confirms "one Opus sub-agent per client" and "merge each client's calls" with the user, then spawns one `sales-call-analysis:call-analyst` per client in one message. The skill's **Analysis** section (10 numbered sections: pains, outcomes, objections, decision criteria each followed by verbatim quotes; what it takes to convert; hook messaging) is the spec the agent follows. Writes `analyses/<client>.md`.
2. `aggregate-call-analyses` — one sub-agent per dimension builds a category → item table with companies, quotes, and counts; assembles `synthesis/YYYY-MM-DD-cross-client-analysis.md`.

Contract: the aggregate skill maps dimensions to the analysis section numbers (1–8). Change one, change the other. Agents are namespaced `<plugin>:<agent>` when spawned.

## plg-growth architecture

Fourteen short skills (~50–100 lines each) in a hub-and-spoke model, with `plg-orchestrator` routing by a table to all 13 spokes by their real names:

- **Fit and levers:** `plg-readiness` (does the free experience prove what buyers decide on?), `plg-revenue-analysis` (revenue driver tree, sensitivity, which lever)
- **Acquisition:** `acquisition-model-selector` (freemium / trial / reverse trial / ungated / demo; `references/model-playbooks.md`), `acquisition-domain` (points to `growth-loops` for viral math and `cro-engine` for signup forms)
- **Funnel stages:** `activation-domain`, `retention-domain`, `monetisation-domain`, `satisfaction-domain`
- **Cross-cutting:** `growth-loops`, `product-led-sales`, `plg-experimentation`, `plg-data-setup` (PLG-specific data only; full tracking plans go to the `event-tracking` plugin), `plg-transformation`

Every skill answers the question directly by default and runs its full analysis (≤1 page: bottom line, top hypotheses, what we don't know, next step) only on request. Plugin-root `references/`: `problem-solving-backbone.md` (eight short house rules, not a methodology tutorial), `work-plan-template.md` (only when a work plan is asked for), `team-structuring.md` (used by revenue-analysis and transformation). No per-skill work-plan examples, no maturity scores, no unsourced benchmarks: the only number kept is Sean Ellis's 40% "very disappointed" bar. No YAML handoffs: the orchestrator routes by reading context.

## event-tracking architecture

Three skills; Claude Code routes by each skill's description (there is no orchestrator):

1. `analytics-use-cases` — stakeholder questions, analysis types, dashboards, and conceptual event needs before any event is named. Writes `tracking/use-cases-<feature>.md`.
2. `event-definition` — event specs (names, properties, firing conditions, user/group properties, PII), with an optional last step that formats them for Amplitude / Mixpanel / PostHog / Segment / GA4 (`skills/event-definition/references/platform-formats.md`). Offers to run use cases first. Writes `tracking/tracking-plan-<feature>.md`.
3. `tracking-plan-review` — audits existing tracking; leads with a verdict and ≤5 top fixes, then the measured ratio per check. No overall score.

Plugin-root shared refs: `platform-constraints.md` (the single source of vendor limits, with a "verify against current vendor docs" hedge), `naming-conventions.md` (how to find existing tracking and detect its convention: match it, don't impose one), `decision-framework.md` (parameterization test, user vs system actor, property value rules). Events must trace to use cases; the parameterization test is the primary design tool. Chaining is by the `tracking/` filenames, not YAML.

## design-system-master architecture

An orchestrator + three capability skills that all read, write, or refactor a single canonical artifact — a **`DESIGN.md`** (the token-referencing `getdesign.md` format: YAML frontmatter of `colors`/`typography`/`rounded`/`spacing`/`components` with `{group.token}` refs, plus prose sections):

1. `design-system-master` — router / `/design-system-master` entry point. Classifies intent (review / optimize / create) and input (a DESIGN.md / a codebase / nothing yet), then routes.
2. `review-design-system` — archetype → accessibility gate (real WCAG contrast math) → complexity-fit gate → ≤5 fixes (3 by default), each anchored to a token/component/section → "Keep" list. About one page, **no score**. Its "What to look for" list is a lookup the model uses, not printed output. Don't reintroduce the old 16-row scorecard or the role-played expert panel.
3. `optimize-design-system` — improves the spec (consolidate/regularize/fill/fix) and/or retrofits it into a product codebase (extract de-facto tokens → emit CSS vars / Tailwind / Style Dictionary → codemod literals→tokens incrementally). Protects the signature.
4. `create-design-system` — builds a complete DESIGN.md from scratch, sized to the product's archetype, using `skills/create-design-system/assets/DESIGN.template.md`.

Distinctive design:

- **References live at the plugin root**: `design-md-format.md`, `archetypes.md`, `patterns-{color,typography,space-shape-elevation,components-theming}.md`, `accessibility.md`, `codebase-bridge.md`, plus `exemplars/` (Linear and Binance: minimal dev-tool and dense fintech). When moving/deleting a reference, grep the whole plugin for both `references/…` and `${CLAUDE_PLUGIN_ROOT}/…` forms.
- **The anti-overfit invariant** — the load-bearing idea. Every skill classifies the product **archetype** first (`archetypes.md`) and judges complexity as **essential** (domain-required — keep) vs **accidental** (redundant/one-off/undocumented — remove). This stops the plugin from naively "simplifying" legitimate complexity (dual-coded green/red, dual font stacks, multi-surface theming, semantic ramps). Keep the essential-vs-accidental guide and the complexity budgets intact.
- **Grounding, not shipped data** — distilled from `design-md-corpus/` (74 specs, untracked). Don't ship the corpus. The corpus has **no numeric contrast ratios**, so the contrast math in `accessibility.md` is the tool's own contribution.
- **Self-contained prose**: optional upstream linter (`npx @google/design.md lint`); degrades to prose guidance without it.

## designing-for-behaviour architecture

A behavioural-design **reviewer** (evaluate + recommend, does NOT implement). One orchestrator skill drives **four read-only lens-analyst agents** in parallel. It reviews an existing product/codebase OR an idea/PRD: how well does this drive behaviour, adoption, and engagement, and what is the smallest integrated set of fixes.

Pipeline (`skills/designing-for-behaviour/SKILL.md`): intake (once, shared) → 4 lenses **in parallel** (one message) → rank gaps (internal 0/1/2/N-A ratings, never reported) → **coherence & anti-bloat review** → report (`behaviour-review-[target].md` + inline summary). The report is ≤2 pages: one-sentence bottleneck, ≤3 core moves, "deliberately NOT adding" (≤5), gaps (≤5), fold-ins (≤3), what we don't know. **No score, percentages, bands, or confidence line** — don't reintroduce them.

- **Six books → four lenses.** `behavioural-loop-analyst` (Atomic Habits / Tiny Habits / Hooked), `cognitive-ease-analyst` (Kahneman), `capability-results-analyst` (Badass), `control-autonomy-analyst` (PCT + anti-manipulation). Each topic lives in one lens. The `foundations.md` "what each lens owns" carve-up and shared analyst protocol keep them in their lanes.
- **Plugin-root refs** shared by skill and agents: `foundations.md` (defs, intake, internal rating scale, lens carve-up, analyst protocol), `lens-{behavioural-loop,cognitive-ease,capability-results,control-autonomy}.md`, `ethics-and-dark-patterns.md`, `coherence-and-anti-bloat.md`, `report-template.md`.
- **The anti-bloat coherence review is the load-bearing idea** (`coherence-and-anti-bloat.md`): turns four lenses of additive recommendations into the smallest set, enforces an archetype-calibrated complexity budget, prefers embedding over adding, runs a subtraction pass. Keep it and the N/A discipline intact.
- **Anchors + ethics by contract.** Every gap/rec carries a concrete anchor (screen/flow/`file:line`/quoted copy/PRD section); the ethics gate reframes or cuts manipulative recommendations, and autonomy wins conflicts.

## user-story-review architecture

One skill (`/user-story-review`) that reads a PRD/backlog and reviews its user stories. Deliberately the smallest plugin here — its design is mostly about what it *refuses* to emit.

Pipeline in `skills/user-story-review/SKILL.md`: find input (arg → newest `PRD-*.md` → any backlog-shaped file → ask) → read PRD context → classify every item into one of five verdicts (READY / NEEDS CONVERSATION / REFRAME / SPLIT-EXPERIMENT / NOT A USER STORY) against the six gates → **triage** → emit.

- **The output budget is the load-bearing idea.** `references/output-contract.md` caps the review at ~1 page: verdict + at most **three** systemic issues + one table row per story + rewrites for the **worst three only**, then a footer naming what's being withheld (splitting options, full question list, non-story work). Depth is pull, never push. The original skill mandated 8 sections including chapter citations, which on a 30-story PRD produced ~10 pages — i.e. it moved the work instead of doing it. **Do not reintroduce sections, raise the caps, or let the rubric be transcribed into the output.** If editing makes the review longer, it is a regression.
- **Substance over syntax.** The reviewer judges whether a story is true and useful, never template compliance; nonstandard syntax is explicitly not a finding, and wording is not reportable unless it causes real misunderstanding.
- **The causal chain is the analytical spine** (`references/review-rubric.md`): observable system change (team's *zone of control*) → user behaviour change (*sphere of influence*) → business impact. Most findings are a symptom of collapsing it. The rubric is a lookup keyed by gate, not a script to walk aloud.
- **No numeric score, ever** — the pattern of failure matters more than arithmetic, and a score hides the failure *type*. Same reason the plugin refuses to force tasks, NFRs, research, or cross-cutting work into fake user stories.
- **Missing context is a finding, not a blank to fill.** Verdict becomes "Not reviewable yet"; never invent a segment or metric to enable a rewrite.
- References are **per-skill** (`skills/user-story-review/references/`), not plugin-root — correct here because there is only one skill. If a second skill lands and shares them, move them to the plugin root and switch pointers to `${CLAUDE_PLUGIN_ROOT}/references/…`.
- Grounding: *Fifty Quick Ideas to Improve Your User Stories* (Adzic/Evans/Korac). Distilled into the rubric and splitting patterns; the book's chapter list and per-finding chapter citations were **deliberately cut** (they consumed output space and helped no reader). Don't re-add a traceability file or chapter numbers.
- Chains off `prd-workflow` by **filename convention** — it auto-discovers the `PRD-[feature-name].md` that `prd-draft` writes, as the last gate before engineering. Keep that glob working if the PRD filename convention changes.

## writing-review architecture

One skill and one agent, built in the `sales-call-analysis` shape. The idea: **a reviewer detects defects, it does not improve the writing** — five linters and a merge, not five writing experts.

1. `review-writing` — infers the brief (purpose, reader, desired change), confirms it with the user, then spawns one `writing-review:writing-reviewer` (Opus) per reviewer in one message: **reader**, **structure**, **argument**, **evidence**, **prose** (`--only` runs a subset). Reviewers never see each other's output (avoids anchoring). The orchestrator then **merges** — dedupe, root-cause grouping, rank, `Found by:` — and must not review the draft again or add findings.
2. The skill's **Reviewers** section is each agent's whole spec (one paragraph per reviewer); **Findings** is the shared output contract: `[Major|Minor] title` → exact quote → Problem → smallest Fix. No quote, no finding; ≤6 findings per reviewer; repeats collapse into one finding with a count.

- **Precision over recall, scope discipline over coverage.** Keep reviewers orthogonal: overlap is a bug. Don't add reviewers (tone, grammar, hooks, concision…) without repeated evidence from real drafts that none of the five catches a class of problem.
- `references/writing-rules.md` is deliberately short: ~6 Zinsser rules and ~11 AI-writing tells. The prose reviewer flags them only when they cost the reader something, and the plugin's own output follows them. Don't grow it into a style guide or banned-word list.

## Removed plugins

`feature-flow` (the `/ship` engineering-delivery workflow) was removed: `prd-workflow` + the superpowers plugin does the job better. Don't resurrect it.

## Distribution

`main` is the published branch — pushing updates it live for anyone who has added the marketplace. Bump `version` in both the plugin's `plugin.json` and the matching entry in `marketplace.json` when shipping breaking changes to a skill or handoff schema.

## Ignored paths

`.remember/` is Claude session state (logs, tmp). Never commit it. `.DS_Store` is also gitignored. `strategic-research/working/` holds local draft artifacts and should stay out of commits. `design-md-corpus/` (74 real `DESIGN.md` specs) is gitignored grounding data for the `design-system-master` plugin — it is not a plugin and must not be committed or shipped; the plugin distills it into `design-system-master/references/` + `references/exemplars/`. (The `designing-for-behaviour` plugin was similarly distilled from 6 behavioural-science books into its `references/`; that raw grounding was consumed during authoring and is not retained in the repo.)
