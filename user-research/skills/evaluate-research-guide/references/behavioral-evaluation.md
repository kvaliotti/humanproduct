# Behavioral Research Guide Evaluation Reference

Synthesized from COM-B / Behaviour Change Wheel (Michie et al.) and B=MAP / Tiny Habits (Fogg).

Use this reference when evaluating guides where the research goal is to understand, drive, change, or sustain a specific user behavior — adoption, activation, engagement, retention, habit formation, feature usage, onboarding completion, conversion actions, churn prevention framed as behavior.

A guide that fails this evaluation will collect rich anecdotes but miss systematic behavioral coverage — producing stories without diagnosis.

---

## Section A: Structural Alignment

### A1. COM-B Structural Integrity

| # | Criterion | What to Check | Score /4 |
|---|---|---|---|
| A1.1 | **Opens with behaviour, not attitude** | Does the guide start by reconstructing what the participant actually did (specific instance), or does it open with opinion/satisfaction questions? | |
| A1.2 | **COM-B sequence logical** | Does the guide move through components in a deliberate order? Recommended: Capability → Opportunity → Motivation (concrete to personal). Random ordering signals the guide was assembled, not designed. | |
| A1.3 | **Time allocations present** | Are minutes allocated per section? Without time-boxing, interviewers spend 80% on the first interesting topic and run out of time. | |
| A1.4 | **Competing behaviours section exists** | Is there a dedicated section exploring what participants do instead of the target behaviour? | |
| A1.5 | **Wrap-up captures missed ground** | Does the guide end with an open question allowing the participant to surface barriers the structure missed? | |

**Red flag:** If A1.1 fails, the guide will prime participants to give attitude data, contaminating everything that follows.

### A2. B=MAP Structural Alignment

| Check | Pass | Fail |
|---|---|---|
| Prompt questions appear before ability questions | Sections ordered P → A → M | Guide starts with "why" / motivation questions |
| Ability questions appear before motivation questions | Ability explored in depth before motivation | Motivation dominates the guide |
| Routine/workflow mapping appears in warm-up | First questions establish behavioral context | Guide jumps straight to attitudes/opinions |
| Synthesis section tests each component in isolation | "If this were easier, would you...?" and "If you had a perfect reminder, would you...?" | No component isolation at close |

**Critical:** If the guide follows neither COM-B nor B=MAP structural order, it will produce motivation-biased data. Restructure entirely.

---

## Section B: COM-B Coverage

For each component, assess whether the guide has probes that will reliably surface barriers.

| # | Component | Minimum Standard | Score /4 |
|---|---|---|---|
| B1 | **Physical Capability** | At least 1-2 probes about physical execution, motor skills, or accessibility. If not applicable, explicitly noted as ruled out. | |
| B2 | **Psychological Capability** | At least 3-4 probes covering knowledge, cognitive skills, memory/attention, decision processes, and self-regulation. This is the richest component — a single question is insufficient. | |
| B3 | **Physical Opportunity** | At least 2-3 probes about environmental context: discoverability, timing, tools, cues, resources. | |
| B4 | **Social Opportunity** | At least 2 probes about social norms, peer behaviour, organisational expectations, social pressure. | |
| B5 | **Reflective Motivation** | At least 3 probes covering beliefs about consequences, self-efficacy, intentions, goals, and identity. | |
| B6 | **Automatic Motivation** | At least 2 probes about emotional responses, habits, impulses, and reinforcement. This component is most frequently missing. | |

### B7: Distribution Balance

| Distribution | Rating |
|---|---|
| All 6 components have adequate probes, roughly proportional to complexity | 4 |
| 5 of 6 covered well; one component light | 3 |
| Heavy cluster in 2-3 components (usually Psych Capability + Reflective Motivation) | 2 |
| Probes don't systematically map to COM-B | 1 |

---

## Section C: B=MAP Component Quality

### C1. Prompt Questions

