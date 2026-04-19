# WTP Research Methods

Phase 6 prescribes specific methods per segment. This file is the method catalogue.

## Selection matrix

| Method | Fits when | Sample size target | Produces | Cost / effort |
|---|---|---|---|---|
| **Van Westendorp** | Calibrating the acceptable range pre-launch | 100–300 per segment | Four price points: too cheap, cheap, expensive, too expensive | Low — survey |
| **Gabor-Granger** | Narrowing within a known range | 80–200 per segment | Purchase probability curve at N prices | Low — survey |
| **Conjoint (choice-based)** | Multi-feature trade-off, Leader identification | 150–400 per segment | Part-worth utility + implicit feature price | Medium — designed survey |
| **Build-Your-Own (BYO)** | Bundle sensitivity, feature priority | 80–200 per segment | Revealed preference on bundle composition | Medium — interactive survey |
| **Most-Least analysis (MaxDiff)** | Forcing Leader / Filler / Killer separation | 100–300 per segment | Ranked list of value drivers | Low-medium — survey |
| **Mom-Test interview** | Pre-PMF; extracting behavior not opinion | 10–25 per segment | Qualitative stories of past behavior | Medium — interviews + analysis |
| **Live price experiment** | Post-PMF, scale; elasticity curve | 1,000+ visitors per cell | Conversion × price, elasticity | Medium-high — eng effort, risk |
| **Feature removal test** | Identifying Fillers vs. Leaders | 500+ users per cell | Usage impact on removal | Medium — eng + analytics |
| **Discounting / Pricing page A/B** | Testing anchor, frame, bundle | 1,000+ visitors per cell | Conversion uplift by frame | Medium |

## Method 1 — Van Westendorp Price Sensitivity Meter

Four questions per respondent:

1. At what price would you consider the product **so expensive** that you would not consider buying it?
2. At what price would you consider the product **expensive**, but still consider buying it?
3. At what price would you consider the product a **bargain** — a great buy for the money?
4. At what price would you consider the product **so cheap** that you would question its quality?

Plot cumulative distributions. Intersection points give:
- **Point of Marginal Cheapness (PMC)** — floor below which quality is questioned
- **Point of Marginal Expensiveness (PME)** — ceiling above which buyers bail
- **Optimal Price Point (OPP)** — intersection of "too cheap" and "too expensive"
- **Indifference Price Point (IPP)** — intersection of "cheap" and "expensive"

**Use for:** acceptable range, pre-launch calibration.

**Limitations:** stated preference. Treat the resulting range as a first-cut hypothesis, not a price decision.

## Method 2 — Gabor-Granger

Present a price; ask purchase probability (1–5 scale or 0–10). Repeat across 5–8 prices, randomizing order.

Produces a demand curve. Compute elasticity: %Δ demand / %Δ price.

**Use for:** demand curve shape, elasticity, tier price-gap design.

**Limitations:** stated preference inflates. Use the curve shape more than the absolute conversion levels.

## Method 3 — Conjoint (choice-based, CBC)

Respondents choose between bundles defined by attribute levels, including price. Example attributes:

| Attribute | Levels |
|---|---|
| Core outcome coverage | Basic / Extended / Premium |
| Integrations | 3 / 10 / 25 |
| SLA | None / 99.5% / 99.9% |
| Price | $50 / $100 / $200 / $400 / $800 |

Each respondent sees 10–15 choice sets. Statistical analysis derives:
- **Part-worth utilities** — value of each attribute level
- **Implicit price** — how much each feature is worth in dollars
- **Segment-level preferences** (via latent-class analysis)
- **What-if simulation** — predicted share at any bundle + price combination

**Use for:** Leader/Filler/Killer differentiation, bundle design, tier pricing.

**Limitations:** expensive to design properly; attribute interactions (e.g., price × SLA) require larger samples. Buyer choices in forced-choice surveys overweight rational factors vs. real-world brand/habit effects.

## Method 4 — Build-Your-Own (BYO)

Respondent composes their own bundle from a menu of features, each with a stated price. Observe what they include, exclude, and their total willingness to spend.

**Use for:** bundle sensitivity, G/B/B tier validation.

**Limitations:** individual feature prices shown anchor the result. Vary anchors across respondents to measure anchoring effect.

## Method 5 — MaxDiff (Most-Least / Best-Worst Scaling)

