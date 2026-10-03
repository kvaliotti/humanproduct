---
name: designing-for-behaviour
description: Review how well a product experience drives user behaviour, adoption, and engagement — find the gaps and recommend the smallest integrated set of fixes that strengthens one coherent core experience instead of bloating it with bolted-on mechanisms. Use whenever the user wants to review, audit, critique, rate, or improve a product, feature, or flow's behavioural design, habit formation, activation, retention, onboarding, engagement loop, or adoption — for an existing product/codebase OR an idea, PRD, or feature description. Trigger on "/designing-for-behaviour", "does this drive engagement", "why don't users come back / adopt this", "review the behavioural design", "will users actually do this", "make this more habit-forming", "score this experience", or when a PRD needs a behaviour-and-adoption read. Grounded in Atomic Habits, Tiny Habits, Hooked, Badass, Thinking Fast and Slow, and Perceptual Control Theory, applied through four lenses plus an anti-bloat coherence review.
user-invocable: true
argument-hint: "[path to code / PRD file, or a feature description]"
---

# Designing for Behaviour

You orchestrate a behavioural-design review. You reconstruct the experience, dispatch four lens-analysts in parallel, rank the gaps, and then run the **coherence and anti-bloat review**, the part that makes this worth running. It turns four lenses' worth of good advice into one strong core experience instead of a pile of mechanisms.

This tool evaluates and recommends. It does not implement.

**Output:** `behaviour-review-[target].md` in the working directory (structure and two-page cap in `${CLAUDE_PLUGIN_ROOT}/references/report-template.md`), plus a short inline summary. No score.

## Stage 0 — Scope and mode

- **Mode A — codebase:** the argument is a path or repo. Reconstruct the experience users actually get.
- **Mode B — PRD / idea:** the argument is a document or a described feature. Reconstruct the intended experience.

Fix the scope to one flow, feature, or surface, not "the whole app." If scope or mode is genuinely unclear, ask one question. Otherwise pick the obvious reading, state it, and proceed.

## Stage 1 — Intake (once, shared by all lenses)

Read `${CLAUDE_PLUGIN_ROOT}/references/foundations.md` and follow its intake for your mode. Cite real screens, files, copy, or PRD sections. Note what you can't observe instead of inventing it.

## Stage 2 — Dispatch the four lenses in parallel

Send all four calls in one message. Use these `subagent_type` names (they may be namespaced `designing-for-behaviour:<name>`):

- `behavioural-loop-analyst` — trigger → action → reward → investment; the return loop.
- `cognitive-ease-analyst` — decision points: fluency, friction, framing, defaults, anchoring, memory.
- `capability-results-analyst` — does the user get better; meaningful vs. empty engagement.
- `control-autonomy-analyst` — what the user controls; disturbances; conflict; anti-manipulation.

Give each the mode, the scope, your intake, and pointers to the real files or PRD. If the input is an inline description with no file, paste the full text into each prompt.

**Fallback** if the plugin agents aren't available: dispatch four `general-purpose` subagents in one message, each told to read `foundations.md` and its one `lens-*.md` and to return the output format from the matching `agents/<lens>-analyst.md`. Resolve `${CLAUDE_PLUGIN_ROOT}` to a real absolute path first; general-purpose agents won't expand it. For a very thin PRD you may run the four lenses inline yourself.

## Stage 3 — Rank the gaps

Merge gaps the lenses share; count a shared moment once and note the convergence. Agreement across lenses is a priority signal. Rank biggest blocker first, using the 0/1 ratings and convergence. Name the bottleneck dimension (behaviour, adoption, or engagement) in a sentence. Do not compute or report a score.

## Stage 4 — Coherence and anti-bloat review

Read `${CLAUDE_PLUGIN_ROOT}/references/coherence-and-anti-bloat.md` and run the full pass over the combined candidate recommendations. Use the lenses' N/A lists and "leave alone" items as inputs to the budget and subtraction steps.

Then apply the ethics gate (`${CLAUDE_PLUGIN_ROOT}/references/ethics-and-dark-patterns.md`) to every surviving recommendation. Start from the ethics flags the control-autonomy and cognitive-ease lenses raised. Reframe or cut anything manipulative. Autonomy wins conflicts.

Resist keeping every good recommendation. A product that implements the whole checklist is unusable.

## Stage 5 — Report

Write the report and the inline summary per `report-template.md`. Lead with the core moves. Stay within the caps.

## Guardrails

- **Anchor everything.** Every gap and recommendation points at a screen, flow, `file:line`, quoted copy, PRD section, or moment. Unanchored claims don't ship.
- **Right-size the machinery.** Not every product needs streaks, tours, or gamification. Use N/A honestly.
- **No invented numbers.** No scores, percentages, or confidence labels. Say what was observed vs. inferred in "What we don't know."
- **Recommendations only.** Diagnose and prescribe; don't implement.
