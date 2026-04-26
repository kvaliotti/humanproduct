# Behavioral Research Analysis Reference

Synthesized from COM-B / Behaviour Change Wheel (Michie et al.) and B=MAP / Tiny Habits (BJ Fogg). Use this reference when the research goal is to diagnose why users do or don't perform a specific behavior — adoption, activation, engagement, retention, habit formation, feature usage, onboarding, conversion.

Both frameworks decompose behavior into components. They complement each other: COM-B provides a comprehensive diagnostic (6 sub-components with TDF drill-down), B=MAP provides a precise action-design lens (3 components with troubleshooting order). Use both on every behavioral dataset.

---

## Table of Contents
1. Extracting Behavioral Instances
2. COM-B Coding
3. TDF Drill-Down
4. B=MAP Coding
5. Per-User Behavioral Profiles
6. Cross-User Pattern Analysis
7. Competing Behaviors and System Dynamics
8. Barrier Prioritization
9. Intervention Mapping
10. Quality Checks
11. Anti-Patterns
12. Output Format

---

## 1. Extracting Behavioral Instances

Before coding anything, extract concrete behavioral episodes from each transcript.

### What counts as behavioral data:

| Data Type | Example | Value |
|-----------|---------|-------|
| **Specific past action** | "Last Tuesday I opened the app after my morning standup" | High — observable behavior with context |
| **Behavioral sequence** | "First I check Slack, then I open the dashboard, then..." | High — reveals anchors and workflow |
| **Failure story** | "I meant to do it but then [specific thing] happened" | High — reveals which component broke |
| **Workaround** | "Instead of using the feature, I just do [alternative]" | High — reveals ability barriers and competing behaviors |
| **Bright spot** | "The one time it worked well was when..." | High — reveals the configuration that succeeds |

### What does NOT count as behavioral data:

| Data Type | Example | Problem |
|-----------|---------|---------|
| **Aspirational statement** | "I'd love to use it more" | Aspiration, not behavior |
| **Opinion about features** | "I think the dashboard is useful" | Attitude, not action |
| **Future prediction** | "I would definitely use that" | Stated intent ≠ behavior |
| **Self-diagnosis** | "I'm just not disciplined enough" | Attribution error — user blames motivation when issue may be ability or prompt |
| **Social desirability** | "Of course I think data-driven decisions are important" | Noise |

### Self-report rule

If a participant says "I usually do X," treat it as a claim requiring corroboration, not as data. Look for the specific instance they describe. If there's no specific instance, flag it as unverified self-report [SR].

---

## 2. COM-B Coding

For each behavioral instance (or non-instance), code the barriers and enablers to the 6 COM-B sub-components.

### Coding Framework

| COM-B Component | Code as barrier when participant describes... | Code as enabler when... |
|-----------------|----------------------------------------------|------------------------|
| **Physical Capability** | Physical difficulty, motor skill issues, accessibility problems, fatigue | Actions executed smoothly, no physical obstacles |
| **Psychological Capability** | Not knowing what to do, confusion, forgetting, cognitive overload, poor decision-making, inability to self-regulate | Clear understanding, easy recall, confident decision-making |
| **Physical Opportunity** | Missing tools/info, bad timing, poor discoverability, environmental friction, no cues/triggers | Everything available, well-timed, prominent, easy to find |
| **Social Opportunity** | Peer discouragement, conflicting norms, no social support, isolation | Peer encouragement, aligned norms, social modelling |
| **Reflective Motivation** | Doesn't believe it'll work, low self-efficacy, no intention/plan, identity conflict, doesn't see consequences | Strong belief in outcomes, confidence, clear plans, identity alignment |
| **Automatic Motivation** | Negative emotion (anxiety, boredom, frustration), no habit, competing impulses, no sense of reward | Positive emotion, habitual, satisfying, intrinsically rewarding |

### Coding Rules

1. **One excerpt can map to multiple COM-B components.** "I didn't know where to find it and I didn't think it mattered" codes to both Psychological Capability (knowledge) and Reflective Motivation (beliefs about consequences).

2. **Code the evidence, not your inference.** If a participant describes frustration, code Automatic Motivation (Emotion). Don't infer they also lack knowledge unless they say so.

