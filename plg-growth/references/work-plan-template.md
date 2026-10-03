# Work plan format

Used when a skill is asked for a work plan. The calling skill supplies the issue-tree branches and metrics.

## Pick the format from the situation

| Situation | Format |
|---|---|
| Direction unclear, early stage | **Objective → strategies → tactics.** One measurable objective, 2–3 strategies each with a hypothesis, tactics with owner and date. |
| Has data, needs to test changes | **Experiment backlog.** Ranked by expected impact, then effort. |
| Must learn before deciding | **Research plan.** Questions, method, who, and which decision each answer unlocks. |

## Each work item

```
### [Short title]
Branch: [issue-tree branch]   Type: research | analysis | decision | experiment | ops
Hypothesis: We believe [X] because [Y].
Metric: [what it moves] — Success: [threshold] — Guardrail: [what must not drop]
Priority: P1/P2/P3   Timeline: [weeks]   Depends on: [what must be true first]
```

## Rules

- Priority comes from sensitivity on the driver tree, not ease. P1 items can start now with no open dependencies.
- Mix work types. All experiments with no research, or all research with no decision, is a smell.
- Experiments name the audience and how long they must run to read a result.
- If the metric isn't instrumented, instrumentation is an explicit item.
- Scope to 6–8 weeks. A six-month list is a wishlist.
