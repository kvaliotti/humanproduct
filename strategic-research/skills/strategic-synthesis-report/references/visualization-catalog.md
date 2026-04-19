# Visualization Catalog

The rule: **one visual = one insight**. A chart that answers no specific question is noise. This catalog maps each upstream data structure to the visual that reads fastest.

## Section-by-section

### Section 2 — Industry Process Map

| Visual | Data source | Why this visual | Pitfall to avoid |
|---|---|---|---|
| **Process tree** | `process_tree` (nested steps) | Hierarchy is the native shape of the data; any other rendering flattens it | Don't render as a flat bullet list — the reader loses the step → sub-step relationship |
| **Matrix heatmap** | `matrix.cells` with `maturity` and `anchor_plays_here` | Two dimensions of information per cell (maturity + anchor coverage) — color + border reads both in a glance | Don't use raw markdown table — maturity disappears without color |
| **Substitute list** | `substitutes` | A simple `<ul>` is faster to read than a chart with 3 items | Don't chart what is legible as text |

### Section 3 — Audience & Segments

| Visual | Data source | Why | Pitfall |
|---|---|---|---|
| **Segment cards grid** | `segments[*]` | Each segment has ~8 fields; cards let the reader compare field-by-field across cards | Don't render as a markdown table — cells become unreadable for 250-word profiles |
| **Stakeholder map table** | `segments[*].stakeholders` | Same columns (user/champion/buyer/blocker/renewer) across all segments = table is natural | Don't draw org-chart tree — stakeholders aren't hierarchical, they are roles |
| **Shared vs. divergent jobs** | `cross_segment.shared_jobs` + `divergent_jobs` | Two parallel lists side-by-side make the contrast legible | Don't merge into one list with asterisks — contrast is lost |

### Section 4 — Willingness-to-Pay

| Visual | Data source | Why | Pitfall |
|---|---|---|---|
| **WTP range chart** (horizontal floating bars) | `segments[*].wtp_band.low_usd` + `high_usd` | Range is a range, not a point; floating bars with midpoint marker communicate both the range and the center | Don't use a line chart — WTP is not a time series |
| **Leaders / Fillers / Killers table** | `segments[*].value_layer` | Three parallel columns per segment — compact comparison | Don't merge — Killers are diagnostic, they belong in their own column |
| **Kano stacked bar** (per segment) | `segments[*].value_layer.leader_outcomes[*].kano_class` | Segment = x axis; Kano class counts = stacked bar; migration risk is visible in the delighter band | Don't use pie charts — multiple pies are impossible to compare |
| **Proof signals radar** | `proof_signals_matrix[*].strength_scores` | Four axes (vividness/speed/travelability/defensibility) = natural radar; 5–7 series is the sweet spot | Don't go past 7 series — radar becomes spaghetti |
| **Proof signals table** | Same source | Supplements the radar with the specific signal text and UX placement — data you can't read off a chart | Don't rely on radar alone — it shows strength but not the signal itself |

### Section 5 — Competitor Evaluation

| Visual | Data source | Why | Pitfall |
|---|---|---|---|
| **Classified set table** | `competitors[*]` with `class` | Class is categorical and a table lets you group visually by class | Don't visualize as a bar chart — the classes aren't ordered |
| **Coverage grid heatmap** | `competitors[*].coverage` cross matrix cells | Two-dimensional coverage map (cells × competitors) — pattern of who covers what is the insight | Don't render as per-competitor bar lists — cross-competitor pattern disappears |
| **Segment affinity matrix** (diverging color scale) | `competitors[*].segment_affinity` | Diverging scale (strong→antagonistic) + anchor's position per cell = one of the most decision-relevant views in the report | Don't use a single-hue scale — diverging is correct because antagonistic is qualitatively different from absent |
| **7 Powers grid** | `competitors[*].seven_powers` | 7 × N table where each cell is one of 5 verdicts = categorical heatmap | Don't summarize as a "moat score" — the 7 powers are qualitatively different |
| **Strategy canvas radar** (per strategic group) | `strategy_canvases[*]` | Factors of competition × 0–5 offer intensity = canonical radar; overlay anchor as dashed line | Don't use one canvas for all competitors — convergence is hidden |
| **Threat ranking table** | `threat_ranking` | Ranked list with mechanism + detail = table is natural | — |
| **Non-consumption pill + evidence block** | `non_consumption_posture` + `non_consumption_evidence` | Categorical (shrinking/holding/growing) = pill; evidence is text | Don't hide in a footnote — posture shift rewrites the GTM |

