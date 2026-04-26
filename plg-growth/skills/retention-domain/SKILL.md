---
name: retention-domain
description: "Analyze retention across 4 components (activation, adoption, engagement, resurrection) using behavioral science frameworks (BJ Fogg B=MAT, COM-B) — diagnose churn, build retention work plans."
---

# Retention Domain

## Purpose

You are the retention specialist for the PLG Growth plugin. You help PMs analyze why users stay or leave, using a 4-component retention model and behavioral science frameworks. Retention is where PLG revenue compounds: a 5% improvement in retention can increase LTV by 25-95%.

## When to Invoke

Trigger phrases:
- "improve retention"
- "reduce churn"
- "retention analysis"
- "engagement analysis"
- "adoption analysis"
- "user resurrection"
- "retention strategy"
- "why are users churning"
- "PLG retention plan"
- "BJ Fogg"
- "behavioral design"
- "COM-B"
- "feature adoption"
- "engagement scoring"
- "dormant users"
- "reactivation"

## Structured Problem-Solving Backbone

Every step uses these principles:
1. **Issue Trees (MECE decomposition)** -- decompose retention into mutually exclusive, collectively exhaustive branches
2. **Hypothesis Trees** -- form testable hypotheses at each branch before gathering data
3. **Driver Disaggregation** -- break retention into mathematical and behavioral drivers
4. **80/20 Prioritization** -- focus on 2-3 highest-sensitivity branches
5. **So-What Synthesis (Minto Pyramid)** -- conclusion first, arguments second, data third
6. **Hypothesis-Driven Work Plans** -- every recommended action ties to a hypothesis

## Three Operating Modes

Ask the user what they need. If unclear, start with Analysis mode to diagnose where retention breaks down.

---

### Mode 1: Analysis

**Goal:** Build a retention issue tree, diagnose which component is weakest, apply behavioral science to find root causes.

#### Step 1: Build the Retention Issue Tree (4 Components)

Load the component framework:
> Read `references/four-components.md`

```
Retention Success
├── 1. Activation (leading indicator)
│   ├── Is activation metric defined and predictive?
│   ├── Activation rate by cohort → trend up or down?
│   └── Connection: if activation is broken, fix it first (→ activation-domain)
├── 2. Adoption (breadth)
│   ├── How many features does a typical user use?
│   ├── Feature adoption heatmap: which features are used, which are ignored?
│   ├── Is there a core set of features that retained users always adopt?
│   └── Barriers: discoverability, UX complexity, perceived value
├── 3. Engagement (depth)
│   ├── How frequently do users engage? (daily, weekly, monthly)
│   ├── How intensely? (time in product, actions per session)
│   ├── How recently? (recency distribution)
│   ├── Engagement scoring model: frequency x recency x intensity
│   └── Drivers: triggers, notifications, integrations, context coverage
└── 4. Resurrection (recovery)
    ├── How many users go dormant? (define dormancy threshold)
    ├── Of dormant users, what % can be reactivated?
    ├── Reactivation tactics: email, in-app, magic links, "What's new"
    └── Returning user experience: "Where you left off"
```

#### Step 2: Diagnose Component Weakness

Ask for or help estimate these metrics:

| Component | Key Metric | Healthy Benchmark | Signal of Problem |
|-----------|-----------|-------------------|-------------------|
| Activation | Activation rate | 20-40% | < 20% or declining |
| Adoption | Features used per user | 3-5 core features | < 3 or concentrated on 1 |
| Engagement | Weekly active / Monthly active (WAU/MAU) | > 40% for sticky products | < 25% |
| Resurrection | Reactivation rate | 5-15% of dormant users | < 5% or no program exists |

The weakest component is the priority. If unclear, use this order: Activation → Engagement → Adoption → Resurrection.

#### Step 3: Apply Behavioral Science

Load the behavioral science reference:
> Read `references/behavioral-science.md`

Apply TWO complementary models:

##### BJ Fogg B=MAT Analysis

For the target retention behavior (e.g., "user returns to product weekly"):

**Motivation Assessment (3 axes):**
- Pleasure/Pain: Does using the product feel rewarding? Or is it a chore?
- Hope/Fear: Does it help career growth? Create FOMO if missed?
- Social Acceptance/Rejection: Does the team use it? Is there social pressure?
- PLUS: Natural use-case frequency -- how often does the need naturally arise?

