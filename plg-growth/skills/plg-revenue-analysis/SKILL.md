---
name: plg-revenue-analysis
description: "Decompose revenue into a driver tree for ANY revenue model, identify highest-leverage branches, and size opportunities. Use when someone asks about revenue levers, growth opportunities, MRR analysis, or which metric to focus on."
---

# PLG Revenue Analysis

## Purpose

You decompose a product's revenue into a mathematical driver tree, populate it with data, run sensitivity analysis, identify the 2-3 highest-leverage branches, size the opportunities, and recommend team structuring. This works for ANY revenue model — SaaS, transactional, marketplace, usage-based, hybrid, ad-supported, or freemium+enterprise.

## When to Invoke

Trigger phrases:
- "analyze my revenue levers"
- "revenue driver tree"
- "where are my biggest growth opportunities"
- "revenue decomposition"
- "PLG revenue analysis"
- "which lever should I focus on"
- "MRR analysis" / "revenue tree" / "growth levers"
- "unit economics" / "LTV analysis" / "CAC analysis"

## Structured Problem-Solving Backbone

1. **Issue Trees (MECE)** — revenue decomposed into mutually exclusive, mathematically complete branches
2. **Hypothesis Trees** — hypothesize which branches have highest leverage before analyzing
3. **Driver Disaggregation** — separate direct (mathematical: x, +, -, /) drivers from indirect (behavioral/correlational) drivers
4. **80/20 Prioritization** — 2-3 branches that drive the most revenue sensitivity
5. **So-What Synthesis (Minto Pyramid)** — lead with the opportunity, then the analysis, then the data
6. **Hypothesis-Driven Work Plans** — each recommendation ties to a testable hypothesis about revenue impact

## Step-by-Step Methodology

### Step 1: Identify Revenue Model and Build Appropriate Tree

Load the revenue tree templates:
> Read `references/revenue-tree-templates.md`

Ask the user: "What is your primary revenue model?" Then select and customize the appropriate tree.

| Revenue Model | Top-Level Formula |
|---|---|
| SaaS/Subscription | Revenue = New MRR + Retained MRR - Churned MRR + Expansion MRR - Contraction MRR + Reactivation MRR |
| Transactional/Marketplace | Revenue = Transactions x AOV, where Transactions = Traffic x Conversion x Frequency |
| Usage-based | Revenue = Active Users x Usage per User x Price per Unit |
| Hybrid | Revenue = Recurring Base + Transactional Top-up + Expansion |
| Ad-supported | Revenue = DAU x Sessions/DAU x Impressions/Session x CPM |
| Freemium + Enterprise | Revenue = Self-serve Revenue + Sales-assisted Revenue (parallel trees) |

For SaaS specifically, load the detailed decomposition:
> Read `references/saas-mrr-lever-trees.md`

### Step 2: Decompose Each Driver Into Sub-Drivers

Continue decomposing until you reach actionable levers. Rules:

1. **MECE at every level.** No overlaps, no gaps.
2. **Mark each split as direct or indirect:**
   - **Direct (mathematical):** Connected by x, +, -, /. Moving the driver MECHANICALLY moves revenue.
   - **Indirect (behavioral/correlational):** Influences a direct driver but the relationship is not purely mathematical. (e.g., "better onboarding" influences "activation rate" which is a direct driver)
3. **Stop decomposing when you reach a lever the team can ACT on.** (e.g., "signup form conversion rate" is actionable; "revenue" is not)
4. **Include both product levers and business levers.** Product levers = things you build. Business levers = pricing, packaging, channels, campaigns.

### Step 3: Populate With Data

For each leaf-level driver, gather:

| Data Point | What to Ask |
|---|---|
| **Current level** | "What is the current value of this metric?" |
| **Trend** | "Is this improving, declining, or flat over the last 3-6 months?" |
| **Benchmark** | "How does this compare to industry/peer benchmarks?" |
| **Confidence** | "How reliable is this number? (Measured precisely? Estimated? Unknown?)" |

If the user does not have data for a driver:
- Note it as a gap
- Use industry benchmarks as proxy (provide them from reference files)
- Recommend measuring it as an action item
- Do NOT skip the branch — unknown drivers are often the highest-leverage ones

### Step 4: Sensitivity Analysis and Prioritization (80/20)

Load the opportunity sizing template:
> Read `references/opportunity-sizing-template.md`

For each leaf-level driver, calculate:

**Sensitivity = "If this driver improves by X%, what is the revenue impact?"**

Method:
1. Take the current revenue formula
2. Hold all other drivers constant
3. Improve the target driver by a realistic amount (10%, 20%, 50%, or to benchmark level)
4. Calculate the delta in revenue

**Prioritization matrix:**

| Driver | Current | Realistic Target | Revenue Impact ($) | Effort (S/M/L) | Priority |
|--------|---------|------------------|--------------------|-----------------|----------|
| [Driver A] | X | Y | $Z | M | P1 |
| [Driver B] | X | Y | $Z | S | P1 |
| [Driver C] | X | Y | $Z | L | P2 |

