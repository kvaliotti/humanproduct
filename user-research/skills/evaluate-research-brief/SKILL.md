---
name: evaluate-research-brief
description: Evaluate and stress-test a user research brief before fieldwork begins. Use this skill when the user says "evaluate my research brief", "review my brief", "is my brief good", "stress-test my research plan", "critique my brief", "score my research brief", "check my brief", "gap analysis on my brief", "rate my brief", "what's wrong with my brief", "audit my research plan", provides a research brief and asks for feedback or quality assessment, or has just completed a research brief (via build-research-brief or otherwise) and wants it evaluated before starting fieldwork. This skill catches the failure modes that produce worthless conversations — before you waste time in the field.
---

# Evaluate Research Brief

Run a structured, scored evaluation of a research brief. Produces a per-criterion scorecard, gap analysis with specific evidence, anti-pattern detection, and a revised brief addressing user-selected gaps.

---

## Step 0: Locate the Brief

The user must provide a research brief to evaluate. Sources:

1. **Pasted in chat** — user pastes the brief text directly
2. **File reference** — user points to a file in the workspace
3. **Just completed skill 1** — brief was output by build-research-brief in a prior turn or session

If no brief is provided, ask: "Which research brief should I evaluate? You can paste it here, point me to a file, or I can look for one in your workspace."

Do not proceed without a brief.

---

## Step 1: Detect the Research Type

Before reading reference files or scoring anything, classify the research based on the brief's content. This determines which evaluation criteria to weight and which reference to use as primary.

### Behavioral Research
The brief centers on **getting users to do (or stop doing) a specific action**. Signals in the brief:

- Target behavior specified (or attempted)
- Adoption, activation, onboarding, engagement, retention, habit formation, feature usage
- Behavior change framing ("users aren't doing X", "how to get users to Y")
- Churn framed as behavior ("users stop logging in after week 2")
- Conversion actions (signup → first value, trial → paid)
- COM-B or B=MAP decomposition present (or should be)

**Action:** Read `references/behavioral-evaluation.md`. This is your primary evaluation framework. Still evaluate general criteria (logistics, ethics, recruitment) from `references/general-evaluation.md`, but weight behavioral criteria highest.

### General Research
The brief centers on **understanding users, validating problems, or informing decisions**. Signals:

- Discovery / exploration focus
- Market validation, willingness to pay, competitive understanding
- Feature prioritization, product-market fit assessment
- Customer segmentation, persona building
- "Why are users churning?" framed as understanding, not behavior change
- Evaluative research (testing prototypes, concepts)

**Action:** Read `references/general-evaluation.md`. This is your primary evaluation framework. Behavioral criteria (COM-B, B=MAP) are informational — note if they'd strengthen the brief, but don't penalize their absence.

### Mixed
The brief touches both — e.g., "understand why users churn AND design interventions to retain them."

**Action:** Read both reference files. Evaluate against both frameworks. Flag the dual nature. Weight each framework proportionally to its presence in the brief.

---

## Step 2: Run the Evaluation

### Evaluation Structure

Run three passes over the brief:

#### Pass 1: Fatal Flaws (stop/continue gate)

Check for issues that invalidate the entire brief. If any are present, flag them immediately — the rest of the evaluation is conditional on fixing these.

**Universal fatal flaws:**
- No research question at all, or question is unfalsifiable
- No connection between research and any business decision ("What will you do differently based on findings?" has no answer)
- Participant definition is absent or completely unfiltered ("users")

**Behavioral fatal flaws (if behavioral/mixed):**
- Problem stated as attitude, feeling, or metric instead of behavior
- Target behavior is not observable (purely internal state)
- Target behavior is actually an aspiration or outcome ("increase engagement")

If fatal flaws found → report them, skip to Step 4 with verdict REWRITE.

#### Pass 2: Criterion-by-Criterion Scoring

Score each applicable criterion. Use the scoring scales from the reference files.

**For General briefs, score these criteria:**

| # | Criterion | Score | Weight |
|---|---|---|---|
| G1 | Research Question Sharpness | /3 | 12% |
| G2 | Big 3 Questions Quality | /3 | 10% |
| G3 | Segment & Participant Definition | /3 | 12% |
| G4 | Risk Map Quality | /3 | 8% |
| G5 | Beliefs & Hypotheses | /3 | 8% |
| G6 | Interview Type & Approach Fit | /3 | 8% |
| G7 | Core Questions Coverage | /3 | 10% |
| G8 | Logistics Viability | /3 | 6% |
| G9 | Incentive Appropriateness | /3 | 3% |
| G10 | Roles & Accountability | /3 | 5% |
| G11 | Bias Controls | /3 | 5% |
| G12 | Analysis Plan | /3 | 5% |
| G13 | Success Criteria & Commitments | /3 | 5% |
| G14 | Ethical Soundness | /3 | 3% |

