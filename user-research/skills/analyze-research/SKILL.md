---
name: analyze-research
description: Analyze user research data — interview transcripts, notes, recordings, survey responses, or observation logs — and produce a structured research analysis with findings, patterns, and actionable recommendations. Use this skill when the user says "analyze my interviews", "analyze my research", "what did we learn from the interviews", "synthesize the research", "pull insights from these transcripts", "analyze these notes", "what patterns do you see", "research analysis", "interview analysis", "process my research data", "turn these interviews into findings", "what are the key takeaways", "code these interviews", "do a thematic analysis", or provides interview transcripts, research notes, or qualitative data and wants structured findings. Also trigger when the user has completed fieldwork (via build-research-guide or otherwise) and wants to move from raw data to insights — ideally with a research brief from build-research-brief to anchor findings against original hypotheses. This skill covers analysis — it produces findings and recommendations, not the research plan (that's build-research-brief) or the interview guide (that's build-research-guide).
---

# Analyze Research

Transform raw research data — interview transcripts, notes, survey responses, observation logs — into a structured analysis with coded findings, cross-participant patterns, and actionable recommendations.

## Two Modes

### Mode A: Analyze for the user (primary)
Use when the user provides research data (transcripts, notes, recordings) and wants analysis done for them. Read the data, apply the appropriate analytical framework, and produce the full analysis deliverable.

### Mode B: Guided analysis (interactive)
Use when the user wants to learn the analysis process or work through it collaboratively. Walk them through each step, explain the framework, and co-create the analysis together.

Default to Mode A unless the user explicitly asks to be walked through the process, says they want to learn how to analyze, or asks for guidance rather than output.

---

## Step 0: Gather Inputs

Before analyzing anything, you need research data and context.

### Required Inputs

| Input | What to look for | Where to find it |
|-------|-----------------|------------------|
| **Research data** | Transcripts, notes, recordings, survey responses, observation logs | User provides files, pastes text, or points to workspace files |
| **Research brief** (if available) | The original research questions, hypotheses, target behavior, segment definitions | Output from build-research-brief skill, or user-provided |
| **Research guide** (if available) | The interview script, question structure, probes used | Output from build-research-guide skill, or user-provided |

### What to do if inputs are missing

- **No research data:** Stop. Ask the user to provide transcripts, notes, or other raw data. Analysis without data is speculation.
- **No research brief:** Proceed, but flag that findings won't be anchored to pre-stated hypotheses. Extract the implicit research question from the data itself and state it explicitly.
- **No research guide:** Proceed. The guide helps you understand what questions were asked, but the data speaks for itself.

### Minimum data threshold

Warn the user if they provide fewer than 5 interviews/data points. Analysis on fewer than 5 risks pattern-matching on noise. Immediate tactical fixes (broken flows, confusing labels) are fine to act on from even 1-2 interviews. Strategic conclusions require 5+.

---

## Step 1: Detect the Research Type

Before reading reference files, classify the research based on the data and any available brief. This determines which analytical framework to emphasize.

### Behavioral Research
The research centers on **why users do or don't perform a specific action**. Signals:

- Research brief specifies a target behavior
- Interview questions probe adoption, activation, onboarding, engagement, retention, habit formation, feature usage
- Transcripts contain behavioral episodes: "I tried to do X but then Y happened"
- Data includes behavior change, conversion, churn framed as behavior
- COM-B or B=MAP decomposition present in the brief

**Action:** Read `references/behavioral-analysis.md`. This is your primary analytical framework. Still use general analysis elements (data classification, quote extraction, journey mapping) from `references/general-analysis.md` where they add value.

### General Research
The research centers on **understanding users, validating problems, or informing decisions**. Signals:

- Discovery / exploration research
- Market validation, willingness to pay, competitive understanding
- Feature prioritization, product-market fit
- Customer segmentation, persona building
- Understanding "why" without a specific behavior to change
- Evaluative research (prototype/concept testing)

