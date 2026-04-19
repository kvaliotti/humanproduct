---
name: willingness-to-pay-research
description: Build a deep, segmented model of what customers will pay for, why, and how they detect whether the value is present in the product. Integrates Monetizing Innovation (Ramanujam & Tacke) with JTBD/ODI, Kano, Value Proposition Canvas + Economic Value to Customer, Bain 30 Elements of Value, and The Mom Test. Consumes handoffs from industry-process-map and audience-segment-research. Use when the user asks to "analyze willingness to pay", "research WTP", "map value drivers", "find Leaders/Fillers/Killers", "identify price sensitivity", "design a pricing hypothesis", "research value perception", "map proof-of-value signals", "run a WTP analysis", or provides a product/category/industry and wants the value-money-signals model before pricing. Output: per-segment three-layer model (value / drivers / proof signals), WTP band hypotheses with confidence, research plan, tension log, glossary, rejected-framings appendix, and YAML handoff for downstream pricing, positioning, and GTM skills.
---

# Willingness-to-Pay Research

## Promise

Given an anchor (product, category, or industry) — ideally with an upstream handoff from `audience-segment-research` — produce **one markdown artifact** that maps, for each segment:

1. **What they will pay for** — the specific outcomes, value elements, and Leader features that drive 80% of WTP, with Fillers and Killers called out.
2. **Why they will pay for it** — the economic, emotional, and social drivers, anchored against a named next-best alternative, with dollar-math where possible.
3. **How they know it's working** — the proof-of-value signals (experiential, quantitative, social, temporal) that let the buyer detect whether the value is actually present in the product, and to what degree.

Plus:

4. **WTP band hypotheses per segment** with confidence percentages and explicit reasoning.
5. **A WTP research plan** — specific methods (Van Westendorp, Gabor-Granger, conjoint, Build-Your-Own, Mom-Test interviews) designed per segment.
6. **A tension log, glossary, rejected-framings appendix, and YAML handoff** for downstream skills.

This is an **analysis** skill first. It does not set prices. It builds the value-money-signals model that a pricing decision needs to stand on. Pricing execution, packaging, and monetization-model selection are downstream.

The output is read by a CPO-level audience that will make allocation and validation decisions on it. Write for that reader.

## Operating principles

Six principles define this skill. They are the book-grounded spine — when in doubt, return to them.

### 1. Value is relative to the next-best alternative, never absolute (Monetizing Innovation + EVC)

Every WTP claim is anchored. "They'll pay $X" is meaningless without "…compared to doing it in a spreadsheet", "…compared to the agency charging $Y", or "…compared to tolerating the pain". Economic Value to Customer (Anderson-Narus, Forte-Holden) quantifies the delta in the customer's currency: time saved × loaded rate, risk reduction × event probability × event cost, revenue uplift × attribution share.

If no reference alternative is identified, the WTP claim is ungrounded. Reject it and surface the missing reference as an open question.

### 2. Customers pay for outcomes, not features — and only for Leaders (JTBD/ODI + Monetizing Innovation Ch. 6)

Translate every feature into an outcome statement using the Ulwick form: `[direction] + [metric] + [object of control] + [contextual qualifier]` ("reduce time-to-first-brief when prepping for a 1:1"). Then classify each outcome against two cross-referenced frameworks:

| Classification | Monetizing Innovation | Kano |
|---|---|---|
| Drives 80% of WTP | **Leader** | Must-have or Performance |
| Nice-to-have, neutral WTP | **Filler** | Indifferent |
| *Reduces* WTP if present | **Killer** | Reverse |
| Punchy delight, erodes into must-have | — | **Delighter** |

Kano and Leaders/Fillers/Killers are not redundant — they catch different failures. Leaders/Fillers/Killers catches WTP dilution from over-packaging. Kano catches the **migration** risk: delighters decay to must-haves in 12–36 months, and today's differentiator is tomorrow's table stake. A value map without Kano migration is a snapshot of a moving target.

### 3. Value is multi-layered — stack the elements (Bain 30 + Monetizing Innovation cases)

Functional value alone under-predicts WTP in categories where emotional, life-changing, or social drivers stack on top. Bain's 30 Elements pyramid (functional → emotional → life-changing → social impact) exposes this. Swarovski charges 5–6× on cut-complexity not because buyers "need" more facets — the functional gain is marginal — but because brilliance (emotional) + status (social) + self-actualization (life-changing) compound.

