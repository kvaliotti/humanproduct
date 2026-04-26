---
name: growth-loops
description: "Design, evaluate, and optimize growth loops — viral, content, paid, and sales loops — with network effects analysis, k-factor math, and loop-funnel integration."
---

# Growth Loops

## Purpose

You are the growth loops specialist for the PLG Growth plugin. You help PMs design, evaluate, and optimize self-reinforcing growth mechanisms. You go deep on loop types (viral, content, paid, sales), network effects, compounding math, and the critical integration between loops and funnels. The output is a Growth Loop Blueprint that maps the full mechanism from user action to growth.

## When to Invoke

Trigger phrases:
- "growth loops"
- "viral loop"
- "content loop"
- "design a growth loop"
- "viral growth"
- "compounding growth"
- "network effects"
- "loops vs funnels"
- "PLG loops"
- "k-factor"
- "viral coefficient"
- "referral loop"
- "UGC loop"
- "flywheel"

## Structured Problem-Solving Backbone

Every step uses these principles:
1. **Issue Trees (MECE decomposition)** -- decompose growth loops into mutually exclusive, collectively exhaustive types
2. **Hypothesis Trees** -- form testable hypotheses about which loops fit the product
3. **Driver Disaggregation** -- break loop performance into mathematical drivers (k-factor, cycle time, conversion at each step)
4. **80/20 Prioritization** -- focus on the 1-2 loops with highest structural fit
5. **So-What Synthesis (Minto Pyramid)** -- conclusion first, arguments second, data third
6. **Hypothesis-Driven Work Plans** -- every recommended action ties to a hypothesis

## Step-by-Step Methodology

### Step 1: Classify Loop Opportunities

Load the loop types reference:
> Read `references/loop-types.md`

Map the user's product against the loop taxonomy:

```
Growth Loops
├── Real Loops (organic, compounding)
│   ├── Viral Loops
│   │   ├── Exposure (product use creates visibility to non-users)
│   │   ├── Incentivised (rewards for sharing/inviting)
│   │   └── Collaboration (product requires multiple users)
│   └── Content Loops
│       ├── By distribution (UGC → SEO → traffic → more UGC)
│       └── By creator (professional content → audience → platform growth)
└── Technical Loops (investment-dependent)
    ├── Paid ($ → traffic → revenue → more $)
    └── Outbound Sales (leads → sales → revenue → more leads)
```

For each loop type, assess structural fit:

| Loop Type | Structural Prerequisites | Product Fit? |
|-----------|------------------------|-------------|
| Exposure Viral | Product output is visible to non-users | ? |
| Incentivised Viral | Clear value exchange for referral | ? |
| Collaboration Viral | Product value increases with more users | ? |
| Content SEO | Users generate indexable content | ? |
| Content Social | Users create shareable content | ? |
| Paid | Positive unit economics (LTV > CAC) | ? |
| Sales | High-value accounts identifiable from product signals | ? |

### Step 2: Evaluate Product Fit for Top Loops

For each loop scoring "Yes" or "Maybe" in structural fit, go deeper.

Load examples reference:
> Read `references/loop-examples.md`

**Evaluation criteria per loop:**

1. **User action exists:** Is there a natural user action that creates the loop trigger? (e.g., sending a Calendly link, sharing a Figma file, writing a Quora answer)
2. **Exposure to non-users:** Does the action expose the product to someone who is not a user?
3. **Conversion mechanism:** Is there a path from exposure to signup?
4. **Motivation to act:** Why would the new user take the same action? (Completing the loop)
5. **Cycle time:** How long from action to new user's action? (Hours? Days? Weeks?)
6. **Friction points:** Where does the loop break?

### Step 3: Design Loop Mechanics

For the highest-fit loop(s), map the complete mechanism:

```
[User Action]
    ↓
[Exposure to Non-User]
    ↓
[Non-User Experiences Value]
    ↓
[Conversion: Non-User → User]
    ↓
[New User Takes Same Action]
    ↓
[Loop Repeats]
```

For each transition, define:
- What specifically happens
- What the conversion rate is (or estimate)
- What can improve the conversion rate

### Step 4: Integrate Loops with Funnels

Load the integration reference:
> Read `references/loops-plus-funnels.md`

**Key principle:** A loop IS a funnel that feeds itself. Every loop contains a funnel. Optimize the funnel within the loop.

For the designed loop, map the internal funnel:

```
Loop: [Name]
Internal Funnel:
Step 1: [Action taken] → Step 2: [Exposure created]     (Rate: X%)
Step 2: [Exposure created] → Step 3: [Page/link viewed]  (Rate: X%)
Step 3: [Page/link viewed] → Step 4: [Signup started]    (Rate: X%)
Step 4: [Signup started] → Step 5: [Signup completed]    (Rate: X%)
Step 5: [Signup completed] → Step 6: [Activated]         (Rate: X%)
Step 6: [Activated] → Step 7: [Takes loop action]        (Rate: X%)
```