Respondents see sets of 4–5 features at a time; pick the **most valuable** and **least valuable**. Repeat across sets so each feature is rated 3–4 times.

Produces a rank-order of value drivers with interval-scaled scores.

**Use for:** separating Leaders (top quartile), Fillers (middle), Killers (bottom, especially if scored negative after transformation).

**Limitations:** no price elicitation — use alongside conjoint or Van Westendorp.

## Method 6 — Mom-Test interview

The most important method pre-PMF. The premise: ask about **past behavior**, never future willingness.

### The three Mom-Test rules

1. Talk about their life, not your idea.
2. Ask about specifics in the past, not generics or opinions about the future.
3. Talk less, listen more.

### The WTP-focused interview script

Opener: "Walk me through the last time you had [pain]."

Past-behavior probes:

- "What did you try before?"
- "How much did you spend on that?"
- "How long did you put up with it before you looked for a fix?"
- "When you last evaluated [alternative], what did you end up paying?"
- "What made you willing to pay that?"
- "If you had stopped paying, what would have gone wrong first?"

Hypothesis-testing (carefully):

- "Last time you paid $X for [alternative], what about it justified that price?"
- "When you renewed, what had you experienced in the previous year that made it an easy yes?"

Forbidden phrasings (Mom-Test violations):

- ❌ "Would you pay $X for this?"
- ❌ "Do you think this would be valuable?"
- ❌ "If we built this, would you use it?"

### Signal extraction

For every interview, extract three things:

1. **Behavioral data points** — actual prices paid for actual things
2. **Value-realization language** — "I knew it was worth it when..." moments (proof signals)
3. **Commitment tests** — did the interviewee offer introductions, time, pre-orders, pilot slots? (Not just verbal enthusiasm.)

Compliments and verbal enthusiasm get recorded at near-zero weight. Only commitments and past spend count.

## Method 7 — Live price experiment

Split traffic across price points; measure conversion.

### Design

- Minimum 2 cells (control + 1 test), ideally 3–5.
- Minimum 1,000 visitors per cell for 10% lift detection at 80% power.
- Run for at least 2 weeks to smooth weekly seasonality.
- Watch for observer effects (if existing customers see different prices, expect backlash).

### Outputs

- Conversion curve vs. price
- Elasticity ≈ %Δ conversion / %Δ price
- Revenue-optimal point (not conversion-optimal — they differ)

**Use for:** post-PMF fine-tuning within a known-viable range.

**Limitations:** requires traffic volume. Price integrity risk — customers comparing notes. Not appropriate when prices are negotiated.

## Method 8 — Feature removal test

Remove a feature from a subset of users; measure impact on usage, retention, NPS.

**Use for:** distinguishing Leaders (removal causes churn or complaint) from Fillers (no impact) from Killers (removal *improves* NPS).

**Limitations:** ethically questionable to remove value customers are paying for without notice. Use in pre-launch flagged cohorts, or via natural experiments (rollout timing).

## Recommended method stack per lifecycle stage

| Lifecycle stage | Recommended stack |
|---|---|
| **Pre-PMF** | Mom-Test interviews (primary) + Van Westendorp (directional) + MaxDiff (feature ranking) |
| **Early PMF** | Mom-Test (retention cohort) + Conjoint (tier design) + Van Westendorp (refinement) |
| **Scaling** | Conjoint (segmentation) + Live price experiment (elasticity) + BYO (packaging) |
| **Mature** | Live price experiment (optimization) + Feature removal (pruning Fillers) + Discounting A/B (capture) |

## Per-segment method assignment

In Phase 6 of the workflow, the output specifies:

| Segment | Primary method | Secondary method | Sample target | Key question(s) to answer |
|---|---|---|---|---|
| S1 | ... | ... | ... | ... |
| S2 | ... | ... | ... | ... |

Each segment gets explicit questions or stimuli — not a generic "run conjoint". Example:

**Segment S1 — High-volume agency buyers**
- Primary: Conjoint with attributes: workflow coverage (basic / full), integrations (5 / 20 / 50), price ($500 / $1500 / $4000 / $8000 / $15000 per month).
- Secondary: 15 Mom-Test interviews with past-behavior focus on agency tool budgets and renewal triggers.
- Key question: is Leader "cross-client reporting" valued highly enough to support a dedicated "Agency tier" at 2–3× the base price, or does per-seat scaling capture the same WTP?
