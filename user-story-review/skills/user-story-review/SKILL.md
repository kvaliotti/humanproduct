---
name: user-story-review
description: Review user stories, epics, PRDs, or a backlog and return a short triage of what is actually wrong — feature requests wearing story clothes, generic actors, fake value statements, solution-led needs, technical layers sliced as stories, outcomes outside the team's control, stories too big or assumption-heavy to survive, and work that should not be a user story at all. Use when the user says "review my user stories", "review the stories in this PRD", "are these stories ready", "is this backlog any good", "check my epics", "these stories feel off", "split this story", "is this story too big", or asks whether a story is ready for refinement, sprint planning, or delivery. Also use after drafting or evaluating a PRD to stress-test its story set before engineering picks it up.
user-invocable: true
argument-hint: [path to PRD/backlog file, or paste stories — blank to auto-discover]
---

# User Story Review

## Core principle

A user story is a **conversation token for discovering and delivering an outcome**, not a miniature requirements document. Judge whether the story is *true and useful*, not whether it complies with "As a… I want… so that…".

## What this skill optimises for

A reviewer that returns forty questions has not saved anyone time — it has moved the work. **The output is a triage, not an essay.** Find the few things that would make this milestone fail, say them in one page, and stop. Depth is available on request; it is never the default.

## Step 1 — Find the input

In order:

1. A path or pasted stories in the invocation.
2. Newest `PRD-*.md` in the working directory (the `prd-workflow` plugin writes this name).
3. Any file that looks like a backlog/epic/story list.
4. Otherwise ask for the PRD — do not review stories with no surrounding context.

If the file has no user stories, say so and stop. Do not invent stories to review.

## Step 2 — Read the PRD context before any individual story

Extract: milestone/business objective and product stage · target segments and stakeholders · current user behaviour and intended behaviour change · expected organisational value · deadlines, risks, dependencies, global constraints · how outcomes will be checked with real users.

**Missing context is a finding, not a blank to fill.** Report it. Never invent it, and never rewrite a story around a metric or segment the PRD does not supply.

A locally reasonable story can still be wrong for this milestone, segment, or stage. Ticket-by-ticket review misses that, so the story-set read comes first.

## Step 3 — Classify every item

One verdict each:

- **READY** — enough basis for a productive team conversation and delivery planning.
- **NEEDS CONVERSATION** — plausible, but one material question is unresolved.
- **REFRAME** — feature request, fake value, generic actor, or solution presented as the need.
- **SPLIT / EXPERIMENT** — valuable direction, too broad or assumption-heavy for one survivable increment.
- **NOT A USER STORY** — technical, operational, cross-cutting, research, or consistency work that should be tracked honestly instead of wrapped in a fake story.

Run each item through the six gates in `references/review-rubric.md`: strategic connection · user and outcome · system change and control · evidence and assumptions · slice and delivery · story-set quality. The rubric is the depth behind the verdict — consult it, don't transcribe it.

## Step 4 — Triage before writing

Rank findings by what they cost, then spend the output budget accordingly:

- **Systemic issues first.** An incoherent segment focus or a horizontally-sliced set invalidates the stories underneath it — fix that before anyone rewords a card.
- **Deep treatment for the worst three only.** Everything else gets one table row.
- **Wording is not a finding** unless it causes a real misunderstanding.
- **Large backlogs (>25 items):** table the whole set, but deep-treat only the top three, and say you sampled.

Then produce the review per `references/output-contract.md`. Use `references/splitting-patterns.md` when recommending a slice — but only when asked for splits, or when a split *is* the top-three finding.

## Rules

- Lead with what can invalidate the work. Never bury it under wording feedback.
- Cite story IDs or exact short phrases as evidence. Every finding gets an anchor.
- Distinguish **defects** from **open product decisions** from **conversation prompts**.
- Rewrite only when the PRD supplies the evidence. Otherwise ask the smallest question that unlocks the rewrite.
- Do not penalise nonstandard story syntax.
- Do not treat acceptance criteria, technical design, or exhaustive documentation as substitutes for conversation.
- Do not force tasks, non-functional targets, UX research, or engineering work into fake user stories.
- Do not call a story "ready" because it is small, estimated, or syntactically complete.
- Do not emit a numeric quality score. The *pattern* of failure matters more than arithmetic; a score hides the type of failure.
- Do not produce a generic INVEST checklist with no prioritisation.

## Chaining

Pairs with the `prd-workflow` plugin: `prd-draft` → `prd-evaluate` → `sit-beh` → this review, as the last gate before engineering. When stories fail on behaviour change or barriers, `sit-beh` is the tool that fixes them.

## Source

Operationalises Gojko Adzic, David Evans, and Nikola Korac, *Fifty Quick Ideas to Improve Your User Stories* (2014).
