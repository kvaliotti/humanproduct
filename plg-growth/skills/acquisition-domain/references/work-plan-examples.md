# Acquisition Work Plan — Domain Examples

Domain-specific worked examples for acquisition work plans. Use alongside the shared skeleton at `${CLAUDE_PLUGIN_ROOT}/references/work-plan-template.md` (work-item format, priority-by-sensitivity, work-type definitions, the three plan formats, generic checklist). Every item ties to a branch of the acquisition issue tree and a metric on the revenue driver tree.

**Acquisition P1 examples:** signup conversion rate when traffic is high, activation rate when signups are strong, channel CAC when burn rate is a concern.

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

Note: for double-sided referral / viral-loop mechanics and k-factor math, route the design work to `growth-loops`; this skill measures the acquisition impact of those loops.

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

## Acquisition-specific checklist additions

On top of the generic checklist in the shared template, verify:

- [ ] Each item connects to a metric on the revenue driver tree
- [ ] Total plan is scoped to 6-8 weeks (not a 6-month wishlist)
- [ ] Channel economics (CAC, LTV:CAC) are known or are an explicit work item