3. **Tag evidence type:**
   - **[B]** = Behavioural (described what they actually did)
   - **[SR]** = Self-report (stated a belief or generalisation)
   - **[O]** = Observed (from analytics, usability recording, or observation)

4. **Preserve context.** Include enough surrounding text that another analyst can verify the coding.

5. **Code enablers too.** Not just barriers — enablers reveal leverage points and what to protect.

---

## 3. TDF Drill-Down Coding

For COM-B components where barriers cluster, apply finer-grained Theoretical Domains Framework coding.

| COM-B Component | TDF Domains | Look for... |
|-----------------|-------------|-------------|
| **Physical Capability** | Skills | Descriptions of being unable to execute physical actions |
| **Psychological Capability** | Knowledge | "I didn't know...", "I wasn't aware..." |
| | Skills (cognitive) | "I couldn't figure out...", "It was too complex..." |
| | Memory, Attention & Decision Processes | "I forgot...", "I was distracted...", "I couldn't decide..." |
| | Behavioural Regulation | "I meant to but didn't...", "I can't stick to it..." |
| **Physical Opportunity** | Environmental Context & Resources | "It wasn't there...", "I didn't have time...", "I couldn't find it..." |
| **Social Opportunity** | Social Influences | "Nobody else does it...", "My manager said...", "People would think..." |
| | Social/Professional Role & Identity | "That's not my job...", "Someone like me doesn't..." |
| **Reflective Motivation** | Beliefs about Capabilities | "I can't do it...", "I'm not good at..." |
| | Beliefs about Consequences | "It won't make a difference...", "What's the point..." |
| | Intentions | "I plan to...", "I haven't decided..." |
| | Goals | "It's not a priority...", "I have other things..." |
| | Optimism | "It probably won't work...", "Things never change..." |
| **Automatic Motivation** | Emotion | "It stresses me out...", "I dread it...", "It feels good..." |
| | Reinforcement | "Nothing happens when I do it...", "I never see results..." |

---

## 4. B=MAP Coding

For every behavioral data point, assign to one or more B=MAP components using these codes.

### Prompt Codes

| Code | Definition | Example Quote |
|------|-----------|---------------|
| **P-EXISTS** | User has a prompt that fires | "My morning standup reminds me to check the dashboard" |
| **P-MISSING** | No prompt exists | "I just forget to do it" / "Nothing reminds me" |
| **P-ANCHOR** | Behavior tied to existing routine (Action Prompt) | "Right after I pour coffee, I open the app" |
| **P-CONTEXT** | Behavior relies on external reminder | "I only do it when I get the notification" |
| **P-PERSON** | Behavior relies on memory | "I try to remember but it doesn't work" |
| **P-MISFIRE** | Prompt exists but fires at wrong moment | "The notification comes when I'm in a meeting" |
| **P-NOISE** | Prompt lost among competing prompts | "I get so many notifications I ignore them all" |
| **P-TRAILING** | User describes precise end-moment of anchor | "After I hit 'send' on the standup update..." |

### Ability Codes

| Code | Definition | Example Quote |
|------|-----------|---------------|
| **A-TIME** | Time is the constraint | "It takes too long, I don't have 15 minutes" |
| **A-MONEY** | Cost is the barrier | "The premium tier is too expensive" |
| **A-PHYSICAL** | Physical effort is the barrier | "I have to click through 6 screens" |
| **A-MENTAL** | Cognitive load is the barrier | "I don't know which option to pick" / "It's confusing" |
| **A-ROUTINE** | Doesn't fit existing workflow | "I'd have to completely change my morning" |
| **A-SKILL** | User lacks know-how | "I don't really know how to interpret the data" |
| **A-TOOL** | Tool/resource missing or inadequate | "The app crashes" / "I can't do it on mobile" |
| **A-TINY** | User found or could find a smaller version | "I just look at the top number, that's enough" |
| **A-STARTER** | User does only the first step | "I open it but then close it without doing anything" |

### Motivation Codes

