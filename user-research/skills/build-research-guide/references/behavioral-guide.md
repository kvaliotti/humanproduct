# Behavioral Research Guide Methodology

Synthesized from COM-B (Capability, Opportunity, Motivation — Behavior) and B=MAP (Behavior = Motivation + Ability + Prompt, from BJ Fogg's Behavior Design). Use this reference when building a research guide for behavioral research — adoption, engagement, retention, onboarding, habit formation, feature usage, or any study where the primary goal is understanding why a specific behavior is or isn't happening.

Both frameworks structure the guide differently:
- **COM-B** provides a comprehensive diagnostic skeleton (6 sub-components with TDF drill-downs)
- **B=MAP** provides a precise troubleshooting order (Prompt → Ability → Motivation) and action-design probes

Use both in every behavioral guide. B=MAP determines the section order. COM-B ensures comprehensive coverage. The general guide reference covers opening, closing, and conversational tactics — this file covers the behavioral core.

---

## Table of Contents
1. Core Principles
2. Guide Architecture
3. Section 0: Warm-Up and Routine Mapping
4. Section 1: Prompt Exploration
5. Section 2: Ability Exploration
6. Section 3: Motivation Exploration
7. Section 4: Competing Behaviors
8. Section 5: Behavior-Level Synthesis
9. COM-B Comprehensive Coverage
10. Adaptive Interviewing: COM-B Screen → TDF Drill-Down
11. Guide Construction Rules
12. Probing Techniques for Behavioral Interviews
13. Note-Taking and Coding System
14. Guide Template

---

## 1. Core Principles

### From the BCW (Behaviour Change Wheel)
1. **Ask about specific instances, not generalities.** "Tell me about the last time you [behavior]" beats "How often do you [behavior]?" People confabulate frequencies; they recall episodes.
2. **Don't ask directly why.** "Why did you / didn't you..." invites post-hoc rationalization. Instead, reconstruct the context, actions, and decision points.
3. **Beware social desirability.** Participants over-report "good" behaviors and under-report "bad" ones. Use indirect probes and triangulation.
4. **Use COM-B as the skeleton, not the script.** Participants don't think in COM-B terms. The guide's job is to elicit COM-B-relevant data through natural conversation.
5. **Adaptive depth.** Use COM-B-level questions first. When a barrier surfaces, drill into the relevant TDF domains for granularity.

### From B=MAP
1. **Follow the troubleshooting order: Prompt → Ability → Motivation.** This is counterintuitive — most researchers start with motivation ("why do you want X?"). B=MAP reverses this because the most common bottlenecks are prompts and ability, not motivation.
2. **Ask for stories, not opinions.** Every question should pull a specific recent instance.
3. **Distinguish behaviors from aspirations.** If the participant answers with an aspiration ("I want to eat healthier"), redirect: "Can you tell me about a specific moment when you made a food choice? What happened?"
4. **Observe, don't just ask.** Self-reported ability is unreliable. What they call "easy" might have friction they've normalized.
5. **Map the full sequence.** Don't study the behavior in isolation. Map: what happens before → the behavior → what happens after. The "before" is where anchors live. The "after" is where celebration (Shine) happens or doesn't.
6. **Look for bright spots.** Some participants already do the behavior successfully. Their B=MAP configuration is the answer key.

---

## 2. Guide Architecture

The guide follows B=MAP's troubleshooting order for section sequence, with COM-B ensuring no component is missed.

| Section | Duration | B=MAP Focus | COM-B Coverage |
|---------|----------|-------------|----------------|
| 0: Warm-Up & Routine Mapping | 5 min | Context for anchors | — |
| 1: Prompt Exploration | 10-15 min | Prompt (existence, type, reliability) | — |
| 2: Ability Exploration | 15-20 min | Ability (5 chain links + 3 levers) | Physical Capability, Psychological Capability, Physical Opportunity |
| 3: Motivation Exploration | 10-15 min | Motivation (PAC sources, competing, durability) | Reflective Motivation, Automatic Motivation, Social Opportunity |
| 4: Competing Behaviors | 5-10 min | Competing behaviors | All components for the competing behavior |
| 5: Behavior-Level Synthesis | 5 min | Full B=MAP reconstruction | — |

Total: 50-70 min. Adjust proportionally for shorter sessions.

---

## 3. Section 0: Warm-Up and Routine Mapping (5 min)

**Purpose:** Establish the participant's daily routines — these are the raw material for identifying anchors and understanding behavior in context.

| Question Type | Example | What It Reveals |
|--------------|---------|-----------------|
| Routine mapping | "Walk me through your typical [morning/workday/evening]." | Existing behaviors that could serve as anchors |
| Recent behavior recall | "Think about the last time you [target behavior area]. What happened right before?" | Natural prompts and sequences |
| Environment description | "Describe your workspace/setup when you typically do [activity]." | Context that enables or blocks ability |

**Rule:** Never start with opinions or attitudes. Start with observable routines and recent events.

---

## 4. Section 1: Prompt Exploration (10-15 min)

**Purpose:** Determine whether the behavior has a prompt, what type it is, and whether it fires at the right moment.

### 1a: Detecting Whether a Prompt Exists

| Question | What It Tests | B=MAP Link |
|----------|--------------|------------|
| "When was the last time you did [behavior]? What happened right before that made you do it?" | Whether any prompt exists | P: existence |
| "Have you ever intended to [behavior] but simply forgot?" | Person Prompt failure | P: reliability |
| "What reminds you to [behavior]? A notification? A habit? Something you see?" | Prompt type classification | P: Person/Context/Action |
| "Are there days when you do [behavior] and days when you don't? What's different about those days?" | Prompt consistency | P: reliability across contexts |

### 1b: Mapping Existing Anchors

| Question | What It Tests | B=MAP Link |
|----------|--------------|------------|
| "What do you always do right before [behavior]?" | Anchor identification | P: Action Prompt |
| "What's the very last thing you do when you [preceding activity]?" | Trailing Edge of potential anchor | P: precision |
| "If you had to describe your routine as a sequence — first I do X, then Y, then Z — where does [behavior] fit?" | Behavior sequencing | P: natural placement |
| "Is there a specific moment in your day when [behavior] would feel natural?" | Anchor-behavior matching | P: location/frequency/theme fit |

### 1c: Prompt Failure Analysis

| Question | What It Tests | B=MAP Link |
|----------|--------------|------------|
| "You mentioned you forgot to [behavior] last [day]. What was different about that day?" | Why prompt failed | P: context disruption |
| "Do you get any reminders or notifications for this? How do you respond to them?" | Context Prompt effectiveness | P: desensitization |
| "When the reminder fires, where are you and what are you doing?" | Prompt-ability alignment | P + A: prompt fires when ability is zero |

---

## 5. Section 2: Ability Exploration (15-20 min)

**Purpose:** Identify which link in the Ability Chain is weakest and what makes the behavior hard to do (Discovery Question).

### 2a: The Discovery Question Sequence

**Never ask:** "Is this hard for you?" (binary, pride-biased)

**Instead, use behavioral excavation:**

| Ability Factor | Question | What It Reveals |
|---------------|----------|-----------------|
| **Time** | "How long does this take you? Walk me through it step by step." | Whether time is the constraint |
| **Time** | "If you had to do this in 2 minutes instead of 10, what would you cut?" | Which sub-steps are the real time sinks |
| **Money** | "What did you need to buy/subscribe to/pay for to do this?" | Financial barriers |
| **Physical effort** | "Show me how you do this. [Observe.] What parts feel tedious?" | Physical friction points |
| **Mental energy** | "When you sit down to do this, what's the first thing you have to figure out?" | Cognitive load at entry |
| **Mental energy** | "Is there a point where you have to make a decision and you're not sure what to choose?" | Decision fatigue / ambiguity |
| **Routine fit** | "Does this slot into something you already do, or do you have to make special time for it?" | Disruption to existing workflow |
| **Routine fit** | "What do you have to stop doing in order to do this?" | Displacement cost |

### 2b: The Breakthrough Question Sequence

**Purpose:** Explore the three ability levers — skills, tools, tiny.

| Lever | Question | What It Reveals |
|-------|----------|-----------------|
| **Skills** | "Was there a point where you didn't know how to do a specific step? What did you do?" | Skill gaps and self-teaching patterns |
| **Skills** | "If someone showed you exactly how to do this in 30 seconds, would that change things?" | Whether a demonstration would shift perception of difficulty |
| **Tools** | "What tools/apps/resources do you use for this? Are there any you've tried and stopped using?" | Tool friction and tool-switching behavior |
| **Tools** | "Is there anything that would make this faster or less annoying?" | Unmet tool needs |
| **Tiny** | "What's the smallest version of this you could do and still feel like you did something?" | Natural Starter Step identification |
| **Tiny** | "If you could only do one part of this, which part would it be?" | Core vs. peripheral sub-behaviors |

### 2c: Observational Ability Assessment

If possible, observe the participant performing the behavior. Score each Ability Chain link:

```
Time:            [Strong / Adequate / Weak]
Money:           [Strong / Adequate / Weak]
Physical effort: [Strong / Adequate / Weak]
Mental energy:   [Strong / Adequate / Weak]
Routine fit:     [Strong / Adequate / Weak]

Weakest link: _______________
```

### COM-B Mapping for Section 2

This section covers three COM-B components through B=MAP's lens:

**Physical Capability** (mapped from Physical effort + Skills):
- "When you were doing [behavior], was there anything that was physically difficult or awkward?"
- "Were there any steps where you had to figure out how to physically do it — tapping, swiping, navigating?"

**Psychological Capability** (mapped from Mental energy + Skills + Knowledge):
- "At that point, did you know what you were supposed to do next?" (Knowledge)
- "How did you figure out what to do?" (Skills, decision processes)
- "Was there a moment where you had to weigh up options or make a decision? Walk me through that." (Decision processes)
- "Was there anything you needed to remember but forgot, or found hard to keep track of?" (Memory/Attention)
- "Were there other things competing for your attention at that moment?" (Attention)
- "Did you have a plan for how you'd approach this, or were you figuring it out as you went?" (Behavioral regulation)

**Physical Opportunity** (mapped from Routine fit + Tools + Environment):
- "Where were you when this happened? What was the setting like?" (Environmental context)
- "Was there anything about the [app/tool/space] that made it easier or harder?" (Environmental context & resources)
- "Did you have everything you needed — time, tools, information — right when you needed it?" (Resources)
- "Was there anything prompting you to do [behavior] at that moment, or did you have to remember on your own?" (Cues/triggers)
- "If I were watching over your shoulder, what would I have seen on the screen?" (Reconstruct physical opportunity)

---

## 6. Section 3: Motivation Exploration (10-15 min)

**Purpose:** Map motivation sources, competing motivations, conflicting motivations, and durability. This comes LAST because by now you know whether the real issue is prompt or ability — not motivation.

### 3a: Motivation Source Identification (PAC)

| Source | Question | What It Reveals |
|--------|----------|-----------------|
| **Person** (intrinsic) | "When you think about [behavior], what feels appealing about it to you personally?" | Internal desire |
| **Person** | "If nobody knew whether you did this or not, would you still do it?" | Intrinsic vs. extrinsic |
| **Action** (benefit/punishment) | "What happens if you do this? What happens if you don't?" | Carrot and stick dynamics |
| **Action** | "Does anything good come from doing this, right in the moment?" | Immediate reinforcement vs. delayed payoff |
| **Context** (social/environmental) | "Do the people around you — colleagues, friends, family — do this too?" | Social pressure / modeling |
| **Context** | "Has anyone asked you to do this, or is it your own idea?" | External pressure |

### 3b: Competing and Conflicting Motivations

| Question | What It Reveals |
|----------|-----------------|
| "When you choose NOT to do [behavior], what are you doing instead?" | Competing behaviors (different behaviors competing for the same moment) |
| "Is there any part of you that doesn't want to do this even though another part does?" | Conflicting motivations (opposing drives toward same behavior) |
| "What's the downside of doing this?" | Hidden costs that suppress motivation |
| "Have you ever been really excited about this and then that excitement faded?" | Motivation Wave pattern |

### 3c: Motivation Durability

| Question | What It Reveals |
|----------|-----------------|
| "How long have you wanted to do this?" | Aspiration (enduring) vs. Wave (temporary) |
| "Was there a specific moment that made you want to start?" | Trigger event for Motivation Wave |
| "On a scale of 1-10, how motivated are you today vs. when you first started?" | Motivation decay rate |
| "What would make you stop wanting to do this entirely?" | Motivation fragility |

### COM-B Mapping for Section 3

**Social Opportunity:**
- "Do the people around you — colleagues, friends, team — also do [behavior]?" (Social norms)
- "Has anyone ever encouraged or discouraged you from doing [behavior]?" (Social influences)
- "How would your [manager/team/peers] react if they knew you did / didn't do [behavior]?" (Social pressure)
- "Is this something people in your [role/community/culture] are expected to do?" (Role & identity)

**Reflective Motivation:**
- "Before you [did/didn't do the behavior], had you thought about doing it? Was there a plan?" (Intentions, Goals)
- "What did you think would happen if you did [behavior]? And if you didn't?" (Beliefs about consequences)
- "How confident were you that you could do it successfully?" (Beliefs about capabilities / self-efficacy)
- "Is [behavior] the kind of thing someone in your role is supposed to do? Does it fit with how you see yourself?" (Identity)
- "Looking back, are you glad you [did/didn't do it]? What would you do differently?" (Evaluative reflection)

**Automatic Motivation:**
- "When you think about doing [behavior], what's the first feeling that comes up?" (Emotion)
- "Is this something you do on autopilot, or does it take deliberate effort every time?" (Habit)
- "Was there a moment where you felt pulled toward doing something else instead?" (Impulses, desires)
- "What would make doing [behavior] feel rewarding — not just useful, but satisfying?" (Reinforcement)
- "Is there anything about [behavior] that feels unpleasant, boring, or anxiety-inducing?" (Emotional barriers)

---

## 7. Section 4: Competing Behaviors (5-10 min)

> "When you didn't do [target behavior], what did you do instead? Walk me through that."

For each competing behavior, briefly probe:
- Why it was easier/more appealing (map to COM-B)
- Whether it's habitual or deliberate
- What would need to change for the target behavior to "win"

---

## 8. Section 5: Behavior-Level Synthesis (5 min)

**Purpose:** Close by having the participant reconstruct the full B=MAP picture in their own words.

| Question | What It Produces |
|----------|-----------------|
| "If you were going to teach someone else to do this, what would you tell them?" | User's mental model of the behavior |
| "What's the one thing that would make the biggest difference in you doing this more consistently?" | User-identified bottleneck (compare against your B=MAP analysis) |
| "If this were ridiculously easy — like 10 seconds — would you do it every time?" | Tests whether ability is the real bottleneck |
| "If you had the perfect reminder at the perfect moment, would that help?" | Tests whether prompt is the real bottleneck |

---

## 9. COM-B Comprehensive Coverage

Use this as a checklist after building the guide. Every COM-B sub-component must have at least 2 probes. Some will be covered naturally by the B=MAP sections above. Fill gaps with the probes below.

| COM-B Component | Sub-component | Minimum Probes | Covered by B=MAP Section |
|----------------|---------------|----------------|--------------------------|
| Capability | Physical | 2 | Section 2 (Ability) |
| Capability | Psychological | 2 | Section 2 (Ability) |
| Opportunity | Physical | 2 | Section 2 (Ability) |
| Opportunity | Social | 2 | Section 3 (Motivation) |
| Motivation | Reflective | 2 | Section 3 (Motivation) |
| Motivation | Automatic | 2 | Section 3 (Motivation) |

---

## 10. Adaptive Interviewing: COM-B Screen → TDF Drill-Down

The BCW recommends a two-level approach:

**Level 1 — COM-B filter questions:** Run through all 6 sub-components with broad probes (Sections 2-3 above). Identify which components show barriers.

**Level 2 — TDF drill-down:** For components where barriers surface, drill into the specific TDF domains:

| COM-B Component | TDF Domains for Drill-Down |
|----------------|---------------------------|
| Physical Capability | Skills |
| Psychological Capability | Knowledge, Skills, Memory/Attention/Decision Processes, Behavioral Regulation |
| Physical Opportunity | Environmental Context & Resources |
| Social Opportunity | Social Influences, Social/Professional Role & Identity |
| Reflective Motivation | Beliefs about Capabilities, Beliefs about Consequences, Intentions, Goals, Social/Professional Role & Identity, Optimism |
| Automatic Motivation | Emotion, Reinforcement |

**Decision rule:** If a COM-B component shows no barrier signal after 2-3 probes, move on. If a barrier surfaces, switch to the relevant TDF domain questions for 3-5 minutes before moving to the next COM-B component.

---

## 11. Guide Construction Rules

### Rule 1: Follow the Troubleshooting Order
Structure the guide as P → A → M. Resist the urge to start with "why" questions (motivation). Start with "what happens" questions (prompts and sequences).

### Rule 2: Ask for Stories, Not Opinions
Every question should pull a specific recent instance. "Tell me about the last time you..." beats "Do you usually..." every time.

### Rule 3: Distinguish Behaviors from Aspirations
If the participant answers with an aspiration ("I want to eat healthier"), redirect: "Can you tell me about a specific moment when you made a food choice? What happened?"

### Rule 4: Use the Discovery Question as Your North Star
"What makes this hard to do?" should be asked in multiple ways, from multiple angles. The weakest Ability Chain link often isn't obvious to the participant — they'll say "I'm just lazy" (motivation attribution) when the real issue is routine fit or mental energy.

### Rule 5: Observe, Don't Just Ask
Wherever possible, watch the participant perform the behavior. Self-reported ability is unreliable. What they call "easy" might have friction they've normalized. What they call "hard" might have a simple Starter Step they haven't considered.

### Rule 6: Map the Full Sequence
Don't study the behavior in isolation. Map: what happens before → the behavior → what happens after. The "before" is where anchors live. The "after" is where celebration (Shine) happens or doesn't.

### Rule 7: Look for Bright Spots
Some participants already do the behavior successfully. Their B=MAP configuration is the answer key. Spend disproportionate time understanding their prompt, ability setup, and what makes it feel natural.

---

## 12. Probing Techniques for Behavioral Interviews

| Situation | Probe | Purpose |
|-----------|-------|---------|
| Participant says "I'm just lazy" | "Let's forget about motivation for a second. Walk me through what would need to happen physically for you to do this right now." | Redirect from motivation attribution to ability analysis |
| Participant says "It's easy, I just don't do it" | "When was the last time you intended to do it but didn't? What was happening at that exact moment?" | Surface missing prompt or competing behavior |
| Participant gives aspirational answer | "That's the goal. Can you tell me about one specific time you did something toward that goal?" | Ground in observable behavior |
| Participant can't identify what's hard | "If I watched you do this on video, where would I see you hesitate or slow down?" | Externalize the ability assessment |
| Participant describes a burst-and-bust pattern | "Tell me about a time when you did it consistently for a while, then stopped. What changed?" | Identify Motivation Wave and what happens when it crashes |

---

## 13. Note-Taking and Coding System

### COM-B Real-Time Coding

Include a coding column in the note-taking template so the researcher can tag responses to COM-B components during the interview.

| Code | Component |
|------|-----------|
| C-Ph | Capability — Physical |
| C-Ps | Capability — Psychological |
| O-Ph | Opportunity — Physical |
| O-So | Opportunity — Social |
| M-Re | Motivation — Reflective |
| M-Au | Motivation — Automatic |

### B=MAP Tags

| Tag | Component |
|-----|-----------|
| P | Prompt (existence, type, reliability) |
| A-T | Ability — Time |
| A-$ | Ability — Money |
| A-PE | Ability — Physical effort |
| A-ME | Ability — Mental energy |
| A-RF | Ability — Routine fit |
| M-Per | Motivation — Person (intrinsic) |
| M-Act | Motivation — Action (benefit/punishment) |
| M-Ctx | Motivation — Context (social/environmental) |
| CB | Competing behavior |

---

## 14. Guide Template — B=MAP + COM-B Format

```
# Research Guide: [Segment / Topic]

**Research Brief:** [title]
**Target Behavior:** "After [CONTEXT], [WHO] will [SPECIFIC ACTION]."
**Hypothesized Bottleneck:** [Prompt / Ability / Motivation]
**Duration:** [X min]

---

## Interviewer Notes

### Conversational Rules (keep visible)
1. Stories, not opinions. "Tell me about the last time..."
2. Never ask "why" — reconstruct context instead
3. Silence is a tool. Wait 3 beats after every question.
4. If they say "I'm lazy" → redirect to ability analysis
5. If they give aspirations → ask for a specific recent instance
6. Validate: "That makes sense." / "I can see why you'd do it that way."

### Dig Triggers
- "I'm just lazy" → redirect to ability
- "It's easy, I just don't" → surface missing prompt
- Aspiration → ground in specific behavior
- Emotion → "Tell me more about that"
- Burst-and-bust → probe what changed

### COM-B Coding Key
C-Ph | C-Ps | O-Ph | O-So | M-Re | M-Au

---

## Opening & Consent (2 min)
[VFWPA or equivalent from general guide reference]

## Section 0: Routine Mapping (5 min)
- Walk me through your typical [time period]
- Think about the last time you [behavior area]. What happened right before?
- Describe your [workspace/setup/environment] when you typically do [activity]

## Section 1: Prompt Exploration (10-15 min)
### 1a: Prompt existence
[Must-ask probes from Section 4 of this reference]
### 1b: Anchor mapping
[Must-ask probes]
### 1c: Prompt failure analysis
[Optional probes — use when prompt issues surface]

## Section 2: Ability Exploration (15-20 min)
### 2a: Discovery Question sequence (5 Ability Chain links)
[Must-ask probes for each link]
### 2b: Breakthrough Question sequence (Skills/Tools/Tiny)
[Must-ask probes for each lever]
### 2c: Observational assessment (if possible)
[Ability Chain scorecard]

### COM-B Coverage Check
- Physical Capability: [probes]
- Psychological Capability: [probes]
- Physical Opportunity: [probes]

## REACHING FOR THE DOOR (halfway mark)
"Thank you so much — I've learned a lot. Is there anything else you think I should know?"
[WAIT. Do not prompt. At least 3 beats of silence.]

## Section 3: Motivation Exploration (10-15 min)
### 3a: PAC source identification
[Must-ask probes]
### 3b: Competing and conflicting motivations
[Must-ask probes]
### 3c: Motivation durability
[Optional probes — use when motivation issues surface]

### COM-B Coverage Check
- Social Opportunity: [probes]
- Reflective Motivation: [probes]
- Automatic Motivation: [probes]

## Section 4: Competing Behaviors (5-10 min)
- "When you didn't do [target behavior], what did you do instead?"
[Probe each: why easier, habitual vs deliberate, what would need to change]

## Section 5: Synthesis (5 min)
- Teach-back: "If you were going to teach someone else..."
- Bottleneck ID: "What's the one thing that would make the biggest difference?"
- Ability isolation: "If this were ridiculously easy — like 10 seconds — would you do it every time?"
- Prompt isolation: "If you had the perfect reminder at the perfect moment, would that help?"

## Closing (2 min)
- "Who else should I talk to?"
- "Is there anything I should have asked?"
[Admin: incentive, consent, next steps]

---

## Brief-to-Guide Mapping

| Brief Research Question | Guide Section(s) | Key Probes |
|------------------------|-------------------|------------|
| [Q1] | Section X | Probes X.1, X.3 |

## Note-Taking Template

| Time | What They Said (verbatim quotes in "") | COM-B Code | B=MAP Tag | Emotion | Follow-up? |
|------|---------------------------------------|------------|-----------|---------|------------|
| | | | | | |
```