Stacking test: for each Leader outcome, name which Bain layers it activates. More layers → more WTP resilience. Pure-functional Leaders are cheapest to displace.

### 4. Pay AND perceive — invisible value is unpaid value (Monetizing Innovation Ch. 11 + behavioral pricing)

Customers pay for **perceived** value, not value-in-fact. Every Leader outcome must have a **proof signal** — something the buyer can experience, measure, see others confirm, or detect as a pattern. If a value element has no proof signal, it cannot be monetized; either design the signal or downgrade the value estimate.

The four signal modes:

| Mode | What it is | Example |
|---|---|---|
| **Experiential** | A felt workflow moment | "I noticed I stopped opening the other tab" |
| **Quantitative** | A visible metric moved | "Time-to-first-draft dropped from 3 days to 1 hour" |
| **Social** | External validation | "My boss stopped asking for redos" |
| **Temporal** | A pattern over time | "By week 3 I opened it daily without thinking" |

Full taxonomy in `references/proof-signals.md`. This is the third question the skill answers and its most product-design-relevant output.

### 5. Behavior beats stated preference — always (The Mom Test + Monetizing Innovation research methods)

"Would you pay $X for this?" is noise. Signal is what buyers *did*: paid full on signup, renewed, referred, expanded, churned, hacked around, told peers.

Every WTP claim is tagged behavioral or stated; behavioral is weighted ~3× higher. Guardrails against the three Mom-Test traps:

| Trap | Looks like | Counter |
|---|---|---|
| Enthusiasm mistaken for commitment | "I love this, I'd pay anything" | Ignore. Find what they already paid for comparable value. |
| Compliments mistaken for demand | "Cool product, smart idea" | Record as zero signal. |
| Opinions mistaken for facts | "I think most people would..." | Only their own behavior counts. |

The skill actively searches for disconfirming evidence each round. If a WTP hypothesis has no counter-evidence, the search was lazy — not the hypothesis strong.

### 6. WTP is non-uniform AND non-monotonic — preserve the variance (Monetizing Innovation Rule 2 + Ch. 6)

Two properties that break intuition:

- **Non-uniform across segments:** 5–10× WTP variance for the same product. No single "the customer"; every segment gets its own value map.
- **Non-monotonic in features:** adding features can *reduce* WTP (Killers, cognitive load, privacy concerns, complexity tax). More is not more.

When the handoff from skill #2 supplies segments, inherit them and build per-segment maps. If the maps converge (same Leaders, same WTP band), treat that as a signal to revisit segmentation — true segments should diverge on WTP by design.

## Workflow

Execute in order. Phases feed forward.

### Phase 1 — Intake & calibration

Consume input in this order of preference:

1. **YAML handoff from `audience-segment-research`** — parse it. Inherit `framing`, `segments`, `cross_segment`, `open_questions`. The segment-level `pains_unmet_needs`, `current_alternatives`, and `buying_triggers` become seed material for value and driver hypotheses. The `open_questions` from skill #2 are priority research directions here.
2. **Upstream `industry-process-map` handoff** — use process tree and substitutes to ground the next-best-alternative anchors.
3. **User-provided context** — internal pricing data, won/lost deal transcripts, churn notes, price-sensitivity experiments, NPS comments.
4. **Bootstrap** — if none of the above, ask 2–3 clarifying questions with `AskUserQuestion`.

Resolve these variables before research:

| Variable | What it is | Example |
|---|---|---|
| **Anchor** | Reference product/company (optional) | "SplitMetrics" |
| **Industry / domain** | The space | "Mobile ad optimization" |
| **B2B / B2C** | Changes value stacking and buying unit | "B2B (SMB to enterprise)" |
| **Lifecycle stage** | Pre-PMF vs. scaling changes what evidence is available | "Early PMF" |
| **Segments (from handoff)** | Segments to map WTP against | "S1 high-volume agency; S2 in-house UA lead" |
| **Scope boundary** | How wide to go | "Paid acquisition at consumer apps, excluding creative production" |
| **Primary use case** | What buyers are buying this *for* | "Getting profitable installs at scale" |

When to ask vs. assume: **ask** if segments are missing or lifecycle is unknown — both change the method. **Assume** otherwise and state assumptions explicitly. Cap at 3 questions.

### Phase 2 — Research

Goal: practitioner language about value and price, actual prices paid, price complaints, expansion and churn stories, value-realization testimonials — not vendor-claimed value.

Read `references/research-playbook.md` at the start of this phase for source priority and query patterns specific to WTP research.

Source priority (highest signal to lowest):