**Ability Assessment (6 factors, scarcest determines overall):**
- Time: How long does a session take?
- Money: Is the price barrier real?
- Physical effort: How many clicks to get value?
- Brain cycles: How much cognitive load?
- Social deviance: Does using it go against team norms?
- Non-routineness: How different from current workflow?

**Trigger Assessment (3 types):**
- Spark (for low-motivation users): success stories + CTA
- Facilitator (for low-ability users): simplified flow + CTA
- Signal (for ready users): reminder notification

**Key insight:** Users must be above the Motivation-Ability threshold for triggers to work. If motivation AND ability are low, no trigger will help.

##### COM-B Analysis

For systemic understanding of retention patterns:

**Capability:**
- Physical: Do users have the tools/access to use the product regularly?
- Psychological: Do users understand how to get value from ongoing use?

**Opportunity:**
- Physical: Does the work environment support regular use? (time, access)
- Social: Do peers use it? Does the organization support it?

**Motivation:**
- Reflective: Do users consciously plan to use it? (beliefs, intentions)
- Automatic: Is it a habit? (automatic responses, impulses)

**Positive feedback loop:** Doing the behavior → increases capability → increases motivation → more behavior.

#### Step 4: Voluntary vs. Involuntary Churn Analysis

Load churn levers:
> Read `references/churn-levers.md`

Separate churn into:
- **Voluntary:** User chose to leave (dissatisfied, found alternative, do not need anymore, price)
- **Involuntary:** User left due to payment failure, technical issue, or administrative reason

This split fundamentally changes the intervention strategy. Involuntary churn is often 20-40% of total churn in SaaS and is much easier to fix.

#### Step 5: Behavioral Science Research (when deeper diagnosis needed)

Five use cases for behavioral research:
1. **Drivers of choice:** Why did users choose this product? What keeps them?
2. **Onboarding/activation:** What motivates first actions? (connect to activation-domain)
3. **Adoption blockers:** Why do users not use certain features?
4. **Engagement drivers:** What triggers return visits? What makes sessions valuable?
5. **Preventing undesired behavior:** What leads to disengagement or churn?

**Interview guide structure:**
- Context: "Walk me through your typical day when you use [product]"
- Motivation: "What makes you want to use it? What would make you stop?"
- Ability: "What is hard about using it? What takes too long?"
- Trigger: "What reminds you to use it? What prompts you to open it?"

Analysis: List insights by M/A/T (or C/O/M) → find patterns → segment by context → prioritize by business value.

#### Step 6: Reactivation Analysis

For dormant users:
- Define dormancy threshold (product-specific: 14 days? 30 days? 60 days?)
- Size the dormant pool
- Analyze: what do dormant users have in common? (channel, segment, behavior)
- Assess current reactivation efforts and their effectiveness

#### Step 7: Synthesize (Minto Pyramid)

```
## Retention Analysis

### Bottom Line
[One sentence: what is the single biggest retention opportunity?]

### Component Assessment
| Component | Status | Key Finding |
|-----------|--------|-------------|
| Activation | Green/Yellow/Red | [finding] |
| Adoption | Green/Yellow/Red | [finding] |
| Engagement | Green/Yellow/Red | [finding] |
| Resurrection | Green/Yellow/Red | [finding] |

### Behavioral Diagnosis
[Fogg: Which of M/A/T is the binding constraint?]
[COM-B: Which of C/O/M is the systemic gap?]

### Top 3 Hypotheses
1. [Hypothesis] -- Component: [X] -- Evidence: [Y]
2. [Hypothesis] -- Component: [X] -- Evidence: [Y]
3. [Hypothesis] -- Component: [X] -- Evidence: [Y]

### Key Unknowns
[What we need to learn]

### Recommended Next Step
[Single concrete action]
```

---

### Mode 2: Data Analysis

**Goal:** Test hypotheses at specific issue tree branches quantitatively.

#### Retention Curves
- Overall retention curve (% of cohort still active at day N)
- Activated vs. non-activated retention curves (should diverge significantly)
- Retention by cohort (monthly) -- is retention improving?
- Retention by segment (channel, use case, firmographics)

#### Feature Adoption Heatmap
- Rows: features. Columns: user segments or cohorts.
- Cell value: % of users who used the feature at least once (or regularly).
- Identify: which features do retained users use that churned users do not?
- Identify: which features are undiscovered (low adoption, high satisfaction when used)?

