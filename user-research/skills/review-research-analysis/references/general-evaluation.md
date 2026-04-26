# General Research Analysis Evaluation Reference

Synthesized from The Mom Test (Fitzpatrick), Deploy Empathy (Hansen), and Just Enough Research (Hall).

Use this reference when evaluating analysis of discovery, validation, segmentation, willingness-to-pay, competitive, evaluative, or any non-behavioral research. For behavioral research (adoption, engagement, retention, habit formation), use the behavioral-evaluation reference instead.

---

## Table of Contents

1. [Sample Sufficiency and Convergence](#1-sample-sufficiency-and-convergence)
2. [Core Questions Answered](#2-core-questions-answered)
3. [Data Quality Audit](#3-data-quality-audit)
4. [False Positive Detection](#4-false-positive-detection)
5. [False Negative Detection](#5-false-negative-detection)
6. [Process Integrity](#6-process-integrity)
7. [Data Extraction Quality](#7-data-extraction-quality)
8. [Three-Dimensional Analysis](#8-three-dimensional-analysis)
9. [Pain and Frequency Assessment](#9-pain-and-frequency-assessment)
10. [Pattern Quality](#10-pattern-quality)
11. [Segment Consistency](#11-segment-consistency)
12. [Evidence Quality — Quote Backing](#12-evidence-quality--quote-backing)
13. [Commitment Ladder Audit](#13-commitment-ladder-audit)
14. [Belief Update Check](#14-belief-update-check)
15. [Earlyvangelist Identification](#15-earlyvangelist-identification)
16. [Viable-Usable-Valuable-Feasible Filter](#16-viable-usable-valuable-feasible-filter)
17. [Bias and Balance Check](#17-bias-and-balance-check)
18. [Actionability](#18-actionability)
19. [Willingness-to-Pay Signals](#19-willingness-to-pay-signals)
20. [Process Diagram / Journey Quality](#20-process-diagram--journey-quality)
21. [Output Artifacts Quality](#21-output-artifacts-quality)
22. [Reporting Quality](#22-reporting-quality)
23. [Decision Readiness](#23-decision-readiness)
21. [Scoring System](#scoring-system)
22. [Common Failure Patterns](#common-failure-patterns)
23. [Red Flags Checklist](#red-flags-checklist)

---

## 1. Sample Sufficiency and Convergence

**PASS if:**
- At least 5 interviews completed per discrete question/problem
- Convergence is evident: multiple participants describe similar processes, tools, or frustrations
- Stop rule was triggered: "We started hearing the same things over and over"
- Diversity in participants (roles, demographics, company sizes) is evident

**NEEDS WORK if:**
- 5 interviews done but answers are wildly divergent → scope was too broad → need research loops (another round of 5 with narrower scope)
- Only one type of customer interviewed (e.g., only churned, no happy customers)

**FAIL if:**
- Business decisions drawn from fewer than 5 interviews
- No diversity in participants
- No stop rule applied — interviews just stopped at an arbitrary number

**Challenge question:** Are you confusing "5 interviews done" with "5 interviews that converge"? The former is a count. The latter is signal.

---

## 2. Core Questions Answered

**PASS if the analysis explicitly answers all 7 core questions (Hansen):**

| Core Question | Answered? | Evidence (specific quotes/data) |
|---|---|---|
| 1. What are they trying to do overall? | | |
| 2. What are the steps in that process? | | |
| 3. Where are they now? | | |
| 4. Where does the problem fit? | | |
| 5. Where do they spend time or money? | | |
| 6. How often do they experience this? | | |
| 7. What have they already tried? | | |

**FAIL if:**
- Any core question is unanswered without justification
- Answers are the analyst's interpretation without supporting quotes
- "What they've already tried" is missing — this is where competitive alternatives live

---

## 3. Data Quality Audit

For every key finding in the analysis, trace it back to its source and classify:

| Finding | Source quote/evidence | Data type | Reliable? |
|---|---|---|---|
| [Finding] | [Exact quote or observed behaviour] | Fact / Compliment / Fluff | Y/N |

**Red flags:**
- Finding supported only by compliments ("They loved it!")
- Finding supported by future-tense promises ("They said they would buy")
- Finding has no source quote — it's a memory or interpretation
- Finding based on what people said they'd do, not what they've already done

**The acid test:** For each finding, ask: "Is this based on what someone **did** (past behaviour, money spent, time invested) or what someone **said** they'd do?" If the latter, downgrade reliability to zero.

---

## 4. False Positive Detection

False positives are the most dangerous failure mode. They convince you you're right when you're wrong.

| Pattern | How to detect | Example |
|---|---|---|
| **Compliments counted as validation** | Analysis says "positive feedback" without any commitment | "Everyone loved the idea" with zero pre-orders, intros, or trials |
| **Fluff counted as demand** | Analysis cites "would buy" or "would use" as demand evidence | "15 of 20 said they would buy" — but none put down a deposit |
| **Pitched enthusiasm mistaken for organic interest** | You described the product, they said nice things, you counted it | They were being polite because you wouldn't shut up |
| **Leading questions producing expected answers** | Questions suggested the answer; respondents agreed | "Don't you hate X?" → "Yeah!" → "Validated!" |
| **Feature requests treated as purchase intent** | "They asked for Excel sync" ≠ "They'll buy if we add Excel sync" | Request without understanding the motivation behind it |

**Fitzpatrick Test:** "If you've only got compliments, you've got nothing. If you've got commitments, you've got data."

---

## 5. False Negative Detection

Less dangerous but still costly — prematurely killing a valid idea.

| Pattern | How to detect |
|---|---|
| Talked to wrong segment | Consistent apathy but segment wasn't sliced properly |
| Asked bad questions | Questions were about your idea, not their life — they shut down |
| Too formal | "Interview" format made them guarded; missed casual signals |
| Premature zoom | Asked about a specific problem before confirming it matters |
| Interpreted lukewarm as negative | "Meh" might mean wrong segment, not wrong idea |

---

## 6. Process Integrity

| Check | PASS Criteria | Red Flags |
|---|---|---|
| Collaborative analysis | Multiple team members participated — not a solo researcher producing a report | One person analyzed, then "presented findings" |
| Observations before patterns | Team reviewed raw data before jumping to groupings | Patterns imposed before data review |
| Observations ≠ interpretations | Clear separation between what happened and what it means | Notes mix raw data with conclusions |
| No premature solutions | Analysis stayed at insight/principle level — solutions came after | Design mandates include specific UI solutions |
| Ground rules followed | Goal = understand user; respect structure; no solutions during analysis | Loudest voice dominated; jumped to solutions |
| Notes exist with exact quotes | Verbatim quotes with signal symbols | Summary from memory written days later |
| Review happened with full team | Business + product people both participated | One person attended and told others what to do |
| Review happened promptly | Within 24 hours of conversation batch | Weeks later, after details faded |
| Big 3 questions updated | Old questions retired, new ones promoted | Same questions for months |
| Learning not bottlenecked | Team can independently cite customer evidence | Only one person "knows the customers" |

---

## 7. Data Extraction Quality

### Coverage Check

Did the analysis extract all relevant data types?

| Data Type | What to look for |
|---|---|
| Goals | What participants want that the product relates to |
| Priorities | What matters most — explicit ranking or implicit from behavior |
| Tasks | Actions participants take toward goals |
| Motivators | Events/situations that trigger the task |
| Barriers | What prevents goal achievement |
| Habits | Regular behaviors (especially unconscious ones) |
| Relationships | People who influence the participant's actions |
| Tools | Objects/devices used during tasks |
| Environment | Context affecting desire/ability to act |

**Red flag:** Only goals and tasks extracted. Barriers, habits, relationships, and environment are where the non-obvious insights live.

### Source Tracing

| Check | What to look for |
|---|---|
| Each observation coded to source | Every finding traces back to a specific participant |
| Verbatim quotes preserved | Not just paraphrased summaries — actual language captured |
| Vocabulary documented | Words participants used, especially where they differ from internal jargon |
| Unanticipated findings flagged | Needs or behaviors the team didn't expect |

**Red flag:** Observations not traceable to individual participants. If challenged, you can't point to the source data.

---

## 8. Three-Dimensional Analysis

| Dimension | What to look for | Example Evidence |
|---|---|---|
| Functional (steps, tools, time, money) | Process mapped, tools identified, time/cost quantified | |
| Emotional (hopes, frustrations, uncertainties, relief) | Emotional language captured, intensity noted | |
| Social (decision-makers, team dynamics, stakeholders, word-of-mouth) | Influence map, approval chains, social proof patterns | |

**FAIL if:**
- Only functional analysis present (the most common failure)
- Emotional insights inferred rather than evidenced by quotes
- Social dynamics ignored — especially decision-making stakeholders beyond the interviewee

**Why this matters:** Functional tells you what to build. Emotional tells you how to market. Social tells you who else needs convincing and how word-of-mouth works. Missing any dimension = incomplete strategy.

---

## 9. Pain and Frequency Assessment

**PASS if:**
- Problems/steps plotted on a pain × frequency matrix (or equivalent prioritization)
- Pain evidenced by concrete data: time spent, money spent, number of steps, manual processes, multiple tools, cost of getting it wrong
- Frequency documented: daily / weekly / monthly / annual / one-time
- High-pain + high-frequency problems explicitly identified as priority opportunities

**FAIL if:**
- No prioritization framework — all findings presented as equally important
- Pain described qualitatively ("they seemed frustrated") without quantitative backing
- Low-pain, low-frequency problems recommended for action

**Challenge questions:**
- For each "high pain" claim: What specific time/money/consequence data supports this?
- For each "high frequency" claim: Did the participant state a specific cadence, or are you guessing?

---

## 10. Pattern Quality

| Check | PASS Criteria | Red Flags |
|---|---|---|
| Patterns emerged from data | Groupings formed through iterative arrangement | Categories predefined before analysis |
| Multiple grouping attempts | Team tried different arrangements before settling | First grouping accepted without rearrangement |
| Patterns named clearly | Each group has a descriptive label tied to a user need | Vague labels ("Interesting stuff," "Technology") |
| Sufficient evidence per pattern | Multiple observations from different participants | Pattern based on one participant's comment |
| Contradictions preserved | Conflicting data noted rather than smoothed over | Only confirming data retained |
| Outliers handled correctly | Non-target participants' data set aside, not forced into patterns | Outlier data distorted the model |

---

## 11. Segment Consistency

| Test | Pass | Fail |
|---|---|---|
| Did conversations target the same specific segment? | All 5–10 people share demographics AND behaviours | Talked to "small businesses" spanning restaurants, SaaS, and freelancers |
| Are problems consistent across the segment? | 3–5 conversations surfaced the same top problems | Every conversation produced different #1 problems |
| Are workarounds consistent? | Similar existing solutions and spending patterns | Wildly different approaches to the same nominal problem |
| Is emotional intensity consistent? | Similar level of caring about the problem | Some furious, some don't care at all |

**If feedback is all over the map after 10+ conversations:** The segment is too broad. The analysis should conclude with "slice the segment" not "the market is diverse."

---

## 12. Evidence Quality — Quote Backing

**PASS if:**
- Every major finding backed by direct quotes from participants
- Quotes attributed (anonymized if needed) so cross-participant patterns visible
- Counter-examples and outliers included, not just confirming evidence
- Analyst distinguishes between what participants said vs. what the analyst inferred

**FAIL if:**
- Findings presented as conclusions without supporting quotes
- Only quotes supporting the analyst's preferred conclusion included
- Analyst's interpretation presented as participant's words

**Challenge questions:**
- Is this what people actually did, or what they said they'd do?
- Are you fishing for validation instead of seeking disconfirming data?
- Are you confusing enthusiasm for commitment?

---

## 13. Commitment Ladder Audit

Map every person in the analysis to their highest commitment level:

| Level | Signal | Value |
|---|---|---|
| 0 | Compliment ("I love it"), stall ("Keep me posted") | Worthless |
| 1 | Agreed to follow-up call | Minimal |
| 2 | Invested time (attended demo, completed trial) | Moderate |
| 3 | Invested reputation (intro'd to boss, vouched internally) | Strong |
| 4 | Invested money (deposit, pre-order, paid pilot) | Very strong |

**Evaluate the pipeline:**
- If most contacts at Level 0–1: Zombie leads, not customers. Analysis should not call these "interested prospects."
- If some at Level 3–4: Real signals. Analysis should weight these heavily.
- If commitment was pushed and rejected: Useful data. Analysis should acknowledge, not hide.

**"Looks great, let me know when it launches" is NOT a pre-order. It is a polite rejection.**

---

## 14. Belief Update Check

| Test | Pass | Fail |
|---|---|---|
| Did the analysis update any prior beliefs? | At least one hypothesis refined, strengthened, or abandoned | All prior beliefs survived unchanged — suspicious |
| Did unexpected findings change anything? | Surprising data led to adjusted plans | Surprises rationalised away or ignored |
| Were disconfirming signals given equal weight? | Negative and lukewarm responses prominent in findings | Analysis only cites enthusiastic respondents |

**Red flag:** If the analysis reads like a pitch deck for your existing idea — citing only supportive data — it's confirmation bias, not analysis.

---

## 15. Earlyvangelist Identification

| Test | Pass | Fail |
|---|---|---|
| Does the analysis identify specific individuals matching all four earlyvangelist criteria? | Named people who: have the problem, know they have it, have budget, have built a workaround | Generic "positive reception from target market" |
| Are these people being kept close? | Follow-up plan for each | Listed and forgotten |
| Is emotional intensity distinguished from politeness? | "WORST PART OF MY DAY" treated differently from "yeah, that's a problem" | All positive responses weighted equally |

---

## 16. Viable-Usable-Valuable-Feasible Filter

| Lens | Applied? | Notes |
|---|---|---|
| **Valuable** — Does the customer need this? Will they pay? | | |
| **Usable** — Can the customer figure out how to use it? | | |
| **Viable** — Can the business support this commercially? | | |
| **Feasible** — Can the team build this? | | |

**FAIL if:**
- Analysis treats customer requests as product requirements without filtering
- "Customers want X, so we should build X" — without evaluating viability or feasibility
- No distinction between what customers can know (valuable, usable) and what only you can know (viable, feasible)

**Key principle (Hansen):** Customers can only know valuable and usable. They cannot possibly know what's viable or feasible for your business. That filter is YOUR job, applied AFTER the interview, never during.

---

## 17. Bias and Balance Check

### Confirmation Bias
- Did the analysis only surface findings supporting a pre-existing hypothesis?
- Were disconfirming data points included and discussed?
- Was the research used to "evaluate" (open to new insights) rather than "validate" (looking to confirm)?

### Loss Aversion Bias
- Is the analysis over-weighted toward negative feedback at the expense of positive signals?
- Are cancellation insights balanced with happy-customer insights?

### Survivorship Bias
- Does the analysis only reflect people who agreed to be interviewed?
- Are there participant types absent from the sample?

### Anchoring Bias
- Did one particularly memorable interview disproportionately shape conclusions?
- Are patterns supported by multiple interviews, not just one vivid story?

**FAIL if:** Any bias clearly distorts conclusions without acknowledgment.

---

## 18. Actionability

**PASS if:**
- Analysis produces specific, concrete actions — not just "interesting findings"
- Actions categorized: marketing, product, pricing, feature, research (further investigation needed)
- Each action maps back to specific evidence from interviews
- "Further research needed" items identified where signal is insufficient

**FAIL if:**
- No actions at all — just a descriptive report
- Actions disconnected from the evidence
- All actions are product/feature changes — marketing, pricing, and positioning actions missing

### Action Quality Check

For each proposed action, verify:

| Check | Pass? |
|---|---|
| Supported by quotes from 2+ participants | |
| Maps to a high-pain and/or high-frequency problem | |
| Passes the viable/usable/valuable/feasible filter | |
| Specifies the expected outcome (what will change) | |
| Identifies what further research/validation is needed | |

### Design Mandates Quality (if present)

| Check | What to look for |
|---|---|
| Mandates are actionable | Each translates into a design decision |
| Mandates are evidence-backed | Each links to specific patterns and source observations |
| Mandates are prioritized | Based on business goals and frequency/severity |
| Mandates avoid solution prescription | State the principle, not the UI element |

---

## 19. Willingness-to-Pay Signals

**Evaluate when pricing/WTP was in scope:**

**PASS if:**
- Current spending documented: what they pay for existing tools at each step
- Time costs documented: how long each step takes
- Frequency documented: how often they pay/spend that time
- Stakes documented: what happens if they don't solve it or get it wrong
- Billing model implications noted: frequency → billing model match

**FAIL if:**
- "They'd probably pay $X" stated without evidence
- Only money costs considered (time costs ignored)
- No analysis of what the customer is already paying across the full process (your floor for pricing)

---

## 20. Process Diagram / Journey Quality

**PASS if:**
- A customer journey map or process diagram shows the steps
- Diagram distinguishes between overall goal process and product-specific decision process
- Steps include annotations for tools, time, money, people involved
- Branches and non-linear paths represented

**FAIL if:**
- No process visualization — just narrative text
- Process assumed/inferred rather than derived from interview quotes

---

## 21. Output Artifacts Quality

Evaluate the quality of specific artifacts the analysis produced. Score only the artifacts that are present — don't penalize missing artifacts if the research type didn't call for them.

### Personas (if produced)

| Check | Pass | Fail |
|---|---|---|
| Based on real interview data | Behavior patterns, goals, quotes from actual participants | "Made up a character" without research foundation |
| Design targets ≠ marketing targets | Personas represent behavior patterns, not market segments | Persona = "Women 25-34 in urban areas" |
| Minimum viable number | As few as needed to cover all relevant behavior patterns (typically 2-4) | Too many personas (>5) dilute focus |
| Includes key fields | Photo, name, demographics, role, quote, goals, behaviors, skills, environment, relationships — all data-derived | Stock photos, invented quotes, assumed skill levels |
| Relationships among personas | Reduces count and creates richer scenarios | Each persona is an island |

**Red flag (Hall):** "A truly useful persona is the result of collaborative effort following firsthand user research. Otherwise you're just making up a character that might be as relevant to the design process as any given imaginary friend."

### Mental Models (if produced)

| Check | Pass | Fail |
|---|---|---|
| Built from affinity diagram | Emerged from data, not sketched from assumptions | Model precedes data collection |
| Includes actions, beliefs, and feelings | Full cognitive space represented | Only actions mapped — beliefs and emotional context missing |
| Gap analysis performed | Mismatches between user expectations and current offering identified | Model created but not applied to design decisions |

### Scenarios (if produced)

| Check | Pass | Fail |
|---|---|---|
| Grounded in interview data | Based on actual reported situations and goals | Invented scenarios assuming ideal conditions |
| Written from user perspective | Not from system or business process perspective | Reads like a use case or feature spec |
| Includes realistic messiness | Interruptions, competing priorities, real-world constraints | Clean, ideal-path scenarios only |

---

## 22. Reporting Quality

| Check | What to look for |
|---|---|
| Brief, well-organized summary | Includes goals, methods, insights, recommendations |
| Accessible format | Persona cards, visual diagrams — things people will reference |
| Source materials organized | Raw notes, recordings accessible for deeper dives |
| Shareable | Non-participants can understand findings without verbal walkthrough |

**Hall's hierarchy:** "A quick sketch of a persona or a photo of findings documented in sticky notes on a whiteboard in a visible location is far superior to a lengthy written report that goes ignored."

---

## 23. Decision Readiness

The ultimate test: can this analysis drive decisions?

| Question | Answer Required |
|---|---|
| What are the highest-priority user needs? | Ranked, evidence-backed list |
| What design mandates follow from the research? | Actionable principles, not vague insights |
| What should we build / not build? | Features and content justified by user patterns |
| What questions remain unanswered? | Gaps identified with plan for further research |
| What assumptions were validated / invalidated? | Tied back to the research brief's risk assessment |

**The Satisfying Click (Hall):** "One way to know you've done enough research is to listen for the satisfying click. That's the sound of the pieces falling into place when you have a clear idea of the problem you need to solve and enough information to start working on the solution." If the analysis produces that click — shared by the team, not just one person — it's working. If the pieces are still rattling: not done yet.

---

## Scoring System

### Criteria and Weights

| # | Criterion | Max Score | Weight |
|---|---|---|---|
| 1 | Sample Sufficiency & Convergence | 3 | 7% |
| 2 | Core Questions Answered | 3 | 7% |
| 3 | Data Quality (facts vs. fluff) | 3 | 8% |
| 4 | False Positive Risk | 3 | 8% |
| 5 | Process Integrity | 3 | 4% |
| 6 | Data Extraction Quality | 3 | 5% |
| 7 | Three-Dimensional Analysis | 3 | 7% |
| 8 | Pain & Frequency Assessment | 3 | 7% |
| 9 | Pattern Quality | 3 | 5% |
| 10 | Segment Consistency | 3 | 7% |
| 11 | Evidence Quality (quote backing) | 3 | 9% |
| 12 | Commitment Evidence | 3 | 5% |
| 13 | Belief Updates | 3 | 4% |
| 14 | VUVF Filter Applied | 3 | 4% |
| 15 | Bias & Balance | 3 | 4% |
| 16 | Actionability | 3 | 9% |
| 17 | Decision Readiness | 3 | 5% |

Scoring per criterion: 1 = Unreliable/Fail, 2 = Partially reliable/Needs Work, 3 = Trustworthy/Pass

**Conditional criteria** (score only when in scope):
- Commitment Ladder Audit (#10) — score when validation/demand testing was the research purpose
- WTP Signals (#17) — score when pricing/WTP was in scope
- Process Diagram (#18) — score when process mapping was in scope
- Earlyvangelist Identification (#13) — score when the research aimed to find early adopters
- Reporting Quality (#19) — score when a deliverable report was produced

When conditional criteria apply, redistribute weights proportionally across all scored criteria.

### Weighted Score Calculation

```
Weighted Score = Σ (criterion_score / 3 × weight × 100)
```

### Decision Thresholds

| Score | Verdict |
|---|---|
| 85-100 | **APPROVED** — analysis is sound, act on findings |
| 70-84 | **REVISE** — address identified gaps before making decisions |
| 50-69 | **MAJOR REWORK** — structural issues in evidence, patterns, or actionability |
| <50 | **REJECT** — analysis cannot be trusted for decision-making |

---

## Common Failure Patterns

| Pattern | Symptom | Fix |
|---|---|---|
| **Pitch deck disguised as analysis** | All findings confirm the team's hypothesis; no disconfirming evidence | Require a disconfirming evidence section for every major finding |
| **Theme soup** | Findings are themes ("Trust," "Speed") without evidence or prioritization | Map every theme to specific quotes, pain × frequency, and actions |
| **Solo analyst syndrome** | One person analyzed and "presented" — no collaborative interpretation | Require multi-person analysis session within 24 hours |
| **Zombie leads counted as demand** | "Interested" contacts at Level 0–1 treated as pipeline | Audit commitment levels; strip anyone without Level 2+ commitment |
| **Functional-only analysis** | Only steps and tools captured; emotions and social dynamics absent | Recode transcripts for emotional language and stakeholder mentions |
| **Feature request laundering** | Customer requests passed through as product requirements | Apply VUVF filter; trace each request to the underlying problem |
| **Prevalence-free claims** | "Users said…" without how many | Add n/N to every finding; flag anything based on <3 participants as weak |
| **Equal-weight findings** | All findings presented as equally important | Apply pain × frequency matrix; rank and prioritize |

---

## Red Flags Checklist

Reject or send back for revision if any of these are present:

- Conclusions drawn from fewer than 5 interviews
- No direct quotes supporting major findings
- Only functional analysis — no emotional or social dimensions
- Customer feature requests taken at face value without process probing
- "Customers want X, so we should build X" without viability/feasibility filter
- Analyst's interpretation presented as participant's words
- Cancellation insights not balanced with happy-customer insights
- No pain/frequency prioritization — all findings equally important
- Actions proposed without mapping to specific evidence
- WTP conclusions based on what people said they'd pay, not what they currently pay
- Analysis reads like a pitch deck for the existing idea
- One memorable interview disproportionately shapes all conclusions

---

## The Ultimate Question

After reviewing the analysis, ask the team:

> "Based on this analysis, are we making a decision based on **what people did** or **what people said they'd do**?"

If the answer is "said they'd do" — you don't have validation. You have hope.

## Rules of Thumb

- "Compliments are the fool's gold of customer learning: shiny, distracting, and entirely worthless." (Fitzpatrick)
- "The more they're giving up, the more seriously you can take their kind words." (Fitzpatrick)
- "It's not a real lead until you've given them a concrete chance to reject you." (Fitzpatrick)
- "If you got an unexpected answer and it didn't change your idea — you're just going through the motions." (Fitzpatrick)
- "There's more reliable information in a 'meh' than a 'Wow!'" (Fitzpatrick)
- "Since human brains are pattern recognition machines, you might start seeing the patterns you want to see that aren't actually there." (Hall)