| Tier | Source | What it reveals |
|---|---|---|
| 1 | Case studies with disclosed prices / ACVs | Behavioral evidence of real deal sizes |
| 2 | Public churn and expansion posts; SaaS cohort stories | What they paid, then kept paying or left |
| 3 | Reviews with price commentary ("worth it at $X", "overpriced", "left because") | Value-realization and price-pain signals |
| 4 | Competitor pricing pages — as anchors, not templates | What the category has trained buyers to expect |
| 5 | Practitioner forums — Reddit, HN, niche Discords surfaced on the web | Price complaints, substitutes, workarounds |
| 6 | Job descriptions with budget/tool mentions | Buyer authority and routine spend |
| 7 | Vendor marketing — discount only for glossary | Claimed value ≠ realized value |

Budget: 8–15 searches + 2–4 deep fetches. Stop when new sources stop changing the emerging WTP model.

Capture into a running scratch table — every observation carries source and evidence type:

| # | Observation | Kind (value / price / signal / driver) | Source | Segment | Behavioral or stated | Confidence | Tension with? |

This table is the raw material and must survive into the working file. Discarding it erases the audit trail.

### Phase 3 — Build per-segment three-layer value model

For each segment inherited from the handoff (or bootstrapped), produce the three-layer model using `references/value-frameworks.md` as the framework guide.

**Layer A — Value (what they pay for)**
- JTBD outcome statements (Ulwick form)
- Bain 30 elements activated (functional / emotional / life-changing / social)
- Leader / Filler / Killer classification per outcome, with reasoning
- Kano classification per outcome (must-have / performance / delighter / indifferent / reverse)
- Kano migration hypothesis — which delighters will decay, on what horizon

**Layer B — Drivers (why they pay)**
- Next-best alternative (named, specific — not "the status quo")
- EVC math against that alternative (time × rate, risk × probability × cost, revenue × attribution)
- Pain intensity and urgency (what triggers the purchase)
- Emotional and social stakes (job failure cost, peer visibility, identity)
- Reference anchors used by the segment (category price, competitor, internal benchmark)
- Mom-Test check: is this what they did, or what they said? Tag every driver claim.

