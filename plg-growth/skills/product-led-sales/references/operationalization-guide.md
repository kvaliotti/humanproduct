# PLS Operationalization Guide

How to build the infrastructure, team, and processes that make Product-Led Sales work at scale.

---

## 1. Data Infrastructure

### The PLS Data Stack

```
Product Events (clicks, actions, features used)
    → Event Tracking (Segment, Rudderstack, custom)
        → Data Warehouse (BigQuery, Snowflake, Redshift)
            → Scoring Model (dbt + Python, or ML platform)
                → CRM Sync (Salesforce, HubSpot)
                    → Sales Dashboards & Alerts
```

### Layer 1: Product Event Tracking

**What to track:**

| Event Category | Examples | Why |
|---------------|----------|-----|
| Core actions | Create project, send message, upload file | Usage depth |
| Feature usage | Each feature touched with timestamp | Feature adoption breadth |
| Team actions | Invite user, create team, share workspace | Collaboration signals |
| Limit events | Hit seat/usage/storage limit, upgrade prompt shown | Expansion signals |
| Billing actions | Pricing page view, plan comparison, checkout start | Buying intent |
| Admin actions | Admin panel access, role management, SSO exploration | Enterprise readiness |
| Integration actions | Integration connected, API key generated | Switching cost depth |

**Implementation requirements:**
- User identification (user ID linked to account/company)
- Account mapping (users → companies, via email domain or explicit org)
- Event schema standardization (consistent naming, properties)
- Real-time or near-real-time event streaming (alerts cannot wait for batch processing)

### Layer 2: Data Warehouse

**Purpose:** Central repository for all product, CRM, and marketing data.

**Key tables/models:**
- `accounts`: Company-level data with firmographics
- `users`: User-level data with roles and permissions
- `events`: Product events with timestamps
- `account_scores`: PQA scores computed daily/hourly
- `user_scores`: PQL scores computed daily/hourly
- `account_health`: Health score combining usage, satisfaction, growth signals
- `pipeline`: CRM pipeline synced back for reporting

**dbt or similar transformation layer:**
- Aggregate user events to account-level metrics
- Compute rolling averages and trends
- Calculate PQA/PQL scores
- Flag accounts crossing thresholds
- Join product data with CRM data for reporting

### Layer 3: Scoring Model

**Start simple, evolve to ML:**

**Phase 1 — Rule-based scoring:**
```sql
PQA_SCORE = 
    (active_users_30d >= 5) * 20 +
    (departments_count >= 2) * 20 +
    (premium_feature_attempts_30d >= 3) * 15 +
    (wow_user_growth > 0.10) * 15 +
    (company_size >= 200) * 15 +
    (integrations_count >= 3) * 15
```

**Phase 2 — Weighted scoring:**
- Use historical conversion data to set weights
- Logistic regression on signal features → conversion outcome
- Output: probability of conversion (0-100%)

**Phase 3 — ML scoring:**
- Train on 6-12 months of PQA → conversion/no-conversion data
- Features: all product signals + firmographics
- Model: gradient boosted trees (XGBoost, LightGBM) or logistic regression
- Output: conversion probability with confidence interval
- Retrain monthly as new data accumulates

### Layer 4: CRM Sync

**Sync product data to CRM (Salesforce, HubSpot):**

| Data Point | CRM Field | Update Frequency |
|-----------|-----------|-----------------|
| PQA score | Custom account field | Daily |
| PQL score | Custom contact field | Daily |
| Active users | Custom account field | Daily |
| Key events (limit hit, pricing page) | CRM activity/task | Real-time |
| Health score | Custom account field | Daily |
| Product usage summary | Custom account section | Daily |

**Sync tools:**
- Census, Hightouch, or Polytomos (reverse ETL)
- Custom integration via CRM API
- Salesforce Connect or HubSpot data sync

**Critical: bi-directional sync.**
- Product data → CRM (for sales)
- CRM outcomes → warehouse (for model training: did PQA convert?)

---

## 2. Tools

### Essential Tools Stack

| Function | Tools | Purpose |
|----------|-------|---------|
| Product Analytics | Amplitude, Mixpanel, PostHog, Heap | Track user behavior, compute engagement metrics |
| CDP | Segment, Rudderstack | Collect and route events to all destinations |
| Data Warehouse | BigQuery, Snowflake, Redshift | Central data repository |
| Reverse ETL | Census, Hightouch | Sync product data to CRM |
| CRM | Salesforce, HubSpot | Pipeline management, account records |
| Sales Engagement | Outreach, SalesLoft, Apollo | SDR outreach automation, sequences |
| Enrichment | Clearbit, ZoomInfo, Apollo | Firmographic data for scoring |
| BI/Dashboards | Looker, Metabase, Mode | PLS dashboards and reporting |

### Optional but Valuable

| Function | Tools | Purpose |
|----------|-------|---------|
| Product-Led Sales Platform | Pocus, Correlated, Calixa | Purpose-built PLS scoring and workflows |
| Conversation Intelligence | Gong, Chorus | Analyze sales calls for PLS effectiveness |
| Customer Success | Gainsight, Vitally, Planhat | Health scoring and expansion management |
| Experimentation | LaunchDarkly, Statsig | Test PLS triggers and messages |

---

