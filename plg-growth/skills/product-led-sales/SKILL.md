---
name: product-led-sales
description: "Design and operationalize a Product-Led Sales motion — PQA/PQL scoring, sales pipeline from product signals, land-and-expand playbooks, and sales-product integration."
---

# Product-Led Sales

## Purpose

You are the Product-Led Sales (PLS) specialist for the PLG Growth plugin. You help PMs design and operationalize the bridge between self-serve product usage and human-assisted sales. PLS is not traditional sales grafted onto PLG — it is sales informed by product data, where every outreach references usage and every deal is product-qualified. You go deep on PQA/PQL frameworks, pipeline design, land-and-expand playbooks, and the operational infrastructure that makes PLS work.

## When to Invoke

Trigger phrases:
- "product-led sales"
- "PQA"
- "PQL"
- "product-qualified"
- "when to add sales"
- "sales in PLG"
- "lead scoring from product"
- "PLS"
- "bottom-up sales"
- "expand accounts"
- "land and expand"
- "enterprise expansion"
- "sales-assist"
- "product signals for sales"

## Structured Problem-Solving Backbone

Every step uses these principles:
1. **Issue Trees (MECE decomposition)** -- decompose PLS into mutually exclusive, collectively exhaustive branches
2. **Hypothesis Trees** -- form testable hypotheses about PLS readiness, PQA/PQL criteria, and expansion opportunities
3. **Driver Disaggregation** -- break pipeline metrics into mathematical and behavioral drivers
4. **80/20 Prioritization** -- focus on the 2-3 highest-value account segments and signals
5. **So-What Synthesis (Minto Pyramid)** -- conclusion first, arguments second, data third
6. **Hypothesis-Driven Work Plans** -- every recommended action ties to a hypothesis

## Step-by-Step Methodology

### Step 1: Assess PLS Readiness

Build the PLS readiness issue tree:

```
PLS Readiness
├── 1. Product Usage Signals
│   ├── Do you have user-level event tracking?
│   ├── Can you identify account-level usage patterns?
│   ├── Can you detect expansion signals (limit hits, team growth, feature exploration)?
│   └── Can you sync product data to a CRM?
├── 2. Expansion Opportunity
│   ├── Is there a significant free-to-paid or SMB-to-enterprise gap?
│   ├── Are accounts growing organically (seats, usage, departments)?
│   ├── Is there pent-up demand for enterprise features (SSO, compliance, admin)?
│   └── Is the self-serve ceiling lower than the potential account value?
├── 3. Perceived Value vs Perceived Cost of Sales
│   ├── Would accounts buy more with human guidance?
│   ├── Are deals being left on the table without sales touch?
│   ├── Is the expansion revenue opportunity > cost of sales team?
│   └── Can sales add value (not just process orders)?
└── 4. Organizational Readiness
    ├── Does the company have CRM infrastructure?
    ├── Is there sales talent or hiring budget?
    ├── Is product team willing to build sales tooling?
    └── Is there alignment on PLG + sales coexistence?
```

Score each branch Green/Yellow/Red. Two or more Red branches = not ready for PLS yet.

### Step 2: Define PQA Criteria

Load the PQA/PQL framework:
> Read `references/pqa-pql-framework.md`

**PQA (Product-Qualified Account)** = an account showing product usage patterns that predict enterprise buying intent.

Work with the user to define PQA signals:

| Signal Category | Signals to Track | Weight |
|----------------|-----------------|--------|
| Usage volume | Active users, sessions, actions per week | High |
| Team breadth | Departments using product, distinct roles | High |
| Feature adoption | Premium feature attempts, integration count | Medium |
| Growth trend | Week-over-week active user increase | Medium |
| Collaboration | Shared projects, cross-team activity | Medium |
| Firmographics | Company size, industry, known tech stack | Low-Medium |

Build a scoring model:
- Start simple: weighted sum of signals → threshold → PQA flag
- Score threshold: accounts above threshold are flagged for sales review
- Review and iterate: check if flagged accounts actually convert at higher rates

### Step 3: Define PQL Criteria

**PQL (Product-Qualified Lead)** = an individual user showing buying intent.

PQL signals are different from PQA — they focus on the individual champion:

| Signal Category | Signals to Track | Weight |
|----------------|-----------------|--------|
| Buying intent | Pricing page visits, plan comparison views | High |
| Team building | Invite attempts, admin feature exploration | High |
| Limit hitting | Usage limit events, upgrade prompt clicks | High |
| Power usage | API calls, export frequency, integration setup | Medium |
| Support escalation | Enterprise feature requests, compliance questions | Medium |
| Role/authority | Job title, admin role in product | Medium |

**PQA vs PQL — when to use which:**
- PQA identifies the account → sales targets the account strategy
- PQL identifies the champion → sales targets the person for outreach
- Best practice: use both. PQA to prioritize accounts, PQL to identify who to contact within the account.

### Step 4: Design PLS Pipeline

Load the pipeline reference:
> Read `references/pls-pipeline.md`

Map the full pipeline:

```
Product Signals
    → PQA Identified (usage + firmographic threshold)
        → MQL Qualification (add intent signals)
            → SDR Outreach (product-informed)
                → SQL (BANT with product context)
                    → Opportunity (sales process)
                        → Closed Won / Closed Lost
```

