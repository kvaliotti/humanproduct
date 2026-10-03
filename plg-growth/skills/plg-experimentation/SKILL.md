---
name: plg-experimentation
description: "Design PLG experiments, generate experiment ideas with behavioural science (B=MAT), calculate sample size and duration, and prioritize an experiment backlog. Use for: PLG experiment, growth experiment, A/B test, experiment design, test this hypothesis, experimentation plan, experiment backlog, what should we test, prioritize experiments, behavioral experiment, B=MAT, sample size calculation, MDE, experiment template. Designs tests; does not analyze results."
---

# PLG Experimentation

Three modes: **design** one experiment (the default), **generate ideas** for a target behaviour, or **prioritize** a backlog. For a narrow question ("how big a sample do I need?"), answer it directly and show the arithmetic.

## Mode 1: Design an experiment

Produce a one-page brief:

1. **Hypothesis:** "We believe [specific change] will cause [effect on metric] for [audience] because [evidence]." If you can't say what result would prove it wrong, rewrite it.
2. **Primary metric:** exactly one, and it must move within the test window. Use a leading metric, such as activation, for short tests. Treat revenue and retention as guardrails or as a follow-up check.
3. **Guardrails:** at least two. One downstream (retention or revenue) and one for quality (support tickets or satisfaction). If a guardrail breaks, the test fails even if the primary metric wins.
4. **Audience and unit:** who is in, who is excluded (internal users, enterprise accounts, users in other tests). Randomize **by account** whenever the change affects team behaviour, such as invites, shared work, or seats. Randomizing users inside one account contaminates the result.
5. **Minimum detectable effect (MDE):** a business decision. It is the smallest lift worth building and maintaining. Get it from revenue-tree sensitivity (`plg-revenue-analysis`).
6. **Sample size:** per arm, n = (z₁₋α/₂ + z₁₋β)² × [p₁(1−p₁) + p₂(1−p₂)] / (p₂ − p₁)². At 95% confidence and 80% power, (1.96 + 0.84)² = 7.84. Always compute it and show the numbers. Don't use a lookup table.
7. **Duration:** total sample ÷ daily eligible traffic, rounded **up to whole weeks**. Avoid holidays and campaigns. If it takes more than about a month, the traffic is too low for an A/B test. Use a fake door, a prototype test, or a Wizard of Oz test instead.
8. **Decision, committed before launch:** what you do if it wins, loses, is inconclusive, or breaks a guardrail. An inconclusive result is not proof of no effect, and by default you don't ship it.

Before you finalize, check the risks: peeking (commit to a date for reading results, or use a sequential method), other tests on the same audience, novelty effects, segments that should be split in advance, and changes bundled together that you can't separate.

Choosing the test type: if you're unsure whether to build it, use a fake door or a prototype. If you know what to build but not its impact, use an A/B test. Use a bandit only for tactical optimization, such as copy. Use a fixed-horizon test for ship-or-kill decisions.

## Mode 2: Generate ideas (B=MAT)

Fogg's model: a behaviour happens when Motivation, Ability, and a Trigger are all present at once.

1. State the target behaviour precisely, e.g. "user does [action] within [time] of [event]." "Improve retention" is an outcome, not a behaviour.
2. Diagnose which part is missing, using evidence:
   - **Motivation:** users start and abandon, skip optional steps, or sign up but never activate.
   - **Ability:** drop-off at one step, "how do I" tickets, heavy use of help docs, slow completion.
   - **Trigger:** capable users never start, use is irregular, or users act after a CS nudge but not on their own.
3. Give 3–5 ideas per missing part. Ability: remove steps, add templates and defaults, use progressive disclosure, offer one-click setup. Trigger: a prompt based on what the user just did, an email triggered by what they did or didn't do, activity from teammates. Motivation: preview the end result before asking for effort, personalize the payoff, lower the perceived commitment.
4. Sequence the fixes: **ability first, then triggers, then motivation**, unless the evidence clearly points to motivation. A trigger with no ability behind it annoys users. Motivation is the hardest to move.

## Mode 3: Prioritize a backlog

Rank each idea High/Medium/Low on impact (from revenue-tree sensitivity), confidence (past test data > funnel data > research > best practice > gut feel), and ease. Treat ICE as a rough sort, not a precise score. Then apply these ordering rules:
- Foundations first: instrumentation and feature flags rank above tests that depend on them.
- Cheap learning tests come before full A/B tests.
- Never run two tests on the same audience and metric at once.
- Among close calls, prefer the one with higher confidence.

Group the ranked list by revenue-tree branch and name the branch that has no experiments.

## Output

Lead with one line:
- **Design:** "Test X on Y, measuring Z. Need N per arm over D weeks. Ship if Z improves by at least the MDE with no guardrail broken."
- **Ideas:** "The bottleneck for [behaviour] is [part], based on [evidence]. Top 3 ideas: …"
- **Backlog:** "Top bet: … Biggest gap: [branch]."

Then the brief, the ideas, or the ranked table. Keep it to about one page.

Don't quote "typical" lifts or MDE ranges. They depend on the product. Use the user's baseline.
