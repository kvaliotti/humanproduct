# Industry Process Map — {anchor_or_industry}

## Framing

| Field | Value |
|---|---|
| **Anchor** | {anchor product/company, or "none"} |
| **Industry** | {short industry name} |
| **End-user persona** | {role the map is taken from} |
| **Scope boundary** | {one-sentence scope note} |
| **Generated** | {date} |

## Process tree

The end-user's workflow, decomposed. Labels are user verbs.

1. {Top-level step}
   1. {Sub-step}
   2. {Sub-step}
      1. {Sub-sub-step if needed}
2. {Top-level step}
   1. {Sub-step}

## Chosen matrix framing

**{Rows axis name} × {Columns axis name}**

One-paragraph rationale for why this framing won over the alternatives. What does this framing surface that the losers hide? What structural insight does it make legible?

## The matrix

|   | {Col 1} | {Col 2} | {Col 3} | {Col 4} |
|---|---|---|---|---|
| **{Row 1}** | Approach: {...}<br>Tools: {...}<br>Maturity: {...}<br>Anchor: ✓/✗ | ... | ... | ... |
| **{Row 2}** | ... | ... | ... | ... |

Legend: ✓ = anchor product plays here. ⊙ = anchor's adjacent/partial coverage. Blank = anchor does not cover.

## Glossary

| Term | Definition |
|---|---|
| {term} | {short, user-facing} |

Include only terms that would be opaque to an outsider but are everyday language for the persona.

## Substitutes & adjacent approaches

What users do *instead* of buying a tool in the obvious category.

- **Manual / spreadsheet:** {description}
- **Agency / consultancy:** {description}
- **In-house build:** {description}
- **Adjacent tool repurposed:** {description}
- **Do nothing / tolerate:** {description}

## Anchor coverage map

*(Include only if an anchor was given.)*

| Coverage | Cells |
|---|---|
| **Direct** | {list of "row × column" cells} |
| **Adjacent / partial** | {list} |
| **Not covered** | {list — these are white space or out-of-scope} |

One paragraph: where is the anchor strong? Where is it narrow? What would a broader end-user view expect the anchor to cover that it doesn't?

## Open questions & calibration notes

Questions that the next skill (user/customer analysis) should probe. Also, things that were uncertain in research and need user/expert validation.

1. {Question}
2. {Question}
3. {Question}

## Appendix — Rejected matrix framings

The 2-3 candidates considered and rejected. Evidence that the final choice was made with alternatives in view.

### Rejected Framing A — {rows × columns}
- Score: {MECE}/5, {Coverage}/5, {Actionability}/5, {End-user grounding}/5
- Why rejected: {one line}

### Rejected Framing B — {rows × columns}
- Score: {...}
- Why rejected: {one line}

### Rejected Framing C — {rows × columns}
- Score: {...}
- Why rejected: {one line}

## Handoff block

```yaml
# industry-process-map handoff
version: 1
generated_at: {ISO-8601 date}

framing:
  anchor: {name or null}
  industry: {name}
  end_user_persona: {name}
  scope_boundary: {sentence}

process_tree:
  - step: {top-level}
    sub_steps:
      - {sub-step}
      - {sub-step}

matrix:
  horizontal_axis: {name}
  vertical_axis: {name}
  rows: [{r1}, {r2}]
  columns: [{c1}, {c2}]
  cells:
    - row: {r1}
      column: {c1}
      approaches: [{a1}, {a2}]
      notable_tools: [{t1}]
      maturity: {commodity|established|emerging|manual|underserved}
      anchor_plays_here: {true|false}
      notes: {optional}

glossary:
  - term: {term}
    definition: {definition}

substitutes:
  - {s1}
  - {s2}

rejected_framings:
  - horizontal_axis: {name}
    vertical_axis: {name}
    score: {total}
    why_rejected: {reason}

open_questions:
  - {q1}
  - {q2}

anchor_coverage:
  covered_cells: [{"r1 | c1"}]
  adjacent_cells: []
  not_covered_cells: []
```
