# Report template

The orchestrator writes the full report to `behaviour-review-[target].md` in the user's working directory, then gives a short inline summary in chat. Use this exact structure so reports are comparable across runs and easy to diff when a product is re-reviewed.

Keep it concrete throughout — every claim carries an anchor (screen/flow/file/copy/moment). Prose over tables where a table would flatten nuance; tables for the scorecard.

## File structure

```markdown
# Behaviour Design Review — [Target name]

**Mode:** [Existing product / codebase | Idea / PRD / feature description]
**Scope:** [the specific experience reviewed — one line]
**Date:** [YYYY-MM-DD]
**Confidence:** [High | Medium | Low] — [one line on what was/wasn't observable]

## 1. What we reviewed
- **Experience:** [the flow/feature/surface and its boundaries]
- **Target behaviour(s):** [observable action(s), with situation and moment]
- **Place in the product:** [where it sits; what precedes/follows]
- **Users & context:** [who, in what real context]
- **Why it matters:** [user outcome | business outcome — kept separate]
- **How behaviour/adoption/engagement are defined here:** [instantiated for this product]

## 2. Scorecard

| Dimension | Score | Band |
|---|---|---|
| **Behaviour** | NN% | [band] |
| **Adoption** | NN% | [band] |
| **Engagement** | NN% | [band] |
| **Overall** | NN% | [band] |

By lens: behavioural-loop NN% · cognitive-ease NN% · capability-results NN% · control-autonomy NN%

[One paragraph: what the numbers say in plain language — which dimension is the bottleneck and why. Lead with the diagnosis, not the number.]

## 3. How it drives behaviour, adoption, and engagement

### Behaviour
[Narrative with anchors: does the target behaviour actually happen? Where does the loop hold and where does it break?]

### Adoption
[Narrative with anchors: breadth — first value speed, spread across core experiences, switching cost.]

### Engagement
[Narrative with anchors: depth — return reasons, meaningful vs empty engagement, compounding.]

## 4. Prioritized gaps
[Ranked, biggest blocker first. For each:]
- **[Gap name]** — [what's missing/broken, with a concrete anchor]. *Lens:* [which]. *Hurts:* [behaviour/adoption/engagement]. *Severity:* [high/med/low].

## 5. Recommendations — one coherent experience
_Output of the coherence & anti-bloat review. This is the part that matters._

### Core moves (do these, in this order)
1. **[Move]** — [what changes]. *Folds into:* [existing surface, or "new surface because…"]. *Lifts:* [dimension(s)]. *Resolves:* [which gaps/lens findings].
2. …

### Fold-ins (embed, don't bolt on)
- **[Mechanism]** → embedded into **[host surface]**, so it's part of the core action, not a new thing to do.

### Deliberately NOT adding (and why)
- **[Rejected/deferred rec]** — [redundant / over budget / N/A for this archetype / conflicting / manipulative / dissolved by a root fix].

### Coherence rationale
[One paragraph: how the surviving set holds together as a single experience, what the dominant path is, and what you kept the product from becoming.]

## 6. Assumptions & limits
[What was inferred vs. observed; what would sharpen a re-review (analytics, real drop-off, etc.).]

## Appendix — lens detail (optional)
[Per-lens scored items with anchors, for the reader who wants the working.]
```

## Inline summary (after writing the file)

Give the user a tight summary in chat — not the whole report. Include:

1. One line: where the report was written.
2. The three dimension scores + overall, with the one-sentence diagnosis of the bottleneck.
3. The **top 3 core moves** (sequenced), one line each.
4. The single most important **"deliberately NOT adding"** call — this is what makes the review trustworthy.
5. One line of coherence rationale — what the product should become, and what it should avoid becoming.

Keep it skimmable. The file has the depth; the chat has the point.