**80/20 rule:** Identify the 2-3 drivers where:
- Revenue impact is largest
- Current performance is furthest below benchmark
- Improvement effort is reasonable (not "rebuild the entire product")

These are your priority levers.

**Opportunity sizing statement:** For each priority lever, produce:
> "If [metric] moves from [current] to [target], monthly revenue impact is [$X], representing [Y%] growth. Annualized: [$Z]."

### Step 5: Team Structuring

Load the team structuring guide:
> Read `references/team-structuring.md`

Based on team size and priority levers, recommend structure:

**Small team (< 5 growth/product people):**
- Focus on single most sensitive lever
- Or: cross-prioritize top 2 levers if they share dependencies
- One person owns the metric, everyone contributes

**Big team (5+ growth/product people):**
- Option A: Organize by revenue type (New, Retained, Expansion — each has a pod)
- Option B: Organize by metrics cluster (Acquisition team, Activation team, Monetization team)
- Option C: Dedicated owner per priority lever with shared resources

### Step 6: Produce Revenue Analysis Brief

Output structure:

```
## Revenue Analysis Brief

### Revenue Model: [type]
### Current Revenue: [$X MRR / $Y ARR]

### Revenue Driver Tree
[Visual tree or table showing full decomposition]

### Data Summary
| Driver | Current | Benchmark | Gap | Trend |
|--------|---------|-----------|-----|-------|
| ... | ... | ... | ... | ... |

### Priority Levers (80/20)

**Lever 1: [Name]**
- Current: [value]
- Target: [value] (benchmark: [source])
- Revenue impact: [$X/month] = [Y% growth]
- Hypothesis: "We believe [specific claim]. If true, [action] will move [metric] from [A] to [B]."
- First action: [specific next step]

**Lever 2: [Name]**
[same format]

**Lever 3: [Name]**
[same format]

### Opportunity Summary
Total addressable opportunity from top 3 levers: [$X/month]
Combined growth potential: [Y%]

### Team Recommendation
[Structure recommendation based on team size]

### Data Gaps
[Metrics that need to be instrumented/measured]

### Next Steps
1. [Action] → tests [hypothesis] → expected impact [$X]
2. [Action] → tests [hypothesis] → expected impact [$X]
3. [Action] → tests [hypothesis] → expected impact [$X]
```

## Beyond-Course Extensions

### Unit Economics Analysis
When the user wants deeper financial analysis:

**LTV (Lifetime Value):**
- Simple: ARPA / Monthly Churn Rate
- Better: ARPA x Gross Margin % / Monthly Churn Rate
- Best: Cohort-based LTV curves by segment

**CAC (Customer Acquisition Cost):**
- Blended: Total Sales & Marketing Spend / New Customers
- By channel: Channel Spend / Channel-attributed New Customers
- Fully loaded: Include onboarding, implementation, support for new customers

**LTV:CAC Ratio:**
- < 1:1 = losing money on every customer (crisis)
- 1:1 to 3:1 = break-even to healthy
- 3:1 to 5:1 = healthy and efficient
- > 5:1 = potentially under-investing in growth

**CAC Payback Period:**
- Months to recover CAC = CAC / (ARPA x Gross Margin %)
- < 6 months = excellent (typical PLG)
- 6-12 months = good
- 12-18 months = acceptable for SLG
- > 18 months = concern

### Cohort Revenue Analysis
When historical data is available:
- Build revenue cohort curves (revenue per cohort over time)
- Identify if newer cohorts are better or worse than older ones
- Separate expansion from retention in cohort view
- Look for "vintage effects" — external factors affecting specific cohorts

## Connection to Other Skills

| Skill | Handoff |
|-------|---------|
| `plg-orchestrator` | Receives diagnostic context, returns priority levers for routing |
| `plg-readiness` | Revenue analysis assumes PLG viability; if not assessed, route to readiness first |
| `acquisition-model-selector` | If top lever is acquisition-related, route to model selector |
| Future domain skills | Priority levers map to specific funnel stages → route to domain skill |

## Inputs Required

- Revenue model type
- Current revenue (MRR/ARR or equivalent)
- As many driver metrics as available (activation rate, churn rate, ARPU, etc.)
- Team size and current structure
- Biggest known pain point (helps prioritize)

## Anti-Patterns

- **Analyzing without data:** The tree is still valuable as a framework even without data. But flag every gap. Unknown drivers are often the most important ones.
- **Too many priorities:** The whole point is 80/20. If the user has 7 priority levers, they have zero. Force rank to 2-3.
- **Confusing direct and indirect drivers:** Clearly label which relationships are mathematical and which are behavioral. This affects how you size opportunities.
- **Ignoring effort:** A 10x revenue-impact lever that takes 2 years to move is less useful than a 2x lever you can move in 2 weeks. Always pair impact with effort.
