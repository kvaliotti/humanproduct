---
name: design-system-master
description: |
  Entry point and router for all design-system work. Use whenever the user wants to work on a design
  system as a whole and it isn't obvious which action they need — e.g. "look at my design system", "help
  with our design tokens", "our UI feels inconsistent", "sort out our colors and typography", "set up a
  design system", "is our design system any good", or they point at a DESIGN.md / codebase / Figma
  export. Diagnoses whether they need to REVIEW (audit quality), OPTIMIZE (improve an existing system,
  including inside a codebase), or CREATE (build one from scratch), then routes to the right skill.
  Grounded in 74 real design systems so it calibrates to the product's archetype instead of forcing
  generic minimalism. Keywords: design system, design tokens, design audit, design review, color system,
  typography scale, spacing, theming, dark mode, component library, brand consistency, DESIGN.md.
user-invocable: true
argument-hint: "[review|optimize|create] [path to DESIGN.md / codebase / or a description]"
---

# Design System Master

The router for design-system work. Three capabilities, one shared knowledge base grounded in a corpus of
74 real design systems (minimal dev-tools → dense financial/enterprise). Your first job is to figure out
**which capability** the user needs and **what input** they have, then hand off — don't try to do
everything in one undifferentiated pass.

## Step 1 — Classify the intent

| If the user wants to… | Route to | Skill |
|---|---|---|
| Judge how good a system is; audit coordination / usability / cohesion; "is it any good", "review", "audit" | **Review** | `review-design-system` |
| Improve an existing system; apply/retrofit it to a product codebase; fix inconsistency; consolidate tokens; "make it better", "clean this up", "roll this out" | **Optimize** | `optimize-design-system` |
| Build a new system; "from scratch", "we have nothing", "set up a design system", "define our tokens/brand" | **Create** | `create-design-system` |

If the request spans two (common: "review it *and* fix it"), run **review first**, present findings, then
offer to continue into **optimize**. Review before optimize is the safe order — you can't improve a system
well until you know what's worth keeping (the rubric's "What to keep" output feeds the optimize pass).

Explicit `review` / `optimize` / `create` as the first argument overrides the classification.

## Step 2 — Identify the input

Look at what the user actually has, because it changes the first move:

- **A `DESIGN.md`** (or a link to one) → read it directly; it's already in the canonical format.
- **A codebase / repo** → the system is implicit in CSS vars, Tailwind config, tokens.json, or repeated
  literals. Use `${CLAUDE_PLUGIN_ROOT}/references/codebase-bridge.md` to extract it before reviewing/optimizing.
- **A live product / screenshots / Figma export** → capture the observable tokens (colors, type, spacing,
  components) into the model first.
- **Nothing yet** (just a product idea/brand) → this is a `create` job.

State briefly what you detected ("You've got a Tailwind config and a lot of inline hex — I'll extract the
de-facto system first") so the user can correct you before you spend effort.

## Step 3 — Orient with the shared knowledge base

All three skills draw on the same plugin-root references. Skim the relevant ones before acting:

- **Format** — `${CLAUDE_PLUGIN_ROOT}/references/design-md-format.md` (the artifact every skill reads/writes)
- **Archetypes & complexity calibration** — `${CLAUDE_PLUGIN_ROOT}/references/archetypes.md`
  (**read this early** — it stops you judging a legitimately-complex system as "bloated")
- **Patterns** — `patterns-color.md`, `patterns-typography.md`, `patterns-space-shape-elevation.md`,
  `patterns-components-theming.md`
- **Rubric** — `${CLAUDE_PLUGIN_ROOT}/references/review-rubric.md`
- **Expert panel** — `${CLAUDE_PLUGIN_ROOT}/references/expert-panel.md`
- **Accessibility** — `${CLAUDE_PLUGIN_ROOT}/references/accessibility.md`
- **Codebase bridge** — `${CLAUDE_PLUGIN_ROOT}/references/codebase-bridge.md`
- **Exemplars** — `${CLAUDE_PLUGIN_ROOT}/references/exemplars/*.DESIGN.md` (5 complete real specs across archetypes)

## The one rule that governs all three capabilities

**Calibrate to the archetype; never impose generic minimalism.** A trading platform that dual-codes
green/red, runs two font families (copy + numerals), and ships two theme surfaces is *correctly complex*.
An enterprise system with a full semantic ramp and inverse tokens is *correctly complex*. Your job is to
tell **essential** complexity (the domain requires it) from **accidental** complexity (redundant tokens,
one-off values, undocumented states) — and only ever remove the second. Read `archetypes.md` before you
judge, build, or change anything.

## Lightweight mode

If the ask is genuinely small ("what's a good spacing scale?", "is #767676 on white accessible?"), just
answer from the relevant reference — don't spin up a full review. Match effort to the request.
