# Growth Team Structuring

How to organize growth teams for PLG execution. The right structure depends on company size, PLG maturity, and where the biggest revenue opportunity sits.

---

## Foundational Principle

Every growth team needs three things:
1. **Dedicated owner** -- a PM who owns the outcome, not a committee
2. **Self-sufficient team** -- PM + design + engineering + data, not dependent on other teams for daily execution
3. **Clear priorities** -- connected to a specific branch of the revenue driver tree, not "do growth"

Without all three, growth work gets deprioritized, delayed, or scattered.

---

## Small Team (< 5 PMs)

### Option A: Focus on Single Highest-Sensitivity Factor

**How it works:**
1. Build or load the revenue driver tree
2. Run sensitivity analysis: for each metric, calculate "if this metric improves by 10%, what is the MRR impact?"
3. Find the ONE metric with the highest sensitivity
4. Dedicate all PM + engineering capacity to that metric
5. Re-evaluate quarterly: has the highest-sensitivity factor shifted?

**Example:**
```
Revenue Driver Tree Sensitivity Analysis:
- Signups +10% → MRR +3%
- Activation rate +10% → MRR +8%   ← HIGHEST SENSITIVITY
- Conversion rate +10% → MRR +6%
- ARPA +10% → MRR +5%
- Churn rate -10% → MRR +4%

Decision: All growth capacity focused on activation rate.
```

**Pros:**
- Maximum focus and depth
- Team becomes expert in one area
- Clear metric ownership
- Easier to show impact

**Cons:**
- Ignores other revenue branches
- Sensitivity can shift (once activation is optimized, the next bottleneck emerges)
- Risk of diminishing returns if the team over-optimizes one metric

**Best for:** Companies with a clear bottleneck, early PLG stage, small team that cannot afford to spread thin.

### Option B: Cross-Prioritize Low-Hanging Fruit

**How it works:**
1. For each branch of the revenue tree, identify the easiest wins (high impact, low effort)
2. Rank all opportunities across branches by ICE score
3. Work on the top 3-5 regardless of which branch they belong to
4. Re-prioritize monthly

**Pros:**
- Captures quick wins across the entire funnel
- Good for early stage when you don't know where the biggest opportunity is
- Demonstrates impact quickly (good for building organizational buy-in)

**Cons:**
- Scattered focus -- team jumps between areas
- No deep expertise develops in any one area
- Hard to attribute impact (improving 5 things a little vs one thing a lot)
- Risk of "local optimization" -- picking easy things that don't compound

**Best for:** Very early PLG stage where the team is still learning where the biggest opportunity is. Use this for one quarter, then switch to Option A.

### Recommendation for Small Teams

**Default to Option A** unless:
- You have no data on where the bottleneck is (use Option B for one quarter to explore)
- The company needs quick wins to justify further PLG investment (use Option B to show breadth of impact)
- Then switch to Option A once you have conviction on the highest-sensitivity factor

---

## Big Team (5+ PMs)

### Option A: By Revenue Type

Organize teams around revenue components from the revenue driver tree.

**Team structure:**

| Team | Owns | Key Metrics | Scope |
|------|------|------------|-------|
| New Revenue | New MRR | Signups, activation rate, conversion rate, ARPA(new) | Acquisition, onboarding, activation, initial monetization |
| Retained Revenue | Retained MRR + Churned MRR | D30/D90 retention, churn rate (voluntary + involuntary), engagement score | Core product engagement, habit formation, churn prevention, dunning |
| Expansion Revenue | Expansion MRR + Contraction MRR | Seat expansion, upgrade rate, add-on attach, NDR | Collaboration features, usage limits, upgrade prompts, add-on discovery |

**Pros:**
- Clear ownership of revenue outcomes
- Each team can trace their work to MRR impact
- Full-stack optimization (team owns the entire journey for their revenue type)
- Natural alignment with finance reporting

**Cons:**
- Handoff complexity: when does a "new" customer become "retained"?
- Some features span teams (e.g., collaboration helps both retention AND expansion)
- Requires enough engineers per team (at least 2-4 each)

**Best for:** Companies where revenue decomposition is clear and MRR is the primary metric. Product-led sales companies where new vs expansion is a meaningful distinction.

### Option B: By Metrics Cluster (AARMS Journey)

Organize teams around customer journey stages.

**Team structure:**

| Team | Owns | Key Metrics | Scope |
|------|------|------------|-------|
| Acquisition | Top of funnel | Visitors, signups, signup rate, CAC, channel attribution | Marketing site, signup flow, referral, SEO, viral |
| Activation | Signup to value | Activation rate, TTV, onboarding completion, setup completion | Onboarding, first-use experience, empty states, setup flow |
| Core Engagement | Active usage | D7/D30 retention, feature adoption breadth, engagement score | Core features, habit formation, re-engagement, notifications |
| Monetisation | Revenue | Free-to-paid conversion, ARPA, expansion, churn | Pricing, packaging, paywalls, upgrade flows, dunning |

**Pros:**
- User-journey aligned: each team owns a specific part of the user experience
- Clear handoff points (signup -> onboarding -> active use -> payment)
- Easier to diagnose where in the journey the biggest drop-off is
- Good for pure self-serve where the journey is linear

**Cons:**
- Some metrics span teams (retention is influenced by activation quality)
- Monetisation team depends on upstream teams for traffic
- Acquisition team may over-optimize for signup volume at the expense of quality

