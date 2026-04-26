# Product-Led Sales Pipeline

## Pipeline Overview

The PLS pipeline differs from traditional sales in one critical way: every stage is informed by product data. The prospect is already using the product. Sales adds value on top of self-serve, not instead of it.

```
Product Usage (always-on monitoring)
    ↓
PQA Identified (product signals + firmographic match)
    ↓
MQL Qualified (add intent signals: pricing page, growth, limits)
    ↓
SDR Outreach (product-informed, references usage)
    ↓
SQL (BANT qualified with product context)
    ↓
Opportunity (AE-led, product-informed sales process)
    ↓
Closed Won / Closed Lost
```

---

## Stage Details

### Stage 0: Product Usage Monitoring (Always On)

**What happens:** All account and user activity is tracked, scored, and synced to CRM.

**Data requirements:**
- User-level event tracking (product analytics)
- Account identification (mapping users to companies)
- PQA/PQL scoring model running continuously
- Real-time data sync to CRM

**Key metrics:**
- Total tracked accounts
- % of accounts with sufficient data for scoring
- PQA score distribution

**Exit criteria:** Account crosses PQA threshold → moves to next stage.

---

### Stage 1: PQA Identified

**What happens:** Account scoring model flags the account as a PQA based on product usage signals and firmographic match.

**Trigger signals:**
- Active users in account exceed threshold (e.g., >5)
- Multiple departments detected
- Usage growth trend is positive
- Firmographic match (company size, industry fit)

**Actions:**
- CRM record created or enriched with product data
- Account assigned to SDR territory/pod
- Product usage dashboard populated for sales team view

**Key metrics:**
- PQA volume per month
- PQA score distribution
- False positive rate (PQAs that never engage with sales)

**Exit criteria:** Intent signals detected → moves to MQL.

---

### Stage 2: MQL Qualification

**What happens:** On top of PQA product signals, intent signals confirm the account is actively considering expansion or purchase.

**Intent signals that upgrade PQA to MQL:**
- Pricing page visited by account user(s)
- Usage limit hit or upgrade prompt clicked
- Team growth acceleration (rapid seat additions)
- Admin/enterprise feature exploration (SSO, SCIM, audit log)
- Support ticket about enterprise features
- Manual request for enterprise pricing or security review

**Actions:**
- SDR reviews account dashboard (product usage summary)
- SDR identifies champion (highest PQL score user)
- Outreach strategy prepared based on specific signals

**Key metrics:**
- PQA → MQL conversion rate (target: 20-40%)
- Time from PQA to MQL (signal detection speed)
- MQL accuracy (do MQLs actually engage with outreach?)

**Exit criteria:** SDR qualifies the lead through outreach → moves to SQL.

---

### Stage 3: SDR Outreach (Product-Informed)

**What happens:** SDR reaches out to the champion with messaging that references their specific product usage. This is the critical differentiator of PLS.

**Outreach principles:**
1. **Reference specific usage:** "I see your team of 12 has been using [Product] for project management across your engineering and design teams"
2. **Acknowledge their success:** "You have completed 47 projects in the last quarter — impressive adoption"
3. **Address observed friction:** "It looks like your team hit the project limit last week"
4. **Offer specific value:** "Teams your size typically benefit from our Team plan, which includes unlimited projects and admin controls"
5. **NEVER generic pitch:** No "Hi, I wanted to introduce [Product]" — they already use it

**Outreach templates by signal:**

**Limit-hit signal:**
> Hi [Name], I noticed your team recently hit the [limit type] limit on [Product]. That usually means things are going well! Teams at this stage often benefit from [Plan], which gives you [specific benefit]. Would it be helpful to walk through what that looks like for your team?

**Team growth signal:**
> Hi [Name], I see your [Product] workspace has grown from 5 to 15 users over the past month. Nice growth! As teams scale, they often need [specific enterprise features]. Happy to share how similar teams manage this transition.

**Enterprise feature exploration signal:**
> Hi [Name], I noticed you were exploring our SSO and admin features. Those are available on our Enterprise plan. Would it be useful to discuss how we can set that up for [Company]?

**Multi-department signal:**
> Hi [Name], [Company] now has teams from [Dept A], [Dept B], and [Dept C] all using [Product]. That is the kind of adoption that often leads to a company-wide rollout. Would you be open to a quick conversation about what that could look like?

