# Activation Work Plan Template

Use this template to generate hypothesis-driven work items for improving activation. Built around the 3-step iterative framework: Segment, Identify, Improve. Minimum 2 full quarters per cycle.

---

## Work Item Format

```
### [Short descriptive title]

**Issue Tree Branch:** [Which branch of the activation issue tree this addresses]
**Hypothesis:** "Users who [action] within [timeframe] are [X]% more likely to [outcome]"
**Segment:** [Which user segment this targets]
**Behavior to Influence:** [The specific supporting behavior to increase]
**Work Type:** Research | Data Analysis | Strategy Decision | Experiment | Operations
**Priority:** P1 (high sensitivity) | P2 (moderate) | P3 (low)
**Connected Metric:** [Activation rate, TTV, or specific supporting metric]
**Success Criteria:** [How we know this worked]
**Quarter:** [Target quarter for execution]
**Dependencies:** [What must be true or done first]
```

---

## The 3-Step Iterative Framework

### Step 1: Segment the User Base

Before optimizing activation, understand that different users activate differently.

**Segmentation dimensions:**

| Dimension | How to Segment | Why It Matters |
|-----------|---------------|----------------|
| Acquisition channel | Organic, paid, referral, product-led | Different channels bring different intent levels |
| JTBD / use case | From onboarding questions or interview data | Different jobs have different aha moments |
| Firmographics | Company size, industry, role | Enterprise users activate differently than SMB |
| Intent level | High-intent (searched for solution) vs. casual (saw an ad) | Casual users need more motivation |

**Output:** 3-5 user segments with sufficient volume (100+ users each) for analysis.

### Step 2: Identify Supporting Behaviors Per Segment

For each segment, re-run the activation analysis:

1. **Run CSI/Aha Score per segment** (see `references/metric-identification.md`)
   - Is the activation metric the same for all segments?
   - Are volume thresholds different? (SMB might need 1 project, enterprise might need 3)
   - Are time windows different? (Enterprise might take longer but still activate)

2. **Map supporting behaviors**
   - Which actions precede activation in each segment?
   - Are there "stepping stone" events that make activation more likely?
   - Example: "Users who watch the intro video are 40% more likely to create a project"

3. **Quantify per segment**
   - Activation rate per segment
   - TTV per segment
   - Drop-off step per segment
   - Supporting behavior completion rate per segment

**Output for each segment:**
> "In the [segment] segment, users who [supporting behavior] within [timeframe] are [X]% more likely to [activate]. Currently, [Y]% of this segment completes this behavior. The primary barrier is [barrier type]."

### Step 3: Improve Supporting Behaviors Through Experiments

For each supporting behavior identified in Step 2, design interventions:

