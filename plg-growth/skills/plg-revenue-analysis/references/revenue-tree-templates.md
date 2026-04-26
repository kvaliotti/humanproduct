# Revenue Tree Templates by Model

Pre-built decomposition templates for 7 revenue models. Select the one that matches, then customize for the specific product.

---

## Template 1: SaaS / Subscription (MRR-Based)

```
MRR
├── New MRR (+)
│   ├── Traffic (visitors)
│   │   ├── Organic search
│   │   ├── Paid acquisition
│   │   ├── Referral / viral
│   │   ├── Direct / brand
│   │   └── Partnerships
│   ├── x Signup conversion rate
│   ├── x Activation rate (signup → qualified user)
│   └── x Paid conversion rate (qualified → paying)
│       └── x ARPA (average revenue per account)
│
├── Retained MRR (=)
│   ├── Previous MRR base
│   ├── - Voluntary churn
│   │   ├── Dissatisfied (product gaps)
│   │   ├── No longer need (use case ended)
│   │   ├── Switched to competitor
│   │   └── Price sensitivity
│   └── - Involuntary churn
│       ├── Payment failure
│       ├── Card expiry
│       └── Billing errors
│
├── Expansion MRR (+)
│   ├── Seat expansion (more users)
│   │   └── Users x Price per seat
│   ├── Usage expansion (more consumption)
│   │   └── Usage units x Price per unit
│   ├── Plan upgrades (higher tier)
│   │   └── Upgrade rate x Tier price delta
│   └── Add-on purchases
│       └── Add-on attach rate x Add-on price
│
├── Contraction MRR (-)
│   ├── Seat removal
│   ├── Plan downgrade
│   ├── Add-on cancellation
│   └── Usage decrease
│
└── Reactivation MRR (+)
    ├── Churned customer pool
    ├── x Reactivation rate
    └── x Reactivated ARPA
```

**Key formulas:**
- Net New MRR = New + Expansion + Reactivation - Churn - Contraction
- MRR Growth Rate = Net New MRR / Starting MRR
- Net Revenue Retention = (Starting MRR - Churn - Contraction + Expansion) / Starting MRR

---

## Template 2: Transactional / E-Commerce

```
Revenue = Transactions x AOV

Transactions
├── Traffic (unique visitors)
│   ├── By channel (organic, paid, referral, direct, social, email)
│   └── By device (desktop, mobile, app)
├── x Browse-to-cart rate
├── x Cart-to-checkout rate
├── x Checkout completion rate
└── x Repeat purchase rate
    └── Purchase frequency (orders per customer per period)

AOV (Average Order Value)
├── Items per order
├── x Average item price
├── + Upsell/cross-sell revenue per order
└── - Discounts/promotions per order
```

**Key formulas:**
- Revenue = Unique Visitors x Conversion Rate x AOV x Purchase Frequency
- Customer LTV = AOV x Purchase Frequency x Customer Lifespan

---

## Template 3: Marketplace (Two-Sided)

```
GMV (Gross Merchandise Value)
├── Supply side
│   ├── Active sellers/providers
│   ├── x Listings per seller
│   └── x Average listing price
├── Demand side
│   ├── Active buyers
│   ├── x Search/browse sessions
│   ├── x Search-to-view rate
│   ├── x View-to-purchase rate
│   └── x Purchases per buyer per period
└── Match quality
    ├── Search relevance
    ├── Recommendation effectiveness
    └── Trust/review score

Revenue = GMV x Take Rate

Take Rate
├── Transaction fee %
├── + Featured listing fees
├── + Subscription fees (seller/buyer premium)
├── + Advertising revenue
└── + Payment processing margin
```

---

## Template 4: Usage-Based

```
Revenue = Active Users x Usage per User x Price per Unit

Active Users
├── Total registered users
├── x Monthly active rate (MAU / registered)
└── Segments: free vs. paid users

Usage per User
├── Sessions per user per period
├── x Actions per session
├── x Units consumed per action
└── Growth trajectory (increasing/stable/declining per cohort)

Price per Unit
├── Base rate
├── x Volume discount curve
├── x Tier pricing (different rates at different volumes)
└── - Credits / free tier allowance
```

**Key formulas:**
- Revenue = Paying Users x Avg Usage x Effective Price per Unit
- Effective price decreases with volume discounts — model this explicitly

---

## Template 5: Hybrid (Recurring + Transactional)

```
Total Revenue
├── Recurring Revenue (subscription base)
│   ├── Subscribers x Subscription price
│   ├── - Churn
│   └── + Upgrades
├── Transactional Revenue (on top of subscription)
│   ├── Transactions per subscriber per period
│   ├── x Transaction value
│   └── x Transaction fee
└── Expansion Revenue
    ├── Add-on services
    ├── Overage charges
    └── Professional services
```

---

## Template 6: Ad-Supported

```
Revenue = Impressions x CPM / 1000

Impressions
├── DAU (daily active users)
├── x Sessions per DAU
├── x Pages/screens per session
├── x Ad slots per page/screen
└── x Fill rate (% of slots filled with ads)

CPM (cost per mille)
├── Base CPM by ad format
├── x Audience quality multiplier
├── x Targeting precision multiplier
├── x Seasonality factor
└── x Direct-sold premium (vs. programmatic)

Alternative metric: Revenue = DAU x ARPDAU (average revenue per DAU)
```

---

## Template 7: Freemium + Enterprise (Parallel Trees)

```
Total Revenue
├── Self-Serve Revenue (PLG tree)
│   ├── Free users
│   │   ├── Signups x Activation rate
│   │   └── Pool for conversion
│   ├── x Free-to-paid conversion rate
│   ├── x Self-serve ARPA
│   ├── - Self-serve churn
│   └── + Self-serve expansion
│
└── Sales-Assisted Revenue (SLG tree)
    ├── PQLs (product-qualified leads from free usage)
    │   ├── Free users hitting PQL criteria
    │   └── x PQL-to-opportunity rate
    ├── + Traditional pipeline (MQLs, outbound)
    ├── x Win rate
    ├── x Enterprise ARPA
    ├── - Enterprise churn
    └── + Enterprise expansion (NRR)
```

**Key insight:** In this model, free users serve double duty — they convert self-serve AND generate PQLs for sales. Both paths must be modeled.

---

## Customization Guidance

When adapting a template:
1. Start with the template closest to the user's model
2. Remove branches that don't apply
3. Add product-specific sub-drivers (e.g., specific feature triggers, channel breakdowns)
4. Verify MECE: every dollar of revenue should trace through exactly one path
5. Label each split as x (multiply), + (add), or - (subtract)
6. Distinguish direct (mathematical) from indirect (behavioral) relationships
