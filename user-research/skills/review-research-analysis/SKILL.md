---
name: review-research-analysis
description: Evaluate and stress-test a completed research analysis before the team acts on its findings. Use this skill when the user says "review my analysis", "evaluate my research analysis", "is my analysis good", "stress-test my findings", "critique my research", "score my analysis", "check my analysis", "audit my research findings", "rate my analysis", "are my conclusions solid", "review the interview analysis", "evaluate findings", provides a research analysis and asks for feedback or quality assessment, or has just completed an analysis (via interview-analysis or otherwise) and wants it reviewed before making product decisions. Also trigger when the user says "next step" after completing interview analysis. This skill catches analytical failures — cherry-picked validation, false positives, wrong behavioral diagnoses, missing dimensions — before the team acts on flawed conclusions.
---

# Review Research Analysis

Run a structured, scored evaluation of a research analysis. Produces a per-criterion scorecard, gap analysis with specific evidence, failure pattern detection, and a revised analysis addressing user-selected gaps.

---

## Step 0: Locate the Analysis and Raw Data

The user must provide the research analysis to evaluate. Sources:

1. **Pasted in chat** — user pastes the analysis text directly
2. **File reference** — user points to a file in the workspace
3. **Just completed skill 5** — analysis was output by interview-analysis in a prior turn or session

If no analysis is provided, ask: "Which research analysis should I evaluate? You can paste it here, point me to a file, or I can look for one in your workspace."

Also request the raw data the analysis was based on:
- Interview transcripts or notes
- Research brief (if available)
- Research guide (if available)

Raw data is essential for verifying whether the analysis faithfully represents what participants said. Without it, the evaluation is limited to internal consistency checks — flag this limitation prominently if raw data is unavailable.

Do not proceed without at least the analysis itself.

---

## Step 1: Detect the Research Type

Before reading reference files or scoring anything, classify the research based on the analysis content. This determines which evaluation framework to use.

### Behavioral Research

The analysis centers on **getting users to do (or stop doing) a specific action**. Signals:

- Target behavior identified (or attempted)
- Adoption, activation, onboarding, engagement, retention, habit formation, feature usage
- Behavior change framing ("users aren't doing X", "how to get users to Y")
- COM-B decomposition present (or should be)
- B=MAP coding, Ability Chain assessment, prompt/anchor analysis
- Intervention functions or Tiny Habit recipes proposed
- Barriers coded to specific behavioral components

**Action:** Read `references/behavioral-evaluation.md`. This is your primary evaluation framework. Still check general criteria (evidence quality, bias, actionability) from `references/general-evaluation.md`, but weight behavioral criteria highest.

### General Research

The analysis centers on **understanding users, validating problems, or informing decisions**. Signals:

- Discovery / exploration findings
- Market validation, willingness to pay, competitive understanding
- Feature prioritization, product-market fit assessment
- Customer segmentation, persona building
- Pain × frequency prioritization
- Commitment ladder or earlyvangelist identification
- "Why are users churning?" framed as understanding, not behavior change

**Action:** Read `references/general-evaluation.md`. This is your primary evaluation framework. Behavioral criteria (COM-B, B=MAP) are informational — note if they'd strengthen the analysis, but don't penalize their absence.

### Mixed

The analysis touches both — e.g., "understanding why users churn AND diagnosing behavioral barriers to retention."

**Action:** Read both reference files. Evaluate against both frameworks. Flag the dual nature. Weight each framework proportionally to its presence in the analysis.

---

## Step 2: Run the Evaluation

### Evaluation Structure

Run four passes over the analysis:

#### Pass 1: Fatal Flaws (stop/continue gate)

Check for issues that invalidate the entire analysis. If any are present, flag them immediately — the rest of the evaluation is conditional.

**Universal fatal flaws:**
- No evidence at all — conclusions are opinions without participant data
- Fewer than 5 interviews and the analysis draws firm conclusions
- Analysis is entirely based on what people said they'd do, with zero evidence of what they actually did
- Analyst's interpretation indistinguishable from participant quotes throughout

**Behavioral fatal flaws (if behavioral/mixed):**
- No COM-B or B=MAP decomposition — findings presented as themes without behavioral coding
- Target behavior never specified — analysis discusses attitudes and feelings, not actions
- Motivation diagnosed as primary bottleneck without evidence that prompt and ability were checked first

**General fatal flaws (if general/mixed):**
- No findings at all — just raw data dump without synthesis
- All findings are compliments and future-tense promises with zero behavioral evidence or commitments
- No prioritization — all findings presented as equally important

If fatal flaws found → report them, skip to Step 4 with verdict REJECT or MAJOR REWORK.

#### Pass 2: Criterion-by-Criterion Scoring

Score each applicable criterion using the scoring scales from the reference files.

**For General analyses, score these criteria:**

