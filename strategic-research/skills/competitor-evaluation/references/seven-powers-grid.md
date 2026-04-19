# Seven Powers Grid — Diagnostic Guide

Source: Hamilton Helmer, *7 Powers: The Foundations of Business Strategy* (2016).

This reference is the diagnostic spine for the 7 Powers section of each competitor profile. Use it to decide whether a claimed advantage is a **Power** (persistent structural moat), an **operational lead** (real today, copyable on a useful horizon), or **asserted-only** (no structural basis).

## What qualifies as a Power

A Power must pass two tests simultaneously:

1. **The Benefit** — it increases cash flow (higher prices, lower costs, or lower investment).
2. **The Barrier** — a competitor cannot replicate it with capital or effort alone over a relevant time horizon.

If only the Benefit is present, it's an operational lead. If only the Barrier is alleged with no real cash-flow consequence, it's asserted-only.

The Barrier tests — use all four:

| Test | Question | If no → |
|---|---|---|
| **Persistence** | Does the advantage hold for 5+ years against smart, funded competitors? | Operational lead |
| **Hardness** | Is replication blocked by structure, not by effort or money? | Operational lead |
| **Self-reinforcement** | Does usage or scale make the advantage deeper over time? | Suspect — verify the structural mechanism |
| **Category fit** | Does the Power operate in this category's economics (margins, purchase cadence, buyer behavior)? | Re-classify or drop |

## The Seven Powers

### 1. Scale Economies

**Definition.** Per-unit cost declines as volume increases, and the leader's per-unit cost is structurally lower than any challenger's.

**Benefit.** Lower cost at equal price → higher margin, or lower price at equal quality → share gain.

**Barrier.** A challenger must replicate the leader's volume to match unit economics — which they cannot, because the leader already has it and will defend.

**Detection signals.** Fixed costs are a large share of total cost; learning curves materially bend with cumulative volume; distribution/logistics density matters; COGS curves diverge by scale.

**Common confusions.**
- **Big ≠ Scale Economies.** A $10B company without a cost curve that bends is just big.
- **Cloud infra ≠ automatic scale advantage.** If everyone rents from AWS, AWS has the scale Power, not your product.

**Rubric.**

| Verdict | Evidence required |
|---|---|
| **Confirmed** | Public or triangulated unit economics showing meaningful per-unit cost gap vs. nearest competitor, plus evidence the gap widens with volume |
| **Partial** | Scale curve exists but gap is small, or competitors are approaching parity |
| **Operational lead** | Leader is operationally efficient but without a structural cost curve |
| **Asserted-only** | Claims "economies of scale" with no unit-cost evidence |

### 2. Network Economies

**Definition.** The value of the product to each user rises as more users join the same network (or compatible networks).

**Benefit.** Price premium and/or retention, because the alternative is a smaller, less valuable network.

**Barrier.** A challenger must bootstrap a network from scratch — and each user's utility is lower on the small network, which keeps it small (the cold-start trap).

**Detection signals.** User interactions with other users drive the value (marketplaces, communication tools, social); cross-side effects on two-sided platforms; "they won't switch until their [team / clients / friends] switch" appears repeatedly in churn-prevention evidence.

**Common confusions.**
- **Many users ≠ Network Economies.** Utility software with millions of users isn't networked unless users gain value from each other.
- **Viral growth ≠ Network Economies.** Virality is a distribution mechanic, not a moat.
- **Local networks.** Some networks are local (delivery, ride-hail). Verify the geographic unit of competition — a global leader may be weak in a specific city.

**Rubric.**

| Verdict | Evidence required |
|---|---|
| **Confirmed** | Documented N-of-N or N-of-(N+1) utility function; churn evidence citing network loss; competitor attempts to replicate have failed at bootstrap |
| **Partial** | Network exists but is thin, or utility per edge is low |
| **Operational lead** | Active community but no structural N-dependence |
| **Asserted-only** | "Community" invoked without utility mechanics |

### 3. Counter-Positioning

**Definition.** The newcomer adopts a new business model that the incumbent cannot copy without damaging its existing business.

**Benefit.** The newcomer captures a segment (often the under-served or bottom) without incumbent retaliation.

**Barrier.** If the incumbent mirrors the newcomer, it cannibalizes its profitable base — rational executives therefore choose not to respond.

