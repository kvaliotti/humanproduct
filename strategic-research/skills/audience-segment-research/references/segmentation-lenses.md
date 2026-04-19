# Segmentation Lenses Catalog

A catalog of segmentation lenses, when each works, when each fails. Use this in Phase 3 to generate candidates, not as a menu to pick from blindly.

**Golden rule (Dunford):** a lens is only viable if the segments it produces are **identifiable** (you can build a prospect list) AND have a **common, specific, unmet, important need** (they care more than the average buyer). Lenses that fail both are descriptive, not strategic.

---

## Lens 1 — Workflow-shape

Cut on the **shape** of the user's work: volume, cadence, complexity, scale, multi-party, asynchronous vs. synchronous, repeatable vs. ad-hoc.

**Examples:**
- Invoice volume: 5/month vs. 500/month
- Campaign cadence: monthly launches vs. weekly refreshes
- Content throughput: 1 piece/week vs. 20/day
- Meeting load: 5 meetings/week vs. 30+
- Team structure: solo operator vs. small team vs. handoff chain

**When it works:**
- Product value scales with workflow intensity
- Users at different volumes have genuinely different needs, not just the same need at different sizes
- Downstream question is packaging tiers

**When it fails:**
- When needs are the same across volumes (then it's just pricing tiers, not segmentation)
- When volume is a dependent variable, not a causal one

**Dunford example:** "Sends many invoices per month" vs. "sends a few" — the first segment's value from QuickBooks integration is categorically different.

---

## Lens 2 — Maturity / sophistication

Cut on how sophisticated the user is about the problem they're solving.

**Schwartz's five levels of awareness** (useful for positioning and messaging):

| Level | User state | Implication |
|---|---|---|
| Unaware | Doesn't know they have the problem | Content-heavy top-of-funnel |
| Problem-aware | Knows the problem, not the solution class | Education-led |
| Solution-aware | Knows solution classes, not vendors | Comparison content |
| Product-aware | Knows vendors, comparing | Differentiation + proof |
| Most aware | Wants to buy from you specifically | Frictionless purchase |

**Also: DIY vs. outsourced vs. automated** — where a segment currently sits on the build/buy/hire spectrum for this problem.

**When it works:**
- The market has a clear maturity curve
- Different maturity levels buy different products at different prices
- Downstream question is "who to sell to first?"

**When it fails:**
- When maturity is uniform across the market
- When sophistication doesn't correlate with willingness to buy

---

## Lens 3 — Use-case / Jobs-to-be-done (JTBD)

Cut on the job the user hires the product to do. Format: *"When [situation], I want to [motivation], so I can [outcome]."*

**Examples for a calendar app:**
- "When a new project kicks off, I want to find three mutually-available 30-min slots for 6 people, so I can get the kickoff on the books today."
- "When I come back from PTO, I want to quickly see what I missed and what's urgent, so I can re-enter work without drowning."

**When it works:**
- The same product serves multiple distinct jobs
- Different jobs have different champions, different triggers, different alternatives
- Downstream question is feature prioritization per segment

**When it fails:**
- When there's essentially one job (don't force multiple)
- When jobs don't map to distinct buyer groups — everyone does all the jobs

---

## Lens 4 — Organizational context (B2B)

Cut on attributes of the buying organization: stage (seed / Series A / growth / scale / enterprise), size (employees, revenue, ACV), regulatory regime (PCI-DSS, HIPAA, SOC2, EU DPA, GDPR), ecosystem (Mac vs. Windows, Salesforce vs. HubSpot, AWS vs. GCP vs. Azure), geography.

**When it works:**
- The regulatory or ecosystem context creates a hard must-have
- Stage-specific workflows differ structurally (a pre-seed startup buys differently from a 5000-person enterprise)
- Downstream question is GTM motion per segment

**When it fails:**
- When context doesn't actually change the buying decision (then it's demographic noise)
- When the segmentation is just "big vs. small" without a behavioral difference

**Dunford example:** "European banks" vs. "US banks" for security software — different regulatory timing, different specific needs.

---

## Lens 5 — Stakeholder archetype (B2B)

