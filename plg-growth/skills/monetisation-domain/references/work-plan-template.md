# Monetisation Work Plan Template

## Work Plan Types

Choose the type based on user situation:

| Situation | Type | Structure |
|-----------|------|-----------|
| Early stage, unclear pricing direction | **OST** | Objectives → Strategies → Tactics |
| Has data, needs to test pricing changes | **Experiment Backlog** | Prioritized experiments |
| Needs to understand willingness to pay | **Research Plan** | Discovery activities |

---

## Type 1: OST (Objectives, Strategies, Tactics)

Use when the user needs strategic direction for monetisation.

### Template

```
## Monetisation Work Plan: OST

### Objective
[Specific, measurable goal]
Example: "Increase free-to-paid conversion from 3% to 5% within 6 months"

### Strategy 1: [Strategy Name]
Hypothesis: "We believe [strategy] will improve [metric] because [reasoning]"

Tactics:
1. [Tactic] -- Owner: [who] -- Timeline: [when] -- Metric: [what to measure]
2. [Tactic] -- Owner: [who] -- Timeline: [when] -- Metric: [what to measure]
3. [Tactic] -- Owner: [who] -- Timeline: [when] -- Metric: [what to measure]

### Strategy 2: [Strategy Name]
Hypothesis: "We believe [strategy] will improve [metric] because [reasoning]"

Tactics:
1. [Tactic] -- Owner: [who] -- Timeline: [when] -- Metric: [what to measure]
2. [Tactic] -- Owner: [who] -- Timeline: [when] -- Metric: [what to measure]

### Key Unknowns
- [What we need to learn before committing to this strategy]

### Success Criteria
- [How we will know the objective is met]
- [Leading indicators to track weekly/monthly]
```

### Monetisation-Specific OST Examples

**Objective:** Increase ARPA from $45 to $65 within 2 quarters

**Strategy 1: Improve tier upgrade rate**
- Hypothesis: "We believe redesigning our pricing page with stronger anchoring will increase Pro plan selection by 15% because current page does not differentiate tiers clearly"
- Tactic 1: Audit pricing page against best practices (Week 1)
- Tactic 2: Design and ship new pricing page with recommended tier highlight (Weeks 2-4)
- Tactic 3: A/B test new page vs old (Weeks 5-8)

**Strategy 2: Launch seat-based expansion program**
- Hypothesis: "We believe proactive seat expansion prompts will increase average seats per account from 4.2 to 6.0 because 35% of accounts have inactive invited users"
- Tactic 1: Build seat utilization dashboard (Week 1-2)
- Tactic 2: Implement "invite your team" prompts at collaboration touchpoints (Weeks 3-5)
- Tactic 3: Launch admin notification when team outgrows plan (Week 6)

---

## Type 2: Experiment Backlog

Use when the user has data and needs to test specific monetisation hypotheses.

### Template

```
## Monetisation Experiment Backlog

### Experiment 1: [Name]
- Branch: [Which issue tree branch this tests]
- Hypothesis: "We believe [change] will [outcome] because [reasoning]"
- Metric: [Primary metric to measure]
- Success criteria: [Threshold for success, e.g., "+10% conversion rate"]
- Audience: [Who sees the test, sample size needed]
- Duration: [Minimum test duration for significance]
- Effort: [S/M/L]
- Risk: [What could go wrong]
- Expected impact: [$ estimate if hypothesis is confirmed]

### Experiment 2: [Name]
[Same format]

### Prioritization
| # | Experiment | Impact | Effort | Risk | Priority Score |
|---|-----------|--------|--------|------|----------------|
| 1 | | H/M/L | S/M/L | H/M/L | |
| 2 | | H/M/L | S/M/L | H/M/L | |
```

### Monetisation-Specific Experiment Examples