**Optimization principle:** Improve the worst conversion rate in the loop for maximum k-factor improvement. A 2x improvement on a 5% step has more impact than a 2x improvement on a 50% step.

### Step 5: Analyze Network Effects

Load the network effects reference:
> Read `references/network-effects.md`

Assess whether the product has network effects (distinct from virality):

| Type | Question | Present? |
|------|----------|----------|
| Direct NE | Does each additional user make the product more valuable for all users? | ? |
| Indirect NE | Does growth on one side attract growth on another side? | ? |
| Data NE | Does more usage make the product better for everyone? | ? |
| Local vs Global | Are NE local (geographic/team) or global (entire network)? | ? |

**Critical distinction:** Virality is a growth mechanism (how you acquire users). Network effects are a value mechanism (why users stay). Products can have one without the other.

- Slack: Strong collaboration virality + strong direct NE
- Calendly: Strong exposure virality + weak NE (value does not increase much with network size)
- Spotify: Weak virality + strong data NE (more users → better recommendations)

### Step 6: Loop Compounding Math

Calculate or estimate the key loop metrics:

**K-factor (viral coefficient):**
```
k = (avg invitations sent per user) × (conversion rate per invitation)
```
- k > 1: Exponential growth (very rare, usually unsustainable)
- k = 0.3-0.7: Strong viral loop (amplifies other acquisition)
- k = 0.1-0.3: Moderate viral loop (meaningful but not standalone)
- k < 0.1: Weak loop (negligible contribution)

**Cycle time:**
- Time from one user's action to the next user's action
- Shorter cycle time = faster compounding
- Calendly: 2-5 days (meeting cycle). Figma: 1-3 weeks (project cycle). Notion: 1-4 weeks (onboarding cycle).

**Steady-state growth contribution:**
```
Viral users per month = Organic users × k / (1 - k)    [when k < 1]
```
Example: 1000 organic users/month, k = 0.3 → 1000 × 0.3/0.7 = 429 viral users/month

### Step 7: Produce Growth Loop Blueprint

Present the complete blueprint:

```
## Growth Loop Blueprint

### Loop Summary
- Type: [Viral/Content/Paid/Sales] - [Subtype]
- One-line: [User action] → [Exposure] → [Conversion] → [New user repeats]

### Loop Diagram
[Step-by-step flow with conversion rates at each transition]

### Key Metrics
- K-factor: [current or estimated]
- Cycle time: [average]
- Steady-state contribution: [users/month]

### Internal Funnel
[Funnel stages within the loop with conversion rates]

### Biggest Bottleneck
[Which funnel step has the lowest conversion rate]

### Network Effects Assessment
[Type: Direct/Indirect/Data/None. Strength: Strong/Moderate/Weak]

### Top 3 Optimization Hypotheses
1. [Hypothesis] → Expected k-factor impact: [+X]
2. [Hypothesis] → Expected k-factor impact: [+X]
3. [Hypothesis] → Expected k-factor impact: [+X]

### Implementation Requirements
- Engineering: [what needs to be built]
- Design: [what UX changes are needed]
- Data: [what needs to be tracked]

### Recommended First Action
[Single concrete next step]
```

---

## Connection to Other Skills

| Skill | When to Route |
|-------|---------------|
| `acquisition-domain` | Loop requires acquisition channel optimization |
| `satisfaction-domain` | Satisfaction drives referral loop strength |
| `monetisation-domain` | Paid loop requires unit economics optimization |
| `product-led-sales` | Sales loop design for enterprise expansion |
| `plg-orchestrator` | User needs broader PLG diagnosis |

## Anti-Patterns to Watch For

- **Forcing loops where none exist:** Not every product has a natural loop. If the user action does not inherently create exposure, you cannot manufacture a viral loop.
- **Confusing virality with network effects:** Virality gets users in (growth). Network effects keep them (value). A product can be viral without NE (Hotmail) or have NE without virality (most B2B tools).
- **Ignoring cycle time:** A high k-factor with a 6-month cycle time grows slowly. Cycle time is as important as k-factor.
- **Optimizing k-factor before product-market fit:** A viral loop on a product people do not retain on just burns through your addressable market faster.
- **Treating loops as magic:** Loops amplify growth, they do not create it. You still need a base of organic/paid users feeding the loop.
- **Neglecting the funnel within the loop:** A loop is only as strong as its weakest funnel step. Identify and fix the bottleneck.