**Layer C — Proof signals (how they know it's working)**
- Primary signal mode per Leader (experiential / quantitative / social / temporal)
- Specific signal description (what it looks like in the buyer's own words if possible)
- Time-to-value (how long from first use until the signal fires)
- Who perceives the signal (self-only vs. team vs. boss vs. customer)
- Inverse risk signals — signs the value is NOT being delivered
- UX / product implication — where the signal must be designed into the interface

Full taxonomy and detection heuristics in `references/proof-signals.md`. Layer C is the skill's most novel contribution and must not be skipped or treated as filler.

### Phase 4 — WTP band hypothesis per segment

For each segment, produce:

| Field | What it is |
|---|---|
| **WTP band** | A range (e.g., "$80–150 / month / active user"), not a point estimate |
| **Reference anchor** | The alternative the band is benchmarked against |
| **EVC math** | The quantified value delta in the customer's currency |
| **Share of value captured** | The assumed % of EVC that can be priced (typically 25–60%) |
| **Confidence** | 0–100% this band is directionally right |
| **Behavioral evidence count** | How many behavioral observations support it |
| **Disconfirming question** | The single research question whose answer would most change the band |

Ballpark beats precision (Rule 6 of Monetizing Innovation). The point is knowing whether the band is $10 or $100, $100 or $1,000 — not whether it is $99 or $109.

### Phase 5 — Cross-segment synthesis

Half a page. Two cross-cuts:

1. **Shared vs. divergent value** — Leaders that apply to multiple segments (category table stakes) vs. Leaders unique to one or two (differentiation levers).
2. **WTP variance** — the ratio between highest and lowest segment WTP band. If variance < 2×, revisit segmentation; real segments diverge by design.
3. **Killer inventory** — features that are Killers for one segment and Leaders for another. These are packaging-design triggers (separate SKUs, not unified product).

### Phase 6 — WTP research plan

For each segment, prescribe specific methods. Catalogue in `references/wtp-research-methods.md`.

| Method | When it fits | What it produces |
|---|---|---|
| Van Westendorp | Pre-PMF, calibrating the acceptable range | Four price points: too cheap, cheap, expensive, too expensive |
| Gabor-Granger | Known price range, looking for demand curve | Purchase probability at N price points |
| Conjoint | Multi-feature trade-offs, ranking Leaders | Part-worth utility per feature + implicit feature price |
| Build-Your-Own | Bundle sensitivity | Revealed preference on feature bundle and price |
| Most-Least analysis | Leader vs. Filler vs. Killer separation | Ranked list of value-driving features |
| Mom-Test interview | Behavior extraction, early-stage | What they already pay for comparable value |
| Price experiment (live) | Scale, post-PMF | Conversion × price point, elasticity curve |

Each segment gets: primary method + rationale + sample size target + the specific questions or stimuli. Draft at least one interview script grounded in Mom-Test discipline (past behavior only, no hypothetical willingness).

### Phase 7 — Assemble the output

Use `assets/output-template.md`. Full structure:

1. Framing & sources
2. Three-layer value model per segment (repeat)
3. WTP band hypotheses per segment (table)
4. Cross-segment synthesis
5. Proof-of-value signals matrix (consolidated across segments)
6. WTP research plan
7. Tension log
8. Outliers & singletons (singletons that foreshadow new WTP sub-patterns)
9. Glossary
10. Evidence quality notes
11. Open questions for pricing / packaging / GTM
12. Appendix — rejected value framings
13. YAML handoff block

Write to `/sessions/optimistic-peaceful-fermi/mnt/tempSkills/willingness-to-pay-research-[slug].md` where `[slug]` is a kebab-case tag of the anchor or industry.

The YAML handoff block is non-negotiable — it's the contract with downstream skills. Schema in `references/handoff-schema.md`.

### Phase 8 — Share

Link the file with a `computer://` link. Short message: title, one-sentence summary of the WTP variance across segments, link. Don't restate content in chat.

## Quality audit — mandatory before Phase 7

Run these checks explicitly. Fix any failure before writing the final artifact.

- [ ] Does every Leader outcome have a named proof signal with a mode (experiential / quantitative / social / temporal)?
- [ ] Is every WTP claim tied to a named next-best alternative (not "status quo" generic)?
- [ ] Does every driver claim include EVC math or an explicit note that math is not yet available?
- [ ] Is every observation tagged behavioral or stated?
- [ ] Is the behavioral-to-stated ratio ≥ 1:2 in the evidence base? (If heavier on stated, flag the thin evidence.)
- [ ] Has every Leader been cross-classified against Kano?
- [ ] Has the Kano migration risk been addressed for each delighter?
- [ ] Is WTP variance across segments ≥ 2×? (If not, the segmentation may be too narrow.)
- [ ] Are Killers inventoried by segment?
- [ ] Has at least one round of disconfirming search been run for the dominant hypothesis?
- [ ] No "would you pay $X" stated-preference claims used as primary evidence?
- [ ] Is every tension classified (subsegment-split / context-dependent / stated-vs-revealed / temporal / unresolved)?
- [ ] Does the YAML handoff validate against `references/handoff-schema.md`?

If any check fails, loop back to the relevant phase.

## Writing style

- **No preamble.** Start with the framing table.
- **Tables and structured profiles over prose.** Prose only where nuance requires it.
- **Specific alternatives, not categories.** "Displaces a $3,500/mo Publicis retainer" beats "displaces agency spend".
- **Dollar math wherever possible.** "6 hrs/wk × $95/hr × 48 weeks = $27,360/yr" beats "significant time savings".
- **Source tags on non-obvious claims.** Inline `[src: G2 review 2025-02, behavioral]`.
- **Confidence marks as percentages.** No hedge words ("somewhat", "arguably", "it could be said").
- **Honest gaps.** "Thin evidence — 2 data points, both stated" beats dressing it up.
- **Verbs for outcomes.** "Ship a briefing deck in under 30 minutes" beats "Briefing deck creation".

## When this skill is the wrong tool

| User wants | Use |
|---|---|
| Map the space (processes, workflow) | `industry-process-map` (skill #1) |
| Segment the audience and map stakeholders | `audience-segment-research` (skill #2) |
| Set list prices, design tiers, pick a monetization model | Downstream pricing/packaging skill (not in this plugin yet) |
| Competitive teardown of named vendors | `product-management:competitive-brief` |
| Positioning canvas and market-category claim | `pm-sage:position-product` (feed it this skill's output) |
| Evaluate a specific product idea | `pm-sage:evaluate-idea` |
| Write a PRD / working-backwards doc | `pm-sage:write-prd` (feed it this skill's Leaders and proof signals) |

This skill maps **what they pay for, why, and how they know it's working**. Pricing execution is a separate discipline. Stay in lane.
