---
name: designing-for-behaviour
description: Evaluate how well a product experience drives user behaviour, adoption, and engagement — score it, find the gaps, and recommend an integrated set of fixes that strengthen a single coherent core experience instead of bloating it with bolted-on mechanisms. Use this skill whenever the user wants to review, audit, critique, score, or improve a product/feature/flow's behavioural design, habit-formation, activation, retention, onboarding, engagement loop, or adoption — whether they point it at an existing product/codebase OR at an idea, PRD, or feature description. Trigger on "/designing-for-behaviour", "does this drive engagement", "why don't users come back / adopt this", "review the behavioural design", "will users actually do this", "make this more habit-forming", "score this experience", or when a PRD/feature needs a behaviour-and-adoption read. Grounded in Atomic Habits, Tiny Habits, Hooked, Badass, Thinking Fast and Slow, and Perceptual Control Theory, applied through four de-duplicated lenses plus an anti-bloat coherence review.
user-invocable: true
argument-hint: "[path to code / PRD file, or a feature description]"
---

# Designing for Behaviour

You orchestrate a behavioural-design review of a product experience. You reconstruct the experience, dispatch four independent lens-analysts in parallel, roll up a score across three dimensions (behaviour / adoption / engagement), rank the gaps, and — the part that makes this worth running — apply a **coherence & anti-bloat review** so the recommendations form one strong core experience rather than a pile of mechanisms that individually make sense and collectively make the product unusable.

This is an **evaluation and recommendation** tool. It stops at prescribed, prioritized changes — it does not implement them. Hand the recommendations to your own dev flow (e.g. `/ship`) to build.

## What you produce

A markdown report `behaviour-review-[target].md` in the working directory (structure in `${CLAUDE_PLUGIN_ROOT}/references/report-template.md`), plus a tight inline summary in chat: the three dimension scores, the top core moves, and the single most important "deliberately NOT adding" call.

## Stage 0 — Scope & mode

From the argument or the conversation, determine:

- **Mode A — existing product / codebase:** the argument is a path, repo, or points at real code. You'll reconstruct the experience the user actually gets, from the code.
- **Mode B — idea / PRD / feature description:** the argument is a document path or a described feature. You'll reconstruct the *intended* experience from the doc.

Then fix the **scope** — the specific experience under review (a flow, feature, or surface), not "the whole app." If the scope or mode is genuinely unclear, ask one focused question; otherwise pick the obvious reading and state it. Don't over-interrogate — a sophisticated user pointing at a signup flow wants you to get on with it.

## Stage 1 — Intake (do this once, for all lenses)

Read `${CLAUDE_PLUGIN_ROOT}/references/foundations.md` and follow its intake protocol for your mode. Reconstruct and write down: the experience and its boundaries, the target behaviour(s), its place in the product, why it exists (user vs. business outcome), the users and their real context, and how behaviour/adoption/engagement are defined *for this product*. Note what you can't observe rather than inventing it.

This intake is shared context you pass to every lens, so they don't each re-derive it. Keep it concrete — cite real screens/files/copy/PRD sections.

## Stage 2 — Dispatch the four lenses (in parallel)

Send **all four Task calls in a single message** so the lenses run concurrently and return independent reads. Each lens re-examines the real artifact through its own frame and returns scored findings, ranked gaps, and candidate recommendations.

The four agents (dispatch by these `subagent_type` names; if your harness namespaces plugin agents, they may appear as `designing-for-behaviour:<name>`):

- `behavioural-loop-analyst` — trigger → action → reward → investment; B=MAP; habit/return loop.
- `cognitive-ease-analyst` — System 1/2, fluency, friction, framing, defaults, anchoring, loss aversion, memory.
- `capability-results-analyst` — does the user get *better*; compelling context; progress curve; empty vs. meaningful engagement.
- `control-autonomy-analyst` — what the user controls; disturbances; conflict; autonomy; anti-manipulation.

Give each agent: the mode, the scope, your Stage-1 intake, and the concrete pointers (files/paths or PRD location) so it can read the real thing. Tell each to stay strictly in its lens. **If the input is an inline feature description with no file to open, paste the full description text into each agent's prompt** — the agent should treat that text as the document, so it has something concrete to analyze rather than a path that doesn't exist.

**Fallback if the plugin agents aren't available as subagent types:** dispatch four `general-purpose` subagents in one message, each instructed to read `foundations.md` + `scoring-rubric.md` + its one `lens-*.md`, evaluate the scope, and return the same output format. A general-purpose subagent won't expand `${CLAUDE_PLUGIN_ROOT}` itself, so first resolve the plugin root to a real absolute path and substitute it into the reference paths you hand them. For a very thin PRD where four subagents would be overkill, you may instead read the four lens references yourself and analyze inline — but the parallel board is the default and is what keeps your context clean for the synthesis.

## Stage 3 — Score

Read `${CLAUDE_PLUGIN_ROOT}/references/scoring-rubric.md`. De-duplicate items where lenses converged on the same moment (count it once), then re-bucket all scored items by dimension and compute: **behaviour / adoption / engagement** percentages, the overall (mean of the three), and each lens's score — with bands and a confidence level. Lead with the three dimension numbers and the one-sentence diagnosis of which is the bottleneck, not the composite.

## Stage 4 — Rank the gaps

Consolidate the lenses' gaps. Merge duplicates (note where lenses converged — that's a priority signal). Rank biggest-blocker-first by how much each gap suppresses behaviour/adoption/engagement, with a concrete anchor for each.

## Stage 5 — Coherence & anti-bloat review (the core of the tool)

Read `${CLAUDE_PLUGIN_ROOT}/references/coherence-and-anti-bloat.md` and run the full pass over the *combined* candidate recommendations: consolidate and de-duplicate, resolve conflicts, enforce a complexity budget calibrated to the archetype, prefer embedding over adding, hunt for the root fix that dissolves several recommendations, run a subtraction pass, and prioritize/sequence. Then apply the ethics gate (`${CLAUDE_PLUGIN_ROOT}/references/ethics-and-dark-patterns.md`) to every surviving recommendation — start from the ethics flags the control-autonomy and cognitive-ease lenses already raised, then scan the rest; reframe or cut anything manipulative; autonomy wins conflicts.

Produce the three buckets: **Core moves** (sequenced, each folding into a named surface), **Fold-ins** (mechanisms embedded, not bolted on), and **Deliberately NOT adding** (what you cut/deferred and why) — plus a one-paragraph coherence rationale. Resist the urge to keep every good recommendation; a product that implements the whole checklist scores 100% and is unusable.

## Stage 6 — Report

Write the full report to `behaviour-review-[target].md` using `${CLAUDE_PLUGIN_ROOT}/references/report-template.md`. Then give the inline summary specified there — skimmable, the point not the depth.

## Guardrails

- **No slop.** Every score, gap, and recommendation carries a concrete anchor (screen/flow/`file:line`/quoted copy/PRD section/moment). Unanchored claims don't ship. Read `foundations.md`'s anti-slop contract if you feel yourself drifting toward generic advice.
- **Right-size the machinery.** Not every product needs streaks, tours, or gamification. Use N/A honestly; the anti-bloat pass exists precisely so the review never tells a focused tool to become a cluttered one.
- **Recommendations only.** Diagnose and prescribe; don't implement.
- **Be honest about confidence.** A reconstructed PRD read is directional; say so. Distinguish observed from inferred.
