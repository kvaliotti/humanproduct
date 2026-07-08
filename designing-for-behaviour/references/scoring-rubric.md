# Scoring rubric

The six source books used three different, incompatible scoring scales (one had none, two used 0/1/2 with different labels). This file unifies them into one scale so lens scores are comparable and can be rolled up deterministically.

## Item-level scale (used by every lens)

Score each checklist item you assess as:

- **0 — absent / weak.** The experience does not do this, or does it so weakly it doesn't count. Requires a concrete observation.
- **1 — partial.** Present but incomplete, inconsistent, or only in some paths.
- **2 — strong / evidenced.** Clearly present and doing its job, with a concrete anchor showing it.
- **N/A — not applicable.** This item is genuinely irrelevant to *this* experience (e.g. streak mechanics for a tax-filing tool used once a year). N/A items are **excluded** from the denominator, not scored 0.

**N/A discipline matters.** Scoring an irrelevant item as 0 punishes a product for lacking machinery it shouldn't have — that's exactly the bloat this plugin exists to prevent. Only score items that a product *of this archetype* would benefit from. When in doubt about relevance, mark N/A and say why in one line. But don't hide behind N/A to avoid a hard call — if the mechanism *would* help and it's missing, that's a 0, not an N/A.

Every 0 or 1 must carry a one-line concrete anchor (the screen/flow/file/copy/moment) or it doesn't count. A score without an anchor is an opinion, and we don't ship opinions.

## Per-lens score

Each lens reports, for the items it actually assessed:

```
lens_score = (sum of scored points) / (2 × number of applicable items)   → 0–100%
```

Report it as a percentage plus a one-word band and the counts, e.g. `behavioural-loop: 44% (Developing) — 9 items, 2×2 / 4×1 / 3×0, 3 N/A` (i.e. (4+4+0)/(2×9) = 44%).

Bands (applied to any percentage — lens, dimension, or overall):

- **0–29% — Absent.** The mechanism barely exists; behaviour is left to chance.
- **30–54% — Developing.** Real gaps; behaviour happens for some users by luck or effort.
- **55–74% — Solid.** Works, with specific weak points worth fixing.
- **75–89% — Strong.** Reliably drives the behaviour; refinements only.
- **90–100% — Exemplary.** Best-in-class; protect it, don't touch it.

## Per-dimension score (behaviour / adoption / engagement)

Because every finding is tagged to one or more of behaviour/adoption/engagement, the orchestrator re-buckets *all* scored items (across all four lenses) by dimension and applies the same formula per bucket. This is what the user cares about most — the three headline numbers:

- **Behaviour** — is the target action actually happening?
- **Adoption** — is the experience being used across the breadth it should be?
- **Engagement** — is it used with the depth/frequency it should be?

An item can count toward more than one dimension (e.g. a return-trigger item counts for engagement; a first-value item counts for behaviour and adoption). Tag honestly; don't spread one item across all three to pad a number.

## Overall score

```
overall = mean of the three dimension percentages
```

Report overall as a percentage + band, but lead with the three dimension numbers, not the single overall — the composite hides which dimension is failing, and the whole point is to know *which*.

## Confidence

State a confidence level (High / Medium / Low) with the score, driven by how much of the experience you could actually observe:

- **High** — codebase mode with the real flow and copy read directly, or a detailed PRD.
- **Medium** — partial visibility; some steps inferred.
- **Low** — thin PRD or a flow you had to reconstruct with significant assumptions.

A low-confidence 40% and a high-confidence 40% are different situations. Never present a score as more certain than the evidence supports. If you're guessing, say the number is directional.

## What the score is for

The score exists to **locate the weakness and track improvement**, not to be a grade. Two products can score 60% for opposite reasons. Always pair the number with the *why* — the ranked gaps and the specific anchors. A score with no attached diagnosis is exactly the kind of empty output this plugin is built to avoid.
