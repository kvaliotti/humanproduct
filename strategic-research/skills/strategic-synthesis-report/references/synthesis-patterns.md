# Synthesis Patterns — Connecting Across Skills

The cross-skill synthesis section earns this skill's place in the pipeline. Without it, the report is four artifacts with a cover page.

This reference catalogs the joins that matter. Each pattern has: what it is, which upstream fields it joins, how to rank results, and what the output looks like.

---

## Pattern 1 — Strategic white space (the flagship)

**What it is.** A segment where a Leader outcome has high opportunity score, a WTP band exists, no competitor holds a 7 Power on that outcome, the matrix cell is underserved, and non-consumption is holding or growing.

**Upstream joins.**

| Input | Field | Signal |
|---|---|---|
| `audience-segment-research` | `segments[i]` with high `pains_unmet_needs.pain_intensity` | Demand side |
| `willingness-to-pay-research` | `segments[i].value_layer.leader_outcomes[j].opportunity_score` ≥ 10 | WTP side |
| `willingness-to-pay-research` | `segments[i].wtp_band.low_usd`/`high_usd` | Monetization viability |
| `competitor-evaluation` | `seven_powers_grid.power_gaps` (Powers no one holds) | Competitive side |
| `competitor-evaluation` | `non_consumption_posture` = holding or growing | Runway side |
| `industry-process-map` | `matrix.cells` with `maturity` = emerging or underserved | Structural side |

**Ranking.** Score each candidate on:

| Weight | Criterion |
|---|---|
| 30 | Opportunity score on the Leader outcome |
| 25 | WTP band midpoint × share of addressable |
| 20 | Number of Power gaps exploitable on the outcome |
| 15 | Maturity of matrix cell (lower = more runway) |
| 10 | Non-consumption trajectory (growing = +10, holding = +5, shrinking = 0) |

Total 100. Cap the output at **3–5 ranked hypotheses**. Lower-scoring ones go into the appendix.

**Output shape.** A ranked list of `ws-card` HTML blocks (see `html-template-guide.md`).

**Failure mode.** The hypotheses end up generic ("underserved PMs want automation"). Fix: every hypothesis names the specific segment ID, the specific Leader outcome, and the specific matrix cell. Specificity = proof of work.

---

## Pattern 2 — Segment × Leader × Competitor join

**What it is.** One table where each row = one segment's top Leader outcome, and columns capture: WTP band, which competitor covers the Leader, which 7 Power that competitor holds on it, and the anchor's position.

**Upstream joins.**

| Input | Field |
|---|---|
| `audience-segment-research` | `segments[i].id`, `.name` |
| `willingness-to-pay-research` | `segments[i].value_layer.leader_outcomes[top 1]`, `segments[i].wtp_band` |
| `competitor-evaluation` | `competitors[*].lfk_lens.leaders_covered` (match outcome), `competitors[*].seven_powers` (on that Leader) |
| `competitor-evaluation` | For each cell: anchor's position (deduced from `segment_affinity[*].anchor_position` where the Leader is the decisive factor) |

**Ranking.** Order rows by WTP band high_usd descending. Highest WTP segment × Leader first. This puts the most valuable whitespace or most threatening competition at the top of the table.

**Output shape.** Single compact table with 6 columns.

**Example row.**

| Segment | Top Leader | WTP band | Covered by | Power held | Anchor position |
|---|---|---|---|---|---|
| s2-mid-market-ua | Predictive LTV per cohort | $4k–$10k/mo | AppsFlyer (strong) | Switching costs (confirmed) | Losing — no cohort model |

**Failure mode.** Empty cells everywhere. This means the upstream LFK lens in skill #4 wasn't populated against skill #3's Leaders. Go back and cross-reference before writing.

---

## Pattern 3 — Kano migration × competitor roadmap

**What it is.** Delighters today that will become must-haves in < 24 months. If competitors are already shipping them, the anchor's current differentiation is about to commoditize.

**Upstream joins.**

| Input | Field |
|---|---|
| `willingness-to-pay-research` | `cross_segment.kano_migration_watchlist[*]` (feature, currently, expected, horizon) |
| `competitor-evaluation` | `winning_factors_ledger[*]` — which competitors already ship the feature |
| `competitor-evaluation` | `seven_powers_grid` — whether they hold a Power on it (commoditization-proof if yes) |

**Ranking.** Sort by horizon ascending (near-term commoditization first). Compute commoditization risk:

