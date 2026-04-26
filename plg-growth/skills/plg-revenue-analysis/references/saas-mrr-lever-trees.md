# SaaS MRR Lever Trees — Full Decomposition

Deep decomposition of each MRR component with specific product levers for each branch.

---

## New MRR

### Formula
New MRR = Traffic x Signup Conv x Activation Rate x Paid Conv x ARPA(new)

### Traffic Decomposition

```
Traffic (monthly unique visitors)
├── Organic Search
│   ├── Branded search (people searching your name)
│   ├── Non-branded search (category/problem terms)
│   ├── Content/blog traffic
│   └── Product-generated SEO (public pages, templates, community)
├── Paid Acquisition
│   ├── Search ads (Google/Bing)
│   ├── Social ads (Meta, LinkedIn, Twitter)
│   ├── Display/programmatic
│   └── Sponsorships/newsletters
├── Referral / Viral
│   ├── User invitations (in-product invite flow)
│   ├── Shared content/outputs (with branding)
│   ├── Referral program (incentivized)
│   └── Word of mouth (organic)
├── Direct / Brand
│   ├── Direct URL visits
│   ├── App store search (if applicable)
│   └── Brand awareness campaigns
└── Partnerships
    ├── Integration marketplace listings
    ├── Co-marketing with partners
    └── Channel/reseller partners
```

**Product levers for traffic:**
- Make product outputs shareable with branding (Loom links, Canva designs)
- Build template/resource gallery for SEO
- Create embed/widget that lives on other sites
- In-product invite flows with clear value prop for invitee
- Integration marketplace presence

### Signup Conversion Rate

```
Signup Conversion (visitor → registered user)
├── Landing page clarity
│   ├── Value prop understanding in <10 seconds
│   ├── Social proof visibility
│   └── CTA clarity
├── Signup friction
│   ├── Number of form fields
│   ├── Account creation method (email, Google SSO, etc.)
│   ├── Credit card requirement (removes 50-80% of signups)
│   └── Email verification requirement
├── Trust signals
│   ├── Security badges
│   ├── Customer logos
│   └── Reviews/ratings
└── Intent match
    ├── Traffic quality (right audience?)
    └── Landing page relevance to traffic source
```

**Benchmarks:**
- Visitor-to-signup: 2-5% (average), 8-15% (best-in-class PLG)
- Removing credit card increases signups 2-4x (but may lower quality)

### Activation Rate

```
Activation Rate (signup → qualified/activated user)
├── Onboarding completion
│   ├── Setup steps completed
│   ├── Drop-off at each step
│   └── Time to complete onboarding
├── Aha moment reached
│   ├── Core action completed (define this!)
│   ├── Value experienced (subjective)
│   └── Return visit within X days
├── Activation barriers
│   ├── Data import required
│   ├── Integration setup required
│   ├── Team invitation required
│   └── Content creation required
└── Segment-specific activation
    ├── By use case
    ├── By team size
    └── By source channel
```

**Benchmarks:**
- Signup-to-activation: 20-40% (average), 50-70% (best PLG)
- Each additional required step drops activation ~20%

### Paid Conversion Rate

```
Paid Conversion (activated → paying)
├── Conversion triggers
│   ├── Feature limit hit
│   ├── Usage limit hit
│   ├── Trial expiration
│   ├── Team growth need
│   └── Proactive upgrade prompt
├── Conversion barriers
│   ├── Pricing complexity
│   ├── Payment friction
│   ├── Approval process required
│   ├── Value not yet proven
│   └── Free tier too generous
└── Conversion optimization
    ├── Upgrade messaging/positioning
    ├── Pricing page clarity
    ├── Payment method options
    └── Trial extension / save flow
```

**Benchmarks:**
- Free-to-paid (freemium): 2-5% (average), 7-15% (best)
- Trial-to-paid: 15-25% (average), 30-50% (best)
- PQL-to-paid: 20-40% (with sales assist)

---

## Churned MRR

### Formula
Churned MRR = Voluntary Churn + Involuntary Churn

### Voluntary Churn Decomposition