**Detection signals.** Incumbent has a high-margin legacy business that would be eroded by the newcomer's model; incumbent publicly dismisses the newcomer ("those customers aren't our customers"); newcomer's pricing, channel, or bundling is structurally at odds with incumbent's P&L.

**Common confusions.**
- **"They're slow to respond" ≠ Counter-Positioning.** Incumbent must be structurally prevented from responding, not merely sluggish.
- **Cheap disruption ≠ Counter-Positioning automatically.** Verify the P&L conflict, not just a price gap.

**Rubric.**

| Verdict | Evidence required |
|---|---|
| **Confirmed** | Documented P&L mechanism by which incumbent response would destroy more value than it would capture; incumbent has already chosen not to respond despite clear awareness |
| **Partial** | Incumbent is conflicted but has not yet ruled out response; response would hurt but not structurally |
| **Operational lead** | Newcomer is faster or cheaper, but incumbent could copy if motivated |
| **Asserted-only** | "Incumbents will never respond because they're dinosaurs" (narrative, not economics) |

### 4. Switching Costs

**Definition.** The user incurs meaningful cost — financial, procedural, cognitive, or relational — to move to a competitor.

**Benefit.** Retention and pricing power on installed base.

**Barrier.** A challenger must compensate the user for the switching cost, shrinking their margin or requiring capital to subsidize migration.

**Types.**
- **Financial** — penalties, unamortized capex, integration rebuild cost.
- **Procedural** — retraining, re-certifying, redesigning workflows.
- **Relational** — embedded contacts, shared data ownership, reputational cost of change.

**Detection signals.** Long retention on an average product; "too painful to switch" in churn-prevention notes; high implementation hours per customer; deep integrations with systems of record (ERP, CRM, billing).

**Common confusions.**
- **Friction ≠ switching cost.** If the friction is on both sides of the decision (the alternative is equally painful to set up), it's category friction, not Power.
- **"Our customers love us" ≠ Switching Costs.** Affection is not a moat.

**Rubric.**

| Verdict | Evidence required |
|---|---|
| **Confirmed** | Measurable retention gap vs. category, with behavioral evidence of switch-attempts aborted; integration depth documented |
| **Partial** | Some customers are deeply embedded (enterprise), others are not (SMB); Power is segment-conditional |
| **Operational lead** | Good onboarding and support create high retention, but without structural embedding |
| **Asserted-only** | "High NPS" invoked as a moat |

### 5. Branding

**Definition.** A durable brand attribute justifies a willingness-to-pay premium for functionally identical or near-identical alternatives.

**Benefit.** Price premium sustained against equivalent offerings.

**Barrier.** Brand takes decades of consistent investment to build in the relevant consumer's affective memory; money alone cannot buy the conditioning.

**Detection signals.** Buyers pay materially more for a logo on equivalent-spec goods; brand appears in buyer self-identity ("I'm a [brand] person"); brand resists crisis with minimal long-term damage.

**Common confusions.**
- **Awareness ≠ Brand Power.** Everyone knows Kodak.
- **B2B rarely has Brand Power.** B2B brand affects consideration (top of funnel) and risk-reduction at enterprise scale, but rarely generates sustained price premium. Be skeptical.
- **"Our category is a brand category" is a red flag.** Verify with WTP data, not marketing materials.

**Rubric.**

| Verdict | Evidence required |
|---|---|
| **Confirmed** | Multi-year price premium on near-identical goods, with buyer surveys or behavioral data attributing the premium to brand associations |
| **Partial** | Brand aids consideration but not pricing; concentrated in one segment |
| **Operational lead** | Strong marketing execution, but switchable |
| **Asserted-only** | "We have great NPS" or "buyers trust us" with no premium evidence |

### 6. Cornered Resource

**Definition.** Preferential access to a valuable resource — talent, patent, contract, license, dataset, location, raw material — that the competitor cannot obtain.

**Benefit.** The resource delivers a product or cost structure the competitor cannot replicate.

**Barrier.** The resource is exclusive or practically unavailable on the market.

**Detection signals.** A specific irreplaceable person, IP, dataset, or agreement; legal or physical constraints on replicating it; loss of the resource would materially damage the company.

**Common confusions.**
- **"Great engineers" ≠ Cornered Resource.** Talent clusters matter, but individual engineers are replaceable on a relevant time horizon unless a specific individual is the mechanism.
- **"Proprietary data" ≠ Cornered Resource automatically.** Ask: could a competitor reconstruct equivalent data via usage, purchase, or scraping within 2–3 years? If yes, it's an operational lead.

