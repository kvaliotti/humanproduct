# Behavioral Frameworks Primer: COM-B and B=MAP

Shared definitions for the two frameworks used across every behavioral reference file in this plugin: **COM-B** (Capability, Opportunity, Motivation — Behavior; Michie et al.'s Behaviour Change Wheel) and **B=MAP** (Behavior = Motivation + Ability + Prompt; BJ Fogg's Behavior Design).

Each skill's own `behavioral-*.md` reference builds on this primer with stage-specific application (research questions to ask, probes to write, coding rubrics, evaluation criteria, or scoring). Read this file first, then the skill-specific reference for how to apply it at that stage of the pipeline.

Both frameworks decompose behavior into components and complement each other: **COM-B provides a comprehensive diagnostic** (6 sub-components, with TDF drill-down for granularity), and **B=MAP provides a precise action-design lens** (3 components with a strict troubleshooting order). Use both wherever behavioral research is in scope.

---

## 1. COM-B: The Six Sub-Components

| Component | Sub-component | Definition |
|-----------|---------------|------------|
| **Capability** | Physical | Does the user have the physical skills, stamina, or motor ability to execute the behavior? Accessibility and motor-skill barriers live here. |
| **Capability** | Psychological | Does the user have the knowledge, cognitive skills, memory, attention, and self-regulation to carry out the behavior? |
| **Opportunity** | Physical | Does the environment enable the behavior — discoverability, timing, tools, resources, cues? |
| **Opportunity** | Social | Do social influences (peers, managers, culture, norms) support or block the behavior? |
| **Motivation** | Reflective | Conscious beliefs, intentions, plans, identity, self-efficacy — does the user believe the behavior leads to a valued outcome and that they can do it? |
| **Motivation** | Automatic | Emotional reactions, habits, impulses, reinforcement — what happens below conscious deliberation? |

**Rule:** Never collapse to the 3 top-level components (C / O / M). Diagnostic power comes from the 6 sub-components — always code, probe, and score at that level.

---

## 2. B=MAP: The Three Components

### Motivation (M) — Why would the user do this?

Identify motivation sources using the **PAC** framework:

| Source | Question | Example |
|--------|----------|---------|
| **Person** (internal) | Does the user already want this? | Intrinsic desire to save time |
| **Action** (benefit/punishment) | What carrot or stick exists? | Bonus for completing onboarding |
| **Context** (social/environmental) | Does the environment push toward this? | Manager requires daily check-in |

