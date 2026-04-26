# Retention Work Plan Template

Use this template to generate hypothesis-driven work items for improving retention. Organized by the 4 retention components. Behavioral science is integrated into experiment design.

---

## Work Item Format

```
### [Short descriptive title]

**Retention Component:** Activation | Adoption | Engagement | Resurrection
**Issue Tree Branch:** [Specific branch within the component]
**Hypothesis:** [What we believe and why]
**Behavioral Lever:** [Fogg: M/A/T | COM-B: C/O/M — which element this targets]
**Work Type:** Research | Data Analysis | Strategy Decision | Experiment | Operations
**Priority:** P1 (high sensitivity) | P2 (moderate) | P3 (low)
**Connected Metric:** [Which metric on the revenue driver tree this moves]
**Success Criteria:** [How we know this worked]
**Timeline:** [Estimated duration]
**Dependencies:** [What must be true or done first]
```

---

## Priority Assignment

Priority comes from two inputs:

1. **Component priority:** Activation > Engagement > Adoption > Resurrection (fix the earliest broken component first)
2. **Sensitivity analysis:** Within a component, which lever moves the retention curve most?

Combined:
- **P1:** Broken component that is earliest in the chain AND high-sensitivity lever
- **P2:** Meaningful lever in a secondary component, or moderate-sensitivity lever in the primary component
- **P3:** Nice-to-have improvement in a component that is already performing

---

## Sample Work Plans by Situation

### Situation A: Does Not Know Why Users Churn (Research Plan)

**Objective:** Diagnose the primary retention failure mode within 6 weeks.

| # | Work Item | Component | Type | Behavioral Lens | Priority | Timeline |
|---|----------|-----------|------|-----------------|----------|----------|
| 1 | Calculate retention curves: overall, activated vs. non-activated, by cohort | All | Data Analysis | Baseline | P1 | Week 1 |
| 2 | Split churn: voluntary vs. involuntary | All | Data Analysis | Baseline | P1 | Week 1 |
| 3 | Implement exit survey (2 questions) on cancellation flow | All | Operations | Motivation diagnostics | P1 | Week 1-2 |
| 4 | Build feature adoption heatmap: retained vs. churned users | Adoption | Data Analysis | Capability assessment | P1 | Week 2 |
| 5 | Calculate engagement scores and segment users into 4 tiers | Engagement | Data Analysis | Baseline | P1 | Week 2-3 |
| 6 | Conduct 10 behavioral interviews (5 retained, 5 churned) using M/A/T guide | All | Research | Full B=MAT diagnosis | P1 | Week 2-4 |
| 7 | Analyze exit survey responses by theme | All | Data Analysis | Motivation diagnostics | P2 | Week 4-5 |
| 8 | Synthesize: behavioral diagnosis (binding constraint per segment) | All | Strategy Decision | COM-B systemic view | P1 | Week 5-6 |

**Hypothesis format:** "We believe retention failure is primarily caused by [low Motivation / low Ability / missing Triggers] in the [component] stage, specifically [detail]. Evidence: [data points and interview themes]."

---

### Situation B: Knows the Problem, Needs Solutions (Experiment Backlog)

**Objective:** Improve 90-day retention from [current]% to [target]% within 2 quarters.

#### Activation Component Experiments

| # | Hypothesis | Behavioral Lever | Experiment | Metric | Success Criteria | Priority |
|---|-----------|-----------------|-----------|--------|-----------------|----------|
| 1 | Reducing onboarding from 7 to 3 steps will increase activation by 20% | Fogg: Ability (Time, Physical Effort) | A/B: full onboarding vs. minimal onboarding | Activation rate | +20% activation, no decrease in 7-day retention | P1 |
| 2 | Template-first experience will increase activation by 25% for users who currently see empty state | Fogg: Ability (Brain Cycles) + Motivation (Pleasure) | A/B: empty state vs. template picker | Activation rate for non-activated at Day 1 | +25% activation | P1 |

