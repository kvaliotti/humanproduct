---
name: retention-domain
description: "Diagnose and improve PLG retention and churn across four components: activation, adoption, engagement, resurrection. Use for: improve retention, reduce churn, why are users churning, retention analysis, retention curve, engagement analysis, engagement scoring, feature adoption, dormant users, reactivation, user resurrection, voluntary vs involuntary churn, dunning, behavioral design, BJ Fogg, B=MAT, COM-B, PLG retention plan."
---

# Retention Domain

Help a PM find where retention breaks and what to do about it. Retention has four components. Find the weakest one, then the behavioural reason behind it.

## Default: answer the question

Most requests are narrow ("how do I read a retention curve?", "is this churn voluntary?"). Answer directly in a few paragraphs, using the rules below only where they help. End with one line offering the full diagnosis. Run it only when asked or when a short answer would mislead.

## Full diagnosis (on request)

1. **Split churn** into voluntary and involuntary. They need different fixes.
2. **Read the curves:** overall, activated vs. not, by monthly cohort, by segment. Early drop points to activation. A slow decline points to engagement. A curve that never flattens points to weak product fit.
3. **Find the weakest component** (below), using the user's own baseline and trend. Do not grade against generic benchmarks.
4. **Name the behavioural constraint** for the target behaviour (below).
5. **Pick fixes** for that component and constraint.

Output, one page at most:
- **Bottom line:** the single biggest retention opportunity, in one sentence.
- **Churn split** and **weakest component**, each with its evidence.
- **Behavioural constraint:** which of motivation / ability / trigger is binding, for which segment.
- **Top 3 hypotheses:** component, hypothesis, evidence.
- **What we don't know** and **next step** (one concrete action).

If the user wants a work plan, turn the hypotheses into items: hypothesis, component, the behavioural lever it targets, metric, guardrail, priority. Put involuntary-churn fixes and the earliest broken component first.

## The four components

Fix the earliest broken component first. Better engagement can't save users who never activated. Resurrection can't save a product that doesn't retain.

- **Activation** — first value. Non-activated users rarely stay. If this is broken, route to `activation-domain`.
- **Adoption (breadth)** — which features users take up. Build a heatmap: features × retained vs. churned users, cell = % using it regularly. Read the quadrants:
  - *Core* (high adoption, tied to retention): make sure everyone gets there.
  - *Hidden gems* (low adoption, tied to retention): a discoverability problem, often the best lever.
  - *Shiny objects* (high adoption, not tied to retention): don't over-invest.
  - *Dead weight*: redesign or remove.
  For a low-adoption feature, tell apart: don't know it exists (views vs. use), can't use it (starts vs. completions), don't see why (trials vs. repeats).
- **Engagement (depth)** — frequency, recency, intensity. A simple score is a weighted mix of the three; tune the weights by how well the score predicts retention in their data, then use it to spot at-risk users. Levers: triggers matched to how often the need really occurs, integrations that put the product where users already work, covering more of the workflow, investment that grows switching cost (data, setup, teammates).
- **Resurrection** — bringing dormant users back. Set the dormancy threshold from the product's natural use frequency, not a generic number. Tactics: "what's new since you left", "where you left off" (restore their state), one-click magic-link return, a short returning-user welcome rather than full onboarding. Stop after a few emails. If revived users churn again fast, the problem is value, not reminders. Spend most effort on prevention.

## Behavioural lens

Use **Fogg (B = MAT)** for one behaviour: behaviour happens when motivation, ability, and a trigger meet. Use **COM-B** (capability, opportunity, motivation) for patterns across users and organisations. Rules that matter:

- Ability is set by its scarcest factor: time, money, physical effort, brain cycles, social deviance, non-routine.
- If motivation and ability are both low, no trigger works. Raise one first.
- Match the trigger to the user. *Spark* (adds motivation) for able but unmotivated users. *Facilitator* (makes it easier) for motivated users who struggle. *Signal* (plain reminder) for users who are both.
- Design for the natural frequency of the need. Daily nudges for a monthly job annoy users and don't build retention.
- Team adoption is an opportunity problem. Individual nudges fail if the team or org doesn't support the tool.

Interviews (retained and churned users): context ("walk me through the last time you used it"), motivation ("what would you miss, what would make you stop"), ability ("what's hard or slow"), trigger ("what makes you open it, what brings you back"). Tag each insight M/A/T, then find the binding one per segment.

## Churn

**Involuntary churn first.** It is technical and cheap to fix. Principles:
- Warn before cards expire and make updating one click from every message.
- Retry failed payments on a schedule and notify after the first failure.
- Never cancel immediately. Downgrade to free before cancelling, and keep the data.
- Use a billing descriptor users recognise. Offer a backup payment method.
- Track recovery at each step and tune the sequence.

**Voluntary churn.** Add a cancellation survey: one required single-choice question (too expensive / missing features / too hard to use / found an alternative / no longer need it / no time / other), one optional free-text question ("what could we have done?"). Then act on the top reason:
- *Dissatisfied* (UX, bugs, missing features, support) → fix the top cause by volume.
- *No longer need it* (project ended, seasonal) → find the next use case; for seasonal products, reactivate at the next cycle.
- *Competitor* → differentiate; don't chase every feature.
- *Price* → show value in-product, offer a lower tier instead of cancel, check the pricing metric (`monetisation-domain`).

**Pre-churn signals** that justify a proactive save: falling login frequency or session depth, a support ticket followed by silence, data export, removed integrations, removed teammates, downgrade questions.

## Don't

- Treat all churn as one number. Segment by tenure, plan, channel, activation, and engagement path.
- Ship features as a retention strategy. Adoption of what exists matters more.
- Do resurrection before prevention.
- Trust DAU/MAU without asking whether the engagement is valuable.
- Build artificial lock-in. Healthy switching costs come from delivered value.

## Route elsewhere

Activation is the weak link → `activation-domain`. Growth limited by top of funnel → `acquisition-domain`. Need revenue impact → `plg-revenue-analysis`. Broader diagnosis → `plg-orchestrator`.