1. Diagnose the barrier (Don't Know / Can't / Don't Want)
2. Select tactics from `references/activation-barriers.md`
3. Design an experiment
4. Run for statistical significance
5. Roll out winners, iterate on losers

**Minimum 2 full quarters per cycle.** Activation improvements compound:
- Quarter 1: Segment + Identify + first experiments
- Quarter 2: Iterate experiments + measure retention impact + plan next cycle

---

## Sample Work Plans by Situation

### Situation A: No Activation Metric Defined (Research Plan)

**Objective:** Define and validate the activation metric within 6 weeks.

| # | Work Item | Type | Priority | Timeline |
|---|----------|------|----------|----------|
| 1 | Extract full product event list from analytics | Operations | P1 | Week 1 |
| 2 | Run CSI/Aha Score across all events x thresholds | Data Analysis | P1 | Week 1-2 |
| 3 | Run Information Value analysis as cross-check | Data Analysis | P2 | Week 2 |
| 4 | Conduct 15 activation interviews (3-pillar method) | Research | P1 | Week 2-4 |
| 5 | Build Linear Customer Journey Map from qual + quant | Strategy Decision | P1 | Week 5 |
| 6 | Define activation metric and baseline rate | Strategy Decision | P1 | Week 5 |
| 7 | Validate: does metric predict 30-day retention at 2x+ rate? | Data Analysis | P1 | Week 6 |
| 8 | Instrument activation metric tracking in product analytics | Operations | P1 | Week 6 |

**Hypothesis format:** "We believe [event] at [threshold] within [timeframe] is the activation metric because CSI = [score] and [N] of [M] interview participants described this as their aha moment."

---

### Situation B: Metric Defined, Rate is Low (Experiment Backlog)

**Objective:** Increase activation rate from [current]% to [target]% within 2 quarters.

| # | Hypothesis | Experiment | Segment | Metric | Success Criteria | Priority | Quarter |
|---|-----------|-----------|---------|--------|-----------------|----------|---------|
| 1 | Users who see a pre-populated template activate 30% more than those who see an empty state | A/B: empty state vs. template-first experience | All new signups | Activation rate | +30% activation for template group | P1 | Q1 |
| 2 | Users who watch the 90-sec intro video are 25% more likely to complete first action | A/B: video prompt on dashboard vs. no video | Users who sign up but take no action in 24h | First action rate | +25% first action for video group | P1 | Q1 |
| 3 | Reducing setup steps from 7 to 3 will cut TTV by 50% | A/B: full setup vs. deferred setup | All new signups | Time-to-value | TTV < 1 hour (from current 2 hours) | P1 | Q1 |
| 4 | Segment-specific onboarding paths will improve activation for marketing use case | A/B: generic vs. marketing-specific onboarding | Marketing use case segment | Segment activation rate | +20% activation for marketing segment | P2 | Q1 |
| 5 | Day-1 email with personalized CTA will recover 15% of users who did not activate on day 0 | A/B: generic vs. personalized day-1 email | Users inactive after 24h | Day-3 activation rate | +15% recovery rate for personalized email | P2 | Q2 |
| 6 | In-app chat trigger at the setup step will reduce drop-off by 20% | A/B: chat trigger at setup step vs. no trigger | Users who reach setup step | Setup completion rate | +20% completion, acceptable support load | P2 | Q2 |

---

### Situation C: Metric Defined, Rate is OK, Wants Optimization (OST Format)

**Objective:** Reduce TTV by 40% and increase activation rate by 10% through segment-specific optimization.

**Strategy 1: Segment-specific activation paths**
| # | Tactic | Type | Priority | Quarter |
|---|--------|------|----------|---------|
| 1.1 | Segment user base by JTBD using onboarding question data | Data Analysis | P1 | Q1 |
| 1.2 | Re-run CSI per segment to validate/find segment-specific metrics | Data Analysis | P1 | Q1 |
| 1.3 | Design segment-specific onboarding flows for top 3 segments | Strategy Decision | P1 | Q1 |
| 1.4 | A/B test segment-specific vs. generic onboarding | Experiment | P1 | Q2 |

**Strategy 2: Reduce time-to-value**
| # | Tactic | Type | Priority | Quarter |
|---|--------|------|----------|---------|
| 2.1 | Map every step from signup to activation with timing data | Data Analysis | P1 | Q1 |
| 2.2 | Identify the 3 slowest steps and root-cause each | Research | P1 | Q1 |
| 2.3 | Prototype "instant value" experience (value before setup) | Experiment | P1 | Q2 |
| 2.4 | Move non-essential setup to post-activation | Experiment | P2 | Q2 |

**Strategy 3: Post-activation engagement handoff**
| # | Tactic | Type | Priority | Quarter |
|---|--------|------|----------|---------|
| 3.1 | Measure activation-to-day-7-retention rate | Data Analysis | P1 | Q1 |
| 3.2 | Design post-activation engagement sequence (milestones, tips, deeper features) | Strategy Decision | P2 | Q2 |
| 3.3 | A/B test post-activation nurture vs. no nurture | Experiment | P2 | Q2 |

---

## Work Plan Review Checklist

Before finalizing a work plan, verify:

- [ ] Activation metric is defined (or metric identification is the first work item)
- [ ] Every item has a hypothesis in the format "Users who [X] within [Y] are [Z]% more likely to [W]"
- [ ] Items are prioritized by drop-off volume, not ease of implementation
- [ ] User segments are explicit (not "all users" for everything)
- [ ] Barrier type is identified for each improvement item (Don't Know / Can't / Don't Want)
- [ ] Success criteria are specific and measurable
- [ ] Plan spans at least 2 quarters (activation is not a sprint project)
- [ ] Mix of quick wins (P1, this quarter) and strategic bets (P1-P2, next quarter)
- [ ] Measurement infrastructure is in place or is an explicit work item
- [ ] Each item connects to activation rate, TTV, or a supporting behavior metric