Scoring: 1 = FAIL, 2 = NEEDS WORK, 3 = PASS

**For Behavioral briefs, score these criteria:**

| # | Criterion | Score | Weight |
|---|---|---|---|
| B1 | Behavioral Problem Definition | /4 | 15% |
| B2 | Target Behavior Selection | /4 | 10% |
| B3 | Behavioral Specification | /4 | 15% |
| B4 | COM-B Coverage | /4 | 20% |
| B5 | B=MAP Decomposition | /4 | 15% |
| B6 | Research Design Alignment | /4 | 15% |
| B7 | Methods & Actionability | /4 | 10% |

Scoring: 1 = Not met (fundamental issue), 2 = Partially met (significant gaps), 3 = Mostly met (minor refinement), 4 = Fully met

**Plus universal criteria (scored for all briefs):**

| # | Criterion | Score |
|---|---|---|
| U1 | Logistics Viability | /3 |
| U2 | Roles & Accountability | /3 |
| U3 | Bias Controls | /3 |
| U4 | Analysis Plan | /3 |
| U5 | Success Criteria | /3 |
| U6 | Ethical Soundness | /3 |

**For Mixed briefs:** Score both General and Behavioral criteria. Use General weights for understanding-oriented sections, Behavioral weights for action-oriented sections.

#### Pass 3: Anti-Pattern Detection

Scan the brief for known failure patterns. Each detected pattern gets flagged with:
- **Pattern name**
- **Evidence** — specific quote or section from the brief
- **Why it's dangerous** — what will go wrong in fieldwork
- **Fix** — concrete rewrite suggestion

Anti-patterns to check (pull the full list from the relevant reference file):
- Comfort questions / no scary question
- Premature zoom
- Validation seeking
- Unfindable segment
- Missing stakeholders
- All market risk, no product risk
- Motivation Trap (behavioral)
- Aspiration Masquerade (behavioral)
- Monolithic User (behavioral)
- Missing Prompt (behavioral)
- Undifferentiated Difficulty (behavioral)
- COM-B tourism (behavioral)
- Motivation monopoly (behavioral)
- Solution baked in (behavioral)

#### Pass 4: Relevance Audit

The previous passes check whether the brief is well-constructed. This pass checks whether everything in the brief **earns its place** given the stated research question and the decision it informs.

For each section in the brief, ask:

1. **Does this section change what you'd ask in interviews?** If removing the section wouldn't change a single probe in the guide, it's overhead — recommend cutting it.
2. **Does this section change who you'd recruit?** If not, it's context for the researcher's head, not the brief.
3. **Does this section inform the decision stated in Section 1?** If the decision wouldn't change regardless of what this section reveals, it's tangential.

**What to flag:**

| Signal | Verdict | Action |
|--------|---------|--------|
| Section directly serves a core research question | Keep | — |
| Section is methodologically complete but doesn't serve any research question | Cut or demote | Recommend removing from the brief or moving to an appendix |
| Research question doesn't connect to the stated decision | Cut the question | If learning the answer wouldn't change the decision, it's curiosity, not research |
| Hypothesis isn't falsifiable through the planned methods | Cut or redesign | Either change the method or drop the hypothesis |
| COM-B component has no corresponding research question (behavioral) | Flag as speculative | Only include components where you have reason to suspect a barrier |
| Full extended sections included but research is simple (5 casual interviews, one segment) | Recommend focused format | The brief's weight should match the research's weight |