| Criterion | What Good Looks Like | Red Flag |
|---|---|---|
| **Prompt existence tested** | "What happened right before you did [behavior]?" | No questions about what triggers the behavior |
| **Prompt type classified** | Questions distinguish Person/Context/Action prompts | All prompt questions assume notifications (Context Prompts only) |
| **Anchors explored** | "What do you always do right before/after?" | Guide treats prompts as something to be designed, not discovered in existing routines |
| **Trailing Edge probed** | "What's the very last thing you do when you [anchor]?" | Anchors left fuzzy ("after breakfast") |
| **Prompt failure diagnosed** | "You mentioned forgetting — what was different that day?" | No questions about when prompts fail or are ignored |
| **Prompt-ability alignment checked** | "When the reminder fires, where are you? Can you act on it?" | Assumes prompts reach users when they have ability to act |

Minimum: 4 questions covering prompts. Score: ___/6

### C2. Ability Questions

| Criterion | What Good Looks Like | Red Flag |
|---|---|---|
| **All 5 Ability Chain links covered** | Separate questions for Time, Money, Physical effort, Mental energy, Routine fit | Missing links (Routine fit and Mental energy most commonly omitted) |
| **Weakest link surfaced** | Questions probe which specific factor is the bottleneck | Generic "is it hard?" without decomposition |
| **Discovery Question asked** | "What makes this hard to do?" asked in multiple ways | No explicit difficulty exploration |
| **Breakthrough Question explored** | Questions about skills, tools, AND making it tiny | Only one lever explored (usually tools) |
| **Starter Step / Scaling Back tested** | "What's the smallest version you could do?" | Only studies the full-size behavior |
| **Behavioral observation included** | Guide includes protocol for watching participant perform | 100% self-report, no observation |
| **Compensatory relationship tested** | "If this were ridiculously easy, would low motivation still block you?" | M and A treated as independent |

Minimum: 5 questions covering ability. Score: ___/7

### C3. Motivation Questions

| Criterion | What Good Looks Like | Red Flag |
|---|---|---|
| **PAC sources distinguished** | Separate questions for Person, Action, Context motivation | "Are you motivated to do this?" (undifferentiated) |
| **Competing motivations mapped** | "When you don't do this, what are you doing instead?" | Assumes the alternative is "nothing" |
| **Conflicting motivations probed** | "Is there any part of you that doesn't want to do this?" | Only explores positive motivation |
| **Motivation durability tested** | Questions about how motivation has changed over time | Assumes current motivation = stable motivation |
| **Motivation Wave detected** | "Was there a time you were really excited and then it faded?" | No questions about motivation decay |
| **Mom Test applied** | Questions about what users DID, not what they SAY they'd do | "Would you use this feature?" type questions |

Minimum: 4 questions covering motivation. Score: ___/6

---

## Section D: TDF Drill-Down Readiness

| # | Criterion | What to Check | Score /4 |
|---|---|---|---|
| D1 | **TDF drill-down probes available** | For each COM-B component, are there additional TDF-domain-level probes ready for when a barrier surfaces? | |
| D2 | **Decision rules for drilling down** | Is it clear when to switch from COM-B-level to TDF-level probes? (e.g., "If participant mentions confusion, use Knowledge and Memory/Attention probes.") | |
| D3 | **TDF-to-COM-B mapping noted** | Can the interviewer see which TDF domain maps to which COM-B component without memorising? | |

---

## Section E: Anti-Pattern Detection

### E1. Opinion vs. Behavior Filter

| Question Type | Status |
|---|---|
| Asks about a specific past behavior | Keep |
| Asks about a specific observable action | Keep |
| Asks for an opinion about a hypothetical | Flag — rewrite |
| Asks for a general attitude | Flag — rewrite |
| Asks for a prediction of future behavior | Remove |
| Asks leading questions about motivation | Remove |

**Threshold:** If more than 30% of questions are opinion/hypothetical, the guide will produce unreliable data. Rewrite those questions to target specific past behaviors.

### E2. Attribution Bias Traps

