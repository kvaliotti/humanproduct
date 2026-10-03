---
name: create-design-system
description: |
  Build a design system from scratch and output a complete DESIGN.md (plus optional codebase tokens).
  Use when the user says "create a design system", "build our design tokens from scratch", "we have
  nothing — set one up", "define our colors/typography/spacing/components", or is starting a new product
  and needs a coherent visual system. Sizes the system to the product's archetype (a fintech gets
  dual-coded up/down tokens and tabular numerals; an enterprise app gets a semantic ramp and inverse
  tokens; a dev-tool stays minimal), commits to one signature move, checks accessibility, and can emit
  CSS variables / Tailwind / Style Dictionary. Keywords: create design system, design tokens from
  scratch, define color palette, type scale, spacing system, component library, brand system, DESIGN.md.
user-invocable: true
argument-hint: "[product/brand name + what it is] [any brand colors, fonts, or references]"
---

# Create a Design System

Produce a complete, accessible `DESIGN.md` sized for the product's domain. Avoid both failures:
**under-building** (a data app with no numeric type, no dense mode, no error states) and
**over-building** (a landing page with an enterprise semantic ramp it will never use).

Read first:
- `${CLAUDE_PLUGIN_ROOT}/references/archetypes.md` — pick the archetype and its complexity budget.
- `${CLAUDE_PLUGIN_ROOT}/references/design-md-format.md` — the output format and token syntax.
- Scaffold: `${CLAUDE_PLUGIN_ROOT}/skills/create-design-system/assets/DESIGN.template.md`.
- The `patterns-*.md` files — the choices per dimension and what real systems did.
- `${CLAUDE_PLUGIN_ROOT}/references/accessibility.md` — build to AA from the start.
- The nearest exemplar in `${CLAUDE_PLUGIN_ROOT}/references/exemplars/` (Linear = minimal dev-tool,
  Binance = dense fintech) as a worked model.
- `${CLAUDE_PLUGIN_ROOT}/references/codebase-bridge.md` — only if emitting to a stack.

## Steps

1. **Gather inputs.** Ask only what you can't infer: what the product is, brand starting points (logo
   colors, a font, references, a mood), surfaces (marketing and/or product, light/dark), constraints
   (stack, accessibility target, default AA). State your assumptions.
2. **Write the complexity budget.** Name the archetype and spell out what it gets, e.g. "fintech-dense:
   one accent + trading up/down, copy family + tabular numerals, semantic ramp, light+dark, dense tables."
   This is the contract for everything below.
3. **Pick one signature move** and commit (Binance's yellow on near-black, Linear's lavender on a 4-step
   dark ladder). Ration the accent so the signature lands.
4. **Foundations, in order.**
   - Color: accent → near-black ink ladder → surface ramp → hairlines → `on-*` tokens → semantic and
     domain tokens only if the budget calls for them → mode tokens if both surfaces exist. Check AA as you go.
   - Type: one family unless code or money demands a second → weight signature → semantic role scale →
     numeric treatment if data-heavy → open-source substitute pinned to weight and tracking.
   - Spacing: one base unit (4 dense, 8 airy) and a regular named scale.
   - Radius: a small scale that expresses intent, one radius per component type.
   - Elevation: one depth strategy and one focus-ring token.
5. **Components.** Core set (buttons, inputs, cards, nav, tags, links) as `{token}`-referencing specs,
   variants and states as separate entries. Add the domain components the product renders (data table +
   number cells, pricing tiers, empty/loading/error). Skip what it won't use.
6. **Prose.** Fill every body section. Do's/Don'ts must encode this system's guardrails (accent rationing,
   weight rule, domain-token discipline). Known Gaps lists what you deferred.
7. **Check.** Contrast sweep of every component pair in every mode. Domain components present? Scales
   regular and role-named? Signature present everywhere it should be? Lint if available:
   `npx @google/design.md lint DESIGN.md`.
8. **Emit (optional).** Use `codebase-bridge.md`. Dark mode is a token remap, never a filter.

## Output

- `DESIGN.md` in the user's working directory.
- A short rationale: archetype, complexity budget, signature.
- Optional token files for the target stack.

Offer `review-design-system` for an independent check and `optimize-design-system` for later evolution.
