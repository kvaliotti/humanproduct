# YAML Handoff Schema

The YAML block at the end of the output is the contract between this skill and downstream skills in the strategic-research plugin (user/customer analysis, competitive analysis, positioning, gap analysis).

Downstream skills parse the block and use it as the map of the space. Break the schema and you break the pipeline.

## Schema

```yaml
# industry-process-map handoff
version: 1
generated_at: <ISO-8601 date>

framing:
  anchor: <product/company name, or null if none given>
  industry: <short industry name>
  end_user_persona: <role/persona the map is anchored on>
  scope_boundary: <one-sentence scope note>

process_tree:
  # Top-level workflow steps with nested sub-steps.
  # Depth can be 2-3 levels. Keep labels as user verbs.
  - step: <top-level step>
    sub_steps:
      - <sub-step>
      - <sub-step>
  - step: <top-level step>
    sub_steps: []

matrix:
  horizontal_axis: <name of row axis, e.g., "Process step">
  vertical_axis: <name of column axis, e.g., "Channel">
  rows:
    - <row label>
    - <row label>
  columns:
    - <column label>
    - <column label>
  cells:
    # Each cell is keyed by "row | column"
    - row: <row label>
      column: <column label>
      approaches: [<approach 1>, <approach 2>]
      notable_tools: [<tool 1>, <tool 2>]
      maturity: <commodity | established | emerging | manual | underserved>
      anchor_plays_here: <true | false>
      notes: <optional short note>

glossary:
  - term: <term>
    definition: <short, user-facing definition>

substitutes:
  # What users do *instead* of tools in the obvious category
  - <substitute 1>
  - <substitute 2>

rejected_framings:
  # The candidates that lost, kept for auditability
  - horizontal_axis: <...>
    vertical_axis: <...>
    score: <total score>
    why_rejected: <one-line reason>

open_questions:
  # Things the next skill (user/customer analysis) should probe
  - <question>
  - <question>

anchor_coverage:
  # Only if an anchor was given
  covered_cells: [<"row | column">]
  adjacent_cells: [<"row | column">]
  not_covered_cells: [<"row | column">]
```

## Validation checklist

Before finalizing, verify:

- [ ] Every row listed in `matrix.rows` has at least one corresponding entry in `matrix.cells` per column (or is explicitly marked as empty/underserved).
- [ ] `process_tree` top-level steps match `matrix.rows` (or are a superset — the matrix may use a coarser grain than the tree).
- [ ] `rejected_framings` has 2-3 entries. If it has 0, the skill didn't actually compare alternatives.
- [ ] `substitutes` is non-empty. If empty, the map is incomplete (user always has a substitute: do nothing).
- [ ] `open_questions` has at least 3 items. This is the runway for skill #2.

## Why this schema matters

Downstream skills need:
- A stable row/column structure to annotate with pains and jobs
- Substitutes to reason about non-consumption and switching costs
- Open questions to scope user interviews
- Anchor coverage to reason about fit and white space

Changing the schema breaks downstream parsing. If a field needs to change, bump `version` and document the breaking change.
