# Behavioral Research Approach

Synthesized from COM-B (Capability, Opportunity, Motivation — Behavior) and B=MAP (Behavior = Motivation + Ability + Prompt, from BJ Fogg's Behavior Design). For the underlying definitions of both frameworks (the 6 COM-B sub-components, PAC, Ability Chain, Prompt types, troubleshooting order), see the shared primer at `${CLAUDE_PLUGIN_ROOT}/references/behavioral-frameworks.md` — read it first. This file covers brief-writing application only: how to turn those frameworks into the specific research questions and hypotheses a brief needs.

Use this reference when the research centers on getting users to perform (or stop performing) a specific action — adoption, engagement, retention, onboarding, habit formation, feature usage. Use both frameworks in every behavioral brief: COM-B provides comprehensive diagnostic coverage, B=MAP provides a precise, ordered action-design lens.

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

**Research questions:**
- What do users currently know/not know about [target behavior]? (Psychological Capability)
- What cognitive load or decision complexity stands in the way — attention, working memory, competing demands? (Psychological Capability)
- What skills (digital literacy, domain knowledge) does this behavior require, and can the user physically execute the required actions — navigate the UI, complete gestures? Any accessibility or motor-skill barriers? (Physical Capability)

### 4b. Opportunity

**Research questions:**
- Is the feature discoverable, accessible, and available at the right moment? What environmental triggers or barriers exist at the moment the behavior should occur? (Physical Opportunity)
- Who influences the user's decision to perform (or not perform) the behavior — peers, managers, community? (Social Opportunity)
- What social norms, cultural expectations, or organizational norms operate in this context — do they support or conflict with the behavior? (Social Opportunity)

### 4c. Motivation

**Research questions:**
- Does the user believe the behavior leads to a valued outcome? Do they intend to do it, and do they believe they're capable (self-efficacy)? (Reflective Motivation)
- Does the behavior align with their professional/personal identity? (Reflective Motivation)
- What emotional reaction does the user have to the behavior or its context — anxiety, boredom, excitement? (Automatic Motivation)
- Is there an existing habit or routine that supports or competes with the behavior? (Automatic Motivation)

---

## 5. B=MAP Decomposition

Use the PAC / Ability Chain / Prompt Type definitions from the shared primer (`${CLAUDE_PLUGIN_ROOT}/references/behavioral-frameworks.md`, section 2). What follows is brief-specific: what must be captured in the brief for each component.

### Motivation (M) — Why would the user do this?

- **Critical filter (Mom Test):** Are you documenting what users actually do or what they say they'd do? Flag which motivation signals come from observed behavior vs. stated intent.
- **Document competing motivations:** Users often have motivations pushing toward and away from the same behavior. Map both vectors.
- **Document conflicting motivations:** The same user may want the outcome but not want the specific behavior. Capture this tension explicitly.
- **State motivation durability:** Enduring, Wave, or Fluctuating (see primer) — this shapes what kind of intervention will hold up.

### Ability (A) — Can the user do this?

- Score all 5 Ability Chain factors (Time, Money, Physical effort, Mental energy, Routine fit — see primer) and hypothesize the weakest link.
- **Discovery Question:** "What is making this behavior hard to do?" — must appear in every behavioral research brief as a hypothesis to test.
- **Breakthrough Question:** "How can we make this behavior easier to do?" — frames the design opportunity via the three ability levers (skill up / better tools / make it tinier — see primer).

### Prompt (P) — What triggers the behavior?

- Classify the current/planned prompt using the three prompt types from the primer (Person / Context / Action-Anchor).
- **Specify the Anchor Moment** if one exists: what existing behavior does (or could) this new behavior follow?
- **Find the Trailing Edge:** the last specific action in the anchor behavior — the precise prompt point.
- **Run the anchor match checklist** from the primer (location / frequency / theme match) before committing to an anchor hypothesis.

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