#### Adoption Component Experiments

| # | Hypothesis | Behavioral Lever | Experiment | Metric | Success Criteria | Priority |
|---|-----------|-----------------|-----------|--------|-----------------|----------|
| 3 | Contextual feature tips will increase adoption of 3 underused features by 30% | Fogg: Trigger (Facilitator) + COM-B: Capability (Psychological) | A/B: feature tips at relevant moments vs. no tips | Feature adoption rate for target features | +30% adoption of each feature | P2 |
| 4 | Feature adoption breadth > 3 features in first month predicts 2x higher 90-day retention | COM-B: Capability building | Data validation study | Correlation between adoption breadth and retention | Statistically significant 2x+ difference | P1 |

#### Engagement Component Experiments

| # | Hypothesis | Behavioral Lever | Experiment | Metric | Success Criteria | Priority |
|---|-----------|-----------------|-----------|--------|-----------------|----------|
| 5 | Weekly digest email will increase WAU/MAU by 10% for at-risk users | Fogg: Trigger (Signal) | A/B: weekly digest vs. no digest for users with engagement score 0.2-0.5 | WAU/MAU for at-risk segment | +10% WAU/MAU, < 1% unsubscribe rate | P1 |
| 6 | Slack integration will increase frequency by 15% for users in Slack-using companies | COM-B: Opportunity (Physical) | Launch integration, measure before/after for integration users vs. control | Sessions per week | +15% frequency for integration users | P2 |
| 7 | In-app value metric ("You saved X hours this week") will increase motivation | Fogg: Motivation (Hope) | A/B: value display on dashboard vs. no display | Engagement score, session frequency | +10% engagement score for treatment group | P2 |

#### Resurrection Component Experiments

| # | Hypothesis | Behavioral Lever | Experiment | Metric | Success Criteria | Priority |
|---|-----------|-----------------|-----------|--------|-----------------|----------|
| 8 | "What's new since you left" email will reactivate 10% of dormant users | Fogg: Trigger (Spark) + Motivation (Hope/Fear) | A/B: what's new email vs. generic "come back" email | Reactivation rate (dormant → active within 7 days) | 10% reactivation from what's new vs. 5% from generic | P2 |
| 9 | Magic link (passwordless return) will increase reactivation email CTR by 50% | Fogg: Ability (Physical Effort, Time) | A/B: magic link vs. standard login link in reactivation emails | Email CTR, reactivation rate | +50% CTR, +20% reactivation | P2 |

#### Involuntary Churn Experiments

| # | Hypothesis | Behavioral Lever | Experiment | Metric | Success Criteria | Priority |
|---|-----------|-----------------|-----------|--------|-----------------|----------|
| 10 | Pre-expiry card notification will prevent 40% of card-expiry churn | Fogg: Trigger (Signal) | Implement pre-expiry emails at 30, 14, 7 days | Card update rate, involuntary churn rate | 40% reduction in card-expiry churn | P1 |
| 11 | Smart payment retries (4 attempts over 7 days) will recover 30% of failed payments | N/A (technical) | Implement dunning retry sequence | Payment recovery rate | 30% recovery rate | P1 |

---

### Situation C: Needs Strategic Retention Program (OST Format)

**Objective:** Build a comprehensive retention program across all 4 components.

**Strategy 1: Fix the activation foundation**
| # | Tactic | Component | Type | Behavioral Lens | Priority | Quarter |
|---|--------|-----------|------|-----------------|----------|---------|
| 1.1 | Validate activation metric predicts 90-day retention at 2x+ rate | Activation | Data Analysis | Baseline | P1 | Q1 |
| 1.2 | Route to activation-domain for deep optimization if rate < 25% | Activation | Strategy Decision | Full B=MAT | P1 | Q1 |

