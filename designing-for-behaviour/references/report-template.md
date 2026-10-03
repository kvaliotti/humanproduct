# Report template

The orchestrator writes `behaviour-review-[target].md` in the working directory, then gives a short inline summary.

**Length cap: two pages.** Lead with the fixes. If the report runs longer, it is reporting findings that did not earn their space. Cut, don't compress.

**No score.** No percentages, bands, grades, overall number, or confidence label. Item ratings stay internal (they ranked the gaps). Name the bottleneck in words instead.

Every claim carries an anchor (screen / flow / `file:line` / quoted copy / PRD section / moment).

## File structure

```markdown
# Behaviour Design Review — [Target]

**Mode:** [Codebase | PRD / idea] · **Scope:** [the experience reviewed, one line] · **Date:** [YYYY-MM-DD]

**Bottleneck:** [One or two sentences: which of behaviour / adoption / engagement is failing, where, and why.]

## Do these, in this order
At most 3 core moves. The first one is usually the root fix that dissolves several gaps.
1. **[Move]** — [what changes]. *Folds into:* [existing surface, or "new, because…"]. *Lifts:* [dimension]. *Fixes:* [gap(s) below].

## Deliberately NOT adding
At most 5. Each: **[Rejected idea]** — [redundant / over budget / N/A for this archetype / conflicts / manipulative / dissolved by move N].
Include anything the subtraction pass says to **remove**.

## Gaps behind these moves
At most 5, biggest blocker first. Mark where lenses converged.
- **[Gap]** — [anchor]. *Hurts:* [dimension]. *Lens(es):* [...].

## Fold-ins
At most 3, only if not already covered by a core move.
- **[Mechanism]** → embedded in **[host surface]**.

## Coherence rationale
One paragraph: the dominant path, how the moves hold together, and what you kept the product from becoming.

## What we reviewed
Experience, target behaviour, users and context, user vs. business outcome. Five lines at most.

## What we don't know
What was inferred rather than observed, and what would sharpen a re-review (real drop-off data, user interviews).

---
Ask for: per-lens findings · the full gap list · what's already strong and should be left alone.
```

## Inline summary (after writing the file)

Keep it under ten lines:

1. Where the report was written.
2. The bottleneck, in one sentence.
3. The top core moves, in order, one line each.
4. The single most important "deliberately NOT adding" call.
5. One line on what the product should become and what it should avoid becoming.
