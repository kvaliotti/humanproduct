# PLG Metrics by Domain

Key metrics organized by AARMS stage and revenue component. For each metric: definition, formula, benchmark range, data source, update frequency, and owning team.

---

## AARMS Stage Metrics

### Acquisition

| Metric | Definition | Formula | Benchmark Range | Data Source | Frequency | Owner |
|--------|-----------|---------|----------------|-------------|-----------|-------|
| Visitors | Unique visitors to marketing site + product | Count distinct anonymous_id on page_viewed | Varies by stage | Analytics (GA, Amplitude) | Daily | Marketing |
| Signups | New accounts created | Count of user_signed_up events | Varies by stage | Product analytics | Daily | Growth |
| Signup rate | % of visitors who sign up | Signups / Visitors | 2-5% (B2B SaaS) | Analytics | Weekly | Growth |
| Channel distribution | % of signups by source | Signups per utm_source / Total signups | Organic > 40% is healthy | Analytics | Weekly | Marketing |
| CAC | Cost to acquire one customer | Total acquisition spend / New paying customers | $50-$500 (B2B SaaS, varies by ACV) | Finance + Analytics | Monthly | Marketing |
| Viral coefficient (k) | Average new users generated per existing user | (Users who invite) x (Avg invites sent) x (Invite acceptance rate) | k > 0.5 is strong, k > 1.0 is viral | Product analytics | Monthly | Growth |
| Payback period | Time to recover CAC | CAC / (ARPA x Gross margin) | < 12 months healthy, < 18 months acceptable | Finance | Quarterly | Finance |

### Activation

| Metric | Definition | Formula | Benchmark Range | Data Source | Frequency | Owner |
|--------|-----------|---------|----------------|-------------|-----------|-------|
| Activation rate | % of signups reaching the activation action | Users with activation_achieved / Users with user_signed_up (same cohort) | 20-40% (B2B SaaS) | Product analytics | Weekly | Growth |
| Time-to-value (TTV) | Time from signup to first value moment | Median(activation_achieved.timestamp - user_signed_up.timestamp) | < 5 min ideal, < 1 day good, < 3 days acceptable | Product analytics | Weekly | Product |
| Onboarding completion rate | % of signups completing onboarding | Users with onboarding_completed / Users with onboarding_started | 40-70% | Product analytics | Weekly | Product |
| Onboarding drop-off by step | % abandoning at each step | (Users at step N - Users at step N+1) / Users at step N | < 15% per step | Product analytics | Weekly | Product |
| Setup completion rate | % completing key setup actions | Users completing [action] / Total signups | Varies by action criticality | Product analytics | Weekly | Product |
| First value action rate | % performing the core value action | Users with first_value_moment / Users with user_signed_up | 25-50% | Product analytics | Weekly | Growth |

### Retention

| Metric | Definition | Formula | Benchmark Range | Data Source | Frequency | Owner |
|--------|-----------|---------|----------------|-------------|-----------|-------|
| D1 retention | % of cohort active on day 1 | Active on day 1 / Signed up on day 0 | 30-50% (B2B SaaS) | Product analytics | Weekly | Product |
| D7 retention | % of cohort active on day 7 | Active on day 7 / Signed up on day 0 | 20-35% (B2B SaaS) | Product analytics | Weekly | Product |
| D30 retention | % of cohort active on day 30 | Active on day 30 / Signed up on day 0 | 15-25% (B2B SaaS) | Product analytics | Weekly | Product |
| D90 retention | % of cohort active on day 90 | Active on day 90 / Signed up on day 0 | 10-20% (B2B SaaS) | Product analytics | Monthly | Product |
| Feature adoption breadth | Avg number of features used per user | Avg count distinct feature_name per user per period | 3-7 features/month is engaged | Product analytics | Monthly | Product |
| Engagement score | Composite metric: frequency x breadth x depth | Weighted: (sessions/week x 0.4) + (features_used x 0.3) + (actions/session x 0.3), normalized 0-100 | > 60 = highly engaged | Product analytics | Weekly | Product |
| Churn rate | % of accounts that cancel or stop using | Churned accounts / Total active accounts at start of period | < 5% monthly (B2B SaaS), < 2% is excellent | Billing + Analytics | Monthly | CS |
| Resurrection rate | % of churned users who return | Reactivated users / Total churned pool | 2-8% monthly | Product analytics | Monthly | Growth |
| Logo retention | % of accounts retained | (Accounts at start - Churned accounts) / Accounts at start | > 90% annual (SMB), > 95% (Enterprise) | Billing | Monthly | CS |

