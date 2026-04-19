---
name: strategic-synthesis-report
description: Synthesize the four upstream research artifacts (industry-process-map, audience-segment-research, willingness-to-pay-research, competitor-evaluation) into a single self-contained HTML strategic report with executive summary, section-by-section analysis, cross-skill insight connections, and interactive visualizations (tables, matrices, heatmaps, strategy canvas radar, WTP range charts). Use this skill when the user asks to "synthesize the research", "build the final report", "create the strategic report", "compile the research into one doc", "generate the HTML report", "wrap up the plugin", or has completed skills #1–#4 in the strategic-research pipeline and wants the closing artifact. Output is one self-contained HTML file saved to the working folder, plus a short companion markdown summary. Consumes YAML handoffs from the four upstream skills plus their markdown bodies; fails loudly if inputs are missing.
---

# Strategic Synthesis Report

## Promise

Given the four upstream artifacts from the `strategic-research` plugin — `industry-process-map`, `audience-segment-research`, `willingness-to-pay-research`, `competitor-evaluation` — produce **one self-contained HTML file** that a CPO-level reader can open in a browser and use to make an allocation decision in a single sitting.

The HTML report contains:

1. **Executive summary** — Minto pyramid: conclusion first, top 3 strategic bets, then supporting evidence.
2. **Section-by-section analysis** — one section per upstream skill, rendered as tables, matrices, heatmaps, and charts (not prose walls).
3. **Cross-skill synthesis** — the novel value of this skill: the insights that only emerge when segments × WTP × competitors × process map are joined together. Specifically: strategic white space (segment has Leader unmet × WTP band exists × no competitor holds a Power × non-consumption is holding/growing).
4. **Confidence & tension consolidation** — a single view of what we believe, how strongly, and where the map still breaks.
5. **Appendix** — open questions, rejected framings, full evidence roll-up.

This skill does not re-do any research. It is a **compression and connection** skill. If an input handoff is missing, it says so and stops — it does not hallucinate a segment or a WTP band.

## Operating principles

### 1. Minto pyramid or it's not an executive summary

The exec summary leads with the single most decision-relevant sentence. Then the three supporting strategic bets. Then the evidence behind each. A reader who bails after paragraph one should still walk away with the answer. No preambles. No "this report will…". The first sentence tells them what to do.

### 2. Connect — don't just stack

The default failure mode of a synthesis skill is a four-section concatenation with a cover page. That is not synthesis — it's a staple. The cross-skill section is non-optional and must produce insights that **could not appear in any single upstream artifact**. Examples:

| Connection | Mechanism |
|---|---|
| **Strategic white space** | Segment from #2 × Leader outcome from #3 × Power gap from #4 × Non-consumption posture from #4 × Matrix cell from #1 |
| **False-positive segment** | Segment from #2 × WTP variance from #3 — if variance < 2×, the segmentation is too narrow; call it out |
| **Kano migration risk** | Leaders from #3 × competitor coverage from #4 — a delighter about to become must-have that all competitors will have in 12 months |
| **Killer-for-Leader trap** | Killer inventory from #3 × competitor Leaders from #4 — where bundling triggers opposite-direction WTP |
| **Non-consumption posture shift** | Non-consumption evidence from #4 × buying triggers from #2 — is the trigger event getting more common? |

Every cross-skill insight cites the upstream IDs it draws from (segment IDs, WTP band IDs, matrix cell IDs, competitor IDs). Traceability is the audit trail.

### 3. Visualize the matrix, not the prose

Matrices from upstream skills (coverage grid, segment affinity, 7 Powers, strategy canvas, proof-signals) are rendered as **actual visual artifacts** — colored heatmaps, radar charts, range bars — not as markdown tables bolted into HTML. A 7-row × 7-col 7 Powers grid with color intensity for verdict (confirmed → operational lead → asserted → N/A) is read in three seconds. The same data as a markdown table takes two minutes.

Chart taxonomy per section is in `references/visualization-catalog.md`. Read it at the start of Phase 4.

### 4. Confidence is a field, not an adjective

Every claim inherits its confidence from the source handoff. The exec summary states the overall confidence as a percentage. Each strategic bet carries its own confidence. Where two inputs disagree, the synthesis surfaces the tension explicitly — it does not pick a winner silently.

### 5. Self-contained HTML

The report is a single `.html` file. CSS inlined in `<style>`. Charts drawn with Chart.js loaded from a CDN (one `<script>` tag). No external images, no React build step, no server required. A user double-clicks the file and it opens in their browser. Printable-to-PDF is the fallback for offline sharing.

### 6. Fail loudly if inputs are missing

If any of the four handoff YAMLs is missing, the skill does not silently paper over the gap. It writes a stub report with a red warning banner naming which upstream skill has not run and exits. The CPO gets the signal that the research is incomplete, not a false sense of completeness.

## Workflow

Execute in order.

### Phase 1 — Intake & validation

Consume input in this order:

