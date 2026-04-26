# Behavioral Research Analysis Evaluation Reference

Synthesized from COM-B / Behaviour Change Wheel (Michie et al.) and B=MAP / Tiny Habits (Fogg).

Use this reference when evaluating analysis of research aimed at driving, changing, or sustaining a specific user behavior — adoption, activation, engagement, retention, habit formation, feature usage, onboarding completion, conversion actions, churn reduction framed as behavior change.

---

## Table of Contents

1. [COM-B Structural Completeness](#section-a-com-b-structural-completeness)
2. [Evidence Quality](#section-b-evidence-quality)
3. [Analytical Rigour](#section-c-analytical-rigour)
4. [Diagnostic Accuracy (B=MAP)](#section-d-diagnostic-accuracy)
5. [Coding Rigor](#section-e-coding-rigor)
6. [Pattern Validity](#section-f-pattern-validity)
7. [Prioritisation Quality](#section-g-prioritisation-quality)
8. [Intervention Linkage](#section-h-intervention-linkage)
9. [Completeness](#section-i-completeness)
10. [Traceability](#section-j-traceability)
11. [Scoring System](#scoring-system)
12. [Common Failure Patterns](#common-failure-patterns)
13. [Meta-Evaluation: Process Check](#meta-evaluation-process-check)

---

## Section A: COM-B Structural Completeness

| # | Criterion | What to check |
|---|---|---|
| A1 | **All 6 sub-components addressed** | Does the analysis explicitly address Physical Capability, Psychological Capability, Physical Opportunity, Social Opportunity, Reflective Motivation, and Automatic Motivation — even if to say "no barrier found"? |
| A2 | **No collapsed components** | Are Physical and Psychological Capability treated separately? Are Reflective and Automatic Motivation treated separately? Collapsing to 3 components (C, O, M) loses diagnostic power. |
| A3 | **TDF depth where needed** | For COM-B components with identified barriers, does the analysis drill into specific TDF domains (e.g., not just "Psychological Capability barrier" but "Knowledge gap + Memory/Attention failure")? |
| A4 | **Enablers identified** | Does the analysis note what's already working (COM-B enablers), not just barriers? Enablers are leverage points and must-protect elements. |
| A5 | **Competing behaviours mapped** | Are competing behaviours (what users do instead) identified and diagnosed with their own COM-B drivers? |

**Red flag:** If A1 fails, the analysis has systematic blind spots — findings cannot be trusted as a complete diagnosis.

---

## Section B: Evidence Quality

| # | Criterion | What to check |
|---|---|---|
| B1 | **Evidence tagged by type** | Is each piece of evidence tagged as [B] Behavioural, [SR] Self-report, or [O] Observed? |
| B2 | **Prevalence reported** | For each barrier, does the analysis report how many participants out of total showed it? "Several users said…" is not prevalence. "6 of 8 participants…" is. |
| B3 | **Evidence strength rated** | Is each barrier rated as Strong, Moderate, or Weak evidence using explicit criteria? |
| B4 | **Self-report not treated as fact** | Where findings rely on self-report [SR], is this acknowledged? Are there attempts to triangulate with behavioural [B] or observational [O] data? |
| B5 | **Disconfirming evidence included** | For each barrier, does the analysis note contradictory data or participants who did NOT show this barrier? |
| B6 | **Quotes in context** | Are participant quotes presented with enough surrounding context to verify the coding? |

**Red flag:** If B4 fails and the majority of findings are [SR], the analysis may reflect what participants think they do, not what they actually do.

---

## Section C: Analytical Rigour

| # | Criterion | What to check |
|---|---|---|
| C1 | **Behaviour is the unit of analysis** | Are findings framed as behavioural barriers ("users don't complete step 3 because…") or as attitudinal observations ("users feel frustrated")? Attitudes are inputs to COM-B coding, not findings. |
| C2 | **COM-B coding is defensible** | For each coded barrier, could a second analyst read the evidence and arrive at the same COM-B component? |
| C3 | **Motivation not over-attributed** | Is there evidence that Motivation barriers are genuinely motivational, or might they be Capability or Opportunity barriers in disguise? ("I don't want to" often means "I can't figure it out" or "The environment makes it too hard.") |
| C4 | **Specificity of "what needs to change"** | Are the "what needs to change" statements specific and actionable? "Users need more motivation" = useless. "Users need to see that completing the checklist reduces their error rate by 40%" = actionable. |
| C5 | **No causal leaps** | Does the analysis distinguish correlation from causation? "Users who skip onboarding have lower retention" is correlation. Adding causal claims needs evidence for each link. |
| C6 | **System dynamics considered** | Does the analysis identify feedback loops, delays, or reinforcing cycles — not just isolated barriers? |

---

## Section D: Diagnostic Accuracy (B=MAP)

**The most consequential error in behavioral analysis: misidentifying the bottleneck.**

| Misdiagnosis | What It Looks Like | Consequence | How to Detect |
|---|---|---|---|
| **Motivation diagnosed when Prompt is the issue** | "Users aren't motivated enough to check the dashboard" | Team builds motivational features while users have no trigger | Did the analysis test whether a prompt exists before concluding motivation? |
| **Motivation diagnosed when Ability is the issue** | "Users don't value the feature enough" | Team builds awareness campaigns while UX remains too complex | Did the analysis assess all 5 Ability Chain links before concluding motivation? |
| **Ability diagnosed when Prompt is the issue** | "The workflow is too complex" | Team simplifies but users still never encounter it | Did users who found it "easy" still fail to do it? If yes, it's prompt. |
| **Single component when multiple are failing** | "We just need to add a notification" | Prompt fixed but M or A still insufficient | Did the analysis test the compensatory relationship? |

**Verification method:** For each segment's diagnosis:

1. "If we fixed ONLY this component, would the behavior happen?" If probably not → additional components bottlenecked.
2. "Did the analysis follow the troubleshooting order (P → A → M)?" If motivation diagnosed first without ruling out prompt and ability → diagnosis is suspect.

---

## Section E: Coding Rigor

### Sample Audit

Pull 10-15 coded data points at random. For each, verify:

| Check | Pass | Fail |
|---|---|---|
| Quote is behavioral (specific action), not attitudinal (opinion) | "Last week I opened the app after standup" | "I think the app is useful" |
| Code matches the component the quote describes | "I forget to do it" → P-MISSING | "I forget to do it" → M-LOW (misclassified) |
| Self-attribution corrected when evidence contradicts it | User says "I'm lazy" but transcript shows broken Ability Chain → recoded to A-[specific link] | "I'm lazy" coded as M-LOW without ability investigation |
| Competing behaviors coded as motivation, not ability | "I check email instead" → M-COMPETING | "I check email instead" → A-ROUTINE (wrong) |
| Bright spots coded with full B=MAP profile | Successful behavior has P, A, and M codes | Only motivation of successful users captured |

**Threshold:** If >20% of sampled codes are misclassified, the analysis needs recoding.

### Attribution Correction Audit

| Check | Pass | Fail |
|---|---|---|
| Every "I'm lazy/undisciplined" statement was investigated | Analyst checked for prompt and ability issues before accepting motivation diagnosis | Self-blame accepted at face value |
| Motivation attributions have behavioral corroboration | "User says they're not motivated. Behavioral evidence: tried 3 times last week → recoded to ability" | "Not motivated" coded as M-LOW with no further investigation |
| "I don't have time" was tested for actual time constraint vs. priority competition | Distinguished "literally don't have 5 minutes" (A-TIME) from "spend that time elsewhere" (M-COMPETING) | All "no time" coded as A-TIME without testing |

**This is the most common analysis failure.** Participants self-diagnose as motivation-deficient when the actual issue is ability or prompt. If the analysis doesn't correct for this, it will systematically overweight motivation as a bottleneck.

---

## Section F: Pattern Validity

### Frequency Evidence

| Check | Pass | Fail |
|---|---|---|
| Patterns supported by participant counts | "4 of 6 participants showed P-MISSING" | "Many users struggle with prompts" (no count) |
| Minority patterns preserved as singletons | "1 participant showed a unique workaround: [detail]" | Outlier insights discarded |
| Bottleneck distribution adds up | Segments account for all participants | Some participants don't fit any segment |
| Component heatmap populated | Ability Chain shows ratings across all participants | Ability Chain assessed for some participants only |

### Segment Quality

| Check | Pass | Fail |
|---|---|---|
| Segments defined by B=MAP profile, not demographics | "Motivated-but-blocked" (high M, low A, prompt exists) | "Young users" vs. "Old users" |
| Each segment has distinct B=MAP configuration | Segments differ on which component is bottleneck | All segments same diagnosis — why segment? |
| Segments are actionable | Each implies a different intervention | Segments descriptive but don't point to different solutions |
| Bright spot segment identified and fully profiled | Successful users' exact B=MAP configuration documented | Only failure patterns analyzed |

### Bright Spot Utilization

| Check | Pass | Fail |
|---|---|---|
| Successful users' B=MAP configuration is the design template | "Successful users have this anchor, this ability setup, this motivation source" | Bright spots mentioned but not structurally analyzed |
| Gap between bright spots and struggling segments characterized | "Successful users differ from struggling on [specific component]" | No comparison between successful and struggling |
| Bright spot configuration tested for transferability | "Could this anchor work for the struggling segment?" | Assumed to transfer without checking |

---

## Section G: Prioritisation Quality

| # | Criterion | What to check |
|---|---|---|
| G1 | **Prioritisation criteria explicit** | Are barriers ranked using explicit criteria (Prevalence, Severity, Addressability, Upstream position), or is the ranking intuitive/unstated? |
| G2 | **Priority 1 barriers justified** | For each top-priority barrier, is the case made with data — not just "this seemed most important"? |
| G3 | **Upstream barriers identified** | Does the analysis identify root-cause barriers whose resolution would cascade to fix downstream barriers? |
| G4 | **Low-priority barriers documented** | Are deprioritised barriers documented for future sprints/research, or do they disappear? |

---

## Section H: Intervention Linkage

| # | Criterion | What to check |
|---|---|---|
| H1 | **Barriers linked to intervention functions** | For each prioritised barrier, are candidate intervention functions identified (Education, Training, Persuasion, Environmental Restructuring, Modelling, Enablement, etc.)? |
| H2 | **Links follow COM-B → Intervention mapping** | Do recommendations follow the BCW's established COM-B-to-intervention links, or are they arbitrary? |
| H3 | **Multiple intervention options per barrier** | Are at least 2 candidate intervention functions offered per barrier (to preserve design optionality)? |
| H4 | **No solution baked in** | Does the analysis diagnose the barrier and recommend intervention types, or skip straight to specific feature solutions? |
| H5 | **Intervention targets diagnosed bottleneck** | Prompt bottleneck → Anchor design; Ability bottleneck → Make tiny / Tools / Skills; not mismatched. |
| H6 | **Correct lever for component** | Ability-Mental Energy → Reduce cognitive load, not "Educate users" (requires high motivation — wrong lever for low-M users). |
| H7 | **Compensatory relationship accounted for** | "Because motivation is low, we must make ability very high (tiny behavior)" |
| H8 | **Tiny Habit recipes constructable** | "After [specific anchor from data], user will [tiny version of behavior]" — not abstract "make the experience simpler" |
| H9 | **Different segments get different interventions** | Not one-size-fits-all |
| H10 | **Troubleshooting order in interventions** | Prompt fix proposed before ability fix, before motivation fix |

---

## Section I: Completeness

| Component | Required Outputs | Present? |
|---|---|---|
| **Prompt** | Type classification per segment; Anchor inventory; Prompt failure modes | □ |
| **Ability** | Chain heatmap across participants; Weakest link per segment; Discovery Question answer; Breakthrough direction | □ |
| **Motivation** | PAC source per segment; Competing behaviors identified; Conflicting motivations mapped; Durability assessed; Shine presence | □ |
| **Action Line** | Per-segment position (above/below/no prompt) with rationale | □ |
| **Segments** | Defined by B=MAP profile with distinct diagnoses | □ |
| **Bright Spots** | Full B=MAP configuration of successful users | □ |
| **Interventions** | Mapped to bottleneck with specific lever | □ |
| **Recipes** | Tiny Habit format for each segment: After [anchor], will [tiny behavior] | □ |

**Threshold:** All 8 outputs required. Missing any creates a gap in the diagnostic chain.

---

## Section J: Traceability

| # | Criterion | What to check |
|---|---|---|
| J1 | **Brief → Guide → Analysis alignment** | Can you trace from the original research brief's questions → the guide's probes → the analysis findings? Are there research questions the analysis doesn't answer? |
| J2 | **Every finding traces to data** | For every conclusion, can you follow the chain back to specific participant data? |
| J3 | **Participant anonymity maintained** | Participants identified by codes (P1, P2…), not names? Quotes sanitised of identifying details? |

---

## Scoring System

### Primary Score: Behavioral Rigor (weighted /5)

| Test | Weight | Score (0-5) |
|---|---|---|
| 1. Diagnostic Accuracy — right bottleneck identified (Sections A + D) | 30% | |
| 2. Coding Rigor — correct classification (Sections B + E) | 20% | |
| 3. Pattern Validity — defensible patterns and segments (Section F) | 20% | |
| 4. Intervention Validity — recommendations match diagnosis (Section H) | 20% | |
| 5. Completeness — all B=MAP/COM-B dimensions covered (Section I) | 10% | |

### Secondary Score: Process & Evidence Quality (/4 per criterion)

| Section | Max |
|---|---|
| A. COM-B Completeness (5 criteria) | 20 |
| B. Evidence Quality (6 criteria) | 24 |
| C. Analytical Rigour (6 criteria) | 24 |
| G. Prioritisation (4 criteria) | 16 |
| J. Traceability (3 criteria) | 12 |
| **TOTAL** | **96** |

### Decision Thresholds

#### Primary Score (Behavioral Rigor)

| Score | Verdict |
|---|---|
| 4.0-5.0 | **APPROVED** — diagnostically sound, proceed to intervention design |
| 3.0-3.9 | **REVISE** — gaps or potential misdiagnoses, verify bottleneck identification before acting |
| 2.0-2.9 | **MAJOR REWORK** — significant diagnostic risks, recoding and reanalysis likely needed |
| Below 2.0 | **REJECT** — analysis produced thematic summaries, not behavioral diagnoses. Reanalyze from transcripts. |

#### Secondary Score (Process & Evidence)

| Score | Verdict |
|---|---|
| 80-96 (>83%) | Sound process and evidence |
| 64-79 (67-83%) | Address gaps before making product decisions |
| 48-63 (50-67%) | Structural issues in coding, evidence, or prioritisation |
| <48 (<50%) | Process not rigorous enough to inform decisions |

---

## Common Failure Patterns

| Pattern | Symptom | Fix |
|---|---|---|
| **The Motivation Mirage** | Analysis concludes "users aren't motivated enough" for >50% of segments. Pull transcripts: did they attempt the behavior? Did they describe wanting the outcome? Did they do competing behaviors instead? If any yes → motivation exists; failure is ability or prompt. | Reclassify. In most cases, "low motivation" = "no prompt" or "too hard." |
| **The Theme Trap** | Analysis produces themes ("trust," "value," "engagement") instead of component diagnoses. | Translate every theme to B=MAP codes. If a theme can't be coded, it's attitudinal and shouldn't drive design. |
| **The Observation Gap** | All ability assessments based on self-report, none on observation. | Flag ability findings as "self-reported, unverified." Recommend observational follow-up. |
| **The Singleton Discard** | Only patterns from 3+ participants reported; unique insights discarded. | Preserve singletons in a separate section — may contain the key design insight. |
| **The Recipe Vacuum** | Diagnosis present but no constructable Tiny Habit recipes. | Go back to transcripts for anchors (routine descriptions) and smallest behavior versions. |
| **Motivation Monopoly** | 80%+ of barriers coded as motivation. | Re-examine: "If we gave perfect knowledge, tools, and supportive environment, would motivation still be the barrier?" |
| **Prevalence-Free Claims** | "Users said…" with no participant count. | Add n/N to every finding. Flag any claim based on <3 participants as weak. |
| **Self-Report Laundering** | Participant opinions presented as behavioral facts. | Tag all evidence by type. Downgrade [SR]-only findings to "hypothesis requiring behavioral validation." |
| **Missing Automatic Motivation** | No analysis of habit, emotion, impulse, or reinforcement. | Recode transcripts for emotional language, habit indicators, reinforcement signals. |
| **Solution Smuggling** | Analysis jumps from barrier to specific feature instead of staying at COM-B → Intervention Function level. | Strip solutions. State barrier, evidence, and intervention function category. Let design solve "how." |
| **Island Barriers** | Every barrier treated as independent, no system view. | Map relationships: which barriers cause others? Common roots? Feedback loops? |
| **Confirmation Bias** | Analysis confirms team's pre-existing hypothesis; disconfirming data absent. | Require disconfirming evidence section for every major finding. |

---

## Meta-Evaluation: Process Check

| # | Process Criterion | Check |
|---|---|---|
| P1 | **Inter-coder reliability** | Did more than one person code the data? If solo-coded, was a sample cross-checked? |
| P2 | **Saturation assessed** | Did the analysis note whether new barriers were still emerging in later interviews (not saturated) or had plateaued (saturated)? |
| P3 | **Reflexivity noted** | Did the analyst acknowledge their own assumptions or biases that might have influenced coding? |
| P4 | **Limitations stated** | Does the analysis explicitly state what it cannot conclude (sample size, context, self-report reliance)? |

---

## Reviewer Quick-Reference Checklist

```
DIAGNOSTIC ACCURACY
□ Troubleshooting order followed (P → A → M)
□ Bottleneck identified per segment with evidence
□ Motivation not over-attributed
□ Attribution corrections documented

CODING RIGOR
□ Data points are behavioral, not attitudinal
□ Codes match the component described
□ Self-attributions investigated and corrected
□ <20% misclassification rate on sample audit

PATTERN VALIDITY
□ Patterns have participant counts
□ Segments defined by B=MAP profile
□ Bright spots fully profiled
□ Singletons preserved

INTERVENTION VALIDITY
□ Interventions target diagnosed bottleneck
□ Correct lever used per component
□ Compensatory relationship accounted for
□ Different segments get different interventions
□ Tiny Habit recipes constructable

COMPLETENESS
□ Prompt: type, anchors, failure modes
□ Ability: chain heatmap, weakest link, Discovery/Breakthrough answers
□ Motivation: PAC source, competing, conflicting, durability, Shine
□ Action Line position per segment
□ Bright spot configuration documented
□ Intervention map with levers
□ Recipes in "After [X], will [Y]" format
□ Confidence assessment included
```
