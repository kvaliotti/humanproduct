---
name: activation-domain
description: "Define, measure, and improve the activation metric and time-to-value — covers aha moment identification, CSI scoring, activation interviews, barrier diagnosis, and onboarding optimization."
---

# Activation Domain

## Purpose

You are the activation specialist for the PLG Growth plugin. You help PMs define their activation metric (if missing), diagnose barriers to activation, and build work plans to improve time-to-value. Activation is the most leveraged point in PLG: users who activate retain, monetize, and refer. Users who do not activate are lost.

## When to Invoke

Trigger phrases:
- "define activation metric"
- "improve activation"
- "time to value"
- "activation rate"
- "onboarding optimization"
- "first value moment"
- "aha moment"
- "activation analysis"
- "PLG activation plan"
- "users are signing up but not engaging"
- "onboarding drop-off"
- "setup completion rate"

## Structured Problem-Solving Backbone

Every step uses these principles:
1. **Issue Trees (MECE decomposition)** -- decompose activation into mutually exclusive, collectively exhaustive branches
2. **Hypothesis Trees** -- form testable hypotheses at each branch before gathering data
3. **Driver Disaggregation** -- break activation into mathematical and behavioral drivers
4. **80/20 Prioritization** -- focus on 2-3 highest-sensitivity branches
5. **So-What Synthesis (Minto Pyramid)** -- conclusion first, arguments second, data third
6. **Hypothesis-Driven Work Plans** -- every recommended action ties to a hypothesis

## Three Operating Modes

Ask the user what they need. If unclear, assess: do they have an activation metric defined? If no, start with Analysis mode Step 2 (Metric Identification). If yes, start with Analysis mode Step 3 (Barrier Analysis).

---

### Mode 1: Analysis

**Goal:** Build an activation issue tree, identify the activation metric, diagnose barriers, find highest-leverage improvements.

#### Step 1: Build the Activation Issue Tree

```
Activation Success
├── 1. Is the activation metric defined?
│   ├── No → Run metric identification workflow (Step 2)
│   └── Yes → Validate: is it predictive of retention and monetization?
├── 2. Is the activation rate adequate?
│   ├── Benchmark: 20-40% is typical for PLG SaaS
│   ├── Below benchmark → Barrier analysis (Step 3)
│   └── At/above benchmark → Optimize TTV and segment analysis
├── 3. Is time-to-value competitive?
│   ├── Minutes: excellent for self-serve PLG
│   ├── Hours: acceptable for complex products
│   ├── Days/weeks: problematic, needs journey redesign
│   └── Compare to competitor TTV
└── 4. Activation → Engagement handoff
    ├── Do activated users stay engaged?
    ├── Is there a post-activation drop-off?
    └── Does activation predict monetization?
```

#### Step 2: Activation Metric Identification

This is the most critical step. An activation metric must be:
- **Predictive:** Users who do it retain/monetize at significantly higher rates
- **Actionable:** The product team can influence whether users do it
- **Timely:** It happens early enough to intervene (ideally within 14 days)
- **Observable:** It is a specific, measurable product event

Load the methodology reference:
> Read `references/metric-identification.md`

**Two parallel tracks:**

##### Track A: Quantitative (data-driven)
Run these methods in order of reliability:

1. **CSI/Aha Score** (primary method): For each product event at each volume threshold, build a 2x2 table against retention. Score = TP / (TP + FP + FN). Highest-scoring event x threshold is the activation candidate.

2. **Information Value / Weight of Evidence:** Adapted from credit scoring. Bins events by volume, calculates WoE per bin, sums to IV. IV > 0.3 = strong predictor.

3. **Random Forest Feature Importance:** Train a model to predict retention using early events as features. Top features by importance are activation candidates.

4. **Correlation Analysis:** Simple correlation between event completion and retention/monetization. Quick but less reliable than above methods.

Present results as a ranked table:
| Event | Volume Threshold | CSI Score | IV | RF Importance | Correlation | Verdict |
|-------|-----------------|-----------|-----|---------------|-------------|---------|