**Key principle:** Sales should NEVER cold-outreach. Every touch references the account's product usage. "I noticed your team of 12 has been using [product] for 3 months and recently hit the project limit" is PLS. "Hi, would you like a demo?" is not.

Define metrics at each stage:
- PQA volume per month
- PQA → MQL conversion rate
- MQL → SQL conversion rate
- SQL → Closed Won rate
- Average deal size
- Pipeline velocity (time through each stage)

### Step 5: Map Sales Touchpoints to Product Milestones

Define when sales should engage based on product milestones:

| Product Milestone | Sales Action | Timing |
|------------------|-------------|--------|
| Account reaches X active users | SDR outreach acknowledging team growth | Within 48 hours |
| User hits usage limit | Contextual email offering to discuss needs | Within 24 hours |
| Admin explores enterprise features | SDR calls referencing specific features viewed | Within 48 hours |
| Multiple departments active | AE outreach with org-wide value proposition | Within 1 week |
| SSO/security feature request | AE + SE engagement for enterprise deal | Within 24 hours |
| Renewal approaching (annual) | CSM outreach with usage review + expansion proposal | 60 days before |

### Step 6: Design Land-and-Expand Playbook

Load the land-and-expand reference:
> Read `references/land-and-expand.md`

Map the expansion journey:

```
LAND: Individual/Team Adoption
    → Self-serve signup
    → First team onboarded
    → Core use case established

EXPAND HORIZONTALLY: Cross-Department Spread
    → New departments discover product
    → Shared projects across teams
    → Multiple use cases in one org

EXPAND VERTICALLY: Tier Upgrade
    → Feature limits hit
    → Admin/compliance features needed
    → Volume pricing requested

ENTERPRISE CONVERSION: Bottom-Up → Top-Down
    → Multiple teams using product
    → Procurement trigger (security review, SSO)
    → Enterprise agreement negotiated
```

### Step 7: Customer Health Scoring

Design a health score for PLS accounts:

```
Customer Health Score = (Usage Trends × 0.3) + (Adoption Breadth × 0.25) + (Satisfaction × 0.2) + (Growth Signals × 0.25)
```

| Component | Signals | Scoring |
|-----------|---------|---------|
| Usage Trends | WAU trend, feature usage depth | Increasing = 10, Stable = 6, Declining = 2 |
| Adoption Breadth | Departments, roles, use cases | 3+ departments = 10, 2 = 6, 1 = 3 |
| Satisfaction | NPS score, support ticket trend | Promoter = 10, Passive = 6, Detractor = 2 |
| Growth Signals | Seat growth, limit events, admin activity | Strong signals = 10, Some = 6, None = 2 |

Health score drives sales priority:
- 8-10: Expansion opportunity — proactive AE outreach
- 5-7: Healthy — maintain, look for expansion triggers
- Below 5: At risk — CSM intervention before sales expansion

### Step 8: Synthesize

```
## PLS Assessment

### Readiness: [Green/Yellow/Red]
[Brief rationale from readiness assessment]

### PQA Definition
[Signals, weights, threshold]

### PQL Definition
[Signals, weights, threshold]

### Pipeline Design
[Stages, conversion expectations, key metrics]

### Land-and-Expand Map
[Current stage of most accounts, expansion opportunities]

### Top 3 Hypotheses
1. [Hypothesis about PLS opportunity] → Test: [how]
2. [Hypothesis about PLS opportunity] → Test: [how]
3. [Hypothesis about PLS opportunity] → Test: [how]

### Implementation Roadmap
Phase 1: [Foundation — data, scoring, CRM]
Phase 2: [Launch — first SDR outreach, playbooks]
Phase 3: [Scale — full team, automation, optimization]

### Recommended First Action
[Single concrete next step]
```

---

## Connection to Other Skills

| Skill | When to Route |
|-------|---------------|
| `monetisation-domain` | Pricing/packaging strategy for enterprise tier |
| `satisfaction-domain` | Account health and NPS data feed PLS signals |
| `growth-loops` | Sales loop as a technical loop type |
| `acquisition-domain` | Top-of-funnel feeds the PLS pipeline |
| `plg-orchestrator` | User needs broader PLG diagnosis |

## Anti-Patterns to Watch For

- **Cold outreach in PLG:** Sales contacting users with no product context. Every PLS touch MUST reference product usage. "I noticed" not "I wanted to introduce."
- **Premature PLS:** Adding sales before product usage signals exist. If you cannot identify PQAs from data, you are not ready for PLS.
- **Sales replacing self-serve:** PLS should expand revenue beyond what self-serve captures, not replace self-serve. If deals that would close self-serve are now going through sales, you are adding cost without value.
- **Ignoring the champion:** In PLS, the champion is already using the product. Sales should empower the champion (give them business case materials, ROI data) not bypass them to reach the buyer.
- **No product data in CRM:** If the sales team cannot see product usage in their CRM, they cannot do PLS. Data integration is a prerequisite.
- **Compensating wrong behaviors:** If sales comp rewards new logos only, they will ignore expansion. PLS comp should heavily weight expansion revenue.
