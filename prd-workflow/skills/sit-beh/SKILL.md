---
name: sit-beh
description: >
  Situation/Behaviour framework for product design — identifies real-life situations users face,
  defines target behaviours, uncovers why those behaviours might not happen (don't know / don't want / can't),
  and brainstorms product-led mechanisms to resolve each barrier. Use this skill when the user mentions
  "situation behaviour", "sit/beh", "sit-beh", "target behaviour", "behaviour framework", wants to analyze
  user situations for a product feature, wants to identify behavioural barriers in their product, or is
  starting product/feature design work and needs to ground it in real-life situations rather than abstract
  personas. Also use when the user has a PRD or product description and wants to turn it into actionable
  design guidance, or when they want to understand why users might not exhibit desired behaviours in their
  product. This skill provides context that enriches other skills (brainstorming, feature-dev, etc.) —
  it never blocks them.
user-invocable: true
argument-hint: "[PRD or product description]"
---

# Situation/Behaviour Framework

Guide the user through a behavioural design framework that replaces abstract persona/segment thinking with concrete, real-life situations. The framework produces actionable product-led mechanisms that directly inform what to build and how.

## When this skill activates

Two modes:

1. **Framework filling mode** — the user wants to create or complete a Sit/Beh analysis for their product/feature
2. **PRD integration mode** — a PRD exists (likely from the prd-draft/prd-evaluate pipeline) and the sit-beh analysis should enrich it with behavioural mechanisms

Check for existing `.sitbeh/` directory in the project root. If framework documents exist there, read them and use them to enrich your work. If not, and the user wants to create one, proceed with filling mode.

## PRD integration mode

When this skill is invoked after prd-draft and prd-evaluate:

1. Read the PRD's "Real-world situations to address (sit-beh)" section
2. Take each situation and run the full framework analysis (Steps 1-4 below)
3. After completing the analysis, update the PRD:
   - Add new acceptance criteria derived from product-led mechanisms
   - Add new user stories for mechanisms that represent distinct functionality
   - Enrich the FAQ with behavioural insights
   - Update situational limitations in the sit-beh section
4. Save the framework to `.sitbeh/` for future reference

## Framework filling mode

### Step 0: Gather input

Accept whatever the user provides — a PRD, a product description, a conversation, or just a vague idea. If the input is thin, ask focused questions:

1. **What are you building?** (product initiative)
2. **What business outcome does success look like?** (business goal — measurable if possible)
3. **Who encounters this and when?** (situations — not personas, but real moments)

If the user provides a PRD or detailed description, extract answers yourself and confirm with the user before proceeding.

### Step 1: Identify situations

Situations are the heart of this framework. They replace personas with real moments. Each situation follows this structure:

> A **[type of person / person that...]** + **[activation moment: during/after/within... context]** + **[desired outcome: to Verb + specific goal]**

Generate 1-3 candidate situations. These should be genuinely different — different contexts, different motivations, different constraints. Not just "new user vs. returning user" but real-life moments.

Present them as a numbered list. Ask the user which situations are worth building scenarios for. They may edit, merge, add, or remove situations.

### Step 2: Build scenario for one situation

Take one situation at a time. For the selected situation, work through these elements in order:

#### 2a. Situational limitations
What significant constraints exist? Format: **[within / taking no more than / with / while / ...]** + **[specific limitation and its context]**

Think about: time pressure, lack of experience, competing priorities, emotional state, information overload, tool unfamiliarity.

#### 2b. Ideal behaviour actions
If you were a coach standing next to this person, what steps would you tell them to go through? Each action follows: **[Action verb]** + **[affected object(s)]** + **[object details]**

These should be concrete and sequential — a realistic chain of actions, not aspirational platitudes. Usually 2-7 actions unique to the situation.

#### 2c. Target behaviour statement
Merge everything into one statement (this is a reference artifact, not user-facing copy):

> **[Person]** + **[activation moment]** + **[desired outcome]** + **[behaviour actions joined by commas]** + **[situational limitations]**

#### 2d. Thinking about the situation
What might this person think when facing this situation? Focus on negative, doubtful, or avoidant thoughts — the internal monologue that could derail the target behaviour. Be specific and authentic.

#### 2e. Feelings about the situation
What emotions follow from those thoughts? These inform UX tone, messaging, and how aggressive or gentle the product experience should be.

### Step 3: Behaviour preconditions & product-led mechanisms

This is where the framework generates its highest value. For **each behaviour action** from step 2b, analyze three preconditions:

| Precondition | Question |
|---|---|
| **Don't know** | They don't know about the need or how to do this action. Why? |
| **Don't want** | They actively avoid or resist this action. Why? (Review thinking from 2d and go beyond it) |
| **Can't** | External barriers or skill gaps prevent them, given situational limitations. Why? |

For each precondition:
1. **Hypothetical reasons** — brainstorm 1-4 specific reasons this precondition might be true
2. **Product-led mechanisms** — for each reason, propose a concrete product/design mechanism that resolves it. These must be specific and implementable, not vague. "Add better UX" is not a mechanism. "Add a sidebar checklist visible only to the meeting owner that shows conflict resolution steps, with each step expandable to show example phrases" is.

### Step 4: Reinforce behaviour

Address two scenarios:

1. **Behaviour completed** — How does the product reinforce success? Think: sense of progress, benchmarks, impact highlighting, next-step suggestions.
2. **Behaviour incomplete / person drops off** — How does the product bring them back? Think: notifications, sticky reminders, blocking elements, re-engagement prompts.

### Step 5: Save and integrate

Save the completed framework to `.sitbeh/` in the project root:

```
.sitbeh/
  README.md           (brief explanation of what these files are)
  initiative.md       (product initiative + business goal)
  situations.md       (all identified situations)
  scenario-{name}.md  (one file per completed scenario, named descriptively)
```

If a PRD exists, also update it with findings:
- New acceptance criteria from product-led mechanisms → add to relevant user stories
- New user stories for mechanisms that are distinct features
- Enriched sit-beh section with full situation statements including limitations
- FAQ updates with behavioural insights

Tell the user: "The framework is saved in `.sitbeh/`. When you work on features in this project, I'll automatically reference it to inform design and implementation decisions."

## Important notes

- This framework is about **real situations, not personas**. If you catch yourself averaging or generalizing, stop and get more specific.
- Product-led mechanisms must be **concrete and implementable**. Not hand-wavy.
- The three preconditions (don't know / don't want / can't) are exhaustive by design. If a behaviour isn't happening, it's always one of these three. Don't skip any.
- Multiple situations may share some mechanisms — that's fine and expected. Note the overlaps.
- The user may want to do only one situation at a time. That's the intended workflow.