**Best for:** Pure self-serve PLG companies with a clear linear journey. Companies where the user experience through the funnel is the primary concern.

### Option C: Hybrid (for very large teams, 10+ PMs)

Combine approaches:

```
Growth Org
├── Acquisition Team (AARMS: Acquisition)
├── Activation Team (AARMS: Activation)
├── Engagement & Retention Team (Revenue: Retained MRR)
├── Monetisation Team (Revenue: New MRR conversion + Expansion MRR)
└── Platform Team (Infrastructure: experimentation, data, feature flags)
```

---

## Team Composition Template

Each growth team needs these roles. Scale engineering headcount based on the complexity of the team's scope.

| Role | Count | Responsibilities |
|------|-------|-----------------|
| PM | 1 | Owns strategy, prioritization, outcomes. Maintains OST. Designs experiments. |
| Designer | 1 | Growth design (UX + conversion optimization). Prototype testing. UI experiments. |
| Engineers | 2-4 | Full-stack capability. Frontend for UI experiments, backend for logic/data. Feature flag management. |
| Analyst | 1 | Funnel analysis, cohort analysis, experiment analysis, metric monitoring. Can be shared across 2 teams max. |
| Researcher | 0.5 (shared) | User interviews, usability testing, qualitative insights. Typically shared across 2-3 teams. |

### Total minimum viable growth team: 5-6 people
- 1 PM + 1 Designer + 2 Engineers + 1 Analyst = 5 people
- This is the minimum to run experiments independently without depending on other teams

### Reporting Structure

Growth teams should report to the **product org**, not marketing:
- Growth requires product authority (ability to change the product)
- Engineering resources follow product org structure
- PM career path is in product

Marketing remains a partner for acquisition channels, content, and brand -- but growth owns the in-product experience.

---

## Growth Review Cadence

### Weekly Growth Review (30 minutes)

**Attendees:** Growth team + PM lead
**Agenda:**
1. Metric check: are key metrics on track? (5 min, dashboard walkthrough)
2. Experiment updates: what's running, what concluded, what's launching? (15 min)
3. Blockers: what's preventing progress? (5 min)
4. Decisions needed: any decisions requiring input from outside the team? (5 min)

**Output:** Updated experiment tracker, blocker escalation list

### Monthly Funnel Review (60 minutes)

**Attendees:** Growth + Product + Marketing + Sales + CS
**Agenda:**
1. Full AARMS funnel walkthrough: metrics, trends, anomalies (20 min)
2. Deep-dive on one area: the stage with the biggest drop-off or opportunity (20 min)
3. Cross-team coordination: handoffs, dependencies, shared opportunities (10 min)
4. Action items and owners (10 min)

**Output:** Updated funnel dashboard, prioritized cross-team actions

### Quarterly Strategy Review (90 minutes)

**Attendees:** Leadership + Growth + Product + Finance
**Agenda:**
1. Revenue driver tree review: what moved, what didn't, why (20 min)
2. Goal progress: on track / off track / adjusted (15 min)
3. Sensitivity re-analysis: has the highest-sensitivity factor shifted? (15 min)
4. Next quarter goals: proposed goals from tree analysis (20 min)
5. Team structure assessment: is the current structure optimal? Reorg needed? (10 min)
6. Resource requests and investment decisions (10 min)

**Output:** Updated revenue tree, next quarter goals, team structure decision

---

## Common Anti-Patterns

| Anti-Pattern | What It Looks Like | Why It Fails | Fix |
|-------------|-------------------|-------------|-----|
| Growth team in marketing | "Growth" means demand gen, ads, content | No product authority, cannot change the product | Move growth to product org |
| Growth as a side project | PM does growth 20% of the time alongside feature work | Growth always loses to feature deadlines | Dedicated PM with protected capacity |
| Growth without data | Team runs experiments without analytics | Cannot measure impact, cannot prioritize | Invest in data first (TASE: Track + Analyse) |
| Growth without engineering | PM designs experiments but has no engineers to build them | Queue behind feature teams, slow execution | Dedicate at least 2 engineers to growth |
| Too many metrics | Team owns 15 metrics across all AARMS stages | Scattered focus, no depth on anything | Pick 1-2 metrics. Use OST for focus. |
| Growth vs Product tension | Growth team optimizes short-term metrics at expense of UX | Dark patterns, user trust erosion, churn | Guardrail metrics required on every experiment |
| No executive sponsor | Growth team exists but has no leadership champion | Budget cut in next reorg, work deprioritized | Get VP+ sponsor before forming the team |

---

## Decision Framework: Which Structure to Choose

```
How many PMs do you have for growth?
    |
    ├── 1 PM
    │   └── Option A: Single sensitive factor
    │       Focus all capacity on the #1 revenue driver
    │
    ├── 2-4 PMs
    │   └── Is the biggest opportunity clear?
    │       ├── YES → Option A: All PMs on one metric (activation, monetization, etc.)
    │       └── NO → Option B: Each PM on a different AARMS stage, learn for one quarter, then consolidate
    │
    └── 5+ PMs
        └── Is your primary motion self-serve or sales-assisted?
            ├── Self-serve → Option B: By AARMS stage
            └── Sales-assisted → Option A: By revenue type (New/Retained/Expansion)
```