| Code | Definition | Example Quote |
|------|-----------|---------------|
| **M-PERSON** | Intrinsic desire drives behavior | "I genuinely want to understand our metrics" |
| **M-ACTION** | Benefit/punishment drives behavior | "My boss checks if I've updated it" |
| **M-CONTEXT** | Social/environmental pressure | "Everyone on my team does it so I do too" |
| **M-COMPETING** | Different behavior competes for same moment | "I end up checking email instead" |
| **M-CONFLICTING** | Opposing drives toward same behavior | "I want to track food but don't want to think about calories" |
| **M-WAVE** | Motivation was high then crashed | "I used it every day for the first week, then stopped" |
| **M-ENDURING** | Motivation stable over time | "I've always cared about this" |
| **M-SHINE** | Positive feeling after behavior | "When I complete my log I feel accomplished" |
| **M-NO-SHINE** | No positive emotion follows behavior | "I do it but it feels pointless" |

---

## 5. Per-User Behavioral Profiles

For each participant, create a behavioral diagnosis that integrates both frameworks.

### COM-B Diagnosis (per user)

| COM-B Component | Barrier? (Y/N/Partial) | Evidence (key quotes, data source tag) | Strength (Strong/Moderate/Weak) | What needs to change? |
|-----------------|----------------------|----------------------------------------|---------------------------------|-----------------------|
| Physical Capability | | | | |
| Psychological Capability | | | | |
| Physical Opportunity | | | | |
| Social Opportunity | | | | |
| Reflective Motivation | | | | |
| Automatic Motivation | | | | |

**Evidence Strength Criteria:**

| Rating | Definition |
|--------|-----------|
| **Strong** | Multiple data points, corroborated by behavioral [B] or observation [O], consistent across contexts |
| **Moderate** | Multiple data points but self-report only [SR], or strong signal from 2-3 points with some behavioral evidence |
| **Weak** | Single data point, self-report only, or contradicted by other data |

**"What needs to change?" rules:** Be specific. Not "Users need more motivation" but "Users need to believe that completing the checklist reduces errors in their next task (Beliefs about Consequences) — currently 6/8 participants described the checklist as performative."

### B=MAP Profile (per user)

```
## Participant: [ID]

### Target Behavior
After [anchor/context], user will [specific action].

### Action Line Position: ABOVE / BELOW / NO PROMPT

### Prompt Profile
- Type: Person / Context / Action / None
- Anchor (if exists): [specific existing behavior]
- Trailing Edge: [precise moment]
- Reliability: High / Medium / Low
- Failure mode: [what causes prompt to fail]

### Ability Profile
- Time:            Strong / Adequate / Weak
- Money:           Strong / Adequate / Weak
- Physical effort:  Strong / Adequate / Weak
- Mental energy:    Strong / Adequate / Weak
- Routine fit:      Strong / Adequate / Weak
- WEAKEST LINK:    [specific factor]
- Discovery Answer: "[what makes this hard for this user]"
- Breakthrough Direction: Skill up / Tools / Make tiny

### Motivation Profile
- Primary source: Person / Action / Context
- Competing motivations: [list with specific competing behaviors]
- Conflicting motivations: [list tensions]
- Durability: Enduring / Wave / Fluctuating
- Shine present: Yes / No

### Diagnosis
[One paragraph: Why this behavior does/doesn't happen for this user,
stated in B=MAP terms. Which component is the bottleneck?]

### Key Quotes (coded)
- "[quote]" → [B=MAP code] [evidence tag]
- "[quote]" → [COM-B component] [evidence tag]
```

---

## 6. Cross-User Pattern Analysis

### 6a: B=MAP Component Frequency Matrix

Count how often each code appears across all participants:

| Code | P1 | P2 | P3 | P4 | P5 | Total | % |
|------|----|----|----|----|----|----|---|
| P-MISSING | ✓ | | ✓ | ✓ | | 3 | 60% |
| A-MENTAL | ✓ | ✓ | | ✓ | ✓ | 4 | 80% |
| M-COMPETING | ✓ | ✓ | ✓ | | ✓ | 4 | 80% |

**Analysis questions:**
- Which component has the most failure codes? That's the primary bottleneck.
- Which specific code within that component is most frequent? That's the precise intervention point.
- Do any participants have all three components working? These are bright spots — study their configuration.