**Key metrics:**
- Outreach response rate (target: 25-40%, should be much higher than cold outreach)
- Positive response rate (target: 15-25%)
- SDR → SQL conversion rate (target: 30-50%)
- Time from first outreach to SQL

**Exit criteria:** Prospect engages, confirms need, meets qualification criteria → SQL.

---

### Stage 4: SQL (Sales-Qualified Lead)

**What happens:** Standard BANT qualification, but enriched with product context.

**Qualification with product context:**

| BANT | Traditional Question | PLS Enhancement |
|------|---------------------|-----------------|
| Budget | "What is your budget?" | "Based on your team of 15, the Team plan would be $X/mo. Does that range work?" |
| Authority | "Who makes the decision?" | "You are the admin on the account. Do you also manage the budget, or should we include someone?" |
| Need | "What problem are you solving?" | "Your team is using [Product] for [observed use case]. What else would you need to roll this out org-wide?" |
| Timeline | "When do you want to start?" | "Your current plan renews on [date]. Does it make sense to upgrade at renewal or sooner?" |

**Key metrics:**
- MQL → SQL conversion rate (target: 40-60%)
- SQL quality: % that progress to Opportunity
- Average deal size at SQL stage

**Exit criteria:** Qualified, budget confirmed, decision-maker identified → Opportunity.

---

### Stage 5: Opportunity

**What happens:** AE manages the deal through the standard sales process, but every conversation and proposal is informed by product data.

**Product data in the sales process:**
- **Discovery call:** AE knows usage patterns before the call. No need to ask "what do you use us for?"
- **Demo:** Tailored to features the account actually uses, plus features they have not discovered
- **Proposal:** Based on actual team size and usage, not estimates
- **ROI calculation:** Populated with real usage data (time saved, projects completed, etc.)
- **Negotiation:** Usage data strengthens the value argument

**Key metrics:**
- SQL → Closed Won rate (target: 30-50%)
- Average deal size
- Sales cycle length (should be shorter than traditional sales due to product familiarity)
- Discount rate (should be lower — product usage proves value)

---

### Stage 6: Closed Won / Closed Lost

**Closed Won:**
- Customer migrated to new plan
- Success handoff to CSM (with full product usage history)
- Account health monitoring begins for expansion tracking

**Closed Lost:**
- Reason logged (budget, timing, competitor, no need)
- Account stays in product usage monitoring
- Re-engagement trigger set (if usage increases again later)

---

## Pipeline Metrics Dashboard

### Volume Metrics
| Stage | Monthly Volume | Conversion Rate | Avg Time in Stage |
|-------|---------------|----------------|-------------------|
| PQA | | | |
| MQL | | | |
| SQL | | | |
| Opportunity | | | |
| Closed Won | | | |

### Velocity Metrics
- **Pipeline velocity:** (# SQLs × win rate × avg deal size) / avg sales cycle days
- **Time from PQA to Close:** Total cycle time
- **SDR productivity:** SQLs per SDR per month
- **AE productivity:** Closed revenue per AE per quarter

### Quality Metrics
- **PQA accuracy:** % of PQAs that eventually convert (should be 3-5x base rate)
- **PQL accuracy:** % of PQLs that respond to outreach
- **Win rate vs non-PLS deals:** PLS deals should win at higher rates
- **Average deal size vs non-PLS:** PLS deals should be larger (product usage as evidence)
- **Sales cycle length vs non-PLS:** PLS deals should close faster

---

## Common Pipeline Failure Modes

| Failure | Symptom | Fix |
|---------|---------|-----|
| Too many PQAs, SDR overwhelmed | Low outreach rate, stale PQAs | Raise PQA threshold, prioritize by score |
| Low response rate | SDRs sending generic messages | Retrain SDRs on product-informed outreach |
| High SQL but low close rate | AEs not using product data in demos/proposals | Build product dashboards into AE workflow |
| Long sales cycle | Prospect already has all info from self-serve | Focus sales on adding unique value (enterprise features, customization, executive alignment) |
| PLS cannibalizing self-serve | Deals that would self-serve are going through sales | Set minimum account size for PLS engagement |