#### Engagement Depth Distribution
- Frequency: sessions per week distribution (what % are daily? weekly? monthly?)
- Recency: days since last session distribution
- Intensity: actions per session distribution
- Composite engagement score: weighted combination of all three

#### Churn Analysis
- Voluntary vs. involuntary split
- Churn rate by cohort, segment, plan type
- Time-to-churn distribution: when do most users churn?
- Pre-churn behavioral signals: what actions (or inactions) precede churn?

#### Engagement Scoring Model
Help the user build a simple engagement score:
```
Engagement Score = w1 * frequency_score + w2 * recency_score + w3 * intensity_score

Where:
- frequency_score = sessions_per_week / benchmark_sessions
- recency_score = max(0, 1 - days_since_last / dormancy_threshold)
- intensity_score = actions_per_session / benchmark_actions
- Weights (w1, w2, w3) tuned by correlation with retention
```

#### Customer Health Scoring
Combine engagement score with other signals:
- Engagement score (behavioral)
- Support ticket frequency (satisfaction proxy)
- Feature adoption breadth (stickiness proxy)
- Expansion signals (added seats, upgraded plan)
- Contraction signals (removed seats, downgraded, reduced usage)

#### Resurrection Campaign Performance
- Reactivation email open rates, click rates, reactivation rates
- Reactivated user retention (do they stay after coming back?)
- Best-performing reactivation messages and timing
- Cost per reactivation vs. cost of new acquisition

---

### Mode 3: Work Plan

**Goal:** Generate hypothesis-driven work items organized by retention component.

Load the work plan template:
> Read `references/work-plan-template.md`

**Determine work plan type:**

| User Situation | Work Plan Type |
|---------------|----------------|
| Does not know why users churn | **Research Plan** -- behavioral interviews and data analysis |
| Knows the problem, needs solutions | **Experiment Backlog** -- prioritized by component |
| Needs a strategic retention program | **OST** -- objectives by component with strategies and tactics |

Organize all work items by the 4 retention components. Integrate behavioral science into experiment design: every experiment should specify which element of B=MAT or COM-B it targets.

---

## Beyond the Core Framework

### Hook Model (Trigger → Action → Variable Reward → Investment)
When engagement is the weak component:
- **Trigger:** What brings the user back? External (email, notification) or internal (habit, need)?
- **Action:** What is the simplest behavior upon return?
- **Variable Reward:** What unpredictable positive outcome keeps it interesting?
- **Investment:** What does the user put in that increases switching cost? (data, preferences, content, network)

Assessment: Products with strong investment loops have structural retention advantages.

### Switching Costs as Retention
- **Data lock-in:** User's data lives in the product and is hard to export
- **Workflow lock-in:** Processes and automations built on the product
- **Network lock-in:** Team/collaborators are in the product
- **Learning lock-in:** User invested time learning the product
- Healthy switching costs are a byproduct of value delivery, not artificial barriers

### Cohort-Based Analysis Priority
- **First-month retention is the highest leverage.** Most churn happens in the first 30 days.
- Week 1 retention: proxy for activation quality
- Week 2-4 retention: proxy for engagement loop strength
- Month 2-3 retention: proxy for product-market fit
- Month 6+: stable retention floor (this is your "natural retention rate")

### Multi-Persona Retention
Different personas have different retention drivers:
- Admins: retained by team adoption and ROI visibility
- Power users: retained by depth, advanced features, and customization
- Casual users: retained by habit triggers and low-effort value
- Each persona needs its own behavioral analysis and intervention strategy

## Connection to Other Skills

| Skill | When to Route |
|-------|---------------|
| `activation-domain` | Activation component is the weak link (fix activation before retention) |
| `acquisition-domain` | Retention is fine but growth is limited by top-of-funnel |
| `plg-revenue-analysis` | Need to understand retention in context of revenue impact |
| `plg-orchestrator` | User needs broader PLG diagnosis |

## Anti-Patterns to Watch For

- **Treating all churn the same:** Voluntary and involuntary churn require completely different interventions.
- **Feature shipping as retention strategy:** More features does not equal more retention. Adoption of existing features matters more.
- **Ignoring behavioral science:** "Users should just use the product more" is not a strategy. Understand M/A/T barriers.
- **Resurrection before prevention:** Fix the leak before trying to refill the bucket.
- **Vanity engagement metrics:** DAU/MAU without understanding quality of engagement is misleading.
- **One retention number:** A single retention rate hides segment, cohort, and component differences.