**Action:** Read `references/general-analysis.md`. This is your primary analytical framework. Borrow behavioral elements (COM-B coding, B=MAP profiling) when the data reveals behavioral patterns worth decomposing, but keep them secondary.

### Mixed
Some research touches both — e.g., "understand why users churn AND identify what behavioral interventions could retain them."

**Action:** Read both reference files. Lead with whichever matches the primary research intent. The understanding part uses general analysis; the intervention design part uses behavioral analysis.

---

## Step 2: Classify and Clean the Data

Before pattern-matching, separate signal from noise across all data points.

### For every data point, classify as:

**Signal (keep and code):**
- **Specific past actions** — concrete things users did, with context (when, where, how)
- **Behavioral sequences** — step-by-step descriptions of how they do things
- **Facts** — verifiable specifics: numbers, tools, timelines, costs, workarounds
- **Commitments** — things they gave up of value (time, reputation, money)
- **Failure stories** — "I tried X but then Y" — reveals what broke
- **Emotional markers** — strong feelings tied to specific moments (not vague sentiment)
- **Bright spots** — instances where the desired outcome happened naturally

**Noise (discard or flag):**
- **Compliments** — positive statements with no commitment behind them ("Love it!", "Sounds great")
- **Fluff** — generic claims, future-tense promises, hypothetical maybes ("I would definitely buy that")
- **Aspirational statements** — what they'd love to do vs. what they actually do
- **Self-diagnosis** — "I'm just lazy" / "I'm not disciplined" (attribution error — flag for re-examination)
- **Social desirability** — saying what sounds good rather than what's true
- **Unanchored feature requests** — suggestions without understood motivation

**Ambiguous (needs follow-up or careful handling):**
- Strong emotion without specific context
- Feature requests you didn't explore the "why" behind
- Lukewarm responses (treat as reliable negatives)
- Self-report that contradicts observed behavior

### Evidence tagging

Tag every coded data point with its source type:
- **[B]** = Behavioral — they described what they actually did
- **[SR]** = Self-report — they stated a belief, preference, or generalization
- **[O]** = Observed — from analytics, usability recording, or direct observation
- **[Q]** = Quote — verbatim language from participant

Preserve enough surrounding context that another analyst could verify the coding.

---

## Step 3: Apply the Analytical Framework

This is where general and behavioral analysis diverge. Follow the instructions in the reference file(s) you loaded in Step 1.

### If General Research → `references/general-analysis.md`

Core analytical methods (apply whichever fit the data):
1. **Customer Journey Mapping** — extract processes, map functional/emotional/social dimensions
2. **Pain and Frequency Matrix** — plot problems on pain × frequency grid
3. **Decision Process Timeline** — map the switch journey (for switch interviews)
4. **Cross-Interview Synthesis** — group by segment, find convergence/divergence
5. **Data Classification** — facts vs. compliments vs. fluff (Mom Test)
6. **Commitment Quality Assessment** — rank signals by reliability
7. **Affinity Diagramming** — cluster observations into patterns, extract design mandates

### If Behavioral Research → `references/behavioral-analysis.md`

Core analytical stages:
1. **Extract behavioral instances** — concrete episodes, not attitudes
2. **Code to COM-B components** — map barriers/enablers to 6 sub-components
3. **Code to B=MAP** — assign Prompt/Ability/Motivation codes
4. **TDF drill-down** — finer-grained coding where barriers cluster
5. **Build per-user profiles** — COM-B diagnosis + B=MAP profile per participant
6. **Cross-user pattern analysis** — frequency matrices, bottleneck distribution, ability chain heatmap
7. **Identify competing behaviors** — what users do instead, and why it persists
8. **System dynamics** — reinforcing loops, balancing mechanisms, delays
9. **Prioritize barriers** — by prevalence, severity, addressability, upstream position
10. **Link to intervention functions** — map barriers to BCW intervention types and Fogg's design levers

### If Mixed → Apply both, clearly separating findings

Use general methods for the understanding-oriented questions. Use behavioral methods for the action-oriented questions. Present findings in two clearly labeled sections so the user knows which framework produced which insight.

