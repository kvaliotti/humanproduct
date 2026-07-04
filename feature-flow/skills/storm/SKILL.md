---
name: storm
description: "Stage-1 design for a feature — turn a description into an agreed design before planning or coding. Trigger on \"design this feature\", \"brainstorm this\", \"storm this\", or when /ship calls it. Big mode for new behavior/surfaces; micro mode for small localized changes."
argument-hint: "<feature description> [--micro|--big]"
allowed-tools: Read, Write, Grep, Glob, Bash, AskUserQuestion
---

# storm — cohesive feature design

Turn an idea into an agreed design. The brainstorm spine drives; a **compact** product lens is folded in — never run product frameworks to full length. Terminal state is a design handed back for planning; do **not** start implementing.

## Choose the mode

- **Micro** — small, localized change: no new entity/surface/renderer, low ambiguity.
- **Big** — new behavior, new surface, real product ambiguity, or multiple moving parts.

`--micro`/`--big` override. If genuinely unsure, ask exactly one sizing question, then proceed.

If a `.sitbeh/` directory exists in the repo (a saved Situation/Behaviour analysis — situations, behavioral barriers, and product mechanisms, produced by a sit-beh skill if the user has one), read the relevant files and use them as the product lens instead of re-asking those questions.

## Microstorm

1. Ask **0–2** targeted clarifications — only for genuine ambiguities. If nothing is ambiguous, ask nothing.
2. State a **2–4 sentence design**: what changes, where (files/surfaces), and done-when.
3. Return it. No design doc.

## Big storm

Work through these; keep the product lens tight (the goal is the few highest-value insights, not pages of framework output).

1. **Explore context** — relevant files, docs, recent commits. Follow existing patterns; note any in-path code that needs targeted improvement.
2. **Product lens — one compact pass, ≤4 questions total**, capturing:
   - **Situation** — who hits this, and when (a real moment, not a persona).
   - **Target behavior** — what should the user do / what changes for them.
   - **Top 1–2 barriers** — from *don't-know / don't-want / can't* — and the mechanism that resolves each.
   - **2–3 edge cases / implicit assumptions** to make explicit (the "obvious but unwritten" ones).
3. **Brainstorm spine:**
   - Ask clarifying questions **one at a time** (multiple-choice when it fits; `AskUserQuestion` is good for this).
   - Propose **2–3 approaches** with trade-offs; lead with your recommendation and why.
   - Present the **design in sections** scaled to complexity — architecture, components, data flow, error handling, testing — agreeing after each.
4. **Write a short design doc** to the repo's `design_doc_dir` (from `.claude/feature-flow.local.md`, default `docs/design`) as `YYYY-MM-DD-<topic>.md`. Then **self-review** it: placeholders/TODOs, internal contradictions, scope creep, requirements readable two ways — fix inline.
5. Ask the user to confirm the written design before handing back.

## Return to caller

Report the agreed design (and doc path, if written) so `/ship` can plan it. Note anything that smells like a **stop-condition** (new capability/entity/renderer, schema/migration, auth/billing/security surface) so planning can flag it.

## Principles

- **YAGNI** — cut what isn't needed yet.
- **Isolation & clarity** — small units, clear interfaces; for each: what it does, how it's used, what it depends on.
- **Improve in place, don't sprawl** — fold targeted fixes for in-path problems into the design; no unrelated refactoring.
- **One question at a time** — don't overwhelm.
