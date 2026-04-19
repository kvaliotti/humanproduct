# Value Frameworks — Layered Model

Five frameworks, stacked. Each does something the others miss. Read this at the start of Phase 3.

| Framework | What it catches | Blind spot covered by another framework |
|---|---|---|
| **JTBD / ODI (Ulwick)** | Outcome statements as WTP drivers | Ignores emotional/social value |
| **Leaders / Fillers / Killers (Monetizing Innovation)** | Feature-to-WTP concentration; Killers destroy value | Doesn't track migration over time |
| **Kano Model** | Must-have vs. delighter vs. indifferent; migration over time | Doesn't classify economic magnitude |
| **Value Proposition Canvas + EVC** | Pains → Pain Relievers, Gains → Gain Creators, with dollar math | Less useful for emotional/identity-driven categories |
| **Bain 30 Elements of Value** | Functional / emotional / life-changing / social stacking | Doesn't indicate trade-off priority |

Use all five. They compose, they don't substitute.

---

## 1. JTBD / ODI (Outcome-Driven Innovation, Ulwick)

### The outcome statement form

`[direction of improvement] + [unit of measure] + [object of control] + [contextual qualifier]`

Examples:
- "**Minimize** the **time** it takes to **prepare for a 1:1** **when context is spread across Slack, email, and last meeting's notes**"
- "**Reduce** the **number of** **deck revisions** **needed** **before a board meeting**"
- "**Increase** the **probability** of **catching a competitive claim** **before it lands in a sales call**"

Customers pay for outcomes framed this way. Features are inputs; outcomes are what is paid for.

### The extraction process

For each segment, extract 5–15 outcome statements. Source them from:
- Interview transcripts with their own phrasing preserved
- Case-study results sections
- Review comments describing what changed after adoption
- Pain statements inverted ("pain: took 3 hours" → "outcome: reduced time to X")

Rank outcomes by **importance** (1–10) and **satisfaction with current alternatives** (1–10). WTP concentrates where importance is high AND satisfaction is low — Ulwick's "opportunity score" = importance + max(importance − satisfaction, 0).

---

## 2. Leaders / Fillers / Killers (Monetizing Innovation Ch. 6)

### Classification

| Class | Definition | Treatment in output |
|---|---|---|
| **Leader** | Drives ≥80% of WTP; 5–10 per segment | Invest heavily; must be in every offering |
| **Filler** | Nice-to-have; neutral WTP impact | Cheap to include; use for tier differentiation |
| **Killer** | Reduces WTP if present (privacy risk, complexity, clutter) | Remove or quarantine, even if cheap to build |

### Classification heuristics

| Signal | Points to |
|---|---|
| "This is the reason I bought it" | Leader |
| "I didn't know it had that" (used casually) | Filler |
| "I had to turn it off" / "it worried me" / "it confused my team" | Killer |
| "Nice bonus" | Filler (rarely Leader) |
| Willingness to pay for feature as standalone | Leader (with confirmation) |

### Reasoning requirement

For every Leader/Filler/Killer classification, record:
- The evidence (source + behavioral or stated)
- The segment it applies to (Leader in one segment can be Filler in another)
- Confidence 0–100%

---

## 3. Kano Model

### Five categories

