# Experiment Design Template

Complete template for designing rigorous PLG experiments. Every experiment must fill out each section before launch. Skip nothing -- incomplete experiments produce uninterpretable results.

---

## 1. HYPOTHESIS

Write a specific, falsifiable hypothesis tied to a lever in the issue tree or revenue driver tree.

**Format:**
> "We believe that [change] will cause [effect] for [audience] because [rationale from issue tree]."

**Good example:**
> "We believe that replacing the 5-field signup form with Google OAuth will increase signup completion rate by 15% for visitors from paid ads because our funnel data shows 40% drop-off at the password creation step, and 72% of our target users have Google Workspace accounts."

**Bad example:**
> "We believe that improving the signup flow will increase conversions." (Not specific -- what change? What effect size? What audience? What evidence?)

**Checklist:**
- [ ] Change is specific and implementable
- [ ] Effect is quantified (even if estimated)
- [ ] Audience is defined
- [ ] Rationale cites data, research, or a specific issue tree branch
- [ ] Hypothesis is falsifiable -- you can clearly say it was wrong

---

## 2. METRIC

### Primary Metric
The ONE metric this experiment is designed to move. Must be:
- Directly influenced by the change
- Measurable within the experiment duration
- Connected to a revenue driver tree branch

**Examples by AARMS stage:**
| Stage | Primary Metric Examples |
|-------|----------------------|
| Acquisition | Signup completion rate, visitor-to-signup conversion |
| Activation | Activation rate (% reaching key action), TTV (time to value) |
| Retention | D7/D30 retention rate, weekly active rate |
| Monetisation | Free-to-paid conversion, upgrade rate, ARPA |
| Satisfaction | NPS, CSAT, CES, support ticket rate |

### Guardrail Metrics
Metrics that MUST NOT degrade. If guardrails break, the experiment fails even if the primary metric improves.

**Common guardrails:**
- **Retention guardrail:** D7 or D30 retention must not drop by more than [X]%
- **Revenue guardrail:** ARPA or LTV must not decrease
- **Quality guardrail:** Support ticket rate must not increase by more than [X]%
- **Experience guardrail:** CSAT/NPS must not drop
- **Engagement guardrail:** Session frequency or depth must not decline

**Rule of thumb:** Include at least 2 guardrails -- one downstream metric (retention or revenue) and one quality metric (support tickets or satisfaction).

### Leading vs Lagging Distinction

| Type | Definition | Example | Use For |
|------|-----------|---------|---------|
| Leading | Changes quickly, predicts future outcome | Activation rate, feature adoption | Primary metric in short experiments |
| Lagging | Takes time to manifest, represents true outcome | Revenue, LTV, churn rate | Guardrail or long-term follow-up |

**Guidance:** Use leading indicators as primary metrics for experiments under 4 weeks. Track lagging indicators as guardrails or in post-experiment follow-up (check 30/60/90 days later).

---

## 3. AUDIENCE

### Target Segment
Define precisely who enters the experiment:
- **User type:** New signups, existing free users, trial users, paid users, specific plan
- **Segment criteria:** Company size, industry, geography, acquisition channel, activation status
- **Exclusions:** Who should NOT be in the experiment? (e.g., internal users, enterprise accounts, users already exposed to similar test)

### Sample Size Calculation

**Formula:**
```
n = (Z_alpha/2 + Z_beta)^2 * 2 * p * (1-p) / MDE^2
```

**Practical defaults (use these unless you have reason to change):**
- Confidence level: 95% (Z = 1.96)
- Statistical power: 80% (Z = 0.84)
- MDE: The smallest effect worth detecting (see section 6)

**Quick reference table (two-sided test, 95% confidence, 80% power):**

| Baseline Rate | MDE (absolute) | Sample Size Per Variant |
|--------------|----------------|------------------------|
| 5% | 1% (5% -> 6%) | 4,770 |
| 5% | 2% (5% -> 7%) | 1,250 |
| 10% | 2% (10% -> 12%) | 3,820 |
| 10% | 5% (10% -> 15%) | 690 |
| 20% | 3% (20% -> 23%) | 4,510 |
| 20% | 5% (20% -> 25%) | 1,720 |
| 50% | 5% (50% -> 55%) | 3,920 |