| # | Criterion | Score | Weight |
|---|---|---|---|
| G1 | Sample Sufficiency & Convergence | /3 | 7% |
| G2 | Core Questions Answered | /3 | 7% |
| G3 | Data Quality (facts vs. fluff) | /3 | 8% |
| G4 | False Positive Risk | /3 | 8% |
| G5 | Process Integrity | /3 | 4% |
| G6 | Data Extraction Quality | /3 | 5% |
| G7 | Three-Dimensional Analysis | /3 | 7% |
| G8 | Pain & Frequency Assessment | /3 | 7% |
| G9 | Pattern Quality | /3 | 5% |
| G10 | Segment Consistency | /3 | 7% |
| G11 | Evidence Quality (quote backing) | /3 | 9% |
| G12 | Commitment Evidence | /3 | 5% |
| G13 | Belief Updates | /3 | 4% |
| G14 | VUVF Filter Applied | /3 | 4% |
| G15 | Bias & Balance | /3 | 4% |
| G16 | Actionability | /3 | 9% |
| G17 | Decision Readiness | /3 | 5% |

Scoring: 1 = Unreliable/Fail, 2 = Partially reliable/Needs Work, 3 = Trustworthy/Pass

**Conditional general criteria** (score only when in scope — redistribute weights proportionally when included):
- Commitment Ladder Audit (G12) — when validation/demand testing was the purpose
- WTP Signals — when pricing/WTP was in scope
- Process Diagram Quality — when process mapping was in scope
- Output Artifacts Quality (personas, mental models, scenarios) — when these artifacts were produced
- Earlyvangelist Identification — when finding early adopters was the goal
- Reporting Quality — when a deliverable report was produced

**For Behavioral analyses, score these criteria:**

Primary Score (Behavioral Rigor):

| # | Criterion | Score | Weight |
|---|---|---|---|
| B1 | Diagnostic Accuracy — right bottleneck identified | /5 | 30% |
| B2 | Coding Rigor — correct classification | /5 | 20% |
| B3 | Pattern Validity — defensible patterns and segments | /5 | 20% |
| B4 | Intervention Validity — recommendations match diagnosis | /5 | 20% |
| B5 | Completeness — all B=MAP/COM-B dimensions covered | /5 | 10% |

Secondary Score (Process & Evidence):

| Section | Max Score |
|---|---|
| COM-B Completeness (5 criteria × /4) | 20 |
| Evidence Quality (6 criteria × /4) | 24 |
| Analytical Rigour (6 criteria × /4) | 24 |
| Prioritisation (4 criteria × /4) | 16 |
| Traceability (3 criteria × /4) | 12 |
| **TOTAL** | **96** |

**For Mixed analyses:** Score both General and Behavioral criteria. Weight each framework proportionally based on the analysis emphasis. State the weighting used.

#### Pass 3: Raw Data Cross-Check

If raw data (transcripts, notes) is available, perform a sample verification:

1. **Quote verification** — select 5-8 key findings and trace them back to the raw data. Does the quote exist? Is it presented in context? Does the analysis interpretation match what the participant said?

2. **Missing signal detection** — scan raw data for signals the analysis didn't capture:
   - Strong emotional language not reflected in findings
   - Disconfirming evidence absent from conclusions
   - Patterns visible in transcripts but missing from analysis
   - Commitment levels or behavioral evidence not noted

3. **Attribution audit** (behavioral only) — for 3-5 coded data points, verify the COM-B/B=MAP classification is defensible from the raw transcript.

If raw data is unavailable, note this limitation and explain that the evaluation is restricted to internal consistency. This is a significant constraint — flag it prominently.

#### Pass 4: Failure Pattern Detection

Scan the analysis for known failure patterns. Each detected pattern gets flagged with:
- **Pattern name**
- **Evidence** — specific quote or section from the analysis
- **Why it's dangerous** — what will go wrong in product decisions
- **Fix** — concrete revision suggestion

**General failure patterns to check:**
- Pitch deck disguised as analysis
- Theme soup without prioritization
- Solo analyst syndrome
- Zombie leads counted as demand
- Functional-only analysis
- Feature request laundering
- Prevalence-free claims
- Equal-weight findings
- Compliments counted as validation
- Leading questions producing expected answers

**Behavioral failure patterns to check:**
- The Motivation Mirage (>50% of barriers coded as motivation)
- The Theme Trap (themes instead of COM-B codes)
- The Observation Gap (all ability assessments from self-report)
- The Singleton Discard (unique insights dropped)
- The Recipe Vacuum (no Tiny Habit recipes constructable)
- Self-report laundering
- Solution smuggling
- Island barriers (no system view)
- Missing automatic motivation
- Attribution bias (self-blame accepted without investigation)

#### Pass 5: Relevance Audit