Also assess:
- **Competing motivations** — what pushes the user toward a *different* behavior in the same moment.
- **Conflicting motivations** — opposing drives toward the *same* behavior (wants the outcome, doesn't want the action).
- **Durability** — is motivation **Enduring** (stable aspiration), a **Wave** (temporary surge that crashes, e.g. right after signup), or **Fluctuating**?
- **Shine** — is there a positive feeling immediately after the behavior that reinforces it? Its absence (No-Shine) predicts the behavior won't stick even if it happens once.

### Ability (A) — Can the user do this?

Assess using the **Ability Chain** — five factors, weakest link determines feasibility:

| Factor | Assessment Question |
|--------|---------------------|
| **Time** | How many seconds/minutes does this take? |
| **Money** | What does this cost the user? |
| **Physical effort** | What physical actions are required? |
| **Mental energy** | How much cognitive load does this demand? |
| **Routine fit** | Does this slot into existing workflows, or require restructuring? |

- **Discovery Question:** "What makes this behavior hard to do?" — must be asked/answered for every target behavior.
- **Breakthrough Question:** "How can we make this behavior easier?" — frames the design opportunity.
- **Three ability levers:** (1) Skill up (training/education), (2) Better tools (UX/automation), (3) Make it tiny (reduce scope/steps — Starter Step or Scaling Back).

### Prompt (P) — What triggers the behavior?

| Prompt Type | Reliability | Example |
|-------------|-------------|---------|
| **Person Prompt** | Low — relies on memory | "I'll remember to check the dashboard" |
| **Context Prompt** | Medium — external reminder | Push notification, email |
| **Action Prompt (Anchor)** | High — wired to an existing behavior | "After I open Slack, I check the dashboard" |

- **Anchor Moment:** the existing behavior a new one can be chained to.
- **Trailing Edge:** the precise last action of the anchor behavior — the exact prompt point.
- **Anchor match quality:** location match, frequency match, theme match.

---

## 3. How COM-B and B=MAP Map to Each Other

| COM-B Component | Corresponding B=MAP Element |
|-----------------|------------------------------|
| Physical Capability | Ability — Physical effort, Skill lever |
| Psychological Capability | Ability — Mental energy, Skill lever |
| Physical Opportunity | Ability — Routine fit, Tool lever; also Prompt (environmental cues) |
| Social Opportunity | Motivation — Context (PAC) |
| Reflective Motivation | Motivation — Person, Action (PAC) |
| Automatic Motivation | Motivation — durability, Shine, competing/conflicting motivations |

---

## 4. Troubleshooting Order and the Action Line

**This order is the single most important rule in both frameworks.** Most people start with motivation — that's wrong.

1. **Is there a prompt?** (Check first) — no prompt means the behavior never gets a chance to happen.
2. **Is there sufficient ability?** (Check second) — even motivated users won't do hard things.
3. **Is there sufficient motivation?** (Check last) — only investigate motivation after confirming prompt and ability are sufficient.

**Action Line** — for any target behavior, hypothesize where the user sits:
- **Above the line** (behavior happens): M and A are sufficient when prompted.
- **Below the line** (behavior doesn't happen): M or A is insufficient.
- **No prompt exists**: the behavior never fires regardless of M and A.

---

## 5. TDF Drill-Down

When a COM-B component shows a barrier, drill into the relevant Theoretical Domains Framework (TDF) domain for granularity:

| COM-B Component | TDF Domains |
|------------------|-------------|
| Physical Capability | Skills |
| Psychological Capability | Knowledge, Skills, Memory/Attention/Decision Processes, Behavioral Regulation |
| Physical Opportunity | Environmental Context & Resources |
| Social Opportunity | Social Influences, Social/Professional Role & Identity |
| Reflective Motivation | Beliefs about Capabilities, Beliefs about Consequences, Intentions, Goals, Social/Professional Role & Identity, Optimism |
| Automatic Motivation | Emotion, Reinforcement |

**Decision rule:** Screen all 6 COM-B components with broad probes/questions first. Where a barrier surfaces, switch to the relevant TDF domain for depth. Where no barrier signal appears after 2-3 probes, move on.

---

## 6. Standard Coding Tags

Use these tags consistently across guides, note-taking templates, and analysis coding so output from one stage is legible at the next.

**COM-B codes:**

| Code | Component |
|------|-----------|
| C-Ph | Capability — Physical |
| C-Ps | Capability — Psychological |
| O-Ph | Opportunity — Physical |
| O-So | Opportunity — Social |
| M-Re | Motivation — Reflective |
| M-Au | Motivation — Automatic |

**B=MAP tags:**

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

**Evidence tags** (apply to every coded data point regardless of framework):

| Tag | Meaning |
|-----|---------|
| [B] | Behavioral — participant described what they actually did |
| [SR] | Self-report — participant stated a belief, preference, or generalization |
| [O] | Observed — from analytics, usability recording, or direct observation |

---

## 7. Core Anti-Patterns (apply at every stage)

| Anti-Pattern | Why It Fails | Fix |
|--------------|---------------|-----|
| **Motivation Trap** | Assumes the problem is that users "don't want to" before checking prompt and ability | Apply the troubleshooting order: P → A → M |
| **Aspiration Masquerade** | Target behavior is really an outcome or aspiration ("increase engagement") | Apply the "can you do it right now?" test — if not, it's not a behavior |
| **Monolithic User** | All users treated as having the same COM-B/B=MAP profile | Segment by behavioral profile, not demographics |
| **Missing Prompt** | Motivation and ability discussed, but no trigger addressed | Always include prompt/anchor analysis |
| **Self-report = truth** | Taking "I always do X" or "I'm just lazy" at face value | Tag as [SR]; investigate whether the real issue is ability or prompt before accepting a motivation attribution |
| **COM-B tourism** | One shallow question per component, no depth | 2-3 questions per component minimum, each probing a different facet |

The "I'm just lazy" self-attribution deserves special attention: participants routinely blame themselves for motivation deficits when the actual bottleneck is a missing prompt or a broken Ability Chain link. Always re-examine self-blame statements for hidden ability/prompt issues before accepting them as a motivation finding.
