---
name: evaluate-research-guide
description: Evaluate and stress-test a user research guide (interview script, discussion guide) before it goes to field. Use this skill when the user says "evaluate my research guide", "review my interview script", "check my discussion guide", "stress-test my guide", "is my research guide ready", "evaluate this interview guide", "review my interview questions", "audit my research guide", "are my interview questions good", "check my guide before fieldwork", "critique my discussion guide", "score my research guide", or provides a research/interview guide and wants structured feedback, gap analysis, a score, or a go/no-go verdict. Also trigger when the user has just finished building a research guide (via build-research-guide or otherwise) and wants it evaluated before going to field. This skill evaluates the guide — it does not create or rewrite it (that's a separate skill).
---

# Evaluate Research Guide

Perform a structured evaluation of a research guide (interview script, discussion guide) before fieldwork begins. A guide can have well-structured questions and still produce bad data — this evaluation catches the subtle ways a guide invites compliments, fluff, false positives, or misses systematic behavioral coverage.

---

## Step 1: Obtain the Guide and Brief

Before evaluating, you need two inputs:

1. **The research guide** to evaluate (required)
2. **The research brief** that the guide was built from (strongly recommended)

If the user provides only the guide, ask whether a brief exists. If it does, request it — evaluating alignment between brief and guide is a core check. If no brief exists, note this as a gap and proceed with the guide alone.

---

## Step 2: Detect the Research Type

Classify the research based on the guide's content and stated goals. This determines which evaluation criteria to emphasize.

### Behavioral Research
The guide centers on **understanding why users do or don't perform a specific action**. Signals:

- Questions about adoption, activation, onboarding completion
- Engagement, retention, habit formation, feature usage
- Behavior change ("why aren't users doing X", "what prevents Y")
- Questions structured around barriers, triggers, routines, ability
- Churn prevention framed as behavior ("users stop logging in after week 2")
- Conversion actions (signup → first value, trial → paid)

**Action:** Read `references/behavioral-evaluation.md`. This is your primary evaluation framework. Still apply core quality checks from the general reference (Mom Test compliance, question quality, dig triggers).

### General Research
The guide centers on **understanding users, validating problems, or informing decisions**. Signals:

- Discovery / exploration questions
- Market validation, willingness to pay, competitive understanding
- Feature prioritization, product-market fit
- Customer segmentation, persona building
- Evaluative research (testing prototypes, concepts, usability)
- Switch interviews, cancellation interviews, long-time customer interviews

**Action:** Read `references/general-evaluation.md`. This is your primary evaluation framework. Borrow behavioral evaluation elements when guide questions touch on user actions or habits, but keep them secondary.

### Mixed
Some guides touch both. Example: a discovery guide that includes a section on why users aren't completing onboarding. The discovery part is general; the onboarding section is behavioral.

**Action:** Read both reference files. Lead with whichever matches the guide's primary focus. Evaluate behavioral sections with the behavioral framework and general sections with the general framework. Flag the dual nature in your output.

---

## Step 3: Evaluate

Run the guide through the evaluation criteria from the relevant reference file(s). For each section, assign a score and provide specific evidence — quote the problematic question, name the missing element, point to the structural gap.

### Universal Checks (Apply to ALL Guides Regardless of Type)

These checks apply whether the research is behavioral, general, or mixed. Run them first.

#### U1. Mom Test Compliance
Run every question through the Mom Test filter. Flag any question that:
- Asks for opinions, predictions, or approval instead of past behavior and facts
- Leads the witness toward a preferred answer
- Could produce compliments or fluff as valid responses
- Begins with "Would you ever...", "Could you see yourself...", "Do you think you..."

#### U2. Question Quality Baseline
- All questions open-ended (not yes/no)
- All questions ask about past/current behavior, not future predictions
- No jargon unless the participant demonstrably uses it
- No loaded or leading language
- Questions use softeners and conversational tone

#### U3. Structure Basics
- Opening establishes context without revealing product/idea
- Questions progress from broad to specific
- Closing includes referral ask and open-ended catch-all
- Guide is organized as flexible probe points, not a rigid script

#### U4. Dig Triggers and Follow-Up
- Guide includes prompts for when emotional signals appear
- Guide includes prompts for when feature requests appear
- Guide includes prompts for when vague/generic answers appear
- Follow-up phrase bank available (mirror, summarize, silence, "tell me more")

#### U5. Brief Alignment (If Brief Available)
- Every research question from the brief has a corresponding probe in the guide
- Guide investigates what the brief specified — no scope creep
- Guide is written for the participant segment defined in the brief

### Behavioral-Specific Checks (When Behavioral Detected)

From `references/behavioral-evaluation.md`:

- **Structural alignment:** COM-B sequence (C → O → M) or B=MAP sequence (P → A → M)
- **COM-B coverage:** All 6 components have adequate probes with balanced distribution
- **B=MAP component quality:** Prompt questions (anchors, types, failure), Ability questions (all 5 chain links, discovery/breakthrough), Motivation questions (PAC sources, competing, conflicting, durability)
- **TDF drill-down readiness:** Drill-down probes available with decision rules
- **Anti-patterns:** Opinion vs. behavior ratio (<30% threshold), attribution bias traps, component coverage balance
- **Probe quality (Section G):** Open-ended not closed, specific instances not generalities, no "why" as primary probe, no leading questions, no jargon/framework language, probes not scripts
- **Methodological safeguards:** Social desirability mitigation, self-report validation, coding system, pilot plan
- **Behavioral specificity of outputs:** Can you fill in COM-B assessment? Ability Chain? Action Line placement? Fogg-format recipe?

### General-Specific Checks (When General Detected)

From `references/general-evaluation.md`:

- **Seven core questions coverage** (Deploy Empathy)
- **Three-dimensional probing:** Functional, Emotional, Social
- **Reaching for the Door placement:** "Is there anything else you think I should know?" must be at the halfway mark, not the end; second half left open for follow-up
- **Interview type match:** Discovery, Switch, Long-time customer, Cancellation, Interactive, Card sort
- **Commitment and advancement:** Appropriate for research stage (discovery = facts, validation = commitment ask, sales = advancement step)
- **Usability test tasks** (if applicable): Scenario framing, realism, metrics
- **Bias prevention:** Sponsor concealed, neutral language, practice session planned
- **Documentation and capture plan:** Notetaker, template, recording, time-coding, between-session protocol
- **Debugging preparedness:** Contingency plans for common scenarios (no-show, short interview, nervous/cagey/angry participant, feature request takeover, expected onboarding, off-topic tangent)
- **Contextual inquiry readiness** (if applicable): Observation protocol, travel logistics, environment documentation, summary/verification step
- **Guide usability:** Scannable, fits on a few pages, printable

### Relevance Audit (Apply to ALL Guides)

The checks above assess whether the guide is well-constructed. This audit checks whether everything in the guide **earns its place** given the available interview time and the research questions it needs to answer.

For each probe in the guide, ask:

1. **Which research question does this probe serve?** If you can't name one, the probe is dead weight. Cut it.
2. **If you got a perfect answer to this probe, would it change what you recommend?** If not, it's interesting but not necessary.
3. **Is this probe doing work that another probe already does?** Redundant probes waste minutes you don't have.

For each section in the guide, ask:

4. **If you cut this entire section, would you still answer the core research questions?** If yes, the section is optional at best.
5. **Is the time allocated to this section proportional to the importance of the research questions it serves?** Don't spend 15 minutes on a secondary question and 5 minutes on the primary one.

**What to flag:**

| Signal | Verdict | Action |
|--------|---------|--------|
| Probe directly serves a core research question | Keep | — |
| Probe is methodologically sound but doesn't serve any research question | Cut | Recommend removing — it steals time from probes that matter |
| Section covers a COM-B component with no hypothesized barrier | Demote to optional | Only spend time on components where there's reason to suspect an issue |
| Guide has more probes than the interview can realistically cover (< 2 min/probe) | Trim | Recommend cutting lowest-relevance probes until time budget works |
| Extensive scaffolding (coding systems, templates) for a simple study | Recommend focused format | The guide's weight should match the research's weight |

**Output for each flagged item:**
- **Probe/section:** [quote the probe or name the section]
- **Research question served:** [which one — or "none"]
- **Recommendation:** Keep / Cut / Make optional / Merge
- **Time recovered:** [estimated minutes freed up]

---

## Step 4: Score

### Scoring Approach

Use two scoring systems depending on the research type detected.

#### For General Research

Rate each dimension PASS / NEEDS WORK / FAIL:

| Dimension | Score |
|---|---|
| Mom Test Compliance | |
| Structure (Opening / Body / Closing) | |
| Question Quality (Core coverage, 3D probing, behavior vs. prediction) | |
| Dig Triggers and Follow-Up Readiness | |
| Bias Prevention | |
| Interview Type Match | |
| Documentation and Capture Plan | |
| Debugging Preparedness | |
| Guide Usability | |
| Brief Alignment | |

**Verdict:** APPROVED / REVISE / REJECT

Any FAIL requires rework before fieldwork.

#### For Behavioral Research

Rate each section on a 4-point scale (4 = fully met, 3 = minor gaps, 2 = significant gaps, 1 = not met):

| Section | Max | Score |
|---|---|---|
| A. Structural Alignment | 20 | |
| B. COM-B Coverage | 28 | |
| C. B=MAP Component Quality (Prompt + Ability + Motivation) | 19 | |
| D. TDF Drill-Down Readiness | 12 | |
| E. Anti-Pattern Detection | 12 | |
| F. Methodological Safeguards | 16 | |
| G. Probe Quality | 24 | |
| H. Brief Alignment | 12 | |
| I. Behavioral Specificity of Outputs | 24 | |

**Thresholds:**
- 90%+ → **Field-ready** — minor polish only
- 75-89% → **Revise probes** — gaps fixable in one pass
- 50-74% → **Restructure** — systematic holes in coverage or quality
- <50% → **Rebuild** — guide is not behaviorally structured

#### For Mixed Research

Score the behavioral sections with the behavioral scorecard and general sections with the general scorecard. Present both, then give a combined verdict.

---

## Step 5: Output

Produce a markdown file with this structure:

```
# Research Guide Evaluation: [Guide Title or Topic]

Date: [Date]
Research Type: [Behavioral / General / Mixed]
Guide evaluated: [filename or description]
Brief evaluated against: [filename or "No brief provided"]

## Verdict: [APPROVED / REVISE / RESTRUCTURE / REBUILD]

[1-2 sentence summary of the verdict and the single most important issue]

## Scorecard

[Appropriate scorecard based on research type]

## Critical Issues (Fix Before Fieldwork)

[Numbered list of FAIL items with specific evidence — quote the problematic question, name the missing element]

## Improvements (Would Strengthen the Guide)

[Numbered list of NEEDS WORK items with specific recommendations]

## Strengths

[What the guide does well — specific, not generic praise]

## Relevance Audit

[For each probe/section that doesn't earn its place:]

| Probe/Section | Research Question Served | Recommendation | Time Recovered |
|---|---|---|---|

**Time budget:** [Total must-ask probes] probes × [available minutes] = [min/probe]. [Pass/Fail — need ≥ 2 min/probe]

---

## Question-Level Annotations

[For each flagged question: quote it, state the problem, provide a rewritten alternative]

## Quick Litmus Test Results

1. If I ran this guide with my mom, could she lie to me? [Yes/No + evidence]
2. If the conversation went perfectly, would I learn facts or collect compliments? [Facts/Compliments + evidence]
3. If I got an unexpected answer, would I know what to do next? [Yes/No + evidence]
4. Could someone leave thinking I was just interested in their life? [Yes/No + evidence]
```

---

## Presenting the Evaluation

Save the evaluation as a markdown file to the user's workspace. After presenting:

1. Highlight the 1-3 changes that would have the biggest impact on data quality
2. **Present the relevance audit** — if probes don't serve a research question or the time budget doesn't work, say so directly: "You have X probes for a Y-minute interview — that's Z minutes per probe. Cut these N probes that don't serve your core questions to get to a realistic pace."
3. If REVISE or worse, offer to walk through the fixes for the critical issues
4. If behavioral guide has component imbalance, name which component is under-covered and why it matters
5. Flag if the guide scope doesn't match the brief scope

If the guide is a focused guide (no coding systems, no note-taking template, no brief-to-guide mapping), evaluate it on its focused scope — these sections are intentionally omitted to keep the guide usable in the interview. Only flag their absence if the research context genuinely requires them (e.g., training new interviewers, multi-site studies needing consistent coding).

Do not over-explain. The evaluation should stand on its own. A short paragraph on the highest-leverage fixes is enough.
