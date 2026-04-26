# Master PLG Issue Tree

This is the complete MECE decomposition of the PLG problem space. Every branch maps to a skill or future skill in the plugin. Use this tree to diagnose where to focus.

## Top-Level Tree

```
PLG Success = Sustainable, product-led revenue growth
│
├── 1. VIABILITY: Is PLG viable for this product?
│   ├── 1.1 Product suitability (4 criteria)
│   │   ├── Self-serve capability
│   │   ├── Low barrier to start
│   │   ├── Value demonstrable pre-purchase
│   │   └── Natural expansion dynamics
│   ├── 1.2 Pillar maturity (3 pillars)
│   │   ├── Design for end user
│   │   ├── Value before capture
│   │   └── Product with GTM intent
│   ├── 1.3 PMF signals
│   │   ├── Sean Ellis test (40%+ "very disappointed")
│   │   ├── Retention curve flattening
│   │   ├── Usage frequency vs. natural frequency
│   │   └── Depth of engagement
│   ├── 1.4 Competitive moat potential
│   │   ├── Network effects (direct / indirect / data)
│   │   ├── Switching costs
│   │   └── Data moat / ecosystem lock-in
│   └── 1.5 Decision-driver alignment
│       ├── Top customer decision drivers identified
│       ├── Drivers provable in free/trial experience
│       └── Activation proves #1 driver
│   → Skill: plg-readiness
│
├── 2. OPPORTUNITY: Where is the biggest revenue opportunity?
│   ├── 2.1 Revenue model identification
│   │   ├── SaaS / Subscription
│   │   ├── Transactional / Marketplace
│   │   ├── Usage-based
│   │   ├── Hybrid
│   │   ├── Ad-supported
│   │   └── Freemium + Enterprise (parallel)
│   ├── 2.2 Revenue driver tree (model-specific)
│   │   ├── Direct (mathematical) drivers
│   │   └── Indirect (behavioral) drivers
│   ├── 2.3 Sensitivity analysis per branch
│   │   ├── Current level vs. benchmark
│   │   ├── Elasticity / leverage
│   │   └── Effort to move
│   ├── 2.4 Opportunity sizing
│   │   └── "If X moves from A to B, revenue impact = Z"
│   └── 2.5 Team structuring for growth
│       ├── Small team: single sensitive factor
│       └── Big team: organize by revenue type or metrics cluster
│   → Skill: plg-revenue-analysis
│
├── 3. MODEL: Which acquisition model fits?
│   ├── 3.1 Product characteristics assessment
│   │   ├── Value demonstration speed
│   │   ├── Onboarding complexity
│   │   └── Data/content dependency
│   ├── 3.2 Model evaluation
│   │   ├── Freemium (unlimited vs limited base)
│   │   ├── Free trial (duration, forcing function)
│   │   ├── Ungated (4-factor suitability)
│   │   ├── Reverse trial (full → downgrade)
│   │   └── Self-service demo (pre-generated)
│   ├── 3.3 Intent-to-model mapping
│   │   └── Different channels/pages → different models
│   ├── 3.4 Multi-model complexity
│   │   ├── Marketing complexity
│   │   ├── Business complexity
│   │   └── Operational complexity
│   └── 3.5 Model selection decision
│   → Skill: acquisition-model-selector
│
├── 4. FUNNEL: Which stage is the bottleneck?
│   ├── 4.1 Acquisition
│   │   ├── Traffic volume and quality
│   │   ├── Channel mix and efficiency
│   │   ├── Signup conversion rate
│   │   └── Cost per acquisition
│   │   → Future skill: plg-acquisition
│   │
│   ├── 4.2 Activation
│   │   ├── Aha moment definition
│   │   ├── Time to value (TTV)
│   │   ├── Activation rate (signup → aha)
│   │   ├── Onboarding completion
│   │   └── Setup success rate
│   │   → Future skill: plg-activation
│   │
│   ├── 4.3 Retention
│   │   ├── Usage frequency vs natural frequency
│   │   ├── Retention curve shape
│   │   ├── Habit formation
│   │   ├── Feature breadth adoption
│   │   └── Engagement depth over time
│   │   → Future skill: plg-retention
│   │
│   ├── 4.4 Monetisation
│   │   ├── Free-to-paid conversion rate
│   │   ├── Pricing model fit
│   │   ├── Upgrade triggers
│   │   ├── Expansion revenue (seats, usage, add-ons)
│   │   ├── Net revenue retention
│   │   └── Involuntary churn (payment failures)
│   │   → Future skill: plg-monetisation
│   │
│   └── 4.5 Satisfaction / Advocacy
│       ├── NPS / CSAT scores
│       ├── Organic referral rate
│       ├── Review/rating signals
│       └── Support ticket trends
│       → Future skill: plg-satisfaction
│
└── 5. CAPABILITIES: What cross-cutting capabilities are missing?
    ├── 5.1 Growth loops
    │   ├── Viral loops (invite, share, embed)
    │   ├── Content loops (UGC, SEO, templates)
    │   ├── Paid loops (reinvest revenue into acquisition)
    │   └── Sales loops (PQLs → sales → expansion)
    │   → Future skill: plg-growth-loops
    │
    ├── 5.2 Product-led sales
    │   ├── PQL definition and scoring
    │   ├── Sales-assist triggers
    │   ├── Self-serve to sales-assist handoff
    │   └── Enterprise expansion playbook
    │   → Future skill: plg-product-led-sales
    │
    ├── 5.3 Experimentation capability
    │   ├── A/B testing infrastructure
    │   ├── Experiment prioritization (ICE/RICE)
    │   ├── Statistical rigor
    │   └── Learning velocity
    │   → Future skill: plg-experimentation
    │
    ├── 5.4 Data infrastructure
    │   ├── Event tracking completeness
    │   ├── User identity resolution
    │   ├── Funnel analytics
    │   ├── Cohort analysis capability
    │   └── Revenue attribution
    │   → Future skill: plg-data-setup
    │
    └── 5.5 Organizational transformation
        ├── Cross-functional alignment
        ├── Growth team structure
        ├── Incentive alignment (sales comp, product goals)
        ├── PLG metrics adoption
        └── Culture shift (ship fast, measure, iterate)
        → Future skill: plg-transformation
```

## How to Use This Tree

### Diagnosis Flow
1. Start at the top. Ask: "Does the user know PLG is viable?" If no → Branch 1.
2. If viable, ask: "Do they know where the revenue opportunity is?" If no → Branch 2.
3. If they know the opportunity, ask: "Do they have the right acquisition model?" If no → Branch 3.
4. If model is set, ask: "Where is the funnel leaking?" → Branch 4 (specific sub-branch).
5. Throughout, check: "Are cross-cutting capabilities missing?" → Branch 5.

### Prioritization Heuristic
- **Pre-PMF products:** Branch 1 (viability) is almost always the priority.
- **Early-stage with PMF:** Branch 3 (model selection) or Branch 2 (revenue analysis).
- **Growth-stage products:** Branch 4 (funnel bottleneck) with Branch 2 for sizing.
- **Mature products adding PLG:** Branch 1 (readiness) + Branch 5.5 (transformation).

### MECE Check
Every growth problem should map to exactly one branch. If it does not, the tree needs extending. If it maps to multiple, pick the one with highest revenue sensitivity.

### Hypothesis Formation Template
For each branch identified as priority:

```
Branch: [X.Y branch name]
Hypothesis: We believe [specific claim about this branch]
Evidence: [What from the diagnostic supports this]
Test: [What action or analysis would confirm/deny]
Impact if true: [Revenue/growth impact estimate]
Route to: [skill name]
```