---

## Step 4: Extract Key Quotes

Pull exact quotes and pair them with context signals. Quotes serve multiple purposes: marketing language, fundraising decks, team alignment, resolving internal disagreements.

For each quote, capture:
```
QUOTE: "[exact words]"
PARTICIPANT: [ID or segment]
CONTEXT: [what they were discussing]
SIGNAL TYPE: [pain / goal / workaround / emotion / bright spot / commitment]
EVIDENCE TAG: [B] / [SR] / [O]
IMPLICATION: [what this means for the product/business]
```

Organize quotes by theme, not by participant. A quote bank organized by theme is immediately useful; quotes organized by interview are just notes.

---

## Step 5: Identify Patterns Across Participants

### Group by segment, not by conversation

Don't analyze one interview at a time. Lay out all coded data and sort by:
1. Problem/barrier mentioned
2. Goal/aspiration mentioned
3. Current workaround
4. Emotional intensity
5. Behavioral profile (for behavioral research)

### Pattern Recognition

For each candidate pattern, assess:

| Pattern | Participants showing it | Strength | Confidence |
|---------|------------------------|----------|------------|
| [pattern] | [count / total] | Strong / Moderate / Weak | High / Medium / Low |

**Strength criteria:**
- **Strong:** 60%+ of participants, corroborated by behavioral evidence [B] or observation [O]
- **Moderate:** 40-60% of participants, or strong signal from fewer but with behavioral evidence
- **Weak:** <40% or based solely on self-report [SR]

### What patterns tell you

- **Consistent problem + consistent workaround + willingness to pay** → Real opportunity. Push for commitments.
- **Consistent problem + no one paying or searching** → Problem exists but isn't must-solve. Vitamins, not painkillers.
- **Inconsistent everything** → Segment too broad. Recommend slicing further.
- **Consistent rejection/apathy** → Problem isn't real, or wrong people. Recommend pivoting segment or problem.

### Divergence is data too

- Wildly different processes → scope too broad → recommend narrowing
- Different terminology for the same thing → language opportunity for the product
- Different contexts for the same goal → potential for multiple segments or pricing tiers

---

## Step 6: Update Beliefs and Hypotheses

If a research brief exists, revisit every stated hypothesis and update:

| Element | Before research | After research | Changed? | Evidence |
|---------|----------------|----------------|----------|----------|
| Customer hypothesis | [from brief] | [updated] | Y/N | [key quotes/data] |
| Problem hypothesis | [from brief] | [updated] | Y/N | [key quotes/data] |
| Solution hypothesis | [from brief] | [updated] | Y/N | [key quotes/data] |
| Willingness to pay | [from brief] | [updated] | Y/N | [key quotes/data] |
| Key risk | [from brief] | [updated] | Y/N | [key quotes/data] |

If no brief exists, state the implicit hypotheses the research reveals and what the data says about each.

**Red flag:** If unexpected answers didn't change any hypothesis, either the wrong questions were asked or data is being ignored.

---

## Step 7: Produce the Analysis Deliverable

### Output Structure

Save a markdown file to the user's workspace. The structure adapts to research type.