```
Voluntary Churn (customer actively cancels)
├── Dissatisfied with product
│   ├── Product quality issues (bugs, performance)
│   ├── Missing features (gaps vs. needs)
│   ├── UX complexity (too hard to use)
│   └── Poor support experience
├── No longer need the product
│   ├── Use case ended (project completed, company closed)
│   ├── Role change (champion left the company)
│   └── Seasonal use (only needed part of year)
├── Switched to competitor
│   ├── Better product fit
│   ├── Better price
│   ├── Better integration with their stack
│   └── Consolidation (competitor acquired by existing vendor)
└── Price sensitivity
    ├── Budget cuts
    ├── Perceived value < price
    └── Found free alternative
```

**Product levers for voluntary churn:**
- Exit survey to identify top reasons
- At-risk scoring (usage decline → proactive intervention)
- Feature request tracking → roadmap alignment
- Champion tracking → alert when champion goes inactive
- Win-back campaigns for common churn reasons

### Involuntary Churn Decomposition

```
Involuntary Churn (payment failure, not intentional)
├── Payment failure
│   ├── Insufficient funds
│   ├── Card declined (fraud protection)
│   └── Bank processing error
├── Card expiry
│   ├── Card expired without update
│   └── No card-update reminder sent
└── Billing errors
    ├── Billing address mismatch
    ├── Currency/tax issues
    └── Corporate card restrictions
```

**Product levers for involuntary churn:**
- Dunning emails (card expiry reminders, payment failure retries)
- Smart retry logic (retry at optimal times)
- Multiple payment methods on file
- Grace period before account suspension
- In-app payment update prompts

**Benchmarks:**
- Monthly gross churn: 3-7% (SMB), 0.5-2% (mid-market), 0.3-1% (enterprise)
- Involuntary churn is typically 20-40% of total churn — low-hanging fruit

---

## Expansion MRR

### Formula
Expansion MRR = Seat Expansion + Usage Expansion + Plan Upgrades + Add-on Purchases

```
Seat Expansion
├── Viral invitation rate (user invites colleagues)
├── x Invitation acceptance rate
├── x Invitee activation rate
├── x Invitee-to-paid conversion (if seat-based pricing)
└── Average seats per account over time

Usage Expansion
├── Usage growth per active user
├── x Marginal price of additional usage
└── Overage triggers and pricing

Plan Upgrades
├── Feature limit triggers
│   ├── Users hitting feature walls
│   ├── Upgrade prompt effectiveness
│   └── Upgrade friction (ease of upgrading)
├── x Upgrade rate (% hitting limit who upgrade)
└── x Tier price delta (revenue increase per upgrade)

Add-on Purchases
├── Add-on visibility and discovery
├── x Add-on relevance to user segment
├── x Add-on attach rate
└── x Add-on average price
```

**Product levers for expansion:**
- In-product prompts when approaching limits
- "Invite your team" flows at natural collaboration moments
- Usage dashboards showing value (justify higher spend)
- Bundle discounts for upgrades (make upgrade feel like a deal)
- Auto-upgrade with notification (usage-based pricing)

**Benchmarks:**
- Net Revenue Retention: 100-110% (good), 110-130% (great), 130%+ (exceptional)
- Seat expansion rate: 5-15% of accounts expand per quarter
- Upgrade rate: 5-10% of eligible users per quarter

---

## Contraction MRR

```
Contraction MRR
├── Seat removal
│   ├── Team downsizing
│   ├── Inactive users cleaned up
│   └── Cost-cutting optimization
├── Plan downgrade
│   ├── Over-provisioned (paying for features not used)
│   ├── Budget reduction
│   └── Competitor offers lower tier at same capability
├── Add-on cancellation
│   └── Add-on value not demonstrated
└── Usage decrease
    ├── Seasonal patterns
    ├── Project completion
    └── Engagement decline
```

---

## Reactivation MRR

```
Reactivation MRR
├── Churned customer pool (total churned accounts)
├── x Reactivation rate
│   ├── Win-back email campaigns
│   ├── Product improvement announcements
│   ├── Seasonal/trigger-based outreach
│   └── Special offers for returning customers
└── x Reactivated ARPA
    ├── Same plan as before
    ├── Lower plan (re-entry)
    └── Higher plan (product improved since they left)
```

**Product levers:**
- Maintain account data for churned users (easy re-entry)
- "What's new" communications to churned pool
- Re-engagement triggers based on original churn reason
- Reduced friction for returning (remember preferences, skip onboarding)

**Benchmarks:**
- Monthly reactivation rate: 0.5-2% of churned pool
- Reactivated customers often have higher retention than average (they came back for a reason)
