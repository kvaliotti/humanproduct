# Strategy Canvas Factors — Selection Heuristics and Traps

Source: W. Chan Kim & Renée Mauborgne, *Blue Ocean Strategy* (2005). The strategy canvas is the central diagnostic tool: a one-page picture of the factors of competition and each competitor's offer intensity on each.

A canvas is only as honest as its factors. Bad factors produce canvases where everyone looks the same, or where one competitor looks like a miracle-worker — either output is useless. This reference governs the Phase 9 factor-selection work.

## What a factor must be

A valid factor of competition meets all five criteria:

1. **A thing the buyer actually trades off.** The factor appears in real shortlist decisions — cited in reviews, won/lost notes, or churn evidence. If no buyer has ever said the factor mattered, it isn't one.
2. **Plottable on a 0–5 or 0–10 offer-intensity scale.** Each competitor's offering can be scored along the factor with a clear anchor for "0 = absent" and "5 = leader". If the factor is binary or categorical (e.g., "has API / no API"), convert it into a continuous factor ("API coverage") or drop it.
3. **Evidence-anchored per competitor.** Every score is backed by at least one piece of behavioral or pattern evidence. Subjective plotting is how canvases lie.
4. **Non-redundant.** Two factors that always move together are one factor. Collapse them.
5. **Concrete, not abstract.** "Quality", "innovation", and "customer-centricity" are not factors. They are moods. "P95 latency on the API", "number of native integrations", and "time to first value for a new user" are factors.

## Sources of good factors

Draw factors from Phase 7 (winning-factors ledger) in this order of preference:

| Source | What it gives | Trust |
|---|---|---|
| Churn-destination verbatims citing a specific factor | Factors that cost retention | High — behavioral |
| Won/lost-deal citations of decisive factors | Factors that decide purchases | High — behavioral |
| Review cluster themes ("what users love / hate") | Factors that drive advocacy and complaint | Medium — pattern |
| Pricing-page benefit hierarchy | Factors vendors think buyers pay for | Low — stated |
| Analyst report feature grids | Factors consultants think matter | Low — stated |
| Your own PM/sales intuition | Factors you believe matter | Lowest — unless tied to evidence above |

Every factor on the canvas should be traceable to at least one of the top three rows.

## Recommended factor count

| Factor count | When to use | Risk |
|---|---|---|
| **4–6** | Early analysis, 3–4 shortlist competitors, category is young | Under-resolved picture; easy to hide differences |
| **6–8** | Default — most mature analyses | — |
| **9–10** | Rich analysis, ≥5 competitors, complex category | Cognitive overload on the canvas; consider splitting into two canvases |
| **11+** | Rarely justified | Canvas becomes unreadable; group factors into themes |

The canvas is a visual compression device. Adding factors to avoid hard tradeoffs is the single most common failure.

## How to anchor the 0–5 scale per factor

For each factor, define what "0" and "5" look like before plotting. Examples:

| Factor | 0 | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|---|
| **Time to first value** | Never reaches first value | > 1 week | 2–7 days | 1–2 days | Same day | < 15 minutes |
| **Native integrations** | None | 1–3 | 4–9 | 10–24 | 25–49 | 50+ |
| **Meeting-prep automation** | Manual only | Templates | Auto-summaries | Auto-tasks | Auto-briefs | Fully pre-built brief per meeting |
| **Admin visibility** | No org view | Per-user exports | Team dashboards | Role-based views | Audit logs | Full org graph with policy controls |
| **Price (inverted — 5 = cheapest)** | $300+/user/mo | $150 | $60 | $30 | $12 | Free / freemium |

Price is typically plotted inverted so the "best" for buyers is high on the canvas across factors.

Write the scale anchors into the canvas output as a footnote. Readers who disagree can then argue with the anchor, not with the scoring.

## Common factor-selection traps

### Trap 1: The SWOT dump
**Symptom.** Factors pulled from an internal brainstorm: "Customer Experience", "Innovation Speed", "Brand Strength".
**Why it fails.** None are plottable, none are buyer-cited, and the canvas will flatter whichever competitor wrote the SWOT.
**Counter.** Require every factor to be rewritten in buyer language and anchored with evidence. If you can't rewrite it, drop it.

### Trap 2: Feature parity bingo
**Symptom.** Factors are a checklist of features (API, SSO, mobile app, Slack integration).
**Why it fails.** Each is binary, uninformative, and ignores the offer-intensity dimension. Everyone will score near-parity once features become table stakes.
**Counter.** Convert features into continuous factors that capture *how well* the feature is delivered. "Has an API" → "API coverage and reliability (0–5)". Drop features that are truly binary and category table-stakes — they don't differentiate.