## 3. Team Structure

### PLS Team Roles

**SDR (Sales Development Representative):**
- Reviews PQA/PQL alerts daily
- Crafts product-informed outreach
- Qualifies leads through initial conversations
- Must have product access and understand usage dashboards
- Quota: SQLs per month, NOT emails sent

**AE (Account Executive):**
- Manages qualified opportunities through close
- Uses product data in demos, proposals, and negotiations
- Handles enterprise deal complexity (procurement, legal, security)
- Must understand the product deeply (ideally a power user themselves)
- Quota: Closed revenue, weighted toward expansion

**CSM (Customer Success Manager):**
- Owns post-sale relationship and expansion
- Monitors account health scores
- Identifies expansion opportunities in existing accounts
- Conducts business reviews with usage data
- Quota: Net revenue retention, expansion revenue

**RevOps / Growth Ops:**
- Builds and maintains PQA/PQL scoring models
- Manages CRM-product data integration
- Creates dashboards and reporting
- Optimizes pipeline and processes
- Reports to both Sales and Product leadership

### Team Sizing

| Company Stage | SDRs | AEs | CSMs | RevOps |
|--------------|------|-----|------|--------|
| Early PLS (testing) | 1 | 1 | 0 (AE covers) | 0 (eng covers) |
| Growth PLS | 2-4 | 1-2 | 1-2 | 1 |
| Scale PLS | 4-8 | 2-4 | 2-4 | 1-2 |

### Handoff Protocols

**PQA → SDR handoff:**
- Automated: account appears in SDR queue when PQA threshold crossed
- SDR has 24-hour SLA to review and decide on outreach
- SDR marks account as "engaged" or "passed" with reason

**SDR → AE handoff:**
- SDR schedules intro call with AE and prospect
- SDR provides: account summary, product usage data, champion profile, qualification notes
- AE has all product data before first call

**AE → CSM handoff:**
- AE introduces CSM before deal closes (warm handoff)
- AE provides: deal context, key contacts, usage baseline, expansion commitments
- CSM has full product usage history from day one

---

## 4. Compensation Design

### Principles

1. **Reward expansion, not just new logos:** PLS is primarily an expansion motion. Comp should reflect this.
2. **Credit the champion's journey:** If a self-serve account expands to enterprise, the AE gets credit for the expansion delta (not the self-serve revenue).
3. **Align with customer success:** CSM comp should include expansion revenue, not just retention.
4. **Do not penalize self-serve:** If an account would have upgraded self-serve, sales should not get credit (avoids PLS cannibalizing self-serve).

### Compensation Structure

**SDR Comp:**
- Base: 50-60% of OTE
- Variable: 40-50% tied to SQL creation
- Bonus: Quality multiplier (SQLs that convert to Opportunity at higher rate = higher payout)

**AE Comp:**
- Base: 50% of OTE
- Variable: 50% tied to closed revenue
- Split: 30% new business, 70% expansion (reflects PLS reality)
- Accelerators: Higher rate above quota, especially for enterprise conversions

**CSM Comp:**
- Base: 70-80% of OTE
- Variable: 20-30% tied to net revenue retention and expansion
- Bonus: Account health score improvement

### Self-Serve Protection

To prevent sales from claiming self-serve conversions:
- Accounts below a minimum size (e.g., <10 users) are self-serve only
- Upgrades that happen without any sales touch are self-serve revenue
- Sales credit begins only after documented outreach and engagement
- "Assist" vs "Originated" distinction in attribution

---

## 5. Playbooks by Scenario

### Playbook A: High-Touch PQA (Large Account, Strong Signals)

**Profile:** 20+ active users, 3+ departments, enterprise firmographic match, multiple intent signals.

**Approach:**
1. AE (not SDR) owns outreach
2. Research the account deeply: org chart, tech stack, news
3. Multi-threaded outreach: champion + their manager
4. Offer executive briefing or strategic workshop
5. Present enterprise value proposition with ROI model

**Timeline:** 2-6 months to close. Higher deal size justifies investment.

### Playbook B: Medium-Touch PQA (Growing Account, Moderate Signals)

**Profile:** 5-15 active users, 1-2 departments, growth trend, some intent signals.

**Approach:**
1. SDR outreach to champion
2. Product-informed messaging referencing usage
3. Offer team plan upgrade with specific benefits
4. Introduce AE if deal complexity warrants it

**Timeline:** 2-8 weeks to close. Shorter cycle, smaller deal.

### Playbook C: Low-Touch PQA (Small Account, Early Signals)

**Profile:** 3-5 active users, one team, early growth signals.

**Approach:**
1. Automated email sequence triggered by PQA score
2. Product-informed but templated messaging
3. Self-serve upgrade path with chat support available
4. SDR engages only if prospect responds

**Timeline:** 1-4 weeks. Most should self-serve with light assist.

### Playbook D: Expansion Within Existing Enterprise Account

**Profile:** Existing enterprise customer with new departments adopting or current departments expanding.

**Approach:**
1. CSM identifies expansion signals in health scoring
2. CSM conducts quarterly business review with usage data
3. Proposal for seat/tier expansion based on growth
4. AE supports for significant upsells or new business unit deals

**Timeline:** Ongoing. Expansion is continuous, not event-based.