Cut on the *role and authority* of the primary decision-maker: individual contributor, team lead, director, VP, C-level. Or: user-led vs. ops-led vs. security-led vs. finance-led buying.

**When it works:**
- Same product sold into different org layers with different procurement processes
- A single company can buy different products from the same vendor through different roles
- Downstream question is sales motion (PLG, sales-led, hybrid)

**When it fails:**
- When one role always buys across all customer types
- When the lens overlaps heavily with org size (collapse to Lens 4)

---

## Lens 6 — Trigger-to-buy

Cut on the event that pushed the customer from *tolerating the problem* to *actively looking for a solution.*

**Common triggers:**
- New hire in a role that owns the problem
- Incident (breach, outage, failed audit, viral negative review)
- Scale threshold (passed X users, Y revenue, Z employees)
- Tool death (deprecation, acquisition, price hike of incumbent)
- Regulation change
- Competitive pressure
- New-year planning cycle

**When it works:**
- Triggers cluster cleanly — most buyers arrive through 2–3 triggers
- Trigger predicts urgency, budget, and feature priorities
- Downstream question is outbound timing and messaging

**When it fails:**
- When triggers are random or unobservable
- When the same trigger produces buyers across all segments (no differentiation)

---

## Lens 7 — Switch-from (competitive alternative)

Cut on *what the user would use if the product didn't exist.*

**Alternative classes:**
- Do nothing / tolerate
- Spreadsheet / docs / notes
- Internal build
- Agency or freelancer
- Incumbent SaaS (named vendor)
- Generic adjacent tool repurposed (e.g., Notion used as a CRM)

**When it works:**
- Customers genuinely cluster by which alternative they displace
- Each alternative class has different switching costs, objections, and value perceptions
- Downstream question is positioning — Head-to-Head vs. Big Fish Small Pond vs. New Game

**When it fails:**
- When "do nothing" dominates all segments (then trigger-to-buy is a better cut)
- When users displace multiple alternatives simultaneously without a dominant one

**Dunford's test:** If two customer types name radically different alternatives, they are probably different segments.

---

## Lens 8 — Two-lens hybrids

Acceptable when one lens alone under-specifies. Examples that often work:

- **Workflow-shape × Sophistication** — e.g., high-volume but low-sophistication ("factory-busy but manual") vs. high-volume high-sophistication ("already automated elsewhere")
- **JTBD × Org context** — e.g., "kickoff scheduling" in startups vs. enterprises
- **Trigger × Stakeholder archetype** — e.g., breach-triggered CISO buying vs. audit-triggered Finance buying
- **Switch-from × Workflow-shape** — e.g., displacing a spreadsheet at 5 users vs. displacing Salesforce at 500

Never more than two. A three-lens matrix is unreadable and pretends to precision it doesn't have.

---

## Anti-lenses (reject as primary)

| Lens | Why Dunford rejects as primary |
|---|---|
| Pure demographics ("men 18–30") | Doesn't predict who cares |
| Pure firmographics ("100–500 employees") | Same |
| Vague psychographics ("design-forward companies") | Not identifiable |
| Investor-vision segments ("future AI-native orgs") | Not a present-tense buyer |
| Vendor-defined categories ("ABM buyers") | Customers rarely self-describe this way |

These can **describe** a segment but cannot **define** one. If the winning lens keys on any of these, rewrite it.

---

## Scoring rubric

Score each candidate lens 1–5 on four criteria. Pick the highest total; break ties on downstream actionability.

| Criterion | Bad (1) | Good (5) |
|---|---|---|
| **Identifiability** | Can't build a prospect list | Mechanical list-build from public attributes |
| **Care intensity** | Members care equally to general market | Specific, unmet, important, common need |
| **Behavioral grounding** | Keys on what people say | Keys on what people do |
| **Downstream actionability** | WTP / positioning can't use it | Segments have distinct price bands, triggers, messaging |

## Meta-note

The catalog is not exhaustive. If the space suggests a different cut — **tech-stack dependency**, **compliance posture**, **team composition archetype** — use it. The catalog is a starting point, not a constraint.

When tempted to pick the safest lens (usually "company size"), pause and ask whether it's actually right. Safe lenses produce safe (already-known) insights.
