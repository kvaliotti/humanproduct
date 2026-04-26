---
name: build-research-brief
description: Build a structured user research brief from a business problem, product question, or behavioral challenge. Use this skill when the user says "create a research brief", "plan my research", "I need to do user research", "research brief", "set up a study", "I want to interview users", "help me scope research", "figure out what to ask users", "research plan", "discovery brief", "I need to understand why users aren't doing X", "how to research this problem", "interview planning", or provides a product/business problem and wants a structured research plan before talking to users. Also trigger when the user mentions user interviews, customer interviews, usability studies, discovery research, or behavioral research in the context of planning or scoping. This skill covers the planning phase — it produces the brief, not the interview guide (that's a separate skill).
---

# Build Research Brief

Create a structured research brief that defines what to learn, from whom, and why — before any fieldwork begins. The brief is the foundation every downstream research artifact depends on: guide, analysis, and review.

## Two Modes

### Mode A: Guided (interactive)
Use when the user provides a vague or partial problem ("I want to do user research on X", "we need to understand why Y"). Walk them through the brief section by section, asking focused questions at each step.

### Mode B: Build from inputs
Use when the user provides substantial context (problem description, hypotheses, goals, target users, constraints). Draft the full brief, then present it for review and refinement.

Default to Mode A unless the user's input already covers 3+ sections of the brief template. In Mode A, batch related questions — never ask more than 3 questions per turn.

---

## Step 1: Detect the Research Type

Before reading reference files or drafting anything, classify the research based on what the user describes. This determines which methodology to emphasize.

### Behavioral Research
The user's problem centers on **getting users to do (or stop doing) a specific action**. Signals:

- Adoption, activation, onboarding completion
- Engagement, retention, habit formation, feature usage
- Behavior change ("users aren't doing X", "how to get users to Y")
- Churn prevention framed as behavior ("users stop logging in after week 2")
- Conversion actions (signup → first value, trial → paid)

**Action:** Read `references/behavioral-approach.md`. This is your primary methodology. Still use general approach elements for logistics, participants, and recruitment.

### General Research
The user's problem centers on **understanding users, validating problems, or informing decisions**. Signals:

- Discovery / exploration ("what do users need?", "is this a real problem?")
- Market validation, willingness to pay, competitive understanding
- Feature prioritization, product-market fit assessment
- Customer segmentation, persona building
- "Why are users churning?" (framed as understanding, not behavior change)
- Evaluative research (testing prototypes, concepts)

**Action:** Read `references/general-approach.md`. This is your primary methodology. Borrow behavioral elements (target behavior specification, COM-B or B=MAP decomposition) when the research touches on user actions, but keep them secondary.

### Mixed
Some briefs touch both. Example: "We want to understand why users churn and design interventions to retain them." The understanding part is general; the intervention design is behavioral.

**Action:** Read both reference files. Lead with whichever matches the user's primary intent. Flag the dual nature to the user.

---

## Step 2: Gather Inputs

Whether guided or building from inputs, collect these before drafting:

### Universal Inputs (always needed)

| Input | What to ask | Why it matters |
|-------|-------------|----------------|
| **Business context** | What product/feature? What stage (pre-launch, growth, mature)? | Frames the entire brief |
| **The problem** | What's happening (or not happening) that triggered this research? | The brief's reason to exist |
| **The decision** | What will you do differently based on findings? | If no decision changes, the research isn't needed |
| **What you already know** | Existing data, hypotheses, assumptions, prior research | Prevents re-learning known things |
| **Constraints** | Timeline, budget, team capacity, access to users | Shapes scope and methods |

### Behavioral Inputs (when behavioral research detected)

| Input | What to ask |
|-------|-------------|
| **Target behavior** | What specific action should users perform? (Not an aspiration — an observable action at a specific moment) |
| **Current state** | Are users doing it partially, not at all, or inconsistently? |
| **Hypothesized barrier** | What do you think is preventing the behavior? |
| **Metrics** | How do you currently measure this behavior? |

### General Inputs (when general research detected)

| Input | What to ask |
|-------|-------------|
| **Current beliefs** | What's your hypothesis about the customer, their problem, and your solution? |
| **Scariest assumption** | What assumption, if wrong, would sink this? |
| **Target users** | Who specifically are you trying to learn from? (Not "users" — a specific segment) |
| **Prior attempts** | What have you already tried or built? What happened? |

### Apply The Mom Test Filter

At every input-gathering step, challenge the user's framing:

- Is this what users **actually do** or what they **say they'd do**?
- Are you looking for validation or genuinely seeking disconfirming data?
- Would an unexpected answer change your plans? If not, the question isn't worth researching.
- Are "positive signals" from users actually compliments disguised as demand?

---

## Step 3: Draft the Brief

### Output Structure

Produce a markdown document following this structure. Include all Universal sections. Include Behavioral or General sections based on the detected research type. Include both if mixed.

```
# Research Brief: [Title]
Date: [Date]
Owner: [Name/Team]
Research Type: [Behavioral / General / Mixed]

## 1. Research Question
[One specific question tied to a business decision]
Decision this informs: [What changes based on findings]

## 2. Background & Current Beliefs
[Business context, what's known, what's been tried]
Hypotheses to test:
- [Hypothesis 1]
- [Hypothesis 2]

## 3. Risk Map
[What goes wrong if assumptions are wrong — ranked by severity]
Elephant in the room: [The question being avoided]

--- BEHAVIORAL SECTIONS (include when behavioral) ---

## 4B. Target Behavior Specification
Behavior statement: "After [CONTEXT], the user will [SPECIFIC ACTION]."
- Who: [specific segment]
- What: [observable action]
- When: [timing/trigger]
- Where: [context/setting]
- How often: [frequency needed]
- With whom: [social context]

Aspiration this serves: [higher-level goal]

## 5B. Behavior Selection Rationale
(If multiple candidate behaviors were considered)
| Behavior | Impact | Likelihood | Spillover | Measurability | Total |
|----------|--------|------------|-----------|---------------|-------|

## 6B. Behavioral Decomposition

### COM-B Analysis
| Component | Sub-component | Hypothesis | Research Question |
|-----------|---------------|------------|-------------------|
| Capability | Physical | | |
| Capability | Psychological | | |
| Opportunity | Physical | | |
| Opportunity | Social | | |
| Motivation | Reflective | | |
| Motivation | Automatic | | |

### B=MAP Analysis
**Motivation:** Primary source (Person/Action/Context), competing motivations, durability
**Ability:** Weakest chain link (Time/Money/Physical/Mental/Routine), Discovery Question hypothesis
**Prompt:** Current type (Person/Context/Action/None), candidate anchors, trailing edge

### Action Line Position: [Above / Below / No prompt]
### Troubleshooting Priority: Prompt → Ability → Motivation

## 7B. Competing Behaviors
| Competing Behavior | Why it persists (driver) | Research implication |
|--------------------|-------------------------|----------------------|

## 8B. Testable Hypotheses
- "We believe [BEHAVIOR] is not happening because [component] is insufficient. Specifically, [hypothesis]. We will test this by [method]."

--- GENERAL SECTIONS (include when general) ---

## 4G. Big 3 Questions
1. [Scary question that could reshape the business]
2. [Murkiest unknown about customer behavior]
3. [Question about willingness to pay/commit]

## 5G. Research Type Classification
[ ] Generative/Exploratory — "What's up with...?"
[ ] Descriptive/Explanatory — "What and how?"
[ ] Evaluative — "Are we getting close?"
[ ] Causal — "Why is this happening?"

## 6G. Customer Segment
- Who: [specific sub-group defined by behavior, not just demographics]
- Where to find them: [channels, communities, lists]
- Existing behavior: [what they do today instead]
- Selection criteria: Profitable? Reachable? Rewarding?

## 7G. Interview Type
[Discovery / Switch / Long-time customer / Cancellation / Interactive / Card sort]
Rationale: [why this type fits]

--- UNIVERSAL SECTIONS (always include) ---

## 9. Participants
- Segment definition: [behavioral criteria, not just demographics]
- Sample size: [5-15, with rationale]
- Recruitment channels: [where and how]
- Screening criteria: [behavior-first screening]
- Incentive: [type and amount]
- Diversity considerations: [demographics, accessibility, org context]

## 10. Core Research Questions
[Numbered list — each tied to a specific section of the brief]

## 11. Methods & Data Sources
| Question/Component | Method | Rationale |
|--------------------|--------|-----------|

## 12. Logistics
- Format: [audio-only / screen share / in-person]
- Duration: [minutes]
- Interviews per day: [max 2]
- Recording: [tool + consent process]
- Note capture: [method]

## 13. Roles
| Role | Owner |
|------|-------|
| Point Person | |
| Interviewer | |
| Notetaker | |
| Recruiter | |
| Analyst(s) | |

## 14. Ethics & Bias Acknowledgment
Known biases: [design, sampling, interviewer, sponsor, social desirability]
Mitigation: [specific actions]
Consent: [process]

## 15. Analysis Approach
[Journey map / Pain-frequency matrix / COM-B mapping / Team review]

## 16. Success Criteria
[What "done" looks like — specific, falsifiable]

## 17. Timeline
- Desk research: [dates]
- Recruiting: [dates]
- Fieldwork: [dates]
- Analysis: [dates]
- Report: [date]

## 18. Commitments & Next Steps
- Early stage: [facts needed]
- Mid stage: [commitments to push for]
- Post-research: [decision/action plan]
```

---

## Step 4: Review & Stress-Test

After drafting, run the brief through these checks before presenting:

### Quality Checks
- [ ] Problem stated as observable behavior or falsifiable question, not vague aspiration
- [ ] Every research question has the power to change a decision
- [ ] At least one question is uncomfortable to ask (Mom Test)
- [ ] Participants defined by behavior, not just demographics
- [ ] Brief distinguishes what users DO from what they SAY
- [ ] No leading questions that assume the answer
- [ ] Success criteria are specific enough to know when you're done
- [ ] If behavioral: target behavior passes the "can you do it right now?" test
- [ ] If behavioral: COM-B covers all 6 sub-components OR B=MAP covers all 3 components
- [ ] If behavioral: troubleshooting order is P → A → M (not starting with motivation)
- [ ] Desk research items identified (don't waste interview time on Google-able questions)

### Anti-Patterns to Flag
| Anti-Pattern | Signal | Fix |
|-------------|--------|-----|
| Validation-seeking | All questions expect positive answers | Add disconfirming questions |
| Aspiration masquerading as behavior | "Increase engagement" as target | Specify the exact action at a specific moment |
| Motivation-first assumption | Brief assumes users don't want to do it | Check prompt and ability first |
| Too-broad segment | "Users" or "small businesses" | Slice until you have a who-where pair |
| No scary questions | Everything feels safe and comfortable | Add the elephant in the room |
| Scope creep | 15+ research questions | Cut to what changes decisions |

---

## Presenting the Brief

Give the user the complete brief as a markdown file saved to their workspace. After presenting:

1. Ask which sections feel weakest or most uncertain
2. Offer to stress-test specific hypotheses
3. Note what desk research should happen before fieldwork
4. Flag if the brief scope is too ambitious for their stated constraints

Do not over-explain. The brief should stand on its own. A short paragraph on what you flagged during the quality check is enough.
