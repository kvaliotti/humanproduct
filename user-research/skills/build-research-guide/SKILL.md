---
name: build-research-guide
description: >
  Build a structured research guide (interview script / discussion guide) from a research brief.
  Use this skill when the user says "create a research guide", "build an interview guide",
  "write a discussion guide", "interview script", "what should I ask in interviews",
  "create my interview questions", "build the guide from this brief", "turn this brief into a guide",
  "help me prepare for user interviews", "write the conversation guide", "research guide",
  "prepare for fieldwork", "I have a brief, now what", or provides a research brief and wants
  the next step — the tactical plan for what to say and ask during customer conversations.
  Also trigger when the user has just completed a research brief (via build-research-brief
  or evaluate-research-brief) and says "next step", "now build the guide", "ready for interviews",
  or otherwise signals they want to move from planning to fieldwork preparation.
  This skill covers guide creation only — it does not conduct analysis (that's a separate skill).
---

# Build Research Guide

Create a structured research guide (interview script / discussion guide) that translates a research brief into the actual questions, probes, and conversational tactics a researcher uses in the field. The guide is the tactical bridge between "what to learn" (brief) and "what to say" (conversation).

## Two Modes

### Mode A: Guided (interactive)
Use when the user provides a vague request ("help me prepare for interviews") or a partial brief. Walk them through the guide section by section, asking focused questions at each step.

### Mode B: Build from inputs
Use when the user provides a complete research brief (from skill 1/2 or pasted directly). Draft the full guide, then present it for review and refinement.

Default to Mode B when a research brief is available. In Mode A, batch related questions — never ask more than 3 questions per turn.

---

## Step 1: Locate the Brief

The guide depends on a research brief. Sources:

1. **Prior skill output** — brief was produced by build-research-brief or evaluate-research-brief in this session or a prior one. Check the workspace for recent brief files.
2. **File reference** — user points to a file
3. **Pasted in chat** — user pastes the brief text
4. **No brief available** — user wants to build a guide without a formal brief. Extract the equivalent inputs conversationally (research question, target users, research type, hypotheses). Warn that a brief-first approach produces sharper guides.

Read the brief fully before proceeding.

---

## Step 2: Detect the Research Type

Classify the research based on the brief's content. This determines which reference file to use as the primary methodology.

### Behavioral Research
The brief centers on **getting users to do (or stop doing) a specific action**. Signals:

- Target behavior specified (e.g., "After [context], user will [action]")
- COM-B decomposition or B=MAP decomposition present
- Adoption, activation, onboarding, engagement, retention, habit formation
- Behavior change framing
- Conversion actions

**Action:** Read `references/behavioral-guide.md`. This is your primary methodology. The guide must follow the B=MAP troubleshooting order (Prompt → Ability → Motivation) and systematically surface COM-B barriers. Still use general guide elements for opening, closing, and conversational tactics.

### General Research
The brief centers on **understanding users, validating problems, or informing decisions**. Signals:

- Discovery / exploration focus
- Market validation, willingness to pay
- Feature prioritization, product-market fit
- Customer segmentation
- Evaluative research (prototypes, concepts)

**Action:** Read `references/general-guide.md`. This is your primary methodology. Borrow behavioral elements (target behavior probes, COM-B screening) when the research touches on user actions, but keep them secondary.

### Mixed
The brief touches both — e.g., "understand why users churn AND design interventions."

**Action:** Read both reference files. Structure the guide with general discovery sections first, then behavioral deep-dive sections. Flag the dual nature to the user.

---

## Step 3: Extract Guide Parameters

From the brief (or through conversation in Mode A), determine:

| Parameter | Source in Brief | Why It Matters for the Guide |
|-----------|----------------|------------------------------|
| **Research question** | Section 1 | Anchors every question in the guide |
| **Interview type** | Section 7G (general) or inferred | Determines script template and opening |
| **Target segment** | Section 9 / 6G | Shapes language, framing, pedestal |
| **Core research questions** | Section 10 | Each must map to guide questions |
| **Hypotheses** | Section 2 / 8B | Questions must test these without leading |
| **COM-B components** | Section 6B (behavioral) | Each component needs probes |
| **B=MAP decomposition** | Section 6B (behavioral) | Drives troubleshooting order |
| **Duration** | Section 12 | Determines depth and section count |
| **Format** | Section 12 | In-person vs. remote affects tactics |

If any critical parameter is missing, ask the user — but never more than 3 questions at once.

---

## Step 3.5: Determine Output Scope

Before building, ask the user:

> "Should I create a **focused guide** — just the probes you'll actually use in the interview, with time boxes and dig triggers — or an **extended guide** that also includes COM-B coding columns, note-taking templates, brief-to-guide mapping, and the full phrase bank? Focused keeps the guide to something you can actually hold in your head during the conversation."

**Default to focused.** Only use extended when the user explicitly requests it or when they're training new interviewers who need the scaffolding.

### Focused Guide includes:
- Opening (VFWPA or equivalent)
- Core question sections with time boxes — **must-ask probes only** (bold)
- Compact dig triggers (4-5 lines, not a full table)
- Reaching for the Door
- Closing (referral ask + catch-all)
- Key conversational rules (top 3-4, not all 13)

### Extended Guide adds:
- Full Interviewer Notes section with complete phrase bank
- Optional probes (italicized) in every section
- COM-B coding column and B=MAP tags for real-time tagging
- Brief-to-Guide Mapping table
- Note-Taking Template
- Full 13 conversational rules

---

## Step 4: Build the Guide

Read the appropriate reference file(s) based on the research type detected in Step 2. Follow the methodology in the reference file to construct the guide.

The guide must:

1. **Map every core research question** from the brief to specific probes in the guide
2. **Test every hypothesis** from the brief — without revealing it to the participant
3. **Follow the correct structure** for the research type (see reference files)
4. **Include conversational tactics** — not just questions, but how to handle fluff, compliments, feature requests, and silence
5. **Time-box each section** — note target minutes per section based on total duration
6. **Mark must-ask vs. optional probes** — bold the probes that must be asked in every interview, italicize optional probes used when signals surface

### Research Type → Guide Structure

**General research** uses the reference file's template matched to interview type:
- Discovery → broad context → problem exploration → digging → commitment → closing
- Switch → previous solutions → point of struggle → decision process → closing
- Long-time customer → usage mapping → feature landscape → satisfaction → closing
- Cancellation → deal with disappointment → contributing factors → decision → closing
- Interactive / Usability → acclimation → first impressions → task scenarios → closing
- Card sort → acclimate → sort → probe gaps → closing

**Behavioral research** uses the B=MAP troubleshooting order:
- Routine mapping → Prompt exploration → Ability exploration → Motivation exploration → Competing behaviors → Synthesis → Closing

**Mixed research** combines both:
- General opening and context sections → Behavioral deep-dive sections → General closing

---

## Step 5: Quality Check

Before presenting, run the guide through these checks:

### Interview Realism Check (run first)
- [ ] **Probe count vs. time budget:** Count all must-ask probes. Divide available interview time (minus opening and closing) by probe count. If you get less than 2 minutes per probe, the guide is overstuffed — the interviewer will either rush through questions or skip half of them. Cut probes until you have 2-3 minutes per must-ask probe.
- [ ] **Core questions capped:** No more than 5-7 core research questions driving the guide. More than that means the brief is trying to learn too much in one study.
- [ ] **Section count:** Focused guides should have 4-6 sections (not counting opening/closing). If you have more, merge or cut sections that don't directly serve a research question.

### Every Guide Must Pass These
- [ ] Every question passes The Mom Test (about their life, not your idea; specifics in the past, not generics about the future)
- [ ] No questions ask "Would you...?", "Do you think...?", or "How much would you pay for...?"
- [ ] Every core research question from the brief has at least one probe in the guide (focused) or at least 2 probes (extended)
- [ ] Every hypothesis from the brief is testable through the guide — without being revealed
- [ ] Opening uses VFWPA framework (or equivalent from the reference) — not "Thanks for agreeing to this interview"
- [ ] "Reaching for the door" question included at the halfway mark
- [ ] Closing includes "Who else should I talk to?" and "Anything I should have asked?"
- [ ] Time allocations noted per section and sum to stated duration
- [ ] Dig triggers specified for emotion, feature requests, and generic claims
- [ ] Guide reads as probes and prompts, not a verbatim script to recite

### Behavioral Guides Must Also Pass These
- [ ] Guide follows Prompt → Ability → Motivation order (not starting with why)
- [ ] All 3 B=MAP components (Prompt, Ability, Motivation) have probes
- [ ] Ability Chain links (Time, Money, Physical effort, Mental energy, Routine fit) each have at least one probe
- [ ] Competing behaviors section included
- [ ] No "Why did/didn't you..." questions (invites rationalization) — use contextual reconstruction instead
- [ ] (Extended only) All 6 COM-B sub-components covered with at least 2 probes each
- [ ] (Extended only) COM-B coding column or tag system included for real-time tagging

### General Guides Must Also Pass These
- [ ] Interview type matches the research question and brief
- [ ] Question bank covers all relevant dimensions (process, frequency/pain, social, emotional)
- [ ] Commitment/advancement section appropriate to research stage
- [ ] If usability test: task scenarios written, prioritized, and don't reveal correct path

---

## Step 6: Save and Present

Save the complete guide as a markdown file to the user's workspace. Filename: `research-guide-[segment-or-topic].md`

After saving:

1. Present a summary: research type detected, interview type, section count, estimated duration, must-ask probe count, and time per probe
2. Highlight any realism check concerns (too many probes for the time, sections that don't serve a research question)
3. If you produced a focused guide, offer: "Want me to expand this into an extended guide with optional probes, coding systems, and note-taking templates?"
4. Offer: "Want me to adjust any section, add probes for a specific hypothesis, or adapt this for a different segment?"

---

## Output Format

Use the **focused** or **extended** template below, based on the scope chosen in Step 3.5.

### Focused Guide (default)

The focused guide is what the interviewer actually carries into the conversation. It should fit on 2-3 printed pages. No coding systems, no mapping tables — just the probes, time boxes, and enough scaffolding to stay on track.

```markdown
# Research Guide: [Segment / Topic]

**Research Type:** [Behavioral / General / Mixed]
**Interview Type:** [Discovery / Switch / etc.]
**Target Duration:** [X minutes]
**Must-ask probes:** [count] | **Time per probe:** [~X min]

---

## Key Rules (keep visible)
1. Stories, not opinions. "Tell me about the last time..."
2. Silence is a tool. Wait 3 beats after every question.
3. [1-2 more rules most relevant to this specific guide]

## Dig Triggers
- Emotion → "Tell me more about that."
- Feature request → "What would that let you do?"
- Generic claim → "When's the last time that happened?"
- "I'm just lazy" → redirect to ability: "Walk me through what would need to happen physically for you to do this."

---

## Opening (X min)
[VFWPA framing or equivalent — written in natural language]

## [Section 2 Title] (X min)
**Purpose:** [what this section answers — tied to a research question]

- **[Must-ask probe 1]**
- **[Must-ask probe 2]**

[Repeat for each section — must-ask probes only, 2-4 per section]

## Reaching for the Door (halfway mark)
"Thank you so much — I've learned a lot. Is there anything else you think I should know?"
[Wait. Do not prompt. At least 3 beats of silence.]

## Closing (X min)
- "Who else should I talk to?"
- "Is there anything else I should have asked?"
[Administrative wrap-up: incentive, consent confirmation, next steps]
```

### Extended Guide

Start with everything in the focused guide, then add these sections:

```markdown
## Guide at a Glance

| Section | Duration | Purpose | Brief Questions Covered |
|---------|----------|---------|------------------------|
| Opening | X min | ... | — |
| ... | ... | ... | Q1, Q3 |

## Full Interviewer Notes

### Conversational Rules (keep visible)
[Top 5-7 rules from the reference file, adapted to this specific guide]

### Phrase Bank (for when you panic)
[5-7 validating/redirecting phrases]

## Optional Probes (per section)

[For each section, add optional probes below the must-ask probes:]

*Optional probes (use when signals surface):*
- *[Probe 3]*
- *[Probe 4]*

## COM-B/B=MAP Coding (behavioral guides)

**COM-B/B=MAP mapping per section:** [which components each section covers]
**Coding key:** C-Ph | C-Ps | O-Ph | O-So | M-Re | M-Au
**B=MAP tags:** P | A-T | A-$ | A-PE | A-ME | A-RF | M-Per | M-Act | M-Ctx | CB

## Brief-to-Guide Mapping

| Brief Research Question | Guide Section(s) | Key Probes |
|------------------------|-------------------|------------|
| [Q1 from brief] | Section X | Probes X.1, X.3 |

## Note-Taking Template

[Section-by-section note-taking structure with space for annotations, emotion symbols, and — if behavioral — COM-B coding column]
```

---

## Rules

1. **The guide is scaffolding, not a cage.** Write probes and prompts, not a verbatim script. The researcher adapts in real time. The guide keeps them on track.

2. **Every question must earn its place.** If a probe doesn't serve a research question from the brief or test a hypothesis, cut it. Guide bloat produces shallow interviews.

3. **Start with behavior, not opinions.** "Walk me through the last time you [X]" always before "What do you think about [Y]." Ground in specifics before exploring attitudes.

4. **The Reaching for the Door question is non-negotiable.** Ask it at the halfway mark. The first half builds trust; the second half produces the deepest insights.

5. **Respect the brief's troubleshooting order.** If the brief specifies P → A → M order (behavioral), the guide must follow it. Don't let the researcher start with "why" questions.

6. **Adapt to interview type.** A discovery guide and a cancellation guide look fundamentally different even for the same product. Use the correct template from the reference file.

7. **Include the meta, not just the questions.** Interviewers need: time allocations, dig triggers, phrase banks, note-taking templates, and COM-B coding tags. A list of questions without these is a bad guide.

8. **Don't over-formalize.** If it feels like a survey, it'll produce survey-quality data. The guide should feel like a conversation plan, not a questionnaire.
