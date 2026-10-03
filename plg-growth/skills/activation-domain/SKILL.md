---
name: activation-domain
description: "Define, measure, and improve PLG activation and time-to-value. Use for: define activation metric, find the aha moment, first value moment, improve activation, activation rate, time to value, onboarding optimization, onboarding drop-off, setup completion rate, users sign up but don't engage, activation analysis, PLG activation plan."
---

# Activation Domain

Help a PM define the activation metric, find why users don't reach it, and pick the few fixes that matter. Activation = the earliest product event that predicts a user will retain or pay.

## Default: answer the question

Most requests are narrow ("how do I find my aha moment?", "setup before or after first value?"). Answer directly in a few paragraphs, using the rules below only where they help. End with one line offering the full analysis. Run the full analysis only when the user asks for it or a short answer would mislead.

## Full analysis (on request)

1. **Metric.** If there is none, find it (below). If there is one, check it predicts retention or payment.
2. **Funnel.** Step-by-step from signup to the activation event. Find the step that loses the most users in absolute numbers.
3. **Barriers.** Classify the big drop-offs as don't know / can't / don't want (below).
4. **Fixes.** One or two tactics per barrier, each as a testable hypothesis.

Output, one page at most:
- **Bottom line:** the single biggest activation opportunity, in one sentence.
- **Activation metric:** the event, threshold, window, the evidence for it, and the current rate.
- **Top 3 barriers:** barrier type, the step, users lost there.
- **Hypotheses:** "If we change X, activation rises because Y."
- **What we don't know** and **next step** (one concrete action).

If the user wants a work plan, turn the hypotheses into items: hypothesis, segment, experiment, metric, guardrail, priority by users affected.

## Finding the activation metric

A good metric is predictive (users who do it retain much better), actionable (the team can move it), early (happens in the first days, so you can intervene), and observable (one tracked event).

**Quant: the CSI / aha score.** For every meaningful event × count threshold (1, 2, 3, 5, 10) × time window (7, 14, 30 days after signup), build a 2×2 against a retention outcome (for example, active in month 2):
- TP = did it and retained, FP = did it and churned, FN = didn't and retained.
- `CSI = TP / (TP + FP + FN)` (Jaccard index). Rank all combinations; the top ones are candidates.
- Use rank, not an absolute cut-off. If the top few are close, let interviews decide.
- Cross-check with information value or a random-forest feature ranking if the data allows. Treat these as discovery tools, not proof.
- Check the winner holds across several monthly cohorts, not one.

**Qual: activation interviews.** Talk to users who activated recently, fit the ICP, and chose the product themselves. Stop when new interviews add no new themes. Three parts:
- **Job:** what were you trying to get done, what did you use before, what made you switch now?
- **Aha:** when did it first feel valuable, what exactly happened on screen, how long after signup, where did you almost give up?
- **Criteria:** what would make you stop, what would you use instead, how would you describe us to a colleague?

Map each aha story to a tracked event. The most common one is your hypothesis. If you have too few users for stable counts, start from interviews and validate with CSI later.

**Validate.** Activated users must retain and pay clearly better than non-activated. If the gap is small, the metric is a proxy; go back.

## Barriers: don't know / can't / don't want

| Type | Signals | Typical fixes |
|---|---|---|
| **Don't know** — unclear what to do or why | Signup then nothing; tours skipped; help searches in session 1; bounce from empty state | Make the first screen match the promise that acquired them; one clear first action; short checklist of real actions (not busywork); contextual tips |
| **Can't** — blocked by friction | Sharp drop at one step; "how do I" tickets; failed imports or integrations; long TTV | Defer every step not needed for first value; smart defaults; templates with sample data; human help at the stuck step |
| **Don't want** — not motivated yet | Browse without committing; low completion despite easy steps; empty state bounce | Pre-generated "wow" from their own data; a first win that takes minutes; sample content; invite a teammate early if the product is better with one |

Fix the step that loses the most users first, whatever the barrier type. A small lift at a busy step beats a big lift at a quiet one.

## Rules worth keeping

- **Setup is not activation.** Completing onboarding means nothing if no value was delivered. Let users get value before you ask for setup.
- **Speed matters as much as rate.** A high activation rate reached slowly often loses to a lower rate reached fast.
- **Segments differ.** Channel, job, role, and intent can each have a different aha moment. Admin and end user, creator and viewer, usually need separate metrics.
- **Activation ends nothing.** If activated users still churn, the gap is the hand-off to habit (what happens after the aha). Route to `retention-domain`.
- **Expect quarters, not weeks.** Segment → find supporting behaviours per segment → experiment → repeat.
- **Good enough now beats perfect later.** If the quant is inconclusive, ship a metric from interviews and revisit.

## Don't

- Pick a vanity metric that is easy to hit but doesn't predict retention.
- Polish onboarding UI before the metric is defined.
- Use fake urgency to push users through setup.

## Route elsewhere

Signups are the bottleneck → `acquisition-domain`. Activated users churn → `retention-domain`. Need the revenue impact → `plg-revenue-analysis`. Broader diagnosis → `plg-orchestrator`.