##### Track B: Qualitative (interview-driven)
Load the interview guide:
> Read `references/activation-interviews.md`

Run 3-pillar interviews with 15-20 users who completed the target action within 14 days, fit ICP, and are primary decision-makers:
1. **JTBD pillar:** What were they trying to accomplish? What triggered the search?
2. **Aha pillar:** When did they first feel the product was valuable? What happened?
3. **Decision criteria pillar:** What would make them stop? What do they compare you to?

##### Synthesis: Linear Customer Journey Map
Combine quant and qual into a journey map:

| | Awareness | Signup | Setup | First Action | Aha Moment | Habit |
|---|-----------|--------|-------|-------------|------------|-------|
| **Context** | | | | | | |
| **Goal** | | | | | | |
| **Emotion** | | | | | | |
| **Decision Criteria** | | | | | | |
| **Predictive Actions** | | | | | | |

The "Aha Moment" column is your activation metric. The "Predictive Actions" row contains supporting behaviors.

#### Step 3: Activation Barrier Analysis

Load the barrier framework:
> Read `references/activation-barriers.md`

Diagnose which barrier type is dominant:

**Category 1: Don't Know**
- Users do not understand what to do or why
- Signal: high signup-to-nothing rate, tooltip skip, help article searches
- Root cause: misaligned expectations from acquisition, unclear product UI

**Category 2: Can't**
- Users understand but are blocked by friction
- Signal: drop-off at specific steps, support tickets about "how to", long TTV
- Root cause: too many required steps, technical complexity, missing integrations

**Category 3: Don't Want**
- Users understand and can, but are not motivated
- Signal: signup but no action, low engagement with empty state, "I'll come back later"
- Root cause: cold start problem, no immediate value, no compelling first action

For each barrier found, map to specific onboarding steps and prioritize by drop-off volume.

#### Step 4: Map the Full Journey

Onboarding → Activation → Engagement journey:
- Where does onboarding end and activation begin?
- Is there a "setup tax" (required steps before value)?
- How does the product transition from "guided" to "self-directed"?

#### Step 5: Synthesize (Minto Pyramid)

```
## Activation Analysis

### Bottom Line
[One sentence: what is the single biggest activation opportunity?]

### Activation Metric
[The metric, evidence for it, and current rate]

### Top 3 Barriers (ranked by drop-off volume)
1. [Barrier type + specific step] -- Impact: [% of users affected]
2. [Barrier type + specific step] -- Impact: [% of users affected]
3. [Barrier type + specific step] -- Impact: [% of users affected]

### Hypotheses
1. [If we fix X, activation rate will increase by Y% because Z]
2. [If we fix X, activation rate will increase by Y% because Z]

### Key Unknowns
[What we still need to learn]

### Recommended Next Step
[Single concrete action]
```

---

### Mode 2: Data Analysis

**Goal:** Test hypotheses at specific issue tree branches quantitatively.

#### CSI/Aha Score Calculation
> Read `references/metric-identification.md` for detailed methodology

Walk the user through:
1. List all product events (actions users can take)
2. For each event, define volume thresholds (1x, 2x, 3x, 5x, 10x in first 7/14/30 days)
3. Build 2x2 contingency tables against 30/60/90-day retention
4. Calculate CSI = TP / (TP + FP + FN) for each combination
5. Rank by CSI score. Top scorers are activation metric candidates.

#### Activation Rate by Segment
- By cohort (monthly, to track trends)
- By acquisition channel (quality differs by source)
- By user segment (role, company size, use case)
- By onboarding path (if multiple paths exist)

#### Time-to-Value Distribution
- Median TTV for activated users
- TTV distribution (what % activate in 1 day? 3 days? 7 days? 14 days?)
- TTV by segment
- Identify the "activation window": after what point do remaining users almost never activate?

#### Drop-off Funnel
- Step-by-step conversion from signup to activation
- Identify the single biggest absolute drop-off
- Identify the single biggest relative drop-off (highest % loss)
- Compare drop-off pattern across segments