| Category | Buyer reaction when present | Buyer reaction when absent |
|---|---|---|
| **Must-have** | Satisfied (it's expected) | Angry (deal-breaker) |
| **Performance** (linear) | More is better | Less is worse |
| **Delighter** (attractive) | Excited | Not missed |
| **Indifferent** | Doesn't care | Doesn't care |
| **Reverse** | Annoyed | Satisfied |

### Mapping to Leaders/Fillers/Killers

| Kano | L/F/K | Notes |
|---|---|---|
| Must-have | Leader (baseline) | Table-stakes; pays but doesn't differentiate |
| Performance | Leader | Scales WTP linearly |
| Delighter | Leader (temporary) | Differentiator today; must-have tomorrow |
| Indifferent | Filler | No action needed |
| Reverse | **Killer** | Critical to catch — adding this reduces WTP |

### The migration hypothesis

Delighters decay to must-haves in 12–36 months in most B2B SaaS categories, faster (6–18 months) in consumer categories. Today's differentiator stops winning. The output must name delighters AND their expected migration horizon.

Classic examples:
- Mobile app for SaaS: delighter in 2012, must-have by 2016
- Single sign-on: delighter in 2014, must-have for enterprise by 2019
- AI-assisted anything: currently delighter in most B2B (2024–2026); likely must-have in 24–48 months

### The Kano survey (optional primary research)

Per feature, ask two questions:
1. "How would you feel if the product HAD this feature?" (5-point: I like it / expect it / neutral / live with / dislike)
2. "How would you feel if the product DIDN'T have this feature?" (same scale)

Cross-tabulate to derive the category. Useful when the skill is used in primary research mode; otherwise infer from qualitative evidence.

---

## 4. Value Proposition Canvas (Osterwalder) + Economic Value to Customer (Anderson-Narus, Forte-Holden)

### Canvas translation

| Customer side | Value proposition side | What to record |
|---|---|---|
| Jobs (JTBD) | — | Use ODI outcome form |
| Pains | **Pain relievers** | How the Leader outcome reduces the pain |
| Gains | **Gain creators** | The economic or emotional upside produced |

### EVC formula

EVC = Price of next-best alternative + Value of performance differential − Cost of switching / adopting

Components to quantify:

| Value component | Formula | Example |
|---|---|---|
| **Time saved** | Hours saved × loaded rate × time horizon | 6 hrs/wk × $95/hr × 48 wks = $27,360/yr |
| **Revenue uplift** | Incremental revenue × attribution × probability | $120k deal × 30% attribution × 40% uplift = $14,400 |
| **Cost avoided** | Event probability × event cost | 10% breach chance × $2M impact = $200,000 expected cost |
| **Risk premium** | Reduction in variance × risk-aversion coefficient | Context-specific; usually qualitative |
| **Option value** | Probability of future opportunity × value | Startup moat; B2B enterprise renewal probability |

### Share of value captured

Vendors typically capture 25–60% of the EVC they create, with the rest going to the customer as "consumer surplus" (the reason they bought). Share depends on:

| Factor | Higher share when | Lower share when |
|---|---|---|
| Category maturity | Category is commoditized — wait, inverted: lower when mature | Category is immature — higher share possible |
| Competitive intensity | Few substitutes | Many substitutes |
| Switching cost | High (enterprise contracts, integrations) | Low (consumer, SaaS tools) |
| Value visibility | Customer can't easily measure | Customer can measure and benchmark |

For WTP band: **WTP ≈ Next-best alternative price + (EVC differential × share captured)**.

### When EVC is hard

Emotional, identity-driven, and life-changing categories (luxury, status, wellness, personal transformation) resist EVC math. In these cases, substitute:
- Comparable-category price (what do people pay for similar status signals?)
- Willingness-to-sacrifice (hours, effort, social cost)
- Historical category price ceilings

Flag explicitly when EVC is not calculable. Don't force numbers that don't exist.

---

## 5. Bain 30 Elements of Value

### The pyramid (bottom to top)

| Level | Elements | WTP weight |
|---|---|---|
| **Functional** | Saves time, simplifies, makes money, reduces risk, organizes, integrates, connects, reduces effort, avoids hassles, reduces cost, quality, variety, sensory appeal, informs | Predictable; EVC-calculable |
| **Emotional** | Reduces anxiety, rewards me, nostalgia, design/aesthetics, badge value, wellness, therapeutic value, fun, attractiveness, provides access | Amplifies functional by 1.3–2× |
| **Life-changing** | Provides hope, self-actualization, motivation, heirloom, affiliation/belonging | Amplifies by 2–4× in the right category |
| **Social impact** | Self-transcendence | Rare; amplifies in mission-driven categories |

(B2B version has 40 elements, but same pyramid structure plus Inspirational, Purpose, Vision — relevant for enterprise deals with executive sponsors.)

### Stacking rule

**More Bain elements activated → more WTP resilience.**

A Leader outcome that activates functional-only ("saves time") is cheapest to displace — any cheaper substitute wins. A Leader that stacks functional + emotional + social ("saves time AND makes me look competent AND signals senior status to my team") has 2–4× the WTP resilience and is much harder to churn.

### Stacking test

For each Leader outcome, name all Bain layers it activates. Document the stack.

Example for an AI Chief of Staff product targeting a senior PM:

- **Functional:** saves time (3 hrs/wk pre-meeting prep), reduces effort (no more Slack archaeology)
- **Emotional:** reduces anxiety (walking into meetings prepared), rewards me (showing up sharper than peers)
- **Life-changing:** self-actualization (being the version of myself I want to be at work)
- **Social impact:** (none directly)

Stack = 5 of 30 elements. High WTP resilience relative to a pure-functional "meeting prep automation" framing.

---

## The composed value map per segment

The three-layer model in Phase 3 uses all five frameworks:

**Layer A (Value):**
- 5–15 ODI outcome statements, ranked by opportunity score
- Each classified as Leader / Filler / Killer (Monetizing Innovation)
- Each cross-classified against Kano (must-have / performance / delighter / indifferent / reverse)
- Kano migration horizon for each delighter
- Bain 30 elements activated per Leader (the stack)

**Layer B (Drivers):**
- Named next-best alternative
- EVC math per Leader (or explicit "not calculable" flag)
- Share of value captured (assumption with reasoning)
- Pain intensity and urgency
- Emotional / life-changing / social stakes

**Layer C (Proof signals):**
- See `proof-signals.md` — the unique deliverable

The WTP band hypothesis in Phase 4 follows directly from Layers A + B.
