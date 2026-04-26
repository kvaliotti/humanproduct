# Opportunity Sizing & Sensitivity Analysis

## Sensitivity Analysis Method

### Step 1: Establish Baseline
Document the complete revenue formula with current values:

```
Example (SaaS):
Current MRR = $100,000
= New MRR ($30,000) + Retained MRR ($65,000) + Expansion MRR ($15,000) - Churn ($8,000) - Contraction ($2,000)

Where New MRR = 50,000 visitors x 5% signup x 30% activation x 8% paid conv x $50 ARPA
= 50,000 x 0.05 x 0.30 x 0.08 x $50 = $30,000
```

### Step 2: One-at-a-Time Sensitivity

Hold all drivers constant. Improve ONE driver by a realistic amount. Calculate impact.

**Template:**

| # | Driver | Current | +10% | +25% | +50% | To Benchmark | Revenue Impact (to benchmark) | % Revenue Lift |
|---|--------|---------|------|------|------|-------------|-------------------------------|---------------|
| 1 | Traffic | 50,000 | 55,000 | 62,500 | 75,000 | 80,000 | +$18,000/mo | +18% |
| 2 | Signup conv | 5% | 5.5% | 6.25% | 7.5% | 8% | +$18,000/mo | +18% |
| 3 | Activation | 30% | 33% | 37.5% | 45% | 50% | +$20,000/mo | +20% |
| 4 | Paid conv | 8% | 8.8% | 10% | 12% | 15% | +$26,250/mo | +26% |
| 5 | ARPA | $50 | $55 | $62.5 | $75 | $65 | +$9,000/mo | +9% |
| 6 | Churn rate | 8% | 7.2% | 6% | 4% | 5% | +$3,000/mo | +3% |

### Step 3: Rank by Impact

Sort the table by "Revenue Impact (to benchmark)" descending. The top 2-3 are your priority levers.

### Step 4: Adjust for Effort

For each top lever, estimate effort:

| Effort Level | Description | Timeline | Team Investment |
|---|---|---|---|
| **S (Small)** | Config change, copy tweak, quick experiment | 1-2 weeks | 1-2 people |
| **M (Medium)** | Feature build, new flow, multi-week experiment | 2-6 weeks | 2-4 people |
| **L (Large)** | Major product change, new capability, re-architecture | 2-6 months | 4+ people |
| **XL (Extra Large)** | Strategic initiative, new product line, org change | 6+ months | Cross-functional |

### Step 5: Priority Score

Priority Score = Revenue Impact x (1 / Effort)

Simplified: divide revenue impact by effort multiplier:
- S = 1
- M = 2
- L = 4
- XL = 8

Highest priority score = best bang for buck.

---

## Opportunity Sizing Statement Format

For each priority lever, produce a clear sizing statement:

### Format
> **Lever:** [Driver name]
> **Current:** [value]
> **Target:** [value] based on [benchmark source / realistic estimate]
> **Monthly revenue impact:** [$X]
> **Annual revenue impact:** [$Y]
> **Percentage growth:** [Z%]
> **Confidence:** [High/Medium/Low] based on [data quality and benchmark reliability]
> **Effort:** [S/M/L/XL]
> **Hypothesis:** "We believe [action] will move [metric] from [current] to [target] because [reason]."

### Example
> **Lever:** Activation rate (signup → aha moment)
> **Current:** 30% (measured via Amplitude event tracking)
> **Target:** 45% based on Mixpanel PLG Benchmark Report median for B2B SaaS
> **Monthly revenue impact:** +$15,000 MRR
> **Annual revenue impact:** +$180,000 ARR
> **Percentage growth:** +15% MRR
> **Confidence:** Medium (current measurement reliable, target based on aggregate benchmark)
> **Effort:** M (4-week onboarding redesign project)
> **Hypothesis:** "We believe simplifying the onboarding flow from 7 steps to 3 and adding pre-populated sample data will move activation from 30% to 45% because exit surveys show 'too many setup steps' as the #1 reason users abandon."

---

## Compound Impact Analysis

When improving multiple levers simultaneously (be careful — assumes independence):

```
Current: 50,000 x 5% x 30% x 8% x $50 = $30,000 New MRR

After improving activation (30% → 45%) AND paid conversion (8% → 12%):
Projected: 50,000 x 5% x 45% x 12% x $50 = $67,500 New MRR
Compound impact: +$37,500/mo (+125%)
vs. sum of individual impacts: +$15,000 + $15,000 = +$30,000 (+100%)
Compound effect: +$7,500 additional from interaction
```

**Warning:** Compound projections are optimistic. Use for upside scenario, not for commitments. Drivers are rarely truly independent.

---

## Prioritization Matrix Visual

Plot drivers on a 2x2:

```
                    HIGH IMPACT
                         │
         "BIG BETS"      │     "QUICK WINS"
         High impact,     │     High impact,
         High effort      │     Low effort
         (Strategic)      │     (Do these FIRST)
                         │
    ─────────────────────┼──────────────────── LOW EFFORT
                         │
         "AVOID"         │     "FILL-INS"
         Low impact,     │     Low impact,
         High effort     │     Low effort
         (Don't do)      │     (If spare capacity)
                         │
                    LOW IMPACT
```

Always start with Quick Wins. Then sequence Big Bets. Avoid the bottom-left quadrant.

---

## Benchmark Sources

When the user does not have benchmarks, use these general SaaS benchmarks:

| Metric | Bottom Quartile | Median | Top Quartile | Best-in-Class |
|--------|----------------|--------|-------------|---------------|
| Visitor-to-signup | <2% | 3-5% | 5-10% | 10-15% |
| Signup-to-activation | <15% | 25-35% | 35-50% | 50-70% |
| Free-to-paid (freemium) | <2% | 3-5% | 5-8% | 8-15% |
| Trial-to-paid | <10% | 18-25% | 25-40% | 40-60% |
| Monthly churn (SMB) | >8% | 5-7% | 3-5% | <3% |
| Monthly churn (mid-market) | >5% | 2-4% | 1-2% | <1% |
| Net revenue retention | <90% | 100-110% | 110-125% | 125%+ |
| LTV:CAC | <1:1 | 2-3:1 | 3-5:1 | 5+:1 |
| CAC payback (months) | >18 | 10-15 | 6-10 | <6 |

**Note:** Benchmarks vary significantly by segment (SMB vs. enterprise), market (established vs. emerging), and business model. Always contextualize.