The previous passes check whether the analysis is well-constructed. This pass checks whether every finding and recommendation **earns its place** given the research question and the decision it was supposed to inform.

For each finding in the analysis, ask:

1. **Does this finding inform the decision stated in the research brief?** If the team wouldn't do anything differently knowing this, it's trivia — interesting but not actionable.
2. **Is the "so what" specific enough to act on?** "Users struggle with onboarding" is a theme, not a finding. If you can't name what the team should do differently because of this finding, it hasn't earned its place.
3. **Does the evidence behind this finding actually support the conclusion?** A finding backed by 1 self-report quote and 6 compliments is noise dressed as signal.

For each recommendation in the analysis, ask:

4. **Does this recommendation follow from a finding, or is it the analyst's opinion?** Recommendations should be traceable to findings. If you can't point to the finding that produced this recommendation, it's speculation.
5. **Is this recommendation within the team's control and scope?** "Change the company culture" is not actionable. "Add a prompt at the end of the standup workflow" is.

For the analysis as a whole, ask:

6. **Did the analysis actually answer the research question?** Sometimes an analysis produces 10 interesting findings but never addresses the core question. Flag this directly.
7. **Is the analysis proportional to the research?** A 20-page analysis for 5 interviews is probably padding. A focused analysis (executive summary, key findings, next steps) may be all that's warranted.

**What to flag:**

| Signal | Verdict | Action |
|--------|---------|--------|
| Finding directly informs the stated decision | Keep | — |
| Finding is interesting but tangential to the research question | Cut or demote to appendix | Note it exists but don't let it compete for attention with primary findings |
| Finding has weak evidence (1-2 self-reports) presented with high confidence | Downgrade or cut | Either lower the confidence or remove if it doesn't survive the downgrade |
| Recommendation doesn't trace to a finding | Cut | Analyst opinion belongs in conversation, not in the deliverable |
| Analysis has 8+ findings | Flag over-inclusion | Recommend prioritizing to 3-5. If everything is important, nothing is. |
| Extensive behavioral decomposition for a simple discovery study | Flag over-engineering | The analysis framework should match the research type and complexity |

**Output for each flagged item:**
- **Finding/recommendation:** [quote the headline]
- **Research question served:** [which one — or "none"]
- **Recommendation:** Keep / Cut / Demote to appendix / Merge with another finding
- **Rationale:** [one sentence]

---

## Step 3: Produce the Evaluation Report

### Output Structure

Save a markdown file to the user's workspace with this structure:

```
# Research Analysis Evaluation

**Analysis evaluated:** [title or filename]
**Research type detected:** [Behavioral / General / Mixed]
**Raw data available:** [Yes — transcripts/notes provided / No — internal consistency only]
**Date:** [date]
**Verdict:** [APPROVED / REVISE / MAJOR REWORK / REJECT]

---

## Fatal Flaw Check

[PASS or list of fatal flaws with evidence]

---

## Scorecard

[Table with all scored criteria, per-criterion score, weight, evidence, and notes]

### Overall Score

**General Analysis:** Weighted Score: [X / 100]
**Behavioral Analysis:** Primary (Rigor): [X / 5.0] | Secondary (Process): [X / 96]
**Mixed:** Both scores with stated weighting

| Score Range (General) | Verdict |
|---|---|
| 85-100 | APPROVED — act on findings |
| 70-84 | REVISE — address gaps before decisions |
| 50-69 | MAJOR REWORK — structural issues |
| <50 | REJECT — cannot trust for decisions |

| Score Range (Behavioral Primary) | Verdict |
|---|---|
| 4.0-5.0 | APPROVED — diagnostically sound |
| 3.0-3.9 | REVISE — verify bottleneck identification |
| 2.0-2.9 | MAJOR REWORK — recoding likely needed |
| <2.0 | REJECT — thematic summaries, not diagnoses |

---

## Raw Data Cross-Check

[If raw data was available:]
### Quote Verification
[5-8 findings checked against source, with pass/fail and notes]

### Missing Signals
[Signals found in raw data but absent from analysis]

### Attribution Audit (behavioral only)
[3-5 coded data points verified against transcript]

[If raw data was NOT available:]
⚠️ This evaluation is limited to internal consistency. No raw data was provided to verify
that the analysis faithfully represents participant input. This means the evaluation cannot
detect cherry-picked quotes, misattributed statements, or missing signals. Confidence in
the scores is reduced accordingly.

---

## Gap Analysis

### Critical Gaps (must fix before acting on findings)
[Numbered list — each with: criterion, what's missing, specific evidence, concrete fix]

### Important Gaps (should fix)
[Same structure]

### Minor Gaps (nice to fix)
[Same structure]

---

## Failure Patterns Detected

| Pattern | Evidence | Risk | Fix |
|---|---|---|---|

---

## Relevance Audit

**Did the analysis answer the research question?** [Yes / Partially / No — with evidence]

[For each finding/recommendation that doesn't earn its place:]

| Finding/Recommendation | Research Question Served | Recommendation | Rationale |
|---|---|---|---|

**Analysis weight vs. research weight:** [Is the analysis proportional to the data? Flag if a 20-page decomposition was produced from 5 interviews.]
**Finding count:** [N findings. If >5, flag over-inclusion — recommend prioritizing.]

---

## Strengths

[What the analysis does well — be specific. Researchers need positive signal too.]

---

## Recommendations

[Prioritized list of 3-5 highest-impact changes, ordered by effort-to-impact ratio]

---

## Mom Test Check

[Specific assessment of whether the analysis's evidence base passes Mom Test filters:
- Which findings are based on what people did vs. what they said they'd do?
- Which findings are compliments or fluff dressed as evidence?
- Which conclusions rely on enthusiasm rather than commitment?
- Is there evidence of commitment at any level (time, reputation, money)?]

---

## The Ultimate Question

> Based on this analysis, is the team making decisions based on **what people did**
> or **what people said they'd do**?

[Direct answer with evidence]
```