**Output for each flagged item:**
- **Section/element:** [what you're questioning]
- **Relevance to research question:** [how it connects — or doesn't]
- **Recommendation:** Keep / Cut / Merge into another section / Move to appendix
- **Rationale:** [one sentence — why this doesn't earn its place]

---

## Step 3: Produce the Evaluation Report

### Output Structure

Save a markdown file to the user's workspace with this structure:

```
# Research Brief Evaluation

**Brief evaluated:** [title or filename]
**Research type detected:** [Behavioral / General / Mixed]
**Date:** [date]
**Verdict:** [APPROVED / REVISE / MAJOR REWORK / REWRITE]

---

## Fatal Flaw Check

[PASS or list of fatal flaws with evidence]

---

## Scorecard

[Table with all scored criteria, per-criterion score, weight, evidence, and notes]

### Weighted Score: [X / 100]

| Score Range | Verdict |
|---|---|
| 85-100 | APPROVED — minor polish only |
| 70-84 | REVISE — address gaps before fieldwork |
| 50-69 | MAJOR REWORK — structural issues |
| <50 | REWRITE — brief is not research-ready |

---

## Gap Analysis

### Critical Gaps (must fix before fieldwork)
[Numbered list — each with: criterion, what's missing, specific evidence from the brief, concrete fix]

### Important Gaps (should fix)
[Same structure]

### Minor Gaps (nice to fix)
[Same structure]

---

## Anti-Patterns Detected

| Pattern | Evidence | Risk | Fix |
|---|---|---|---|

---

## Relevance Audit

[For each section/element that doesn't earn its place:]

| Section/Element | Serves Research Question? | Recommendation | Rationale |
|---|---|---|---|

**Brief weight vs. research weight:** [Is the brief's complexity proportional to the research? Flag if a 15-page brief is being written for 5 casual interviews.]

---

## Strengths

[What the brief does well — be specific. Researchers need positive signal too.]

---

## Recommendations

[Prioritized list of 3-5 highest-impact changes, ordered by effort-to-impact ratio]

---

## Mom Test Check

[Specific assessment of whether the brief's questions pass The Mom Test:
- Which questions could your mom lie to you about?
- Which questions fish for validation?
- Which questions ask about hypothetical future behavior instead of past/current?
- Which questions invite compliments?]
```

---

## Step 4: Present Results and Offer Next Steps

After saving the evaluation report:

1. Present the verdict and weighted score
2. Show the scorecard as a table
3. Highlight the top 3 critical gaps with concrete fixes
4. List detected anti-patterns
5. **Present the relevance audit** — if any sections don't earn their place, say so directly: "Sections X and Y don't serve your research question — I'd recommend cutting them to keep the brief focused."
6. Note strengths

Then offer:
- "Want me to produce a revised brief addressing the [N] critical gaps and cutting the [N] flagged sections?"
- "Want to drill into any specific criterion?"
- "Want me to rewrite specific sections?"

If the user selects gaps to fix, produce a revised version of those sections only — don't rewrite what's already strong.

---

## Scoring Calculation

### General Brief Score
```
Weighted Score = Σ (criterion_score / max_score × weight × 100)
```
Where max_score = 3 for all general criteria.

### Behavioral Brief Score
```
Weighted Score = Σ (behavioral_criterion_score / 4 × behavioral_weight × 100)
                + Σ (universal_criterion_score / 3 × universal_weight_remainder × 100)
```
Universal criteria share the remaining weight after behavioral criteria (split evenly among 6 universal criteria from the leftover).

For behavioral briefs, behavioral criteria account for 100% of the behavioral score. Universal criteria are reported separately as a logistics/process readiness check but do not affect the behavioral score. Present both:
- **Behavioral Rigor Score:** [X/100] — the primary score
- **Process Readiness Score:** [X/18] — logistics, roles, bias, analysis, success criteria, ethics

### Mixed Brief Score
Weight behavioral and general scores proportionally based on the brief's emphasis. State the weighting used.

---

## Rules

1. **Evidence over opinion.** Every score must cite a specific passage, section, or absence in the brief. "This section is weak" is not acceptable. "Section 4 lists 'users' as the target without behavioral criteria, screening method, or channel" is.

2. **Calibrate severity to research type.** A missing COM-B decomposition is a critical gap for a behavioral brief but merely a suggestion for a general discovery brief. A missing "Big 3 Questions" is critical for general but less relevant for behavioral.

3. **Challenge source signals.** When the brief cites evidence ("users told us", "survey showed"), apply Mom Test filters: Is this what users did or what they said? Is this demand or enthusiasm? Is this an opinion or a fact?

4. **Don't inflate.** If the brief is bad, say so. A researcher who goes to the field with a broken brief wastes everyone's time — theirs, the participants', and the team's. Being kind here means being direct.

5. **Don't evaluate what isn't there.** If the brief is a rough draft missing logistics, don't FAIL it on logistics — note it as "not yet addressed" and focus scoring on what's present. Distinguish between "wrong" and "not yet written." If the brief is a focused brief (no logistics, roles, timeline, or detailed decompositions), evaluate it on its focused scope — these sections are intentionally omitted to keep the brief actionable. Only flag their absence if the research context genuinely requires them.

6. **Preserve the researcher's intent.** The goal is to strengthen the brief, not to impose a different research question. If the researcher's question is valid but poorly structured, fix the structure. Don't substitute your question.

7. **Flag when the brief is solving the wrong problem.** If the brief investigates a behavior but the real issue is product-market fit, or vice versa — say so. This is the highest-value feedback you can give.