**Rubric.**

| Verdict | Evidence required |
|---|---|
| **Confirmed** | Named specific resource, documented exclusivity or structural unavailability, demonstrated cash-flow dependence on the resource |
| **Partial** | Resource is hard to obtain but not exclusive; alternatives exist |
| **Operational lead** | "We hire well" or "our data is rich" without structural exclusivity |
| **Asserted-only** | Vague claims of proprietary anything |

### 7. Process Power

**Definition.** Embedded organizational capability that cannot be copied by observing or hiring away pieces. It lives in coordinated systems, tacit knowledge, and slow-built practice.

**Benefit.** Sustained quality, cost, or speed advantage that competitors cannot match by imitation.

**Barrier.** Long learning periods, path-dependent investments, and hysteresis — competitors can buy the parts but cannot assemble the whole.

**Detection signals.** Decades of iteration on a specific operational system (e.g., Toyota Production System); competitor attempts to copy have failed publicly; insiders who leave cannot reproduce the advantage elsewhere.

**Common confusions.**
- **"Great culture" ≠ Process Power.** Without a measurable operational consequence, it's vibes.
- **Short company age.** True Process Power usually takes 10+ years to build. Young companies asserting it are almost always wrong.

**Rubric.**

| Verdict | Evidence required |
|---|---|
| **Confirmed** | Multi-decade operational history, documented competitor attempts to copy that failed, measurable operational gap (quality, cost, throughput) |
| **Partial** | Strong ops practice present, but not yet category-defining |
| **Operational lead** | Good execution; team quality |
| **Asserted-only** | "Culture of excellence" |

## The Category Gravity Lens

Before declaring any Power confirmed, check the category structure:

- If 3+ shortlisted competitors hold the same Power, it is a **category rule** — the anchor either needs that Power or a counter-position against it. The rule isn't an advantage; it's an entry ticket.
- If no one in the shortlist holds any Power at all, the category is **structurally rivalrous** — margins are durable only through operational excellence, and the strategic question is whether the anchor can stay ahead operationally (fast decay risk).
- If exactly one competitor holds 3+ Powers, the category is likely **already decided** — re-examine whether the anchor should compete directly or counter-position.

## Operational-lead vs Power — the defaults

Default to **operational lead** unless the structural mechanism is named and verified. This is a feature, not a bug:

- Operational leads are real advantages — they drive current P&L. Naming them correctly prevents overestimating durability.
- Power claims without mechanism are a form of self-flattery that mis-informs allocation decisions.
- The downstream synthesis skill allocates investment. It needs a truthful Powers grid, not an aspirational one.

## Evidence weighting

| Evidence type | Weight | Example |
|---|---|---|
| **Behavioral** | 3× | Churn patterns, won/lost data, price realization, retention curves |
| **Pattern** | 2× | Multiple independent reviewers citing the same mechanism |
| **Stated by third parties** | 1× | Analyst reports, press coverage |
| **Stated by the company** | 0.5× | Homepage, pitch decks, earnings calls |
| **Self-declared "moat"** | 0× (priors only) | The word "moat" in a pitch deck is a flag to verify, not evidence |

Require at least one behavioral or two pattern signals to classify any Power as Confirmed.

## Output format for the 7 Powers section

For each competitor, produce a 7-row grid:

| Power | Verdict | Mechanism (one line) | Evidence tier | Confidence |
|---|---|---|---|---|
| Scale Economies | Operational lead | Cost/user flat above 10k seats; no volume curve | Behavioral | 70% |
| Network Economies | Asserted-only | Claims "community moat"; utility not N-dependent | Stated only | 40% |
| Counter-Positioning | N/A | No incumbent P&L conflict at play | — | 90% |
| Switching Costs | Partial | Enterprise integrations; SMB churns at 18% annually | Behavioral | 75% |
| Branding | Asserted-only | Strong NPS; no price premium vs. peers | Stated only | 55% |
| Cornered Resource | N/A | No named exclusive asset | — | 95% |
| Process Power | N/A | 4-year-old company — insufficient time | — | 90% |

Close with one line: **"Unfair advantage call: 1 partial Power (Switching Costs, enterprise-only). Operational lead elsewhere. Confidence 70%."**
