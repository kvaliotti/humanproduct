# Acquisition Work Plan Template

Use this template to generate hypothesis-driven work items for product-led acquisition. Every item ties to a branch of the acquisition issue tree and a metric on the revenue driver tree.

---

## Work Item Format

Each work item follows this structure:

```
### [Short descriptive title]

**Issue Tree Branch:** [Which branch of the acquisition issue tree this addresses]
**Hypothesis:** [What we believe and why]
**Work Type:** Research | Data Analysis | Strategy Decision | Experiment | Operations
**Priority:** P1 (high sensitivity) | P2 (moderate sensitivity) | P3 (low sensitivity)
**Connected Metric:** [Which metric on the revenue driver tree this moves]
**Success Criteria:** [How we know this is done / worked]
**Timeline:** [Estimated duration]
**Dependencies:** [What must be true or done first]
```

---

## Priority Assignment

Priority comes from sensitivity analysis on the revenue driver tree:

- **P1 (High Sensitivity):** Moving this lever by 10% has outsized impact on revenue. Examples: signup conversion rate when traffic is high, activation rate when signups are strong, channel CAC when burn rate is a concern.
- **P2 (Moderate Sensitivity):** Meaningful impact but not the biggest lever. Important for sustained growth.
- **P3 (Low Sensitivity):** Good practice but low immediate impact. Do when P1 and P2 are addressed.

---

## Work Type Definitions

### Research
Filling knowledge gaps. No data yet, need qualitative or secondary research.
- User intent mapping
- Channel landscape analysis
- Competitor acquisition teardown
- ICP interview for acquisition triggers

### Data Analysis
Quantitative investigation of existing data to test a hypothesis.
- Funnel conversion analysis
- Channel attribution audit
- Viral coefficient calculation
- Cohort-based quality analysis

### Strategy Decision
Using evidence to make a directional choice.
- Which product-led acquisition strategies to pursue
- Channel portfolio allocation
- Signup flow architecture
- Pricing/packaging impact on acquisition

### Experiment
Testing a specific change with measurable outcome.
- A/B test on signup flow
- New referral incentive test
- Sidecar product MVP launch
- New channel pilot

### Operations
Enabling infrastructure and processes.
- Analytics/tracking implementation
- Attribution tooling setup
- A/B testing infrastructure
- Team ownership and RACI definition

---

## Sample Work Plans by Situation

### Situation A: Early Stage, Unclear Direction (OST Format)

**Objective:** Identify and validate the highest-leverage acquisition channel within 8 weeks.

**Strategy 1: Understand where ICP discovers products**
| # | Tactic | Type | Priority | Timeline |
|---|--------|------|----------|----------|
| 1.1 | Interview 10 recent signups on how they found us | Research | P1 | Week 1-2 |
| 1.2 | Map ICP online watering holes (communities, publications, search queries) | Research | P1 | Week 1-2 |
| 1.3 | Audit competitor acquisition channels (SimilarWeb, social presence, SEO) | Research | P2 | Week 2-3 |

**Strategy 2: Evaluate product-led acquisition fit**
| # | Tactic | Type | Priority | Timeline |
|---|--------|------|----------|----------|
| 2.1 | Score 4 product-led strategies using evaluation matrix | Strategy Decision | P1 | Week 3 |
| 2.2 | Calculate viral coefficient if any sharing exists | Data Analysis | P1 | Week 3-4 |
| 2.3 | Assess product-driven SEO potential (indexable content, search volume) | Research | P2 | Week 3-4 |

**Strategy 3: Run initial channel experiments**
| # | Tactic | Type | Priority | Timeline |
|---|--------|------|----------|----------|
| 3.1 | Launch top-scored product-led strategy as MVP | Experiment | P1 | Week 5-7 |
| 3.2 | Run small paid test on highest-potential channel ($500-1000) | Experiment | P2 | Week 5-7 |
| 3.3 | Measure signup volume, activation rate, and quality per channel | Data Analysis | P1 | Week 8 |

---

### Situation B: Has Data, Needs Experiments (Experiment Backlog)

| # | Hypothesis | Experiment | Metric | Success Criteria | Priority | Timeline |
|---|-----------|-----------|--------|-----------------|----------|----------|
| 1 | Removing password requirement will increase signup conversion by 15% | A/B test: password vs. magic link signup | Signup conversion rate | +15% conversion, no decrease in 7-day retention | P1 | 2 weeks |
| 2 | Adding Google OAuth will capture 25% of signups who currently abandon | A/B test: add Google OAuth option | Signup completion rate | 25% of new signups use OAuth, overall conversion +10% | P1 | 2 weeks |
| 3 | Referral incentive (both sides get 1 month free) will achieve k=0.3 | Launch double-sided referral with tracking | Viral coefficient, referral signup rate | k-factor > 0.3 within 30 days | P2 | 4 weeks |
| 4 | Personalized onboarding by use case will improve signup-to-activation by 20% | A/B test: generic vs. use-case-specific post-signup flow | Signup-to-activation rate | +20% activation for personalized group | P1 | 3 weeks |
| 5 | Template gallery pages will rank for 50+ long-tail keywords within 3 months | Create 20 template landing pages with SEO optimization | Indexed pages, organic traffic, template-sourced signups | 50+ keywords ranking page 1-2 in 90 days | P2 | 12 weeks |

---

### Situation C: Needs Discovery (Research Plan)

| # | Research Question | Method | Hypothesis to Test | Deliverable | Timeline |
|---|------------------|--------|-------------------|-------------|----------|
| 1 | What triggers our ICP to search for a solution? | 10 user interviews (recent signups) | ICP searches when [trigger event] occurs | Trigger event map with frequency estimates | Week 1-3 |
| 2 | Which channels reach our ICP at the moment of trigger? | Channel mapping + SimilarWeb + social listening | Top 3 channels are [X, Y, Z] based on ICP presence | Channel-market fit scorecard | Week 2-4 |
| 3 | Do our users share product output naturally? | Product analytics: share/export event analysis | At least 20% of active users share output externally | Viral feasibility assessment with k-factor estimate | Week 3-4 |
| 4 | What do competitors do for acquisition? | Competitive teardown (5 competitors) | Competitors rely on [channel types] which we can differentiate from | Competitive acquisition landscape map | Week 3-5 |
| 5 | What is our true CAC by channel? | Attribution analysis across all channels | CAC varies by 3x+ across channels | Channel economics spreadsheet with LTV:CAC | Week 4-6 |

---

## Work Plan Review Checklist

Before finalizing a work plan, verify:

- [ ] Every item has a hypothesis (not just "improve X")
- [ ] Items are prioritized by revenue sensitivity, not ease
- [ ] Mix of work types (not all experiments, not all research)
- [ ] Dependencies are explicit (what blocks what)
- [ ] Success criteria are specific and measurable
- [ ] Timeline is realistic given team capacity
- [ ] Each item connects to a metric on the revenue driver tree
- [ ] P1 items can start immediately (no unresolved dependencies)
- [ ] Total plan is scoped to 6-8 weeks (not a 6-month wishlist)
