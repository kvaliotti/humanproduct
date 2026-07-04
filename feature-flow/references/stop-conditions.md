# Stop-conditions — when autonomous mode must halt and ask

In `auto` mode `/ship` runs implement → PR without pausing. That is only safe because it **stops and asks the human** the moment it hits something that changes the shape of the work or carries outsized risk. If any of these fire, STOP, summarize what you found, and wait for direction — do not decide unilaterally.

## Default stop-conditions (generic)

- **New capability or primitive** — the feature needs something that doesn't exist yet: a new entity/table, a new subject type, a custom renderer, or a branching/stateful workflow.
- **Schema or data migration** — any DB schema change, migration, or backfill.
- **Auth / billing / security / money surface** — anything touching authentication, authorization, payments, credits, or secrets.
- **Plan ambiguity** — the plan can be read two ways, or a task can't be implemented as written without a guess that materially affects behavior.
- **Scope expansion** — the work turns out larger than the approved plan (new tasks, new surfaces).
- **Repeated failure** — `retry_budget` exhausted on a task (default 3 failed fix attempts). Per the `debug` skill, 3+ failures signals a wrong approach/architecture, not another fix.
- **Destructive or outward-facing action** — deleting data, force-pushing, mutating remote/prod state, or anything hard to reverse.

## Extending per repo

A project's `.claude/feature-flow.local.md` `stop_conditions` list is **added** to these — never replaces them. Put project-specific tripwires there (e.g. "touches the LLM prompt/eval config", "renames a queue topic", "edits a large JSON/JSONB column").

## How to surface

Report: which condition fired, the specific task/finding that triggered it, and 1–2 concrete options for how to proceed. Then wait.