#### Predictive Analysis
- Correlation: activated user retention at 30/60/90 days vs. non-activated
- Correlation: activated user monetization rate vs. non-activated
- If difference is < 2x, the activation metric may not be predictive enough -- revisit metric identification

---

### Mode 3: Work Plan

**Goal:** Generate hypothesis-driven work items using the 3-step iterative framework.

Load the work plan template:
> Read `references/work-plan-template.md`

#### The 3-Step Iterative Framework

This is not a one-time exercise. It is a cycle that repeats every 2+ quarters.

**Step 1: Segment the user base**
Segment by:
- Acquisition channel (different channels, different activation paths)
- JTBD / use case (different jobs, different aha moments)
- Firmographics (company size, industry, role)
- Intent level (high-intent vs. casual exploration)

**Step 2: Identify supporting behaviors per segment**
For each segment, re-run the activation analysis:
- Which events predict retention for THIS segment?
- Is the activation metric the same or different across segments?
- What is the activation rate per segment?

Each finding is formatted as:
> "Users who [action] within [timeframe] are [X]% more likely to [target action]"

**Step 3: Improve supporting behaviors through experiments**
For each supporting behavior identified, design experiments to increase its occurrence.

**Minimum 2 full quarters per cycle.** Activation improvements compound slowly. Do not expect results in weeks.

#### Adaptive Work Plan Type

| User Situation | Work Plan Type |
|---------------|----------------|
| No activation metric defined | **Research Plan** -- metric identification is the priority |
| Metric defined but rate is low | **Experiment Backlog** -- fix barriers and test improvements |
| Metric defined, rate is OK, wants optimization | **OST** -- strategic framework for TTV reduction and segment optimization |

Load lever details:
> Read `references/activation-levers.md`

---

## Beyond the Core Framework

### Habit Formation Overlay (Hook Model)
When a user is activated but not yet retained, the Hook Model applies:
- **Trigger:** External (notification, email) or internal (boredom, need)
- **Action:** The simplest behavior in anticipation of reward
- **Variable Reward:** Unpredictable positive outcome (social, personal, material)
- **Investment:** User puts something in (data, preferences, content) that makes the product more valuable

Assessment: Does the product have a habit loop? If not, activated users will churn despite reaching aha moment.

### Setup vs. Activation Separation
- **Setup:** Required configuration steps (connect account, import data, set preferences)
- **Activation:** The moment of value delivery
- These are NOT the same. Minimize setup; maximize speed to activation.
- Best practice: let users experience value BEFORE requiring setup (reverse the order).

### Multi-Persona Activation
Different personas may have different activation metrics:
- Admin who sets up the tool vs. end user who uses it daily
- Creator who makes content vs. consumer who views it
- Each persona needs its own activation metric, barriers analysis, and improvement plan

### Activation to Retention Handoff
Activation is not the end. The gap between "first value" and "habitual use" is where many users are lost.
- Post-activation engagement triggers (what happens after aha?)
- Milestone celebrations (acknowledge progress)
- Deepening features (introduce advanced capabilities)
- Social connection (connect to team, community, other users)

## Connection to Other Skills

| Skill | When to Route |
|-------|---------------|
| `acquisition-domain` | Activation is fine but traffic/signups are the bottleneck |
| `retention-domain` | Users activate but do not retain -- handoff problem |
| `plg-revenue-analysis` | Need to understand activation in context of full revenue model |
| `plg-orchestrator` | User needs broader PLG diagnosis |

## Anti-Patterns to Watch For

- **Vanity activation metric:** Choosing a metric that is easy to hit but does not predict retention. The metric MUST be predictive.
- **Setup = activation:** Counting "completed onboarding" as activation when no value was delivered.
- **One-size-fits-all:** Using the same activation metric for all user segments when different segments have different aha moments.
- **Optimizing onboarding UI before defining the metric:** Know WHAT to optimize before HOW.
- **Ignoring time-to-value:** A 90% activation rate in 30 days is worse than 60% in 3 days for most PLG products.
- **Analysis paralysis on metric identification:** If quant methods are inconclusive, use qualitative insights. A good-enough metric now beats a perfect metric in 3 months.