- High: horizon ≤ 12 months AND 2+ competitors already ship AND no Power held
- Medium: horizon ≤ 24 months AND 1 competitor ships
- Low: horizon > 24 months OR no competitor ships

**Output shape.** Table with commoditization-risk pill per row.

**Failure mode.** Every row is flagged high-risk → the report looks alarmist. Fix: verify horizon estimates; Kano migration estimates ≤ 12 months are rare in reality. Bias toward medium.

---

## Pattern 4 — Non-consumption trajectory × trigger-event frequency

**What it is.** Non-consumption posture from skill #4 joined with buying-trigger frequency from skill #2. If non-consumption is growing and triggers are common, category-creation opportunity. If shrinking and triggers rare, maturity — positioning shifts from education to displacement.

**Upstream joins.**

| Input | Field |
|---|---|
| `competitor-evaluation` | `non_consumption_posture` (shrinking / holding / growing) |
| `competitor-evaluation` | `non_consumption_evidence` (specific text) |
| `audience-segment-research` | `segments[i].buying_triggers` (event list) |
| Inferred | Frequency: how often do triggers fire per segment? (hypothesize from language — "weekly sprint planning" = high, "once-every-funding-round" = low) |

**Output shape.** Table: segment × triggers × frequency × non-consumption posture × implication.

**Implication column.** Four archetypes:

| Non-consumption | Trigger frequency | Implication |
|---|---|---|
| Growing | High | **Category creation** — education GTM, land with adjacent tool |
| Growing | Low | **Latent market** — wait for trigger or force it |
| Holding | High | **Displacement** — beat the workaround head-on |
| Holding | Low | **Thin segment** — deprioritize |
| Shrinking | High | **Consolidating** — ride the maturing wave, compete on differentiation |
| Shrinking | Low | **Saturated** — avoid |

**Failure mode.** All segments get "displacement". Fix: segment-by-segment reasoning, not averaged.

---

## Pattern 5 — Killer-for-Leader trap (packaging)

**What it is.** A feature that is a Killer for segment A (reduces WTP) but a Leader for segment B. Bundling both in one SKU destroys segment A's purchase; unbundling opens two clean offers.

**Upstream joins.**

| Input | Field |
|---|---|
| `willingness-to-pay-research` | `cross_segment.killer_inventory[*].killer_for` + `.leader_for` |

**Output shape.** Table: feature × killer_for segments × leader_for segments × packaging implication (separate SKU / quarantine / remove).

**When to surface.** Only if `killer_inventory` is non-empty. This pattern often reveals packaging decisions, not product decisions.

---

## Pattern 6 — False-positive segmentation

**What it is.** If WTP variance across segments is < 2×, the segments are actually one segment in disguise. The synthesis surfaces this and recommends either re-segmentation or acceptance of a single-segment strategy.

**Upstream joins.**

| Input | Field |
|---|---|
| `willingness-to-pay-research` | `cross_segment.wtp_variance_ratio` |
| `audience-segment-research` | `segmentation.scores` (to see which criterion is the weakest) |

**Output shape.** Single-paragraph finding in the cross-skill section, with a flag in the exec summary.

---

## Pattern 7 — Process-map white cell × segment pain intensity

**What it is.** Matrix cells from skill #1 that are marked `underserved` and that correspond to a pain in a high-opportunity segment from skill #2.

**Output shape.** Short table of underserved cells × segments × pains × confidence.

**When to surface.** When skill #1's `maturity` field flags underserved cells. This pattern is often redundant with Pattern 1 — use it only if Pattern 1 didn't surface a cell.

---

## Anti-patterns (don't do these)

| Anti-pattern | Why it's wrong |
|---|---|
| Average WTP across segments into one number | Segments exist precisely because WTP varies. Averaging erases the value of skill #3. |
| Show only the anchor on the strategy canvas | The anchor is only interesting *relative to* the strategic group. Omit the group and the canvas is a waste. |
| Declare a white space without a Power gap | If the Power is held by any competitor, there is no structural white space — only a near-term product gap. |
| Hide tensions in prose | The tension log is the audit trail. Prose hides contradictions; the log preserves them. |
| Cite upstream skills by name, not by ID | "From the audience research" is not traceable. "From s2-mid-market-ua" is. |

---

## The closing test

After writing the cross-skill section, ask: **could any of these insights have been produced by any single upstream skill alone?** If yes, the insight is not a synthesis — it's a restatement. Cut it and find the joins.