| Trap | Example | Problem | Fix |
|---|---|---|---|
| **Self-blame trap** | "Why don't you do [behavior] more often?" | Participant cites motivation ("I'm lazy") when real issue is ability or prompt | "Walk me through what happens on a day when you don't do [behavior]." |
| **Aspiration trap** | "What would you like to do differently?" | Produces aspirations, not behavioral data | "What have you actually tried to change?" |
| **Social desirability trap** | "Do you think [behavior] is important?" | Everyone says yes; zero signal | "When was the last time you actually did [behavior]?" |
| **Frequency inflation trap** | "How often do you [behavior]?" | Participants overestimate frequency | "Think about this past week specifically. On which days did you do [behavior]?" |
| **Motivation inflation trap** | "How motivated are you?" | Interview context inflates motivation | "Think of your lowest-motivation day this week. What happened with [behavior]?" |

**Threshold:** If the guide contains 3+ attribution bias traps, the data will misdiagnose the behavioral bottleneck.

### E3. Component Coverage Balance

| Component | Minimum | Ideal | Imbalanced |
|---|---|---|---|
| Prompt | 4 questions | 6-8 | <3 questions |
| Ability | 5 questions | 8-10 | <4 questions |
| Motivation | 4 questions | 6-8 | >12 questions (motivation-heavy) |

**Common imbalance:** 80% motivation questions, 20% ability, 0% prompt. This is the default when guides are written without a behavioral framework. The guide will conclude "users aren't motivated enough" even when the real issue is a missing prompt or a broken Ability Chain link.

---

## Section F: Methodological Safeguards

| # | Criterion | What to Check | Score /4 |
|---|---|---|---|
| F1 | **Social desirability mitigated** | Does the guide use indirect probes for sensitive behaviours? Does it normalise non-performance ("Many people don't do X — tell me about your experience")? | |
| F2 | **Self-report validated** | Is there a plan to cross-reference what participants say with behavioural data (analytics, observation)? Or at minimum, probes requesting concrete evidence ("Show me...", "When exactly...")? | |
| F3 | **Coding system included** | Is there a COM-B/B=MAP tagging column/system so responses can be mapped to components during or immediately after the interview? | |
| F4 | **Piloted** | Has the guide been tested in at least one practice interview? Probe wording that reads well on paper often fails in conversation. | |

---

## Section G: Probe Quality

| # | Criterion | What to Check |
|---|---|---|
| G1 | **Open-ended, not closed** | "Walk me through what happened when you got to that screen" vs. "Did you find it confusing?" |
| G2 | **Specific instances, not generalities** | "The last time" or "a specific occasion" vs. "usually" or "in general" |
| G3 | **No "why" as primary probe** | "Why" invites rationalisation. Use "What was happening when...", "What did you do next..." |
| G4 | **No leading questions** | "What were you feeling?" not "How frustrated were you?" |
| G5 | **No jargon or framework language** | Participants should never hear "capability", "opportunity", "motivation", "COM-B", "TDF", "B=MAP", "prompt", "ability chain" |
| G6 | **Probes, not scripts** | Flexible probe points, not verbatim scripts |

---

## Section H: Brief Alignment

| # | Criterion | What to Check |
|---|---|---|
| H1 | **Target behaviour matches** | Does the guide investigate the exact behaviour specified in the brief (same Who/What/When/Where/How often/With whom)? |
| H2 | **All brief research questions covered** | For every research question in the brief, is there at least one corresponding probe in the guide? |
| H3 | **No scope creep** | Does the guide stay focused on the target behaviour, or does it wander into adjacent topics, satisfaction, or feature wishlists? |

---

## Section I: Behavioral Specificity of Outputs

Will this guide produce data that maps to the behavioral model?

