# PQA and PQL Framework

## PQA: Product-Qualified Account

### Definition

A Product-Qualified Account (PQA) is an account (company/organization) showing product usage patterns that predict enterprise buying intent. PQA is an account-level concept — it identifies which companies are ripe for sales engagement based on how their users are collectively using the product.

### Signal Categories

#### Usage Volume Signals
- **Active users in account:** Number of distinct users active in the last 7/14/30 days
- **Session frequency:** Average sessions per user per week
- **Action volume:** Total product actions per account per week
- **Core feature usage:** % of core features used by at least one user

Interpretation: Higher volume = more embedded in workflows = more likely to pay/expand.

#### Team Breadth Signals
- **Departments represented:** Number of distinct departments using the product (inferred from email domains, team names, or role data)
- **Distinct roles:** Number of different job functions using the product
- **Geographic spread:** Users from multiple offices/locations
- **Cross-team collaboration:** Shared projects or resources across teams

Interpretation: Broader adoption = harder to rip out = higher expansion potential.

#### Feature Adoption Signals
- **Premium feature attempts:** Users trying to access gated features (clicking locked features, viewing upgrade prompts)
- **Integration count:** Number of integrations connected (more integrations = more embedded)
- **API usage:** API calls indicate technical investment in the product
- **Advanced feature adoption:** Usage of non-basic features (reporting, automation, admin)

Interpretation: Deep feature adoption = high switching costs = expansion opportunity.

#### Growth Trend Signals
- **Week-over-week active user increase:** Growing accounts are expanding organically
- **Seat addition velocity:** Rate of new users being invited
- **Usage acceleration:** Increasing actions per user over time
- **New use case adoption:** Account starts using product for new workflows

Interpretation: Growing accounts are the highest-priority PLS targets.

#### Firmographic Signals
- **Company size:** Larger companies have higher expansion ceiling
- **Industry:** Some industries have higher ACV potential
- **Tech stack:** Companies using complementary tools may have higher intent
- **Funding stage:** Recently funded companies are more likely to invest in tools

Interpretation: Firmographics set the ceiling; product usage signals set the priority.

### Building a PQA Scoring Model

**Step 1: List all available signals**
Inventory what product data you can access at the account level.

**Step 2: Weight signals by predictive power**
Start with expert judgment (assign weights 1-10), then validate with data:
- Pull the list of accounts that converted to enterprise in the last 12 months
- Check which signals those accounts exhibited before conversion
- Adjust weights based on actual predictive power

**Step 3: Create a composite score**
```
PQA Score = (Active Users × W1) + (Departments × W2) + (Premium Feature Attempts × W3) + (Growth Trend × W4) + (Firmographic Score × W5)
```

Normalize to 0-100 scale.

**Step 4: Set threshold**
- Examine score distribution
- Set threshold where conversion rate jumps (typically top 10-20% of accounts)
- Accounts above threshold = PQA → enter sales pipeline

**Step 5: Validate and iterate**
- Track PQA → conversion rate monthly
- Compare PQA conversion rate to non-PQA conversion rate (should be 3-5x higher)
- Adjust weights and thresholds quarterly based on actual outcomes

### Example PQA Scoring

| Signal | Weight | Score (0-10) | Weighted |
|--------|--------|-------------|----------|
| Active users (>10) | 3 | 8 | 24 |
| Departments (>2) | 2.5 | 6 | 15 |
| Premium feature attempts (>5/month) | 2 | 9 | 18 |
| WoW user growth (>10%) | 2 | 7 | 14 |
| Company size (>200) | 1.5 | 8 | 12 |
| Integration count (>3) | 1 | 5 | 5 |
| **Total** | | | **88/130 → 68%** |

Threshold: 60% → This account is a PQA. Enter pipeline.

---

## PQL: Product-Qualified Lead

### Definition

A Product-Qualified Lead (PQL) is an individual user showing buying intent through product behavior. PQL is a user-level concept — it identifies who within an account is the likely champion or buyer.