### Monetisation

| Metric | Definition | Formula | Benchmark Range | Data Source | Frequency | Owner |
|--------|-----------|---------|----------------|-------------|-----------|-------|
| Free-to-paid conversion | % of free users who become paying | subscription_created / user_signed_up (cohorted, 30/60/90 day window) | 2-5% at 30 days, 5-10% at 90 days (B2B SaaS) | Billing + Analytics | Weekly | Growth |
| Trial-to-paid conversion | % of trial users who convert | subscription_created / trial_started | 15-25% (opt-in trial), 40-60% (opt-out/CC required) | Billing | Weekly | Growth |
| ARPA (Avg Revenue Per Account) | Average monthly revenue per paying account | Total MRR / Total paying accounts | $50-$500 (SMB SaaS), $1K-$10K (mid-market) | Billing | Monthly | Finance |
| Expansion rate | % of existing MRR from expansion | Expansion MRR / Beginning-of-period MRR | > 5% monthly is strong | Billing | Monthly | Growth |
| Contraction rate | % of existing MRR lost to downgrades | Contraction MRR / Beginning-of-period MRR | < 2% monthly | Billing | Monthly | CS |
| Net Dollar Retention (NDR) | Revenue retained + expanded from existing customers | (Beginning MRR + Expansion - Contraction - Churn) / Beginning MRR | > 100% good, > 120% excellent | Billing | Monthly | Finance |
| LTV | Lifetime value of a customer | ARPA / Monthly churn rate (simplified) or ARPA x Avg customer lifetime | LTV/CAC > 3x | Billing + Analytics | Quarterly | Finance |
| LTV/CAC ratio | Efficiency of acquisition spending | LTV / CAC | > 3x healthy, > 5x excellent | Finance | Quarterly | Finance |
| Time to conversion | Days from signup to first payment | Median(subscription_created.timestamp - user_signed_up.timestamp) | < 14 days strong, < 30 days acceptable | Analytics + Billing | Monthly | Growth |

### Satisfaction

| Metric | Definition | Formula | Benchmark Range | Data Source | Frequency | Owner |
|--------|-----------|---------|----------------|-------------|-----------|-------|
| NPS | Net Promoter Score | % Promoters (9-10) - % Detractors (0-6) | > 30 good, > 50 excellent (B2B SaaS) | Survey tool | Quarterly | Product |
| CSAT | Customer Satisfaction Score | Avg satisfaction rating (1-5 or 1-7 scale) | > 4.0/5.0 | Survey tool | Monthly | Support |
| CES | Customer Effort Score | Avg effort rating for key flows | < 3.0/7.0 (lower = less effort = better) | Survey tool | Monthly | Product |
| PMF score | Product-Market Fit indicator | % respondents "very disappointed" if product gone | > 40% = PMF (Sean Ellis test) | Survey tool | Quarterly | Product |
| Support ticket rate | Tickets per 100 active users | Support tickets / Active users x 100 | < 5 per 100 users/month | Support tool | Monthly | Support |
| Time to resolution | Avg time to resolve support tickets | Avg(ticket_resolved.timestamp - support_ticket_created.timestamp) | < 4h first response, < 24h resolution | Support tool | Weekly | Support |

---

## Revenue Component Metrics

For SaaS businesses, total MRR decomposes into six components. Each component has its own driver metrics.

### New MRR

**Formula:** New customers x ARPA(new)

**Driver decomposition:**
```
New MRR
= Signups x Activation rate x Conversion rate x ARPA(new)
```

| Driver | Metric | How to Improve | Sensitivity |
|--------|--------|---------------|-------------|
| Signups | Count of user_signed_up | Acquisition channels, signup optimization | Medium |
| Activation rate | activated / signed_up | Onboarding, TTV reduction, setup assistance | High |
| Conversion rate | paid / activated | Pricing, packaging, paywall design, sales-assist | High |
| ARPA(new) | Revenue per new customer | Pricing, plan design, anchoring, expansion hooks | Medium |