---

## Step 4: Present Results and Offer Next Steps

After saving the evaluation report:

1. Present the verdict and score(s)
2. Show the scorecard as a table
3. Highlight the top 3 critical gaps with concrete fixes
4. List detected failure patterns
5. **Present the relevance audit** — if findings don't serve the research question or recommendations don't trace to findings, say so directly: "Findings X and Y are interesting but don't inform the decision you set out to make. I'd recommend cutting them and leading with Finding Z, which directly answers your research question."
6. Note strengths
7. If raw data was unavailable, state the confidence limitation

Then offer:
- "Want me to produce a revised analysis addressing the [N] critical gaps and cutting the [N] tangential findings?"
- "Want to drill into any specific criterion?"
- "Want me to rewrite specific sections?"
- "Want me to do a deeper cross-check against the raw data?" (if raw data is available but you did a light pass)

If the user selects gaps to fix, produce revised versions of those sections only — don't rewrite what's already strong.

---

## Scoring Calculations

### General Analysis Score
```
Weighted Score = Σ (criterion_score / 3 × weight × 100)
```

### Behavioral Analysis Score

**Primary (Rigor):**
```
Weighted Score = Σ (test_score × weight)
```
Result is on a 0-5 scale.

**Secondary (Process & Evidence):**
```
Score = Σ (section_scores)
```
Result is on a 0-96 scale. Convert to percentage for threshold comparison.

### Mixed Analysis Score
Weight behavioral and general scores proportionally based on the analysis emphasis. State the weighting used. Report both component scores and the blended verdict.

---

## Rules

1. **Evidence over opinion.** Every score must cite a specific passage, quote, or absence in the analysis. "This section is weak" is not acceptable. "Section 4 claims high demand but the only evidence is 3 compliments and zero commitments" is.

2. **Calibrate severity to research type.** A missing COM-B decomposition is a critical gap for a behavioral analysis but merely a suggestion for a general discovery analysis. A missing commitment ladder is critical for validation research but irrelevant for exploratory.

3. **Challenge source signals.** When the analysis cites evidence, apply Mom Test filters: Is this what users did or what they said? Is this demand or enthusiasm? Is this an opinion or a fact? Are you confusing compliments for commitment?

4. **Verify against raw data when available.** The most valuable thing this evaluation can do is catch where the analysis diverges from what participants actually said. Always perform the raw data cross-check when transcripts/notes are provided.

5. **Don't inflate.** If the analysis is bad, say so. A team that acts on flawed analysis wastes engineering resources, misses the real problem, and loses time they can't get back. Being kind here means being direct.

6. **Don't evaluate what isn't there.** If the analysis is a first draft missing certain sections, note "not yet addressed" and focus scoring on what's present. Distinguish between "wrong" and "not yet written."

7. **Preserve the researcher's intent.** The goal is to strengthen the analysis, not impose a different interpretation. If the researcher's conclusions are valid but poorly evidenced, fix the evidence chain. Don't substitute your conclusions.

8. **Flag when the analysis is answering the wrong question.** If the analysis investigates behavior but the real issue is product-market fit, or the analysis maps pain points but the real need was behavioral diagnosis — say so. This is the highest-value feedback you can give.

9. **Behavioral trumps attitudinal.** When evaluating evidence quality, always weight behavioral evidence (what people did) above self-report (what people said) above opinion (what people think). Flag when the analysis treats these as equivalent.

10. **Check the system, not just the parts.** For behavioral analyses, verify that the analysis identifies feedback loops, upstream causes, and compensatory relationships between components — not just isolated barriers. For general analyses, verify that findings connect to each other and to the broader user context, not just stand as independent observations.