### Signal Categories

#### Buying Intent Signals (Highest Weight)
- **Pricing page visits:** User viewed pricing page (especially multiple times)
- **Plan comparison:** User compared plans side by side
- **Upgrade flow started:** User began but did not complete upgrade
- **Billing page access:** User visited billing or invoice pages
- **Enterprise contact form:** User submitted or viewed enterprise contact form

#### Team Building Signals
- **Invite attempts:** User tried to invite teammates (especially above free tier limit)
- **Admin features explored:** User accessed admin panel, permissions, roles
- **Workspace setup:** User created teams, channels, or organizational structures
- **SSO/SAML inquiry:** User explored or requested SSO setup

#### Limit-Hitting Signals
- **Usage limit events:** User hit storage, seat, project, or API limits
- **Upgrade prompt interactions:** User clicked "upgrade" prompts in product
- **Feature gate interactions:** User attempted to use gated premium features
- **Rate limit hits:** API rate limit exceeded

#### Power Usage Signals
- **API usage:** Regular API calls indicate technical investment
- **Export frequency:** Regular data exports suggest the product is embedded in workflows
- **Integration setup:** User connected multiple integrations
- **Automation creation:** User built workflows or automations

#### Role and Authority Signals
- **Job title:** VP, Director, Head of, Manager (buying authority indicators)
- **Admin role in product:** Has admin or owner permissions
- **Email domain match:** Matches the target company domain
- **Multiple team management:** Manages multiple teams or projects

### Building a PQL Scoring Model

**Combine three signal types:**

```
PQL Score = Product Signals (60%) + Firmographic Signals (25%) + Behavioral Signals (15%)
```

**Product Signals (60%):**
- Pricing page visits (0-10)
- Limit-hitting events (0-10)
- Feature gate interactions (0-10)
- Team building actions (0-10)

**Firmographic Signals (25%):**
- Company size score (0-10)
- Industry fit score (0-10)
- Role/title authority score (0-10)

**Behavioral Signals (15%):**
- Email engagement with product comms (0-10)
- Content downloads (guides, case studies) (0-10)
- Webinar/event attendance (0-10)

### PQA vs PQL: How They Work Together

```
Step 1: PQA scoring identifies high-potential ACCOUNTS
    → "This company has 15 active users across 3 departments with growing usage"

Step 2: PQL scoring identifies the CHAMPION within those accounts
    → "Sarah (VP Product) visited pricing 3x, hit the seat limit, and explored SSO"

Step 3: Sales outreach targets Sarah with account-level context
    → "Sarah, I noticed your team of 15 at [Company] has been using [Product] heavily.
       You recently hit the seat limit. Can we discuss a plan that fits your team's growth?"
```

### Implementation Path

**Phase 1: Simple Rules (Month 1-2)**
- PQA: Account with >5 active users AND >2 departments → flag
- PQL: User who visited pricing page 2+ times OR hit a usage limit → flag
- Manual review by sales: confirm or dismiss

**Phase 2: Weighted Scoring (Month 3-6)**
- Build composite scores with signal weights
- Set thresholds based on Phase 1 conversion data
- Semi-automated: scores trigger alerts, humans decide outreach

**Phase 3: ML Scoring (Month 6+)**
- Train model on historical PQA/PQL → conversion outcomes
- Automated scoring with confidence intervals
- Sales sees prioritized list with predicted conversion probability
- Continuous model retraining on new data

### Common Pitfalls

- **Too many PQLs:** If every user is a PQL, the signal is meaningless. Keep threshold high enough that PQLs convert at 3-5x the base rate.
- **Ignoring negative signals:** Churned users, declining usage, and support complaints should reduce PQL scores.
- **Static scoring:** User behavior changes. Re-score regularly (daily or weekly), do not flag once and forget.
- **No feedback loop:** Sales must report back whether PQLs were actually qualified. Use this feedback to tune the model.
