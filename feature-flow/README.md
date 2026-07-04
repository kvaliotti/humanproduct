# feature-flow

An end-to-end feature-delivery workflow for Claude Code. One command takes a feature from a rough description to an open PR — sequencing the pieces you already have (plan approval, subagents, `/code-review`, `/simplify`, commit/PR) behind a lean, consistent spine.

```
/ship <feature description> [--step] [--auto] [--micro|--big]
```

## The pipeline

```
branch/isolation → design (storm) → plan → ⛱ APPROVAL GATE
   → implement → test → verify → review+simplify → PR → finish
```

- **Autonomous after plan approval** (default): approve the plan once, then it runs to PR without pausing — halting only when a **stop-condition** fires. `--step` pauses at every stage.
- **Model-tiered**: a strong model authors the plan (the contract); a cheaper model implements against it; verify + review wrap it. The cost saving is real because the plan and the verify gate are strong.
- **Subagent-driven**: implementation is pushed out of the orchestrator to implementer subagents (Task tool) so the main session's context stays clean for planning, gating, and debugging. Coupled work goes to one subagent in a coherent thread; genuinely independent, disjoint-file tasks go to parallel subagents (multiple Task calls in one message). Inline editing is reserved for the rare truly-trivial change.

## Components

| Component | Role |
|---|---|
| `skills/ship` | Orchestrator — the `/ship` entry point; sequences the stages and enforces the gates. |
| `skills/storm` | Stage-1 design — brainstorm spine + a compact product lens (situation, behavior, don't-know/don't-want/can't, edge cases). Big + micro modes. |
| `skills/verify` | Evidence-based verification gate — runs the right subset by what changed and pastes real output. |
| `skills/debug` | Root-cause debugging — confirm intended behavior (ask if unsure), find the root cause, then fix at the source. Invoked when verify fails or a bug appears; also usable standalone. |
| `references/stop-conditions.md` | What "major" means → when autonomous mode halts and asks. |
| `references/test-policy.md` | Per-task test policy: invariant-critical → test-first, feature → test-after, trivial → none. |
| `references/squash-safe-finish.md` | Detect merges by PR state, not SHA (fixes the squash "did it merge?" trap). |
| `config/feature-flow.config.example.md` | Copy into a repo as `.claude/feature-flow.local.md` to tune behavior. |

## Setup

1. Install the plugin (e.g. `claude --plugin-dir /path/to/feature-flow`, or add to a marketplace).
2. In each project, copy `config/feature-flow.config.example.md` to `.claude/feature-flow.local.md` and tune the verify commands, test policy, stop-conditions, and PR settings. `/ship` offers to create this for you on first run.

## Design notes

- **Generic spine, per-repo config**: no project specifics are hardcoded — gates and tripwires come from `.claude/feature-flow.local.md`.
- **The plan is the contract**: it's the human approval boundary that makes autonomy safe, the decomposition that enables parallelism, and the artifact implementer and reviewer both check against.
- **Reuse over rebuild**: `/ship` leans on native plan approval, `/code-review`, `/simplify`, and `commit-commands` rather than reimplementing them.