### 6b: Bottleneck Distribution

| Primary Bottleneck | Count | % of Participants |
|-------------------|-------|-------------------|
| Prompt (no prompt or unreliable) | | |
| Ability (weakest chain link insufficient) | | |
| Motivation (insufficient or competing) | | |
| Multiple (2+ components insufficient) | | |

**Fogg's prediction:** In most behavioral research, Prompt and Ability are the primary bottlenecks for 60-80% of participants. If Motivation shows as primary bottleneck for >50%, verify you haven't fallen into the attribution trap — where users self-diagnose as "unmotivated" when the real issue is ability or prompt.

### 6c: Ability Chain Heatmap

| Ability Factor | Weak (count) | Adequate (count) | Strong (count) |
|---------------|-------------|-------------------|----------------|
| Time | | | |
| Money | | | |
| Physical effort | | | |
| Mental energy | | | |
| Routine fit | | | |

**The column with the most "Weak" entries is the primary ability intervention point.**

### 6d: COM-B Barrier Frequency

| COM-B Component | Barrier count | Enabler count | Net |
|-----------------|--------------|---------------|-----|
| Physical Capability | | | |
| Psychological Capability | | | |
| Physical Opportunity | | | |
| Social Opportunity | | | |
| Reflective Motivation | | | |
| Automatic Motivation | | | |

### 6e: Segment Identification by Behavioral Profile

Cluster participants by their B=MAP configuration:

| Segment | Typical Profile | Example |
|---------|----------------|---------|
| **Habituated** | Strong anchor, high ability, moderate motivation, Shine present | Power users who do it automatically |
| **Motivated but blocked** | High motivation, weak ability (specific chain link), prompt exists | Users who want to but find it too hard |
| **Willing but forgotten** | Adequate motivation, adequate ability, no prompt | Users who'd do it if reminded |
| **Wave riders** | Motivation Wave pattern, ability untested, prompt irrelevant during low-M phases | Users who do it intensely then abandon |
| **Competing behavior wins** | Competing motivation dominates, alternative behavior has better B=MAP | Users whose existing habit is stronger |

---

## 7. Competing Behaviors and System Dynamics

### Competing Behaviors Table

| Competing Behavior | Frequency (participants) | COM-B driver(s) | B=MAP profile | Relationship to target |
|--------------------|-------------------------|-----------------|---------------|----------------------|
| [what they do instead] | [N/total] | [which components] | [M/A/P config] | [directly competes / occupies same slot / undermines] |

### System Dynamics Check

Ask these questions of your coded data:

- **Reinforcing loops:** Is there a loop where NOT doing the behavior makes it harder next time? (E.g., not using the feature → less knowledge → even less likely to use it.)
- **Balancing mechanisms:** Is there anything naturally pushing toward the behavior that you should amplify rather than fight?
- **Delays:** Is the feedback from the behavior too delayed to reinforce it? (E.g., benefit appears weeks later, but cost is immediate.)

---

## 8. Barrier Prioritization

Not all barriers are equal. Prioritize using:

| Criterion | Question |
|-----------|---------|
| **Prevalence** | How many participants showed this barrier? |
| **Severity** | When present, did it completely block the behavior or just reduce it? |
| **Addressability** | Can the product/service team realistically change this? |
| **Upstream position** | Is this a root cause that, if resolved, would reduce other barriers? (E.g., fixing knowledge gaps may also improve self-efficacy.) |

### Priority Matrix

| | High Addressability | Low Addressability |
|---|---|---|
| **High Prevalence + Severity** | **Priority 1** — Act first | **Priority 2** — Investigate workarounds |
| **Low Prevalence + Severity** | **Priority 3** — Address if cheap | **Deprioritise** — Monitor only |

---

## 9. Intervention Mapping

For each prioritized barrier, map to both frameworks' intervention levers.

### COM-B → BCW Intervention Functions

