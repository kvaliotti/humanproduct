---
name: optimize-design-system
description: |
  Improve an existing design system and/or roll it into a product codebase. Use when the user says
  "optimize/improve our design system", "clean up our tokens", "our styles are inconsistent",
  "consolidate our colors", "apply this design system to our app", "retrofit these tokens", "reduce token
  bloat", or "add dark mode / semantic colors properly". Works on the spec (consolidate tokens, regularize
  scales, fill gaps, fix contrast) and on the codebase (extract the de-facto system, emit CSS variables /
  Tailwind / Style Dictionary, codemod literals to tokens incrementally). Removes accidental complexity
  without touching complexity the domain needs, and protects the signature. Keywords: optimize design
  system, consolidate design tokens, design consistency, retrofit tokens, dark mode, semantic colors,
  Tailwind, CSS variables.
user-invocable: true
argument-hint: "[path to DESIGN.md and/or codebase] [what to improve, or 'audit + fix']"
---

# Optimize a Design System

Remove accidental complexity, keep essential complexity, never destroy the signature.

Read first:
- `${CLAUDE_PLUGIN_ROOT}/references/archetypes.md` — defines what complexity to protect.
- `${CLAUDE_PLUGIN_ROOT}/references/design-md-format.md` — keep the spec canonical as you edit.
- `${CLAUDE_PLUGIN_ROOT}/references/codebase-bridge.md` — for the codebase path (extract, emit, codemod).
- `${CLAUDE_PLUGIN_ROOT}/references/accessibility.md` — re-run after every color or mode change.
- The `patterns-*.md` file for each dimension you touch.

## Two paths (often both)

- **Spec:** edit the `DESIGN.md`. Merge near-duplicate tokens, snap off-scale values, rename literal names
  to roles, add missing states and modes, fix contrast, bring prose and tokens into lockstep.
- **Codebase:** extract the de-facto system, diff it against the target, emit tokens to the stack, then
  codemod literals to tokens. Follow the retrofit procedure in `codebase-bridge.md`.

Say which path applies.

## Steps

1. **Know the current state.** If no review was just done, do a fast one (`review-design-system` steps 1–4).
   You need the archetype, the top problems, and the Keep list before changing anything.
2. **Confirm the direction** in one line: polish the spec, roll it into a named stack, or evolve it (add
   dark mode, a semantic ramp, a second brand).
3. **Plan.** List the changes as a table: change · type (consolidate / regularize / fill gap / a11y /
   rename) · how widely used · effort · touches Keep list? Highest-frequency tokens first: fixing `canvas`
   or `ink` once fixes every screen. Get a go-ahead before large edits. Anything touching the Keep list
   needs explicit sign-off.
4. **Guard every removal.** Ask: is this accidental or essential? A second font carrying numerals or code,
   green/red price tokens, a second theme where marketing and product genuinely differ, a semantic ramp in
   an enterprise suite, colors that map 1:1 to a taxonomy: all essential. Keep them and discipline them.
   When unsure, ask the user.
5. **Apply in small batches.** Show each diff with a one-line reason. Spec: keep variants and states as
   separate entries; update Do's/Don'ts and Known Gaps. Codebase: one family of literals per step, product
   shippable after each. Never a big-bang rewrite.
6. **Verify.** Re-run the contrast sweep in every mode (surface remaps are where AA regressions appear).
   Confirm the signature survived. Lint if available: `npx @google/design.md lint DESIGN.md`.

## Output

- The updated `DESIGN.md` and/or emitted token files and codemod diffs.
- A short change log: what changed, why, and a line confirming the Keep list survived.
- Deferred items, added to Known Gaps.

Match effort to the ask. "Just consolidate the colors" means the consolidation plus a contrast recheck,
not the full plan.
