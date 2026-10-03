# Foundations: shared definitions, intake, and lens protocol

The orchestrator and every lens-analyst read this first. Shared work happens once, here, so each lens spends its attention only on its own lane.

## Vocabulary

Three dimensions: **behaviour**, **adoption**, **engagement**. They fail for different reasons and get fixed differently, so keep them apart.

- **Behaviour** — a concrete, observable action toward an outcome. "Creates a project" is a behaviour. "Feels motivated" or "understands the value" is not.
- **Activation** — the first time a user gets the core value. Not signup, setup, or a finished tutorial. It is a moment inside behaviour and adoption, not a fourth dimension.
- **Adoption (breadth)** — how many of the core experiences a user actually uses per period.
- **Engagement (depth)** — how often or how deeply a user performs a core experience per period.

Tag every finding to one or more of the three dimensions. A finding you can't tag is probably not a finding.

## Anti-slop contract

Generic advice ("add onboarding", "reduce friction", "use social proof") is worthless. Every finding and recommendation is anchored to the experience under review:

- **Point at the artifact.** Name the screen, flow, step, empty state, notification, `path/to/file.tsx:line`, or PRD section. "The onboarding is weak" is slop. "`OnboardingWizard` asks for company size, role, and 3 integrations before the user sees a populated dashboard" is a finding.
- **Quote the real copy.** Button labels, headlines, empty-state text. If you are inferring, say so ("assuming the CTA reads 'Get started'").
- **Name the moment.** "When a returning user opens the app with zero new data."
- **One sharp finding beats five vague ones.** Return the few that move behaviour.
- **Say when something is fine.** Marking an item strong or N/A protects the product from machinery it doesn't need.

## Rating items (internal, not a score)

Rate each checklist item you assess:

- **0** — missing or too weak to count.
- **1** — partial: present but incomplete or only on some paths.
- **2** — strong: clearly doing its job.
- **N/A** — irrelevant to this archetype (streaks for a once-a-year tax tool).

Ratings exist to rank gaps and to feed the anti-bloat review. Never add them up, convert them to percentages, or present them as a grade.

**N/A discipline.** Rating an irrelevant item 0 punishes a product for lacking machinery it shouldn't have. That is the bloat this plugin exists to prevent. Only rate items a product of this archetype and natural frequency would benefit from. But don't hide behind N/A: if a mechanism would help and is missing, it's a 0.

Every 0 or 1 needs a one-line anchor, or it doesn't count.

## Intake: reconstruct the experience first

The orchestrator does this once and passes it to every lens. A lens rating an experience nobody reconstructed will hallucinate. Write down:

1. **The experience under review** and its boundaries ("the trial-to-paid upgrade flow", not "the whole app").
2. **The target behaviour(s)** — stated observably, with the situation and moment.
3. **Its place in the journey** (acquisition / activation / core loop / expansion), and what comes before and after.
4. **Why it exists** — the user outcome and the business outcome, kept separate.
5. **The users** and their real context (time, energy, attention, device, current habits and tools).
6. **What counts here** — what activation is for this product, and the natural frequency of the core loop.

### Mode A — existing product / codebase

- Map the entry points and screens for the flow. Trace the first-run path from signup to first value and list every gate (form, permission, config, verification, paywall).
- Find the triggers that bring users back and where each one lands them.
- Find what persists and accumulates between sessions.
- Find the empty states, error states, and the returning user with nothing new. Behaviour breaks there.
- Read the real copy.
- Flag what code can't tell you (real drop-off, what users feel) as an assumption.

Search widely, cite narrowly: only cite files that carry a finding.

### Mode B — idea / PRD / feature description

- Extract the intended flow step by step. Where the PRD is silent about a step, the silence is a finding.
- Check whether target behaviours are stated observably or hidden behind intent words ("users will engage more").
- Look for undesigned moments: the return trigger, the empty state, the second session, lapse and recovery, the failure path.
- "Users will invite teammates" without a trigger, an easy action, and a reason is a hope, not a mechanism.
- Frame findings as risks ("as specified, nothing brings a user back on day 2"), not observed facts.
- No document, just an inline description? That text is the document.

## What each lens owns (and does not)

The lenses are carved so nothing is rated twice. If you notice something outside your lens, note it in one line for the orchestrator and move on. Don't rate it.

- **behavioural-loop** — the repeatable loop: is there a trigger, is the action easy enough to happen, is there a reward, does investment load the next cycle. Owns habit formation, the return loop, and recovery after a lapse.
- **cognitive-ease** — the moment of decision: at each choice point, is the desired action the fast, obvious, low-effort, low-risk one. Framing, defaults, anchoring, salience, memory of the experience.
- **capability-results** — does the user actually get better at something they care about outside the product; the novice-to-capable curve; meaningful vs. empty engagement; attention drained by feature bloat.
- **control-autonomy** — what the user is trying to control, whether the product helps without creating conflict or dependence, whether the product is itself a disturbance. The anti-manipulation backbone.

Shared concerns (these definitions, ethics, the coherence and anti-bloat review) are handled once by the orchestrator, not re-checked by each lens.

## Lens-analyst protocol

1. Read this file and your one `lens-*.md`.
2. Re-examine the real artifact through your lens. Don't rely only on the orchestrator's intake. Codebase: open the actual components, flows, and copy. PRD: read the actual document.
3. Rate the applicable items. Use N/A honestly.
4. Rank your gaps, biggest blocker first.
5. Write candidate recommendations, each tied to a gap. Prefer fixes that fold into an existing surface. Don't worry about total bloat; the orchestrator's coherence pass prunes and integrates.
6. Return only your agent's output format. Be specific or say nothing; unanchored findings are discarded.