| COM-B Barrier | Applicable Intervention Functions |
|---------------|----------------------------------|
| Physical Capability gap | Training, Enablement |
| Psychological Capability gap (knowledge) | Education, Training |
| Psychological Capability gap (cognitive/regulation) | Training, Enablement, Environmental Restructuring |
| Physical Opportunity barrier | Environmental Restructuring, Enablement, Restriction |
| Social Opportunity barrier | Modelling, Enablement, Environmental Restructuring |
| Reflective Motivation gap | Education, Persuasion, Incentivisation, Modelling |
| Automatic Motivation gap | Persuasion, Incentivisation, Coercion, Environmental Restructuring, Modelling, Enablement |

### B=MAP → Fogg's Design Levers

| Bottleneck | Lever | Specific Intervention Direction |
|-----------|-------|---------------------------------|
| No prompt | Design an Action Prompt (Anchor) | Identify existing behavior to anchor to; match location, frequency, theme |
| Prompt misfires | Fix timing or type | Move prompt to moment when user has ability to act |
| Ability: Time | Make behavior tiny (Scale Back) | Reduce to smallest meaningful version |
| Ability: Mental energy | Make behavior tiny (Starter Step) | Reduce to first step only |
| Ability: Skill | Skill up (one-time) | Provide demonstration or tutorial |
| Ability: Tool | Provide better tool | Remove friction from the interaction |
| Ability: Routine fit | Redesign sequence | Find where behavior fits naturally |
| Motivation: Competing | Remove competing prompt OR make target easier | Competing behavior wins because it has better B=MAP; equalize |
| Motivation: Wave | Don't rely on motivation — focus on A and P | Make behavior so tiny it doesn't need high motivation |
| Motivation: No Shine | Add celebration/reinforcement | Create immediate positive feedback loop |

### Intervention Output Format

For each Priority 1 barrier:
```
BARRIER: [specific barrier, not general]
COM-B COMPONENT: [which sub-component]
B=MAP CODE: [which code]
EVIDENCE: [participant count, key quotes with tags]
INTERVENTION FUNCTIONS (BCW): [2-3 candidates with brief rationale]
DESIGN LEVERS (Fogg): [specific lever + direction]
RECOMMENDED DIRECTION: [one paragraph synthesis]
```

---

## 10. Quality Checks

### Check 1: Attribution Correction

Before finalizing, review every instance where a participant said "I'm lazy / I'm not disciplined / I just don't want to." For each:
- Is there evidence of a prompt issue that the user didn't identify?
- Is there evidence of an ability issue that the user normalized?
- Did the user actually try and fail (ability issue) or never start (prompt issue)?

**Rule:** Reclassify motivation attributions only when behavioral evidence supports a different component. Document the reclassification and evidence.

### Check 2: Bright Spot Analysis

For every participant who succeeds at the behavior:
- What is their exact prompt? (Anchor + Trailing Edge)
- What is their ability configuration? (All 5 links)
- What motivation source sustains it?
- Is Shine present?

**The successful B=MAP configuration is the design blueprint.** It tells you what needs to be true for the behavior to happen.

### Check 3: Compensatory Relationship Verification

For users below the Action Line, test:
- If we increased ability significantly (made it tiny), would current motivation be sufficient?
- If we provided a perfect prompt, would current M + A be above the line?

This determines whether you need to fix one component or multiple.

### Check 4: Recipe Construction Test

For each segment, attempt to write a Tiny Habit recipe:

> After [ANCHOR from their routine], they will [TINIEST VERSION of target behavior].

If you can't write this recipe from your data, you're missing either anchor information or ability reduction options. Go back to the transcripts.

### Check 5: Troubleshooting Order Verification

Verify the analysis followed P → A → M order:
1. **Prompt checked first** — No prompt means behavior never gets a chance
2. **Ability checked second** — Even motivated users won't do hard things
3. **Motivation checked last** — Only investigate after confirming prompt and ability are sufficient

If the analysis jumped to motivation first, re-examine the data for prompt and ability evidence.

---

## 11. Anti-Patterns in Behavioral Analysis

