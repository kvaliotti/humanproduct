# Behavioral Research Approach

Synthesized from COM-B (Capability, Opportunity, Motivation — Behavior) and B=MAP (Behavior = Motivation + Ability + Prompt, from BJ Fogg's Behavior Design). Use this reference when the research centers on getting users to perform (or stop performing) a specific action — adoption, engagement, retention, onboarding, habit formation, feature usage.

Both frameworks decompose behavior into components. They complement each other: COM-B provides a comprehensive diagnostic (6 sub-components), B=MAP provides a precise action-design lens (3 components with troubleshooting order). Use both in every behavioral brief.

---

## Table of Contents
1. Defining the Problem in Behavioral Terms
2. Selecting the Target Behavior
3. Specifying the Target Behavior
4. COM-B Decomposition
5. B=MAP Decomposition
6. Mapping the Action Line
7. Competing Behaviors
8. Segments by Behavioral Profile
9. Framing Testable Hypotheses
10. Methods Matched to Components
11. Anti-Patterns
12. Quality Checklist

---

## 1. Defining the Problem in Behavioral Terms

The most common error: confusing aspirations/outcomes with behaviors.

| Layer | Definition | Example |
|-------|-----------|---------|
| **Aspiration** | Abstract desire | "Users want to be more productive" |
| **Outcome** | Measurable result | "Complete 3 tasks per day in the app" |
| **Behavior** | Specific action at a specific moment | "After opening the app, user clicks 'Start Focus Session'" |

**Rule:** If you can't do it right now at a specific moment, it's not a behavior — it's an aspiration or outcome. Research briefs that target aspirations produce fuzzy insights. Research briefs that target behaviors produce actionable ones.

**COM-B template:**
> The problem is that [WHO] is/isn't doing [WHAT behavior] in [WHAT context], and this matters because [IMPACT on user/business outcome].

**B=MAP template:**
> After [CONTEXT/TRIGGER], the user will [SPECIFIC ACTION].

If you can't fill in both blanks in either template, the brief isn't specific enough. If the problem is vague ("users don't engage"), decompose it into candidate behaviors before selecting one.

---

## 2. Selecting the Target Behavior

When multiple behaviors contribute to the problem, score each before committing the brief to one:

| Criterion | Question | Score 1-4 |
|-----------|----------|-----------|
| **Impact** | If this behavior changed, how much would it move the outcome? | |
| **Likelihood of change** | How realistic is it that we can influence this behavior? | |
| **Spillover** | Will changing this behavior positively affect related behaviors? | |
| **Measurability** | Can we observe or measure whether this behavior changed? | |

Select the behavior with the highest total. If two tie, prefer higher Impact.

---

## 3. Specifying the Target Behavior

Every behavioral research brief must answer all six questions. Incomplete specification = unfocused research.

| Element | Question | Example |
|---------|----------|---------|
| **Who** | Who needs to perform the behavior? | New users in their first 7 days |
| **What** | What do they need to do differently? | Complete the 3-step onboarding checklist |
| **When** | When should they do it? | Within the first session after signup |
| **Where** | In what context/setting? | Mobile app, during commute or idle time |
| **How often** | What frequency is needed? | Once (completion) or daily (habit) |
| **With whom** | Who else is involved or influences the behavior? | No collaborator required; triggered by system nudge |

---

## 4. COM-B Decomposition

Structure research questions around what might need to change for the target behavior to occur. All 6 sub-components must be addressed.

### 4a. Capability

**Physical Capability** — Does the user have the physical skills or stamina?
- Can the user physically execute the required actions (navigate UI, complete gestures)?
- Are there accessibility or motor-skill barriers?

**Psychological Capability** — Does the user have the knowledge, cognitive skills, and mental bandwidth?
- Does the user know the behavior exists and what it involves?
- Can they remember what to do and when?
- Can they plan, prioritize, and self-regulate to carry out the behavior?
- Do they have the mental bandwidth (attention, working memory) given competing demands?

**Research questions:**
- What do users currently know/not know about [target behavior]?
- What cognitive load or decision complexity stands in the way?
- What skills (digital literacy, domain knowledge) does this behavior require?

### 4b. Opportunity

**Physical Opportunity** — Does the environment enable the behavior?
- Is the feature discoverable, accessible, and available at the right moment?
- Are there time, resource, or tool constraints that block the behavior?
- Does the physical/digital environment prompt or cue the behavior?

**Social Opportunity** — Do social influences support the behavior?
- Is the behavior normative among peers, team members, or the user's community?
- Do managers, colleagues, or social networks encourage or discourage it?
- Are there cultural or organizational norms that conflict with the behavior?

**Research questions:**
- What environmental triggers or barriers exist at the moment the behavior should occur?
- Who influences the user's decision to perform (or not perform) the behavior?
- What social norms or expectations operate in this context?

### 4c. Motivation

**Reflective Motivation** — Conscious beliefs, intentions, and plans.
- Does the user believe the behavior will lead to valued outcomes?
- Does the user intend to do it? Have they made a plan?
- Does the behavior align with their professional/personal identity?
- Do they believe they are capable of doing it (self-efficacy)?

**Automatic Motivation** — Emotional responses, habits, impulses.
- What emotional reaction does the user have to the behavior or its context?
- Is there an existing habit or routine that supports or competes with the behavior?
- Are there impulses, desires, or aversions at play?

**Research questions:**
- What does the user believe will happen if they do/don't perform the behavior?
- What are their goals and priorities — does this behavior rank?
- What emotional associations (anxiety, boredom, excitement) attach to the behavior or context?

---

## 5. B=MAP Decomposition

### Motivation (M) — Why would the user do this?

Identify motivation sources using the PAC framework:

| Source | Question | Example |
|--------|----------|---------|
| **Person** (internal) | Does the user already want this? | Intrinsic desire to save time |
| **Action** (benefit/punishment) | What carrot or stick exists? | Bonus for completing onboarding |
| **Context** (social/environmental) | Does the environment push toward this? | Manager requires daily check-in |

**Critical filter (Mom Test):** Are you documenting what users actually do or what they say they'd do? Flag which motivation signals come from observed behavior vs. stated intent.

**Document competing motivations:** Users often have motivations pushing toward and away from the same behavior. Map both vectors.

**Document conflicting motivations:** The same user may want the outcome but not want the specific behavior. Capture this tension explicitly.

**Motivation durability:** Is motivation enduring (aspiration-level), wave-like (temporary surge after signup, then crash), or fluctuating?

### Ability (A) — Can the user do this?

Assess using the Ability Chain — five factors, weakest link determines feasibility:

| Factor | Assessment Question |
|--------|-------------------|
| **Time** | How many seconds/minutes does this take? |
| **Money** | What does this cost the user? |
| **Physical effort** | What physical actions are required? |
| **Mental energy** | How much cognitive load does this demand? |
| **Routine fit** | Does this slot into existing workflows or require restructuring? |

**Discovery Question:** "What is making this behavior hard to do?" — This must appear in every behavioral research brief as a hypothesis to test.

**Breakthrough Question:** "How can we make this behavior easier to do?" — This frames the design opportunity.

**Three ability levers to explore:**
1. Can users skill up? (training, education)
2. Can we provide better tools? (UX, automation)
3. Can we make the behavior tinier? (reduce scope, simplify steps)

### Prompt (P) — What triggers the behavior?

Classify the current/planned prompt:

| Prompt Type | Reliability | Example |
|-------------|------------|---------|
| **Person Prompt** | Low — relies on memory | "I'll remember to check the dashboard" |
| **Context Prompt** | Medium — external reminder | Push notification, email reminder |
| **Action Prompt (Anchor)** | High — wired to existing behavior | "After I open Slack, I check the dashboard" |

**Specify the Anchor Moment** if one exists: What existing behavior does (or could) this new behavior follow?

**Find the Trailing Edge:** What is the last specific action in the anchor behavior? This is the precise prompt point.

**Anchor match quality checklist:**
- Location match: Does the anchor happen in the same place/app? ✓/✗
- Frequency match: Does the anchor happen at the needed frequency? ✓/✗
- Theme match: Is the anchor thematically related? ✓/✗

---

## 6. Mapping the Action Line

For each target behavior, hypothesize where users currently sit:

- **Above the line** (behavior happens): M and A are sufficient when prompted → Research focus: why it works, what sustains it
- **Below the line** (behavior doesn't happen): M or A insufficient → Research focus: which component is the bottleneck
- **No prompt exists**: Behavior never fires regardless of M and A → Research focus: prompt design

### Troubleshooting Order

This order is critical — most people start with motivation, which is wrong:

1. **Is there a prompt?** (Check first) — No prompt means the behavior never gets a chance to happen
2. **Is there sufficient ability?** (Check second) — Even motivated users won't do hard things
3. **Is there sufficient motivation?** (Check last) — Only investigate motivation after confirming prompt and ability are sufficient

---

## 7. Competing Behaviors

List behaviors that currently occupy the same "slot" as the target behavior:

| Competing Behavior | Why it persists (COM-B driver) | B=MAP profile | Research implication |
|--------------------|-------------------------------|---------------|----------------------|
| E.g., User skips onboarding and goes straight to exploring | Automatic motivation (curiosity impulse) + low reflective motivation (doesn't see onboarding value) | High M (explore), High A (no steps needed), Strong P (app open = prompt) | Explore beliefs about onboarding value; test whether curiosity can be channeled into onboarding |

For each competing behavior, note which COM-B component or B=MAP factor makes it persist. This reveals what your intervention must overcome.

---

## 8. Segments by Behavioral Profile

Different user segments may have the same aspiration but different behavioral profiles. Segment by COM-B or B=MAP configuration, not demographics.

| Segment | COM-B Profile | B=MAP Profile | Research Priority |
|---------|---------------|---------------|-------------------|
| Power users | High C, High O, High M | High M, High A, Strong anchors | Why it works — protect and replicate |
| New users | Low Psych Capability, Low Phys Opportunity (discoverability) | Motivation wave (high then crash), Low A (multiple weak links), No anchors | Ability and prompt first |
| Churned users | Capability degraded, Opportunity narrowed (lost habit slot) | Competing motivations won, A degraded, Prompts became noise | What broke — which component failed |

**Rule:** Never write a one-size-fits-all brief. If segments have different behavioral profiles, they need different research questions.

---

## 9. Framing Testable Hypotheses

Every hypothesis in the brief should follow this structure:

> "We believe [BEHAVIOR] is not happening because [M/A/P or COM-B component] is insufficient. Specifically, [precise hypothesis]. We will test this by [method]."

**Examples:**
- "We believe users don't complete onboarding because the behavior requires too much mental energy (Ability Chain: mental effort is weakest link). We will test this by observing where users pause or abandon."
- "We believe users don't return to the dashboard because no prompt exists in their workflow (Prompt: no anchor). We will test this by mapping their existing morning routine for anchor points."
- "We believe users don't share reports with teammates because social opportunity is absent (COM-B: Social Opportunity — sharing isn't normative in their team culture). We will test this by probing team communication norms in interviews."

---

## 10. Methods Matched to Components

| Component | Suitable Methods |
|-----------|-----------------|
| **Psychological Capability** | Interviews (knowledge probes, think-alouds), usability tests |
| **Physical Capability** | Observation, usability tests, accessibility audits |
| **Physical Opportunity** | Analytics (funnel data, feature exposure), environment audits, diary studies |
| **Social Opportunity** | Interviews (social context probes), ethnographic observation, surveys |
| **Reflective Motivation** | Interviews (belief/identity probes), card sorts, surveys |
| **Automatic Motivation** | Observation, experience sampling, implicit association tasks |
| **Ability Chain factors** | Task analysis, timed observations, cognitive walkthroughs |
| **Prompt/Anchor mapping** | Diary studies, daily routine mapping, workflow observation |

**Caution on self-report:** People are unreliable reporters of their own behavior frequency and drivers. Triangulate self-report with behavioral data (analytics, observation). Ask about specific recent instances, not generalities.

---

## 11. Anti-Patterns

| Anti-Pattern | Why It Fails | Fix |
|-------------|-------------|-----|
| Brief targets "increase engagement" | Aspiration, not a behavior | Specify the exact behavior at a specific moment |
| Brief assumes motivation is the problem | Skips prompt and ability checks | Follow troubleshooting order: P → A → M |
| Brief doesn't specify the prompt | Can't study behavior that has no trigger | Map existing workflows first, identify anchors |
| Brief treats all users the same | Different behavioral profiles need different research | Segment by M/A/P or COM-B configuration |
| Brief asks "why don't users want to do X?" | Assumes motivation deficit | First ask: "Is there a prompt? Is it easy enough?" |
| Brief focuses on what users say vs. do | Mom Test violation — stated intent ≠ observed behavior | Distinguish stated motivation from observed behavior |
| Brief conflates aspiration with behavior | "Users want to be productive" ≠ "Users click Start Focus Session" | Apply the "can you do it right now?" test |

---

## 12. Quality Checklist

Before finalizing the brief, confirm:

- [ ] Problem is stated as observable behavior, not attitude or aspiration
- [ ] Target behavior scored on Impact, Likelihood, Spillover, Measurability
- [ ] Behavioral specification complete (Who/What/When/Where/How often/With whom)
- [ ] Research questions cover all 6 COM-B sub-components
- [ ] B=MAP decomposition covers Motivation (with PAC), Ability (with Chain), Prompt (with type + anchor)
- [ ] Troubleshooting order follows P → A → M
- [ ] Action Line position hypothesized
- [ ] Competing behaviors identified with drivers
- [ ] Segments defined by behavioral profile, not demographics
- [ ] Hypotheses are structured and testable
- [ ] Methods matched to specific components
- [ ] Brief distinguishes what users DO from what they SAY they do
- [ ] No leading questions that assume the answer
