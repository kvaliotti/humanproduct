# Growth Team Structuring Models

## Overview

How you structure your team around revenue levers determines execution velocity. The right structure depends on team size, priority levers, and organizational context.

---

## Small Team (< 5 Growth/Product People)

### Model A: Single-Lever Focus

**When to use:** One lever dominates the sensitivity analysis (>50% of the total opportunity).

**Structure:**
- 1 Growth lead (owns the metric, runs experiments, coordinates)
- 1-2 Engineers (builds experiments and features)
- 1 Designer or PM (user research, design, prioritization)
- Shared: data/analytics support

**How it works:**
- Entire team focuses on one metric for 6-12 week sprints
- Run rapid experiments (1-2 per week)
- Rotate to next lever only when: (a) metric reaches target, (b) diminishing returns, or (c) new data changes priority

**Example:** "Our activation rate is 22% vs 40% benchmark. All growth effort focuses on onboarding optimization for Q1."

### Model B: Cross-Lever Sprint

**When to use:** Two levers are close in priority AND share dependencies (e.g., activation and paid conversion both require onboarding changes).

**Structure:** Same as Model A, but:
- Alternate focus every 2-3 weeks between the two levers
- Or: split the team (2 on lever A, 2 on lever B) if work is parallelizable

**Caution:** Do not split a small team across more than 2 levers. Context-switching kills velocity.

### Small Team Anti-Patterns
- Trying to work on all levers at once (nothing moves)
- No dedicated metric owner (accountability gap)
- Not running experiments (building features instead of testing hypotheses)
- Changing focus every week based on latest fire

---

## Medium Team (5-15 Growth/Product People)

### Model C: Revenue-Type Pods

**When to use:** Multiple MRR components (New, Retained, Expansion) are all significant priorities.

**Structure:**
```
Growth Lead (cross-pod coordination)
├── New MRR Pod (3-5 people)
│   ├── PM/Growth lead
│   ├── 1-2 Engineers
│   └── Designer
│   Metrics: Traffic, signup conv, activation, paid conv
│
├── Retention Pod (3-5 people)
│   ├── PM/Growth lead
│   ├── 1-2 Engineers
│   └── Data analyst
│   Metrics: Churn rate, engagement depth, NPS
│
└── Expansion Pod (3-5 people)
    ├── PM/Growth lead
    ├── 1-2 Engineers
    └── Designer
    Metrics: NRR, seat expansion, upgrade rate
```

**Pros:** Clear ownership, focused metrics, career paths.
**Cons:** Handoff friction between pods, potential for local optimization.

### Model D: Metrics-Cluster Teams

**When to use:** Funnel stages are more natural boundaries than revenue components.

**Structure:**
```
Growth Lead
├── Acquisition Team
│   Metrics: Traffic, signups, CAC
│   Focus: Landing pages, channels, signup flow
│
├── Activation Team
│   Metrics: Activation rate, TTV, onboarding completion
│   Focus: Onboarding, aha moment, first value
│
└── Monetization Team
    Metrics: Paid conversion, ARPU, NRR, churn
    Focus: Paywall, pricing, upgrade flow, retention
```

**Pros:** Natural user-journey alignment, easier to identify handoff points.
**Cons:** Can miss cross-funnel interactions.

---

## Large Team (15+ Growth/Product People)

### Model E: Full Revenue-Lever Organization

**Structure:**
```
VP Growth
├── Acquisition (5-8 people)
│   ├── Organic/SEO sub-team
│   ├── Paid acquisition sub-team
│   └── Viral/referral sub-team
│
├── Activation & Onboarding (4-6 people)
│   ├── New user onboarding
│   └── Feature adoption
│
├── Monetization (4-6 people)
│   ├── Self-serve conversion
│   ├── Pricing & packaging
│   └── PQL-to-sales handoff
│
├── Retention (4-6 people)
│   ├── Engagement & stickiness
│   ├── Churn prevention
│   └── Reactivation
│
├── Expansion (3-5 people)
│   ├── Seat growth
│   ├── Usage growth
│   └── Upgrade/upsell
│
└── Growth Platform (3-5 people)
    ├── Experimentation infrastructure
    ├── Data & analytics
    └── Growth tooling
```

### Model F: Lever + Horizontal Capabilities

**Structure:**
```
VP Growth
├── Lever Teams (vertical, own metrics)
│   ├── Team Acquisition
│   ├── Team Activation
│   ├── Team Monetization
│   └── Team Retention
│
└── Horizontal Capabilities (serve all lever teams)
    ├── Data Science / Analytics
    ├── Experimentation Platform
    ├── Growth Engineering (shared components)
    └── Growth Design (shared designers)
```

---

## Dedicated Owner Model

Regardless of structure, every priority lever needs a **dedicated owner**:

| Role | Responsibility |
|---|---|
| **Metric owner** | Accountable for the number. Reports on it weekly. Understands all sub-drivers. |
| **Hypothesis generator** | Maintains a backlog of hypotheses about what will move the metric. |
| **Experiment runner** | Designs and runs experiments to test hypotheses. |
| **Insight synthesizer** | Turns experiment results into learnings and next hypotheses. |

In a small team, one person wears all 4 hats. In a large team, these can be distributed.

---

## Structuring Decision Framework

Ask these questions to select the right model:

| Question | If Yes → | If No → |
|---|---|---|
| Is one lever >50% of the opportunity? | Single-lever focus (Model A/B) | Multi-lever structure (Model C-F) |
| Is team < 5 people? | Model A or B | Model C+ |
| Are revenue components fairly independent? | Revenue-type pods (Model C) | Metrics-cluster teams (Model D) |
| Does team need to share engineers/designers? | Lever + Horizontal (Model F) | Full lever org (Model E) |
| Is there a separate data/analytics team? | Embed analysts in pods | Include in Growth Platform |

---

## Metrics Cadence

Regardless of structure, establish this cadence:

| Cadence | Activity |
|---|---|
| **Daily** | Check key metrics dashboards (automated alerts for anomalies) |
| **Weekly** | Growth review: each lever owner reports metric, running experiments, learnings |
| **Bi-weekly** | Experiment review: analyze completed experiments, decide next experiments |
| **Monthly** | Revenue deep-dive: full tree analysis, reprioritize levers, adjust team allocation |
| **Quarterly** | Strategic review: recalculate sensitivity analysis, shift team structure if needed |

---

## Common Pitfalls

1. **Org chart follows strategy, not the other way around.** Pick the levers first, then structure the team. Do not let existing team structure dictate which levers to focus on.

2. **Rotate, do not re-org.** If priorities shift, rotate people between focuses rather than restructuring. Re-orgs are expensive.

3. **Measure inputs, not just outputs.** Revenue is an output. Experiments run, hypotheses tested, and learning velocity are inputs. Track both.

4. **Growth is cross-functional.** Growth teams need engineering, design, data, product, and sometimes marketing/sales. A "growth PM" without engineering capacity is just a person with opinions.

5. **Avoid "growth theater."** Running experiments that are too small to matter, or A/B testing button colors when the real problem is a broken value prop. Focus experiments on the priority levers identified in the revenue analysis.