```
# Research Analysis: [Title]

**Date:** [date]
**Research type:** [Behavioral / General / Mixed]
**Data analyzed:** [N interviews/observations/surveys, participant IDs/segments]
**Research brief:** [linked if available, or "none provided"]

---

## Executive Summary
[3-5 sentences: what you studied, the headline finding, the primary recommendation]

---

## 1. Data Overview
- Participants: [count, segments represented]
- Data quality: [signal-to-noise ratio, any concerns]
- Coverage: [which research questions have strong data, which are thin]

## 2. Data Classification Summary
| Category | Count | % of total data points |
|----------|-------|----------------------|
| Specific past actions [B] | | |
| Self-report [SR] | | |
| Observed [O] | | |
| Discarded (compliments/fluff) | | |

--- GENERAL SECTIONS (include when general/mixed) ---

## 3G. Key Findings by Theme
[For each theme: pattern name, strength, supporting evidence, key quotes, implications]

## 4G. Customer Journey Map
[If process data exists: steps, functional/emotional/social dimensions, pain points, time/money costs]

## 5G. Pain and Frequency Matrix
[2×2 grid with problems plotted; pricing signals extracted]

## 6G. Segment Patterns
[Convergence and divergence by segment; recommendations for segment refinement]

## 7G. Earlyvangelist Identification
[Participants showing all 4 signs: have the problem, know they have it, have budget, cobbled together own solution]

## 8G. Commitment Quality Assessment
[Ranked signals: nothing → words → time → reputation → money → combined]

--- BEHAVIORAL SECTIONS (include when behavioral/mixed) ---

## 3B. COM-B Behavioral Diagnosis
[Completed COM-B-D form: each component assessed with evidence, strength rating, and what needs to change]

## 4B. B=MAP Coding Summary
### Bottleneck Distribution
[% Prompt / % Ability / % Motivation as primary bottleneck]

### Ability Chain Heatmap
[Cross-participant weak/adequate/strong per factor]

### Prompt Profile
[Types in use, anchor quality, failure modes]

## 5B. Per-Segment B=MAP Profiles
[For each behavioral segment: profile, diagnosis statement, key evidence]

## 6B. Bright Spot Configuration
[What the successful B=MAP profile looks like — the design blueprint]

## 7B. Competing Behaviors
[What users do instead, COM-B drivers, B=MAP profile of competing behavior]

## 8B. System Dynamics
[Reinforcing loops, balancing mechanisms, feedback delays identified in the data]

## 9B. Intervention Map
[For each priority barrier: COM-B component, barrier, evidence, candidate intervention functions (BCW) and design levers (Fogg)]

## 10B. Recommended Behavior Recipes
[For each segment: "After [anchor], they will [tiny behavior]" — only if data supports it]

--- UNIVERSAL SECTIONS (always include) ---

## Hypothesis Update
[Table: before/after for each hypothesis from the brief, or implicit hypotheses extracted]

## Quote Bank
[Organized by theme, with context and evidence tags]

## Confidence Assessment
| Finding | Confidence | Basis |
|---------|------------|-------|
| [finding] | High / Medium / Low | [why — sample size, evidence type, consistency] |

## Warning Signs
[Any of: all compliments no commitments, inconsistent data suggesting broad segment, unexpected answers that should change plans, missing data that limits conclusions]

## Recommended Next Actions
1. [Highest-priority action with rationale]
2. [Second priority]
3. [Third priority]
- Next 3 research questions (if more research needed)
- Segment changes to consider
- Commitment escalation targets

## Open Questions
[What the data doesn't answer; what needs follow-up research]
```

---

## Step 8: Quality Checks

Before presenting the analysis, verify:

### Universal Checks
- [ ] Every finding cites specific participant data, not general impressions
- [ ] Signal clearly separated from noise — compliments and fluff discarded or flagged
- [ ] Evidence tagged as [B] behavioral, [SR] self-report, or [O] observed
- [ ] Distinction maintained between what participants DID vs. what they SAID
- [ ] Patterns assessed for strength (participant count, evidence type)
- [ ] Findings won't surprise anyone who read the raw data — no interpretive leaps
- [ ] Divergent/disconfirming data reported, not hidden
- [ ] No unsupported causal claims
- [ ] Confidence levels stated for each major finding
- [ ] Recommendations are specific and actionable, not vague

### Behavioral-Specific Checks
- [ ] All transcripts coded to COM-B components (6 sub-components, not collapsed)
- [ ] B=MAP coding distinguishes Prompt, Ability, and Motivation
- [ ] TDF drill-down completed for components with clustered barriers
- [ ] Attribution correction done — "I'm lazy" re-examined for hidden ability/prompt issues
- [ ] Competing behaviors mapped with their COM-B/B=MAP drivers
- [ ] System dynamics (loops, delays) identified where present
- [ ] Barriers prioritized by prevalence, severity, addressability, upstream position
- [ ] Priority barriers linked to intervention functions (BCW) and design levers (Fogg)
- [ ] Bright spots analyzed — successful configuration documented as design blueprint
- [ ] Motivation not assumed as primary bottleneck without checking prompt and ability first