### Section 6 — Cross-Skill Synthesis

| Visual | Data source | Why | Pitfall |
|---|---|---|---|
| **White-space cards** (ranked) | Join of 5 upstream fields | Each hypothesis has structured sub-fields (segment, Leader, Power gap, matrix cell, non-consumption) — card renders all five without a table's visual noise | Don't collapse to a bullet list — the structure is the value |
| **Segment × Leader × Competitor join matrix** | Join of #2, #3, #4 | The synthesis section's key artifact — one table shows the whole story per segment | Don't split into three tables — joining is the point |
| **Kano migration × competitor roadmap table** | `kano_migration_watchlist` × `winning_factors_ledger` | Time-and-coverage combination = table with horizon and commoditization-risk columns | Don't chart horizon as a timeline — the reader needs to scan per-feature, not per-month |
| **Non-consumption trajectory table** | `non_consumption_posture` + `segments[*].buying_triggers` | Segment-by-segment, qualitative | — |

### Section 7 — Confidence & Tensions

| Visual | Data source | Why | Pitfall |
|---|---|---|---|
| **Confidence pyramid KPI cards** | Roll-up counts of evidence tiers | Four KPIs, one per tier = fastest-reading summary | Don't render as pie chart — pies hide the absolute counts |
| **Traffic-light table** | Per-skill evidence quality | Small table with a green/amber/red grade cell per skill | — |
| **Tension log table** | Union of upstream tension logs | Preserves claim-A, claim-B, class, resolution per row | Don't "resolve" tensions in the synthesis — hold them visible |

## Color semantics (must remain consistent)

| Meaning | Color token | Used in |
|---|---|---|
| Sequential intensity (0 = absent → 5 = mature) | `--heat-0` … `--heat-5` | Matrix maturity heatmap, coverage grid |
| Diverging affinity (antagonistic ← absent → fit → strong) | `--aff-anti` / `--aff-absent` / `--aff-weak` / `--aff-fit` / `--aff-strong` | Segment affinity matrix |
| Categorical verdict (confirmed / partial / operational / asserted / N/A) | `--verdict-*` | 7 Powers grid |
| Good / warn / bad (traffic light) | `--good / --warn / --bad` | Confidence pills, evidence traffic light, risk cards |

Do not invent new colors ad hoc. Adding a new semantic needs a new token in the `:root` block.

## Chart count budget

A strategic synthesis report should have **6–10 charts** total. More than that and the reader drowns; fewer than that and you're leaving insight on the table.

Minimum required charts:

- WTP range chart (section 4)
- Kano stacked bar (section 4)
- Proof signals radar (section 4)
- At least one strategy canvas radar (section 5)

Everything else can be styled tables and cards. A markdown table dropped into HTML is still readable; a missing chart in a required slot is not.

## When a visualization doesn't fit the data

Some handoffs will be thin. If a chart would have 1–2 data points, **skip the chart and render the data as text**. A 2-bar chart is a lie by decoration. The rule: if the reader can grasp the data from 20 words, no chart is needed.

If a handoff is missing (fallback stub case), render the chart canvas as the placeholder with a `<p class="dim">Unavailable — requires [skill] to be run.</p>` message. Do not render an empty chart.