| Output Test | Pass | Fail |
|---|---|---|
| Can you fill in the COM-B assessment from the answers? | Each component has dedicated questions | Some components have no questions |
| Can you fill in the Ability Chain assessment from the answers? | Each link has dedicated questions | Some links have no questions |
| Can you classify the prompt type from the answers? | Questions distinguish Person/Context/Action | Prompt type indeterminate |
| Can you identify the PAC motivation source from the answers? | Separate questions per source | Motivation is undifferentiated |
| Can you place the user on the Action Line from the answers? | Both M and A assessed, prompt existence confirmed | Only one component assessed |
| Can you generate a Fogg-format recipe from the answers? | "After [anchor], user will [behavior]" constructable | Anchors and specific behaviors not captured |

---

## Common Failure Patterns

| Pattern | Symptom | Fix |
|---|---|---|
| **Satisfaction interview in disguise** | Opens with "How do you feel about...", majority opinion-based | Restructure to open with behavioural reconstruction; convert opinion probes to context probes |
| **Capability + Motivation only** | No probes for Physical Opportunity or Social Opportunity | Add environment, trigger/cue, social norm, and peer behaviour probes |
| **Automatic Motivation missing** | No probes for emotion, habit, impulse, or reinforcement | Add "What's the first feeling...", "Is this autopilot or deliberate...", "What would make it satisfying..." |
| **Leading the witness** | "Don't you think the new feature would help?" | Rewrite as neutral, open probes |
| **Script rigidity** | Verbatim questionnaire read in order | Convert to probe points with flexibility notes; mark must-ask vs. follow-if-relevant |
| **No drill-down protocol** | COM-B covered but no depth when barriers surface | Add TDF drill-down probes with decision rules |
| **Scope drift** | Covers target behaviour plus 3 other topics | Cut everything not directly investigating the target behaviour's barriers |
| **Motivation-first assumption** | Guide starts with and emphasises motivation | Restructure: P → A → M. Check prompt and ability before motivation |
| **Only full-size behavior studied** | No Starter Step or scaling-back questions | Add "What's the smallest version you could do?" |

---

## Quick Revision Playbook

| Problem Found | Revision Action |
|---|---|
| Guide starts with motivation | Move motivation section to end. Add routine mapping as opener. |
| No prompt questions exist | Add Prompt Exploration section with anchor mapping and prompt failure analysis. |
| Ability treated as monolithic | Break into 5 Ability Chain questions. Add Discovery Question and Breakthrough Question. |
| All questions are opinion-based | Rewrite each as "Tell me about the last time..." or "Walk me through..." |
| No observation protocol | Add: "Can you show me how you do this?" or "Let's walk through this together." |
| Only full-size behavior studied | Add Starter Step question: "What's the smallest version you could do?" |
| No component isolation at end | Add: "If this were 10x easier..." and "If you had a perfect reminder..." |
| Segments not distinguishable | Add questions that differentiate behavioral profiles: when it works vs. when it doesn't. |
| No COM-B coding system | Add tagging column so responses map to components during the interview. |

---

## Reviewer Checklist (Quick Reference)

```
STRUCTURE
[ ] Guide follows P → A → M order (B=MAP) or C → O → M order (COM-B)
[ ] Opens with routine/workflow mapping or behavioral reconstruction
[ ] Closes with component isolation questions
[ ] Time allocations present per section

COM-B COVERAGE
[ ] Physical Capability: 1-2 probes (or explicitly ruled out)
[ ] Psychological Capability: 3-4 probes
[ ] Physical Opportunity: 2-3 probes
[ ] Social Opportunity: 2 probes
[ ] Reflective Motivation: 3 probes
[ ] Automatic Motivation: 2 probes

B=MAP COVERAGE
[ ] Prompt: 4+ questions (existence, type, anchors, failure)
[ ] Ability: 5+ questions (all 5 chain links, discovery, breakthrough)
[ ] Motivation: 4+ questions (PAC sources, competing, conflicting, durability)

ANTI-PATTERNS
[ ] <30% opinion/hypothetical questions
[ ] No attribution bias traps
[ ] Component coverage is balanced (not motivation-heavy)
[ ] All outputs map to behavioral model components

SAFEGUARDS
[ ] Social desirability mitigated
[ ] Self-report validation planned
[ ] Coding system included
[ ] Guide piloted
```