**For conversion metrics:** Use proportions formula above.
**For continuous metrics (e.g., revenue, time):** Use means formula: n = (Z_alpha/2 + Z_beta)^2 * 2 * sigma^2 / delta^2 where sigma = standard deviation of the metric, delta = minimum detectable difference in means.

### Randomization Method
- **User-level:** Each user independently assigned. Best for individual-user products.
- **Account-level:** All users in an account see the same variant. Required when the feature affects team behavior.
- **Session-level:** Only for very short-lived experiments (e.g., landing page copy). Risk: same user sees different variants across sessions.
- **Cluster-level:** Randomize by geography, company size, or cohort. Use when individual randomization creates spillover effects.

**Default:** User-level randomization unless the feature involves collaboration or team dynamics.

---

## 4. VARIANT

### Control
Describe the current experience precisely:
- What does the user see/experience today?
- What is the current flow, copy, design, logic?
- Screenshot or mockup if possible

### Treatment
Describe the change precisely:
- What exactly is different from control?
- Be specific: "CTA button changes from 'Start Free Trial' to 'Start Building Free'" not "change the CTA"
- One change per treatment (unless you have a strong reason for bundling)

### Why Treatment Should Win
Articulate the causal mechanism:
- What behavioral principle supports this? (B=MAT component, cognitive bias, UX heuristic)
- What data supports this? (User research, funnel analysis, competitive analysis, best practice)
- What is the chain: change -> user perception/behavior -> metric movement?

**One change per experiment.** If you bundle multiple changes, you cannot attribute the effect. Exception: when changes are tightly coupled (e.g., new onboarding flow where steps depend on each other).

---

## 5. DURATION

### Minimum Duration Calculation
```
Minimum days = (Sample size per variant * Number of variants) / Daily eligible traffic
```

**Example:** 4,000 per variant * 2 variants = 8,000 total. Daily eligible traffic = 500 users/day. Minimum = 16 days.

### Business Cycle Considerations
- **Include full weeks:** Always run for complete weeks to capture weekday/weekend patterns. Round UP to the nearest full week.
- **Avoid holidays:** Do not start or end experiments during holidays, major events, or marketing campaigns that distort traffic.
- **Seasonality:** If your product has monthly billing cycles, run across at least one full cycle.
- **Payroll cycles:** For B2B products, include at least one payroll period if testing pricing or payment features.

### Maximum Duration
- **Cap at 4 weeks** for most experiments. Beyond 4 weeks, external factors contaminate results.
- **Exception:** Retention or monetization experiments may need 6-8 weeks for lagging metrics to manifest.
- **Anti-peeking rule:** Do NOT check results before minimum duration unless guardrail alerts fire. Pre-commit to a check date.

### Duration Decision Table

| Scenario | Recommended Duration |
|----------|---------------------|
| High traffic, leading metric | 2 weeks (minimum 1 full week) |
| Medium traffic, leading metric | 3-4 weeks |
| Low traffic, leading metric | Consider qualitative test instead |
| Any traffic, lagging metric (revenue, retention) | 4-8 weeks |
| Fake door / painted door | 1-2 weeks |
| Prototype / user test | 3-5 days |

---

## 6. SUCCESS CRITERIA

### Minimum Detectable Effect (MDE)
The smallest change worth detecting. This is a BUSINESS decision, not a statistical one.

**How to set MDE:**
1. **Revenue tree sensitivity:** If this metric improves by X%, how much revenue impact? Use the revenue driver tree to calculate.
2. **Implementation cost:** What is the ongoing cost of maintaining this change? The revenue impact must exceed it.
3. **Opportunity cost:** Could you run a higher-impact experiment instead?

**Rule of thumb:** MDE should be the smallest improvement that would make you say "yes, this was worth building and maintaining."

**Common MDE ranges:**
| Metric Type | Typical MDE Range |
|------------|------------------|
| Signup conversion | 2-5% relative improvement |
| Activation rate | 3-10% relative improvement |
| Retention (D30) | 2-5% relative improvement |
| Free-to-paid conversion | 5-15% relative improvement |
| ARPA | 3-10% relative improvement |

### Statistical Significance Threshold
- **Default:** p < 0.05 (95% confidence)
- **High-stakes decisions** (pricing, core UX change): p < 0.01 (99%)
- **Low-stakes optimization** (copy, color, minor UI): p < 0.10 (90%) is acceptable

