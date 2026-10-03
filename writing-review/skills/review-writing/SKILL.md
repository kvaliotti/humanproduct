---
name: review-writing
description: Review a draft like a linter, not an editor. Five narrow reviewers (reader, structure, argument, evidence, prose) run in parallel as independent sub-agents; each quotes the exact words at fault, says why it matters, and proposes the smallest fix. The findings are merged into one ranked review. Includes Zinsser-style clutter checks and AI-writing tells. Use when the user asks to review, critique, edit, tighten, or give feedback on a draft, essay, blog post, memo, doc, email, or announcement; asks "is this clear", "does this argument hold up", "check my claims", "fact-check this", or "does this sound like AI"; or wants only one kind of review.
argument-hint: "[file or pasted text] [--only reader,structure,argument,evidence,prose]"
---

# Review Writing

A reviewer finds defects. It does not improve the writing. Read `references/writing-rules.md` first: the prose reviewer checks against it, and everything this skill writes follows it.

## Orchestration

1. Get the draft: a file path, pasted text, or the draft the user just named.
2. Infer the brief from the draft and the conversation:
   - **Purpose:** what the document is for.
   - **Reader:** who reads it and what they already know.
   - **Desired change:** what the reader should think or do afterwards.

   Show the brief and the reviewers you'll run (all five, unless `--only` or the user asked for one kind). Confirm with AskUserQuestion. If you can't tell who the reader is, ask.
3. Spawn the reviewers in one message: `subagent_type: "writing-review:writing-reviewer"`, `model: "opus"`. Pass each one its reviewer name, the brief, the draft (path, or the text if pasted), and the path to this file (`${CLAUDE_PLUGIN_ROOT}/skills/review-writing/SKILL.md`). Never show one reviewer another's output.
4. Merge, as below. Show the review in chat. If the draft is a file, also write the review to `<draft-name>-review.md` beside it.
5. Offer to apply the fixes. If the user agrees, apply only the listed fixes and change nothing else.

## Reviewers

Each reviewer stays in its lane. A problem that belongs to another reviewer is not yours.

**reader**: Where will this fail for the stated reader? Assumptions they don't share, terms they won't know, objections they'll raise that go unanswered, context they need and don't get, claims they won't believe, passages that don't serve the desired change. Tie every problem to words in the text; no imagined readers.

**structure**: Treat the document as control flow. Conclusions before their setup, key points buried late, ideas repeated, sections doing two jobs, jumps in topic or abstraction, sections that don't advance the purpose, a missing section the argument needs. Paragraph level and up. Prefer the smallest move (cut, swap, move one paragraph) to a new outline.

**argument**: List the material claims and what supports each, then test the support. Flag unsupported conclusions, hidden assumptions, non sequiturs, correlation sold as causation, contradictions, overgeneralisation, conclusions bigger than their premises, false dichotomies, circular reasoning, and an obvious counterargument left standing. Name the type: missing evidence, weak evidence, invalid reasoning, or unstated assumption. Don't fact-check. Don't invent objections to look rigorous.

**evidence**: Pick the factual claims the argument rests on, not every sentence. Check the evidence given, and search the web for the claims that matter and lack support. Flag unsupported claims, sources about a different population or period, old or weak sources behind strong claims, statistics without context, and wording more certain than the evidence. Say which: no evidence found, evidence is mixed, evidence contradicts the claim, or evidence supports only a weaker claim. Link what you found. No literature reviews.

**prose**: Sentence-level friction only. Ambiguous or vague wording, unclear references ("this", "it"), sentences that need rereading, needless words and repetition, needless abstraction or jargon, misleading wording, and the patterns in `references/writing-rules.md`. Report a wording change only if the reader gains something concrete: clearer, shorter, or truer. Never because another phrasing sounds nicer.

## Findings

Every reviewer reports in this format and nothing else:

```
### [Major|Minor] Short title
> Exact quote (section, if the draft has headings)

**Problem:** what goes wrong for the reader, in one or two sentences.
**Fix:** the smallest change that removes it.
```

- **Major:** hurts comprehension, credibility, logic, or the purpose. **Minor:** real but local friction.
- No quote, no finding. For a structure problem, quote the section's first sentence.
- Smallest fix: narrow a claim, define a term, cut a sentence, move a paragraph, split a sentence, add a premise. When the fix is wording, give the replacement words.
- If you're unsure it's a problem, leave it out. Report at most 6 findings; if you found more, keep the most material and say how many you dropped.
- A defect that repeats is one finding, with up to 3 quotes and a count.
- No praise, no summary of the draft, no rewritten paragraphs, no "consider perhaps". If nothing material is wrong, write "No material issues."

## Merge

Combine the reviewers' findings. Don't review the draft again and don't add findings of your own.

- Start with the **Brief** and a one-line **Verdict**: which finding to fix first, and why.
- Merge findings with the same root cause. Keep the clearest Problem and the smallest Fix, and add **Found by:** with each reviewer's name.
- Keep quotes exact.
- **Major issues**, then **Minor issues**; within each, rank by how much the issue hurts the purpose.
- End with a line naming any reviewer that found nothing, so the reader knows it ran.
