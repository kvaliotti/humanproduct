# Behavioral Science for Retention

Two complementary frameworks for understanding and designing retention behaviors. Use Fogg for specific behavior design. Use COM-B for systemic analysis.

---

## Framework 1: BJ Fogg Behavior Model (B = MAT)

**Core principle:** Behavior happens when Motivation, Ability, and a Trigger converge at the same moment. If any one is missing, the behavior does not occur.

### Motivation (M)

Three core motivators, each with a positive and negative pole:

#### 1. Pleasure / Pain
- **In SaaS context:** Does using the product feel rewarding or frustrating?
- Pleasure: time saved, task completed, beautiful output, satisfying interaction
- Pain: bugs, slow load, confusing UI, tedious data entry
- **Retention impact:** Products that feel good to use get opened more often

#### 2. Hope / Fear
- **In SaaS context:** Does the product help career growth or create FOMO if missed?
- Hope: "This tool makes me better at my job," "I am learning something"
- Fear: "If I do not check this, I will miss something important," "Competitors are using this"
- **Retention impact:** Hope drives initial adoption. Fear drives habitual checking (use carefully).

#### 3. Social Acceptance / Rejection
- **In SaaS context:** Does the team use it? Is there social pressure?
- Acceptance: "Everyone on my team uses this," "My manager recommended it"
- Rejection: "I am the only one not using it," "People expect me to have this data"
- **Retention impact:** Social products have structural retention advantages

#### Natural Use-Case Frequency
Beyond the three motivators, assess: **How often does the need naturally arise?**
- Daily need: messaging, task management, email → frequent natural triggers
- Weekly need: reporting, project review, planning → weekly triggers
- Monthly need: invoicing, analytics review → monthly triggers
- Event-driven: hiring, fundraising, incident response → sporadic triggers

**If the natural frequency is low, no amount of triggers will create daily usage.** Design for the natural frequency, not against it.

### Ability (A) = Simplicity

Six factors determine ability. **The scarcest factor determines overall ability** (like the weakest link in a chain).

#### 1. Time
- How long does a session take to get value?
- Target: meaningful value in < 5 minutes for daily-use products
- SaaS example: A dashboard that takes 30 seconds to show key metrics vs. one requiring 10 minutes of configuration

#### 2. Money
- Is the price a barrier to continued use?
- Free tier removes this entirely. Trial period defers it.
- SaaS example: User loves the product but cannot justify the price to their manager

#### 3. Physical Effort
- How many clicks, scrolls, and navigations to get value?
- Every additional click is a decision point where the user might stop
- SaaS example: 3-click path to key action vs. 8-click path through nested menus

#### 4. Brain Cycles (Cognitive Load)
- How much thinking does the product require?
- Jargon, complex settings, ambiguous options all increase cognitive load
- SaaS example: "Configure your webhook endpoint" vs. "Turn on notifications"

#### 5. Social Deviance
- Does using the product go against team or organizational norms?
- Using an unapproved tool, changing established workflows, adopting before the team
- SaaS example: Individual adopts a new PM tool but the team uses something else

#### 6. Non-Routineness
- How different is the product from the user's current workflow?
- Familiar patterns (spreadsheet-like, email-like) reduce this barrier
- SaaS example: A radically new interface paradigm vs. a familiar layout with added power

### Triggers (T)

Three types of triggers, matched to user state:

#### Spark (Trigger + Motivation boost)
- **For:** Users with high ability but low motivation
- **Design:** Combine the trigger with an inspirational or aspirational message
- **Examples:** "See how [company] grew 3x using this feature" + CTA
- **SaaS application:** Success stories, ROI calculators, peer benchmarks sent as notifications

#### Facilitator (Trigger + Ability boost)
- **For:** Users with high motivation but low ability
- **Design:** Combine the trigger with a simplification of the task
- **Examples:** "Your report is ready -- just click to view" (eliminates steps)
- **SaaS application:** Pre-built templates, one-click actions, guided workflows triggered by email or notification

#### Signal (Neutral reminder)
- **For:** Users with both high motivation and high ability
- **Design:** Simple reminder that the opportunity exists
- **Examples:** "You have 3 new comments" or "Weekly report is available"
- **SaaS application:** Activity notifications, scheduled reminders, digest emails

### The Motivation-Ability Curve

```
High Motivation
    |     * Triggers work here
    |    /  (above the curve)
    |   /
    |  /
    | /
    |/ ← The activation threshold curve
    |
    |  Triggers fail here
    |  (below the curve)
    +------------------------→ High Ability
```

**Key insight:** Users must be above the curve for triggers to work. If both motivation and ability are low, improve one of them first -- triggers alone will not help.

**Design implication:** For a given behavior, first assess where users sit on the M-A plane. Then:
- Below the curve: improve ability (simplify) or motivation (reframe value) FIRST
- Above the curve but not acting: add the right trigger type
- Above the curve and acting: optimize frequency and timing of triggers

---

## Framework 2: COM-B Model

**Core principle:** Behavior is a function of Capability, Opportunity, and Motivation, which form a positive feedback loop.

### Capability

#### Physical Capability
- Motor skills, tool access, device availability
- **SaaS context:** Does the user have the right device? Browser? Internet speed? Access permissions?
- **Retention relevance:** If users cannot access the product from their primary work device, they will not use it regularly

#### Psychological Capability
- Knowledge, comprehension, thought processes
- **SaaS context:** Does the user understand the product? Can they plan how to use it? Do they know the features?
- **Retention relevance:** Users who do not understand advanced features will not adopt them (limits breadth)

### Opportunity