### Practical Significance
Even if statistically significant, ask: "Is this effect large enough to matter?"
- Calculate the annual revenue impact of the observed effect
- Compare against the effort to maintain the change
- Consider: will this effect compound (e.g., activation improvement) or is it one-time?

---

## 7. DECISION FRAMEWORK

Pre-commit to decisions BEFORE seeing results. This prevents post-hoc rationalization.

### If Treatment Wins (stat-sig + practically significant):
- **Ship** the treatment to 100% of users
- Document the learning: what worked and why
- Update the issue tree: mark this hypothesis as validated
- Identify follow-up: can this win be amplified?

### If Treatment Loses (stat-sig negative):
- **Revert** to control
- Document the learning: why did the hypothesis fail?
- Update the issue tree: mark this hypothesis as disproved
- Generate next hypothesis: what does this failure tell us about the real bottleneck?

### If Inconclusive (not stat-sig):
- **Do NOT interpret as "no effect"** -- absence of evidence is not evidence of absence
- Diagnose: Was sample too small? Was MDE too ambitious? Was there high variance?
- Options: (a) extend the experiment if close to significance, (b) redesign with larger effect size, (c) run qualitative research to understand why
- Default: Do not ship. Move to next experiment.

### If Guardrails Break:
- **Kill the experiment immediately** regardless of primary metric
- Investigate: what caused the guardrail degradation?
- Redesign the treatment to avoid the negative effect

---

## 8. EXPERIMENT TYPES

### A/B Test (Standard)
- **What:** Random split, one control + one treatment, fixed duration
- **When:** Clear hypothesis, sufficient traffic, measurable metric
- **Pros:** Simple, interpretable, high confidence
- **Cons:** Needs traffic, takes time

### Multivariate Test
- **What:** Test multiple variables simultaneously (e.g., headline x CTA x image)
- **When:** Many variables to optimize, very high traffic
- **Pros:** Tests interactions between variables
- **Cons:** Needs massive traffic (sample per combination), complex analysis

### Sequential Test (Bandit)
- **What:** Dynamically allocate traffic to winning variant
- **When:** Continuous optimization, high cost of losing variant
- **Pros:** Minimizes regret, faster to converge
- **Cons:** Lower statistical rigor, harder to interpret, novelty effects

### Fake Door / Painted Door
- **What:** Show a feature that does not exist yet. Measure click/interest.
- **When:** Validate demand before building
- **Pros:** Zero engineering cost, fast
- **Cons:** Can frustrate users, measures intent not usage
- **Implementation:** Add button/link, show "Coming soon" or waitlist on click, measure CTR

### Wizard of Oz
- **What:** Users experience the feature, but the backend is manual
- **When:** Validate value proposition before building automation
- **Pros:** Tests real value, not just interest
- **Cons:** Does not scale, labor-intensive

### Prototype Test
- **What:** Interactive mockup tested with real users
- **When:** Validate UX/flow before engineering investment
- **Pros:** Fast, cheap, rich qualitative data
- **Cons:** Small sample, no quantitative significance

---

## 9. PRIORITIZATION: ICE SCORING

### Impact (1-10)
Connect to the revenue driver tree:
- 10: Directly moves a top-level revenue driver (e.g., activation rate, conversion rate)
- 7-9: Moves a sub-driver with high sensitivity
- 4-6: Moves a sub-driver with moderate sensitivity
- 1-3: Moves a metric loosely connected to revenue

### Confidence (1-10)
Based on evidence quality:
- 10: Prior A/B test data showing similar effect
- 8-9: Strong quantitative data (funnel analysis, cohort data)
- 6-7: Qualitative research (user interviews, usability tests)
- 4-5: Industry best practice or competitive analysis
- 2-3: Team intuition with some supporting logic
- 1: Pure gut feeling

### Ease (1-10)
Based on implementation effort:
- 10: Copy/config change, ships in hours
- 8-9: Front-end only, ships in 1-2 days
- 6-7: Front-end + minor backend, ships in 1 week
- 4-5: Significant engineering, ships in 2 weeks
- 2-3: Major engineering + design, ships in a month
- 1: Requires infrastructure changes, multi-month

### ICE Score = Impact x Confidence x Ease
- Score range: 1-1000
- Top quartile: prioritize for next sprint
- Second quartile: queue for backlog
- Bottom half: park or kill

**Tie-breaking:** When ICE scores are close, prefer higher confidence (you learn faster from experiments you expect to work).
