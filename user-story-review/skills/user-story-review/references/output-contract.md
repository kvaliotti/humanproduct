# Output Contract

**Target: one page, inline.** Four sections, hard caps, then stop. If the review runs past a page, you are reporting findings that did not earn their space.

Write it inline. Only write `user-story-review-[prd-name].md` if the user asks for a file.

## 1. Verdict

One line: overall state (**Ready** / **Needs revision** / **Not reviewable yet**) + how many stories are ready.
One line: the dominant reason.
One line: counts by verdict.

If PRD context is missing, the verdict is **Not reviewable yet** — list what is missing, ask for it, and stop. Do not review stories against context you invented.

## 2. The 3 things that will sink this

At most **three** systemic issues — the ones that affect multiple stories or invalidate the set. Each is one sentence plus a bracketed evidence anchor (story IDs or a quoted phrase).

Not here: copy-editing, single-story nitpicks, anything you would not stop a sprint for.

Fewer than three is a valid answer. Three is a cap, not a quota.

## 3. Stories

One row per story. One primary issue per row. Keep cells under ~10 words.

| ID | Verdict | Primary issue | Next move |
|---|---|---|---|

Secondary issues only when they change the next action.

## 4. Rewrites — worst 3 only

Only for stories where the PRD supplies enough evidence. If it does not, put the smallest unlocking question in the "Next move" cell instead and skip the rewrite.

A useful default shape — not mandatory syntax:

> **For [specific segment], enable [observable system change], so they can [observable behaviour change], contributing to [PRD impact].**
> **Currently:** [observable current behaviour] · **Expected evidence:** [signal/range/test]

## 5. Footer

One line naming what you're holding back, so the user can pull it:

> Ask for: splitting options · full question list · non-story work · the rubric behind any verdict

Deferred until asked — never volunteered:

- **Splitting options** — 2–3 slicing dimensions per SPLIT story, ordered by learning value, pattern named (`splitting-patterns.md`).
- **Full question list** — open decisions grouped by owner (PM/business · design/research · engineering/data/security/legal · cross-functional). Ask concrete questions: "Which segment?", "How much change?", "What would disprove this?", "What can we omit?" — never "Can you clarify?".
- **Non-story work** — engineering, operational, research, or cross-cutting items that should be tracked separately, and how each connects back to a product outcome.

Exception: if a split or a non-story item *is* one of the top three, it belongs in section 2 with its recommendation inline.

---

## Worked example

The shape to aim for. Note how much is left out.

**PRD context:** Objective — cut the time UK finance ops spends finding customer-data discrepancies. Segment — UK back-office reconciliation specialists. Today they run three reports and compare spreadsheet exports by hand.

---

### Verdict: Needs revision — 0 of 1 stories ready

The one story optimises query speed while the actual bottleneck is manual comparison.
0 READY · 0 NEEDS CONVERSATION · 1 REFRAME · 0 SPLIT · 0 NOT A STORY

### The thing that will sink this

1. **Query speed is being treated as the outcome.** Speed is in the team's control, but the goal is finding discrepancies faster — faster queries leave the manual spreadsheet comparison untouched. ["faster reporting queries", "work more efficiently" — US-1]

### Stories

| ID | Verdict | Primary issue | Next move |
|---|---|---|---|
| US-1 | REFRAME | Solution substitutes for the need | Observe the reconciliation workflow; reframe around finding discrepancies |

### Rewrite

> **For UK back-office reconciliation specialists, show discrepancies across the three customer-data sources in one comparison view, so they can identify records needing verification without manually combining reports.**
> **Currently:** specialists run three reports and compare exports by hand · **Expected evidence:** median time from starting reconciliation to a discrepancy list falls to an agreed range

**Blocking decision:** does "identify discrepancies" close the milestone, or must the story cover resolving them too?

---

Ask for: splitting options · full question list · the rubric behind this verdict