#### Physical Opportunity
- Environmental cues, time availability, tool access
- **SaaS context:** Does the user have time in their workflow for this tool? Is it accessible where they work?
- **Retention relevance:** If the product requires a quiet hour to use but the user is in back-to-back meetings, opportunity is the constraint

#### Social Opportunity
- Social norms, peer behavior, organizational support
- **SaaS context:** Do colleagues use it? Does the manager endorse it? Is it part of the team's process?
- **Retention relevance:** Products adopted by teams retain better than products adopted by individuals

### Motivation

#### Reflective Motivation
- Conscious plans, beliefs, intentions, evaluations
- **SaaS context:** "I plan to use this every Monday for my weekly report"
- **Retention relevance:** Reflective motivation drives initial adoption but is effortful to maintain

#### Automatic Motivation
- Habits, emotional responses, impulses
- **SaaS context:** "I just open it every morning without thinking"
- **Retention relevance:** Automatic motivation is the goal -- it means the product is a habit

### The Positive Feedback Loop

```
Behavior (use the product)
    ↓
Increases Capability (user learns more)
    ↓
Increases Motivation (user sees more value)
    ↓
More Behavior (use the product more)
    ↓
... (virtuous cycle)
```

**Design implication:** The first few uses are the hardest. Once the loop starts, it sustains itself. Focus intervention energy on starting the loop (activation and early engagement).

---

## When to Use Which Framework

| Situation | Use Fogg | Use COM-B |
|-----------|----------|-----------|
| Designing a specific trigger/notification | Primary | Secondary |
| Understanding why a specific action is not happening | Primary | Secondary |
| Analyzing systemic retention patterns | Secondary | Primary |
| Understanding organizational adoption barriers | Secondary | Primary |
| Designing an experiment to increase a behavior | Primary | Secondary |
| Building a retention strategy across segments | Secondary | Primary |
| Diagnosing why a feature is underused | Primary | Primary |

**Rule of thumb:** Fogg for micro (one behavior, one user). COM-B for macro (patterns across users and contexts).

---

## Research Methodology

### Interview Guide for Behavioral Research

Conduct 15-20 interviews with a mix of retained and churned/at-risk users.

**Opening:**
"I want to understand your daily experience with [product]. There are no right or wrong answers."

**Context Questions:**
- "Walk me through a typical day when you use [product]."
- "When was the last time you used it? What were you doing?"
- "How does [product] fit into your overall workflow?"

**Motivation Questions (maps to M in Fogg, M in COM-B):**
- "What makes you want to use [product]?"
- "What is the most valuable thing it does for you?"
- "If you had to stop using it, what would you miss most?"
- "What would make you stop using it?"

**Ability Questions (maps to A in Fogg, C in COM-B):**
- "What is the hardest part about using [product]?"
- "Is there anything that takes too long?"
- "Is there anything you wish was simpler?"
- "What have you tried to do but could not figure out?"

**Trigger Questions (maps to T in Fogg, O in COM-B):**
- "What reminds you to open [product]?"
- "What prompts you to use it? A notification? A meeting? A deadline?"
- "Do your colleagues use it? How does that affect your usage?"
- "If you forget to use it for a few days, what brings you back?"

### Analysis Process

1. **Categorize each insight** by M/A/T (Fogg) or C/O/M (COM-B)
2. **Find patterns:** Which category has the most insights? That is likely the binding constraint.
3. **Segment by context:** Do different user types have different binding constraints?
4. **Prioritize by business value:** Which constraint, if resolved, affects the most users or highest-value users?

### Output: Behavioral Diagnosis

```
Binding constraint: [Motivation / Ability / Trigger] (Fogg)
Systemic gap: [Capability / Opportunity / Motivation] (COM-B)

Evidence:
- [N] of [M] users cited [specific issue] related to [constraint]
- [Segment X] is primarily limited by [constraint]
- [Segment Y] is primarily limited by [different constraint]

Implication:
- For [Segment X]: Design [Spark/Facilitator/Signal] intervention
- For [Segment Y]: Improve [Ability factor / Capability type] first
```

---

## Design Patterns

### Pre-Design Behavioral Checklist

Before designing any retention feature or experiment, answer:

- [ ] What specific behavior am I trying to increase? (Be precise)
- [ ] What is the natural frequency of this behavior's use case?
- [ ] What is the current motivation level? (Which of the 3 motivators applies?)
- [ ] What is the current ability level? (Which of the 6 factors is scarcest?)
- [ ] What triggers exist today? (Internal or external?)
- [ ] Where does the user sit on the Motivation-Ability curve?
- [ ] What type of trigger is needed? (Spark, Facilitator, or Signal?)

### Behavioral Design Critique

When reviewing a proposed feature or experiment:

1. **Does it address the binding constraint?** If motivation is the problem, a simplification (ability improvement) will not help.
2. **Is the trigger matched to the user state?** Sending a Signal to a low-motivation user wastes the touchpoint.
3. **Does it account for natural frequency?** Designing daily triggers for a monthly-use product will annoy, not retain.
4. **Is the social context considered?** Individual interventions may fail if organizational opportunity is the constraint.

### Experiment Ideation Through Behavioral Components

For each behavioral component, generate experiment ideas:

**Motivation experiments:**
- Show ROI/value metrics ("You saved 3 hours this week")
- Social proof ("Your team completed 50 tasks this week")
- Loss framing ("Your streak of 5 weeks will reset if you do not log in")

**Ability experiments:**
- Reduce steps (remove a required field, skip a screen)
- Simplify language (replace jargon with plain language)
- Add templates/defaults (pre-fill what you can)

**Trigger experiments:**
- Test notification timing (morning vs. afternoon vs. event-driven)
- Test channel (email vs. push vs. in-app vs. Slack)
- Test message type (Spark vs. Facilitator vs. Signal)