| Anti-Pattern | What it looks like | Fix |
|-------------|-------------------|-----|
| **Theme soup** | Findings as "themes" with no COM-B/B=MAP structure — "Users want simplicity" | Re-code every theme to a component. If it doesn't map, it's not a behavioral finding. |
| **Quote cherry-picking** | One vivid quote justifying a barrier, ignoring contradictory data | Report prevalence counts and note disconfirming evidence. |
| **Motivation monopoly** | All barriers coded as motivation — "They just don't want to" | Re-examine for Capability and Opportunity barriers disguised as motivation. "I don't want to" often means "I don't know how" or "it's too hard." |
| **Collapsing COM-B** | Treating COM-B as single dimension ("they lack capability") | Always code to the 6 sub-component level. |
| **Ignoring enablers** | Only coding barriers, missing what's working | Code enablers too — they reveal leverage points and what to protect. |
| **Self-report = truth** | Taking "I always do X" at face value | Tag as [SR], check against [B] and [O] data, note discrepancies. |
| **No competing behaviors** | Target behavior analyzed in isolation | Map what users do instead and why it persists. |
| **Aspiration as behavior** | "Users want to be productive" treated as target behavior | Apply "can you do it right now?" test. |
| **Solution baked in** | Analysis assumes the intervention ("tooltip will help") before diagnosing | Strip solution. Diagnose COM-B/B=MAP barrier first. |
| **Monolithic user** | All users treated as having same behavioral profile | Segment by B=MAP configuration. |

---

## 12. Output Format

```
## Research Analysis: [Study Name]

### 1. Target Behavior Definition
After [context], user will [specific action].
[COM-B problem statement: WHO isn't doing WHAT in WHAT CONTEXT because IMPACT]

### 2. Data Overview
- Participants: [count, segments]
- Behavioral instances extracted: [count]
- Non-behavioral data discarded: [count, categories]

### 3. COM-B Behavioral Diagnosis
[Completed COM-B-D form with evidence strength ratings for each of 6 sub-components]

### 4. B=MAP Bottleneck Distribution
[Table: % Prompt / % Ability / % Motivation as primary bottleneck]

### 5. Per-Segment Behavioral Profiles
[For each segment: COM-B diagnosis + B=MAP profile + diagnosis statement + key evidence]

### 6. Ability Chain Heatmap
[Cross-participant table of weak/adequate/strong per factor]

### 7. Bright Spot Configuration
[What the successful B=MAP profile looks like — the design blueprint]

### 8. Competing Behaviors
[What users do instead, COM-B drivers, B=MAP configuration]

### 9. System Dynamics
[Reinforcing loops, balancing mechanisms, delays]

### 10. Barrier Priority Matrix
[Prioritized by prevalence, severity, addressability, upstream position]

### 11. Intervention Map
[For each Priority 1 barrier: COM-B component, B=MAP code, evidence,
BCW intervention functions, Fogg design levers, recommended direction]

### 12. Recommended Behavior Recipes
[For each segment: After [anchor], they will [tiny behavior]]

### 13. Confidence Assessment
[Which findings are well-supported vs. hypothetical]

### 14. Open Questions
[What B=MAP/COM-B components remain unclear; what needs follow-up]
```

---

## Deliverable Checklist

Before presenting findings, confirm:

- [ ] All transcripts coded to COM-B components (6 sub-components)
- [ ] All behavioral instances coded to B=MAP (P/A/M codes)
- [ ] Evidence tagged as [B] behavioural, [SR] self-report, or [O] observed
- [ ] TDF drill-down completed for clustered barrier components
- [ ] COM-B-D form populated with evidence strength ratings
- [ ] Per-user B=MAP profiles completed
- [ ] Cross-user frequency matrices built
- [ ] Bottleneck distribution calculated
- [ ] Ability chain heatmap populated
- [ ] Competing behaviors mapped with COM-B/B=MAP drivers
- [ ] System dynamics (loops, delays) identified where present
- [ ] Attribution correction done (self-blamed motivation re-examined)
- [ ] Bright spots analyzed (successful configuration documented)
- [ ] Barriers prioritized by prevalence, severity, addressability, upstream
- [ ] Priority 1 barriers linked to BCW intervention functions AND Fogg design levers
- [ ] Behavior recipes attempted for each segment
- [ ] Compensatory relationships tested (which component fix would be sufficient?)
- [ ] No unsupported claims — every conclusion traced to specific participant data
- [ ] Distinction maintained between what participants DID vs. what they SAID
- [ ] Troubleshooting order verified: P → A → M