### Trap 3: Vendor-biased factors
**Symptom.** The factor list looks suspiciously like the anchor's feature differentiators.
**Why it fails.** You'll inflate the anchor's curve. The canvas becomes a self-portrait.
**Counter.** Force at least two factors where you expect the anchor to score low. If you can't find any, you're either in a monopoly or not being honest.

### Trap 4: Non-consumption blindness
**Symptom.** All factors describe trade-offs among SaaS competitors; none describe the axis that matters to non-consumers.
**Why it fails.** The Four Actions Framework can't find Create candidates, because no factor captures what non-consumers value.
**Counter.** Add 1–2 factors drawn from non-consumption research: "time investment to get value", "tolerable learning curve", "graceful-degradation in partial use", "zero-config setup".

### Trap 5: The meta-factor
**Symptom.** A factor that's actually an outcome of other factors — e.g., "Productivity".
**Why it fails.** It won't plot independently; every other factor feeds into it.
**Counter.** Decompose into the 2–3 underlying factors that produce the outcome.

### Trap 6: Incomparable units
**Symptom.** Factors mix objective units (price) with subjective ratings (ease of use) without normalization.
**Why it fails.** Plotting becomes arbitrary.
**Counter.** Pick either all subjective 0–5 intensity scores with published anchors, or all objective metrics (but then you're not drawing a canvas, you're drawing a spider chart). Mixing is fine only if anchors are explicit.

### Trap 7: Canvas vanity — one canvas for all competitors
**Symptom.** 8 competitors on one canvas, each with a differently shaped curve, pretty to look at.
**Why it fails.** Convergence within strategic groups is hidden by averaging unlike competitors.
**Counter.** Cluster competitors into strategic groups first. One canvas per group (2–3 competitors each), plus one overlay canvas comparing the anchor against the group it most threatens.

### Trap 8: Forgetting the Four Actions
**Symptom.** The canvas lists competitor curves but no Eliminate / Reduce / Raise / Create annotations for the anchor.
**Why it fails.** The canvas describes the past. Blue Ocean analysis is about the anchor's *next* curve.
**Counter.** Every canvas ends with an explicit Four Actions summary pointed at the anchor. If the Create candidate is empty, do more non-consumption research.

## The Four Actions Framework — quality bar

For the anchor's planned curve, each of the four actions must be specific:

| Action | Quality bar | Bad example | Good example |
|---|---|---|---|
| **Eliminate** | Names a factor the industry includes but buyers don't value | "Simplify our UI" | "Remove the 'team roles' factor — 0 of 32 churn verbatims cite roles as a retention driver; configurator overhead is a top-3 adoption blocker" |
| **Reduce** | Names a factor the industry over-invests in relative to buyer needs | "Spend less on marketing" | "Reduce native-integration breadth from 50+ to the top 6 cited in reviews; reallocate to setup-time factor" |
| **Raise** | Names a factor under-served by the industry standard | "Be better at support" | "Raise time-to-first-value from category median 3 days to < 2 hours by pre-configuring based on calendar access" |
| **Create** | Names a factor the industry has never offered | "Build AI features" | "Create 'graceful failure' factor — the tool should still deliver 50% of its value when one integration is broken; no competitor scores above 1 today" |

A good Four Actions set rebalances the anchor's curve toward non-consumers and away from parity with incumbents. A bad one is a roadmap memo in canvas clothing.

## Offer-intensity scoring procedure

For each competitor × factor cell:

1. Write the scale anchors for the factor once.
2. Find at least one piece of evidence that pins the competitor's score. Behavioral > pattern > stated.
3. Write the score (0–5) with a one-sentence evidence anchor.
4. If evidence is absent or contradictory, record the score as a range (e.g., "3–4") and flag the uncertainty.
5. Do not plot a score you cannot defend with evidence. If fewer than half the cells can be defended, return to Phase 2.

## Output format for the canvas

```markdown
### Strategy canvas — [strategic group name]

Competitors plotted: [A, B, C]

| Factor | 0–5 anchor definition | [A] | [B] | [C] | Anchor (projected) |
|---|---|---|---|---|---|
| [Factor 1] | 0=absent, 5=leader | 3 [evidence] | 4 [evidence] | 2 [evidence] | 5 (planned) |
| [Factor 2] | ... | ... | ... | ... | ... |

#### Four Actions (for the anchor)
- **Eliminate:** [factor + rationale + evidence]
- **Reduce:** [factor + rationale + evidence]
- **Raise:** [factor + rationale + evidence]
- **Create:** [factor + rationale + evidence, drawn from non-consumption]

#### Convergence and white-space read
- **Convergence zones:** [factors where all competitors are scoring 3+]
- **White spots:** [factors where no one scores above 2]
- **Strategic group summary:** [one sentence]
```

If the canvas has no Create candidate and no white spot, it's telling you the category is mature and operational-excellence-driven. That's a valid finding — write it explicitly, don't fake a white spot to make the canvas more interesting.