### Retained MRR

**Formula:** Retention rate x Existing MRR

| Driver | Metric | How to Improve | Sensitivity |
|--------|--------|---------------|-------------|
| Retention rate | 1 - churn rate | Engagement depth, habit formation, switching costs | Very High |
| Existing MRR | Current paying account base x ARPA | Historical growth (cannot improve directly) | N/A |

### Churned MRR

**Formula:** Churn rate x Existing MRR

Split into:
- **Voluntary churn:** User actively cancels. Driven by dissatisfaction, budget, competitor switch, no longer need.
- **Involuntary churn:** Payment fails and is not recovered. Driven by expired cards, insufficient funds, bank declines.

| Driver | Metric | How to Improve | Sensitivity |
|--------|--------|---------------|-------------|
| Voluntary churn rate | Active cancellations / Total accounts | Product value, CS intervention, offboarding flow | High |
| Involuntary churn rate | Failed + unrecovered payments / Total accounts | Dunning emails, card updater, retry logic | Medium (but easy win) |
| Recovery rate | Recovered payments / Failed payments | Dunning sequence, in-app payment update prompts | Medium |

### Expansion MRR

**Formula:** Expansion rate x Existing MRR

Split into:
- **Seat expansion:** Adding more users to the account
- **Plan upgrades:** Moving to a higher-tier plan
- **Add-on purchases:** Buying additional features/modules

| Driver | Metric | How to Improve | Sensitivity |
|--------|--------|---------------|-------------|
| Seat expansion rate | New seats / Total seats | Collaboration features, invite flows, team value | High |
| Upgrade rate | Plan upgrades / Total accounts on lower plans | Usage limits, feature gating, upgrade prompts | High |
| Add-on attach rate | Add-on purchases / Total paying accounts | Add-on discovery, contextual upsell | Medium |

### Contraction MRR

**Formula:** Contraction rate x Existing MRR

| Driver | Metric | How to Improve | Sensitivity |
|--------|--------|---------------|-------------|
| Downgrade rate | Plan downgrades / Total accounts on higher plans | Value delivery at higher tiers, feature usage | Medium |
| Seat removal rate | Removed seats / Total seats | Team engagement, admin satisfaction | Low-Medium |

### Reactivation MRR

**Formula:** Reactivation rate x Churned pool x ARPA

| Driver | Metric | How to Improve | Sensitivity |
|--------|--------|---------------|-------------|
| Reactivation rate | Reactivated accounts / Total churned accounts | Win-back campaigns, product improvements, re-engagement email | Low-Medium |
| Churned pool size | Cumulative churned accounts | Historical (cannot reduce directly) | N/A |
| ARPA(reactivated) | Revenue per reactivated customer | Re-activation offers, plan simplification | Low |

---

## Metric Ownership Matrix

| Team | Owns These Metrics | Contributes To |
|------|-------------------|---------------|
| Marketing | Visitors, signups, signup rate, CAC, channel distribution | Acquisition dashboard |
| Growth | Activation rate, TTV, conversion rate, viral coefficient, expansion rate | All AARMS dashboards |
| Product | Feature adoption, engagement score, onboarding completion, D7/D30 retention | Activation + Retention dashboards |
| CS / Support | Churn rate, NPS, CSAT, support ticket rate, logo retention | Retention + Satisfaction dashboards |
| Finance | MRR, ARPA, LTV, NDR, payback period | Revenue driver tree dashboard |
| Sales | PQL conversion, sales-assisted revenue, expansion (enterprise) | Monetisation dashboard |

---

## Metric Review Cadence

| Cadence | What to Review | Who Attends | Format |
|---------|---------------|-------------|--------|
| Daily | Signups, activation rate, key events volume (anomaly detection) | Growth PM (async) | Automated alert / dashboard check |
| Weekly | AARMS funnel metrics, experiment status, week-over-week trends | Growth team | 30-min meeting with dashboard walkthrough |
| Monthly | MRR components, cohort analysis, feature adoption, churn analysis | Growth + Product + Finance | 60-min meeting with deep-dive on 1-2 areas |
| Quarterly | Revenue driver tree full review, goal progress, strategy alignment | Leadership + Growth + Product + Finance | 90-min meeting with strategic recommendations |