1. **YAML handoff from `competitor-evaluation`** (skill #4) — this is the richest handoff. It already references segment IDs, WTP band IDs, and matrix cell IDs from the upstream skills. If present, use it as the spine.
2. **YAML handoff from `willingness-to-pay-research`** (skill #3) — inherits from #1 and #2. Parse `segments`, `wtp_band`, `proof_signals_matrix`, `cross_segment`.
3. **YAML handoff from `audience-segment-research`** (skill #2) — inherits from #1. Parse `segmentation`, `segments`, `stakeholders`, `cross_segment_tensions`, `global_outliers`.
4. **YAML handoff from `industry-process-map`** (skill #1) — the root. Parse `process_tree`, `matrix`, `substitutes`, `anchor_coverage`.
5. **The four markdown bodies** — for quotes and inline evidence that don't survive the YAML compression.

Validation:

- [ ] Are all four YAML handoffs present? If not, which is missing?
- [ ] Do segment IDs in #3 and #4 match IDs declared in #2?
- [ ] Do matrix cell IDs in #4 match cells declared in #1?
- [ ] Does the anchor name match across all four?
- [ ] Is any `version` field a major bump from the schema this skill was built against?

If any check fails, halt and write the stub warning report (see Phase 7 fallback).

Ask clarifying questions with `AskUserQuestion` only when the handoffs leave a real ambiguity — for instance, if the user wants a specific audience framing (investor, board, internal-exec) that changes tone. Cap at 2 questions. If the handoffs are complete, skip straight to Phase 2.

### Phase 2 — Build the executive summary

The executive summary is the hardest section. Write it last, but frame it first so the rest of the report stays pointed at it.

Executive summary structure (Minto):

| Component | Content | Length |
|---|---|---|
| **Top-line recommendation** | One sentence: the allocation decision implied by the research. | 1 sentence |
| **Confidence** | Overall confidence as a percentage, with the single largest evidence gap named. | 1 sentence |
| **Top 3 strategic bets** | Each bet names: the segment, the Leader outcome, the competitive mechanism, and the confidence %. | 3 bullets |
| **Top 3 risks** | Each risk names: the mechanism, the specific trigger, and the upstream evidence. | 3 bullets |
| **What we know vs. what we're still missing** | Evidence-quality honesty. | 2 sentences |

Rule: if the exec summary can be copy-pasted into any other strategic report, it is too generic. It must reference specific segments, specific Leaders, specific competitors, specific matrix cells. Specificity is the proof of work.

### Phase 3 — Build section-by-section analyses

One section per upstream skill. Each section follows the same three-part structure:

1. **What we learned** — the 3–5 sentences of findings, Minto-ordered.
2. **The key visual** — the one chart or matrix that most compresses the section's evidence.
3. **Supporting detail** — tables, per-segment cards, or per-competitor profiles rendered with visual hierarchy (not as undifferentiated markdown tables).

Per-section chart expectations are in `references/visualization-catalog.md`. At minimum:

| Upstream skill | Required visuals |
|---|---|
| `industry-process-map` | Process tree (HTML tree) + matrix heatmap (maturity + anchor-coverage) |
| `audience-segment-research` | Segment cards grid + stakeholder map per segment + adjacency/cannibalization grid |
| `willingness-to-pay-research` | WTP range chart per segment (low–high bars) + Leaders/Fillers/Killers table per segment + Kano classification chart + proof-signals strength radar |
| `competitor-evaluation` | Coverage grid heatmap + segment affinity matrix heatmap + 7 Powers grid heatmap + strategy canvas radar (per strategic group) + threat ranking |

### Phase 4 — Build the cross-skill synthesis (the new value)

This is where the skill earns its place. Four sub-sections:

**4.1 Strategic white space** — produced by joining:

- `industry-process-map.matrix.cells` where `anchor_plays_here = false`
- `audience-segment-research.segments` where pain intensity is high
- `willingness-to-pay-research.segments.value_layer.leader_outcomes` where `opportunity_score ≥ 10`
- `competitor-evaluation.seven_powers_grid.power_gaps` (nobody holds the Power)
- `competitor-evaluation.non_consumption_posture` (holding or growing = runway)

Render as a ranked table: each row is a white-space hypothesis, columns are the five inputs it draws from, plus a synthesized confidence score (weighted average of contributing confidences, capped by the lowest).

**4.2 Segment × WTP × Competitor winning-factor join** — one matrix where:

- Rows = segments (from #2)
- Columns = Leader outcomes + WTP band (from #3)
- Cells = which competitor covers this Leader for this segment, which 7 Power they hold on it, and what the anchor's position is

This makes the competitive picture per segment, per Leader legible in one view — the key blind spot of single-skill reports.

**4.3 Kano migration watchlist × competitor roadmap** — cross-reference:

- `willingness-to-pay-research.cross_segment.kano_migration_watchlist` (delighters becoming must-haves)
- `competitor-evaluation.winning_factors_ledger` (what competitors already have)

Flag: any delighter currently held only by a Power-light competitor that is expected to become a must-have in < 12 months → category commoditization risk.

**4.4 Non-consumption trajectory × segment urgency** — cross-reference:

- `competitor-evaluation.non_consumption_posture` + `non_consumption_evidence`
- `audience-segment-research.segments.buying_triggers`

If non-consumption is growing and trigger events are common, this is a category-creation opportunity. If non-consumption is shrinking and triggers are rare, the category is maturing — positioning must shift from education to displacement.

Every cross-skill cell must cite the upstream IDs it joins. The citations are the audit trail.

### Phase 5 — Build the confidence & tension consolidation

Three consolidated views:

1. **Confidence pyramid** — highest to lowest: claims with ≥3 behavioral sources, claims with 1–2 behavioral, claims pattern-only, claims stated-only. Counts per tier.
2. **Tension log** — union of `tensions_global` from #4, `cross_segment_tensions` from #2 and #3, and any newly surfaced tensions from the cross-skill join. Classified, not resolved.
3. **Evidence-quality traffic light** — per upstream skill: green / amber / red based on behavioral ratio, primary-sources-distinct, and disconfirming searches performed.

### Phase 6 — Build the HTML file

Use `assets/html-template.html` as the scaffold. The template ships with:

- Self-contained CSS (design-system styles for cards, tables, heatmaps, KPIs)
- Chart.js via CDN (one `<script>` tag)
- Placeholder sections (`<section id="exec-summary">` etc.) that the skill fills in
- Heatmap CSS utility classes (`.heat-1` through `.heat-5`)
- Strategy-canvas radar helper (`renderStrategyCanvas(canvasId, factors, series)`)
- WTP range-chart helper (`renderWTPRanges(canvasId, segments)`)

Read `references/html-template-guide.md` before starting to generate the file. It covers:

- How to inject data into the template
- Color palette for matrices (sequential for maturity/strength, diverging for affinity)
- Accessibility notes (color + icon for color-blind readers)
- Print-layout CSS breaks
- Mobile responsiveness

Write the HTML artifact to `/sessions/adoring-cool-cray/mnt/tempSkills/strategic-synthesis-[slug].html` where `[slug]` is a kebab-case tag of the anchor or industry.

Also write a companion 1-page markdown summary to `/sessions/adoring-cool-cray/mnt/tempSkills/strategic-synthesis-[slug].md` — the same exec summary, for reading in terminal / Slack.

### Phase 7 — Share (or fail gracefully)

**Happy path:** Link the HTML file with a `computer://` link. Message: title, one-sentence summary of the top recommendation, confidence %, link. Do not restate content in chat.

**Fallback (inputs missing):** Write a stub HTML report with a red warning banner. The banner names which upstream skill has not run and links to that skill. The body contains whichever sections *can* be populated from the partial inputs. Link the stub with the `computer://` link and a message that explicitly says what is missing.

## Quality audit — mandatory before Phase 6

Run these checks explicitly. Fix any failure before writing the HTML.

- [ ] Exec summary leads with a single-sentence recommendation (Minto).
- [ ] Every strategic bet in the exec summary cites at least 2 upstream IDs (segment, Leader, competitor, matrix cell, or Power).
- [ ] Every cross-skill insight cites at least 2 upstream skills' IDs.
- [ ] No section is a markdown-table dump — every section has at least one genuine visual (chart, heatmap, or styled matrix).
- [ ] Confidence is rendered as a percentage everywhere, never as hedge words.
- [ ] Every tension from upstream tension logs is preserved in the consolidated log.
- [ ] White-space hypotheses each name: segment, Leader, Power gap, matrix cell, non-consumption posture.
- [ ] HTML passes the `double-click test`: file opens in a browser with no broken chart, no missing script, no console error.
- [ ] Print stylesheet is present (`@media print` block) and tested mentally (no fixed-position overlays, no color-only distinctions).
- [ ] Any missing upstream input triggers the fallback stub — no silent gaps.

## Writing style

- **Minto everywhere.** Conclusion sentence first. Supporting sentences second. Data third.
- **No hedge words.** "Arguably", "somewhat", "in some sense" are banned. Replace with a confidence %.
- **Specific citations.** `[s1-high-volume-agencies]` beats "high-volume agencies". IDs thread through the whole report.
- **Tables and visuals over prose.** Prose only where a connection needs explanation.
- **Verbs in headings and labels.** "Own the briefing cadence" beats "Briefing cadence ownership".
- **One sentence per bullet.** Bullets longer than a sentence either become a sub-bullet list or become a paragraph.
- **Confidence on every claim.** Inline as `(72%)` after the claim or as a column in tables.

## When this skill is the wrong tool

| User wants | Use |
|---|---|
| Map the space (processes, workflow) | `industry-process-map` (skill #1) |
| Segment the audience and map stakeholders | `audience-segment-research` (skill #2) |
| Willingness-to-pay / pricing sensitivity | `willingness-to-pay-research` (skill #3) |
| Classified competitive set + 7 Powers + strategy canvas | `competitor-evaluation` (skill #4) |
| A PRD grounded in this synthesis | `pm-sage:write-prd` (feed it the cross-skill section) |
| Positioning canvas from this synthesis | `pm-sage:position-product` (feed it the segments + Leaders + alternatives) |
| A board update from this synthesis | `product-management:stakeholder-update` (feed it the exec summary) |

This skill compresses, connects, and renders. It does not research. It does not decide. It equips the decider.
