# Monetisation Work Plan — Domain Examples

Domain-specific worked examples for monetisation work plans. Use alongside the shared skeleton at `${CLAUDE_PLUGIN_ROOT}/references/work-plan-template.md` (plan formats, work-item format, priority-by-sensitivity, work-type definitions, generic checklist).

---

## OST Examples

**Objective:** Increase ARPA from $45 to $65 within 2 quarters

**Strategy 1: Improve tier upgrade rate**
- Hypothesis: "We believe redesigning our pricing page with stronger anchoring will increase Pro plan selection by 15% because current page does not differentiate tiers clearly"
- Tactic 1: Audit pricing page against best practices (Week 1)
- Tactic 2: Design and ship new pricing page with recommended tier highlight (Weeks 2-4)
- Tactic 3: A/B test new page vs old (Weeks 5-8)

**Strategy 2: Launch seat-based expansion program** *(example assumes a seat-based model — adapt the expansion motion to the product's pricing metric: usage tiers, outcome volume, etc.)*
- Hypothesis: "We believe proactive seat expansion prompts will increase average seats per account from 4.2 to 6.0 because 35% of accounts have inactive invited users"
- Tactic 1: Build seat utilization dashboard (Week 1-2)
- Tactic 2: Implement "invite your team" prompts at collaboration touchpoints (Weeks 3-5)
- Tactic 3: Launch admin notification when team outgrows plan (Week 6)

---

## Experiment Backlog Examples

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

## Research Plan Examples

**Research Question:** "What is the optimal pricing metric and price range for our Pro plan?"

**Study 1: Van Westendorp Price Sensitivity**
- Objective: Identify acceptable price range for Pro plan
- Method: Van Westendorp 4-question survey (see `references/research-methods.md`)
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