### General-Specific Checks
- [ ] Data classified: facts vs. commitments vs. compliments vs. fluff
- [ ] Commitment quality ranked (nothing → words → time → reputation → money)
- [ ] Earlyvangelists identified (or their absence noted)
- [ ] Feature requests decomposed to underlying scenarios, not taken at face value
- [ ] Pain/frequency matrix populated (if sufficient data)
- [ ] Social and emotional dimensions captured, not just functional

### Anti-Patterns to Catch

| Anti-Pattern | What it looks like | Fix |
|-------------|-------------------|-----|
| **Theme soup** | Findings as vague themes ("Users want simplicity") without structure | Re-code every theme to analytical framework. If it doesn't map, it's not a finding. |
| **Quote cherry-picking** | One vivid quote justifying a finding while ignoring contradictory data | Report prevalence counts and note disconfirming evidence |
| **Acting on one interview** | Strategic conclusions from a single participant | Flag and recommend waiting for 5+ |
| **Motivation monopoly** | All barriers coded as motivation — "They just don't want to" | Re-examine for Capability/Ability and Opportunity/Prompt barriers disguised as motivation |
| **Self-report = truth** | Taking "I always do X" at face value | Tag as [SR], note discrepancy with [B]/[O] data |
| **Compliment counting** | Treating "Love it!" as validated demand | Apply commitment quality scale — compliments are worthless without commitment |
| **Ignoring enablers** | Only coding what's broken, missing what works | Code enablers too — they reveal leverage points |
| **Over-indexing on negatives** | Cancellation feedback feels more urgent than it is due to loss aversion | Balance with positive data |
| **Confusing requests with decisions** | Customer feature requests treated as product decisions | Customers know valuable and usable. Only you know viable and feasible. |

---

## Presenting the Analysis

After saving the analysis file:

1. Present the executive summary and top 3 findings
2. Highlight the highest-confidence, highest-impact insight
3. Note any warning signs in the data
4. State what the data does NOT answer (open questions)
5. Offer to drill into specific themes, segments, or behavioral components

Then offer:
- "Want me to produce the intervention map in more detail?" (behavioral)
- "Want me to draft personas from this data?" (general)
- "Want me to compare findings against your original hypotheses?"
- "Want me to extract marketing copy from the quote bank?"
- "Ready to move to research analysis evaluation?" (skill 6 handoff)

---

## Rules

1. **Data over interpretation.** Every claim must trace to specific participant data. "Users struggle with onboarding" is not a finding. "5 of 7 new users abandoned the checklist at step 3, citing confusion about what 'workspace setup' means [B]" is.

2. **Prevalence over vividness.** A dramatic quote from one participant is less meaningful than a quiet pattern across five. Report both, but weight prevalence.

3. **Behaviors over attitudes.** What people did matters more than what they said they'd do. When self-report [SR] contradicts behavioral evidence [B], trust the behavior.

4. **Challenge the Motivation Trap.** When data suggests users "aren't motivated," re-examine for prompt and ability barriers first. Users who say "I'm lazy" often mean "the prompt doesn't exist" or "it's too hard." Reclassify only with evidence.

5. **Preserve disconfirming data.** If most participants love the feature but two had serious problems, report both. Cherry-picking creates false confidence.

6. **Don't design solutions in the analysis.** The analysis tells you the problem and its severity. Solutions are a separate step. Intervention functions and design levers point a direction — they're not feature specs.

7. **Flag data quality issues.** If transcripts are thin, if important probes were missed, if the sample skews in ways that limit generalizability — say so. Honest analysis includes its own limitations.

8. **Separate findings from recommendations.** Findings are what the data shows. Recommendations are your analytical judgment about what to do. Keep them in distinct sections so the reader can evaluate each independently.