**Experiment: Annual Discount Test**
- Branch: Conversion to Paid > Payment Options
- Hypothesis: "We believe increasing annual discount from 17% to 25% will increase annual plan selection from 40% to 55% because our audience is budget-conscious SMBs"
- Metric: % of new paid customers choosing annual
- Success criteria: Annual selection rate > 50% without reducing total conversion
- Audience: New paid signups, need 500 per variant
- Duration: 4 weeks minimum
- Effort: S
- Risk: Lower per-customer revenue if annual cannibalization is too high
- Expected impact: +$8 LTV per customer (reduced churn from annual lock-in)

**Experiment: Usage Limit Upgrade Prompt**
- Branch: Conversion to Paid > Freemium Limitations
- Hypothesis: "We believe showing an upgrade prompt at 80% of free plan limit will increase conversion by 12% because users are most motivated when they can see the ceiling"
- Metric: Free-to-paid conversion rate within 7 days of prompt
- Success criteria: >8% conversion from prompt viewers
- Audience: Free users approaching limits, need 1000+ per variant
- Duration: 6 weeks
- Effort: M
- Risk: Users may feel pressured, could increase churn from free tier
- Expected impact: +200 conversions/month at current traffic

---

## Type 3: Research Plan

Use when the user needs to learn about willingness to pay, pricing perception, or competitive positioning before making decisions.

### Template

```
## Monetisation Research Plan

### Research Question
[What do we need to learn?]

### Study 1: [Method]
- Objective: [What this study answers]
- Method: [Van Westendorp / MaxDiff / Interviews / Competitive Analysis]
- Participants: [Who, how many, how recruited]
- Timeline: [Design, field, analysis]
- Deliverable: [What the output looks like]
- Decision it informs: [What strategy/tactic depends on this]

### Study 2: [Method]
[Same format]

### Research Sequence
[Which studies must happen first to inform later ones]

### Interim Decisions
[What can we decide now vs what must wait for research]
```

### Monetisation-Specific Research Examples

**Research Question:** "What is the optimal pricing metric and price range for our Pro plan?"

**Study 1: Van Westendorp Price Sensitivity**
- Objective: Identify acceptable price range for Pro plan
- Method: Van Westendorp 4-question survey (see research-methods.md)
- Participants: 200 current free users + 100 current paid users
- Timeline: Design (1 week), Field (2 weeks), Analysis (1 week)
- Deliverable: Acceptable price range, optimal price point, indifference price
- Decision it informs: Pro plan price setting

**Study 2: MaxDiff Feature Prioritization**
- Objective: Which features drive willingness to pay for Pro vs Enterprise
- Method: MaxDiff survey with 12 features across 10 choice sets
- Participants: 200 users (mix of free and paid)
- Timeline: Design (1 week), Field (2 weeks), Analysis (1 week)
- Deliverable: Ranked feature importance scores, tier allocation recommendation
- Decision it informs: Feature allocation across tiers

**Study 3: Upgrade Decision-Driver Interviews**
- Objective: Understand qualitative triggers and barriers for upgrade
- Method: 30-minute semi-structured interviews
- Participants: 8 recent upgraders + 8 power free users + 4 downgraders
- Timeline: Recruit (1 week), Interview (2 weeks), Synthesize (1 week)
- Deliverable: Trigger event taxonomy, barrier map, value proof points
- Decision it informs: Upgrade prompt timing, messaging, and friction removal

**Research Sequence:** Study 3 (interviews) first to inform survey design, then Studies 1 and 2 in parallel.

---

## Universal Work Item Format

Regardless of plan type, every work item should include:

```
### [Item Name]
- Issue tree branch: [Which branch this addresses]
- Hypothesis: "We believe [X] because [Y]"
- Action: [Specific, concrete action]
- Owner: [Person or team]
- Timeline: [Start and end date]
- Metric: [How we measure success]
- Success criteria: [Threshold]
- Dependencies: [What must happen first]
- Risk: [What could go wrong and mitigation]
```