**Strategy 2: Deepen feature adoption**
| # | Tactic | Component | Type | Behavioral Lens | Priority | Quarter |
|---|--------|-----------|------|-----------------|----------|---------|
| 2.1 | Build feature adoption heatmap (retained vs. churned) | Adoption | Data Analysis | COM-B: Capability | P1 | Q1 |
| 2.2 | Identify "hidden gem" features (low adoption, high retention correlation) | Adoption | Data Analysis | COM-B: Capability | P1 | Q1 |
| 2.3 | Design discoverability campaigns for top 3 hidden gems | Adoption | Experiment | Fogg: Trigger (Facilitator) | P1 | Q2 |
| 2.4 | Build feature announcement system (in-app changelog) | Adoption | Operations | Fogg: Trigger (Signal) | P2 | Q2 |

**Strategy 3: Build engagement loops**
| # | Tactic | Component | Type | Behavioral Lens | Priority | Quarter |
|---|--------|-----------|------|-----------------|----------|---------|
| 3.1 | Implement engagement scoring model | Engagement | Operations | Baseline | P1 | Q1 |
| 3.2 | Design trigger system matched to natural use-case frequency | Engagement | Strategy Decision | Fogg: Trigger design | P1 | Q1 |
| 3.3 | Build and test notification strategy (type x timing x channel) | Engagement | Experiment | Fogg: Trigger (Spark/Facilitator/Signal) | P1 | Q2 |
| 3.4 | Launch integration with top 2 adjacent tools | Engagement | Operations | COM-B: Opportunity (Physical) | P2 | Q2 |
| 3.5 | Implement value display ("You saved X hours") | Engagement | Experiment | Fogg: Motivation (Hope) | P2 | Q2 |

**Strategy 4: Build resurrection capability**
| # | Tactic | Component | Type | Behavioral Lens | Priority | Quarter |
|---|--------|-----------|------|-----------------|----------|---------|
| 4.1 | Define dormancy threshold and size the dormant pool | Resurrection | Data Analysis | Baseline | P1 | Q1 |
| 4.2 | Build reactivation email sequence (4-email drip) | Resurrection | Operations | Fogg: Trigger (Spark) | P2 | Q2 |
| 4.3 | Implement "Where you left off" returning user experience | Resurrection | Experiment | Fogg: Ability (Brain Cycles, Non-Routineness) | P2 | Q2 |
| 4.4 | Implement magic link in all reactivation communications | Resurrection | Operations | Fogg: Ability (Physical Effort) | P2 | Q2 |

**Strategy 5: Plug involuntary churn**
| # | Tactic | Component | Type | Behavioral Lens | Priority | Quarter |
|---|--------|-----------|------|-----------------|----------|---------|
| 5.1 | Implement full dunning sequence (pre-expiry + retries + notifications) | Churn | Operations | Technical | P1 | Q1 |
| 5.2 | Build downgrade path (free tier instead of cancellation) | Churn | Strategy Decision | Fogg: Motivation preservation | P1 | Q1 |
| 5.3 | Implement exit survey and analyze monthly | Churn | Operations | Diagnostics | P1 | Q1 |

---

## Work Plan Review Checklist

Before finalizing a retention work plan, verify:

- [ ] Voluntary vs. involuntary churn split is known (or is a work item)
- [ ] Work items are organized by the 4 retention components
- [ ] The earliest broken component is addressed first (Activation before Engagement)
- [ ] Every experiment specifies which behavioral lever it targets (Fogg M/A/T or COM-B C/O/M)
- [ ] Involuntary churn fixes are included (highest ROI, often overlooked)
- [ ] Hypotheses are specific and testable
- [ ] Success criteria include both the target metric AND a guardrail metric
- [ ] Engagement scoring or health scoring is in place (or is a work item)
- [ ] Research is planned if the binding constraint is unknown
- [ ] Plan includes both quick wins (dunning, notifications) and strategic bets (engagement loops, adoption campaigns)
- [ ] Each item connects to a retention metric: overall retention rate, component-specific rate, or engagement score
