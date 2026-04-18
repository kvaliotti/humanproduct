---
name: prd-draft
description: >
  Turn messy product input into a structured PRD using a proven template. Use this skill when the user
  mentions "PRD", "product requirements", "product doc", "write a spec", "draft a PRD", wants to turn
  rough notes or ideas into a product document, has messy input they want structured into a feature spec,
  or says things like "here's what I'm thinking, turn it into a PRD". Also trigger when the user provides
  unstructured product thinking (bullet points, voice notes, Slack dumps, brainstorms) and wants it
  formalized. After drafting, this skill hands off to prd-evaluate for gap analysis.
user-invocable: true
argument-hint: "[messy input, rough notes, or product idea]"
---

# PRD Drafting Skill

Transform unstructured product thinking into a structured PRD. The goal is to preserve every meaningful detail from the user's input while organizing it into a format that engineering, design, and stakeholders can act on.

## When this skill activates

Two modes:

1. **From scratch** — user provides messy input (notes, ideas, Slack dumps, voice transcripts, bullet points) and wants a PRD
2. **Refinement** — user already has a partial PRD and wants it completed or restructured into the template

## Step 1: Absorb the input

Read everything the user provides. Do not ask clarifying questions yet. First, extract and organize what's already there:

- **Problem signals** — what pain, frustration, or missed opportunity is described?
- **Solution signals** — any features, flows, or mechanisms mentioned?
- **User/persona signals** — who is affected? In what real-world moments?
- **Constraints** — anything explicitly out of scope, time-bound, or blocked?
- **Success signals** — any metrics, goals, or definitions of "done"?

Create a mental map of what's present and what's missing before proceeding.

## Step 2: Ask targeted gap-filling questions

Only ask about what's genuinely missing — not what can be reasonably inferred. Group questions into one message, max 5 questions. Focus on:

1. **Problem clarity** — if the problem statement is vague or missing
2. **Who and when** — if situations/users aren't concrete enough for sit-beh format
3. **Success measurement** — if there's no way to know whether this worked
4. **Hard constraints** — technical, timeline, or scope constraints not mentioned

Do not ask about things you can draft and have the user validate. Drafting is faster than interviewing.

## Step 3: Draft the PRD

Use the exact template structure below. Fill every section with content from the user's input. Where the input is thin, make your best inference and mark it with `[INFERRED — please validate]` so the user can confirm or correct.

Read the PRD template from `references/prd-template.md` and populate it.

Key principles for each section:

### Problem section
Keep it to 1-3 sentences. State the problem, who has it, and why it matters now. Do not pad with context the reader already knows.

### Success measurement
Only include if the user provided or implied metrics. Do not fabricate metrics. If no metrics are available, write: "To be defined after solution validation." This is honest and avoids fake precision.

### Real-world situations (sit-beh format)
This is the most important section. Convert whatever user/persona information exists into concrete situation statements:

> **[activation moment]** + **[type of person]** + **wants to [desire]** + **[precise limitation]**

Each situation should be a real moment in time, not a persona description. If the user's input doesn't have enough specificity, draft 2-3 candidate situations based on what you can infer and mark them for validation.

### User flows & diagrams
Include a Mermaid diagram if the flow has more than 3 steps or involves branching logic. For simple linear flows, a numbered list is sufficient.

### Key features (user stories)
Write as user stories with acceptance criteria. Each story should map to one or more situations from the sit-beh section. Number them (US-1, US-2, etc.) with acceptance criteria (AC-1, AC-2, etc.).

Acceptance criteria should be specific and testable — not "works correctly" but "displays confirmation toast within 500ms of submission, including the appointment date and provider name."

### Out of Scope
If the user mentioned constraints, list them. If not, infer reasonable scope boundaries based on the problem statement and mark them as `[INFERRED]`.

### FAQ
Populate with questions that came up during your analysis of the input. These are questions a reasonable engineer or designer would ask. Provide your best answers.

## Step 4: Present and iterate

Present the full PRD. Then explicitly say:

> "This PRD is ready for gap analysis. Say **'evaluate'** and I'll run the prd-evaluate skill to find missing use cases, edge cases, and UI/UX gaps. Or edit the PRD first if anything needs correction."

## Output format

Save the PRD to `PRD-[feature-name].md` in the current working directory. Use kebab-case for the filename. Also display it in the conversation for immediate review.

## Chaining with other skills

After the user approves the draft (or asks to proceed):
1. **prd-evaluate** — runs gap analysis on the PRD, finds missing use cases and edge cases
2. **sit-beh** — runs full behavioural analysis on the situations, generating product-led mechanisms
3. PRD gets updated after each step

This is a sequential pipeline. Each skill enriches the PRD.
