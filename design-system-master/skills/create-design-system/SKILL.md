---
name: create-design-system
description: |
  Build a design system from scratch and output a complete DESIGN.md (plus optional codebase tokens).
  Use when the user says "create a design system", "build our design tokens from scratch", "we have
  nothing — set one up", "define our colors/typography/spacing/components", or is starting a new product
  and needs a coherent visual system. Picks the archetype and complexity budget for the domain (a fintech
  gets dual-coded up/down tokens and tabular numerals; an enterprise app gets a semantic ramp and inverse
  tokens; a dev-tool stays minimal), chooses one signature move, defines foundations → components → usage
  rules, checks accessibility, runs a five-lens expert panel, and can emit CSS variables / Tailwind /
  Style Dictionary. Grounded in 74 real systems. Keywords: create design system, design tokens from
  scratch, define color palette, type scale, spacing system, component library, brand system, DESIGN.md.
user-invocable: true
argument-hint: "[product/brand name + what it is] [any brand colors, fonts, or references]"
---

# Create a Design System

Produce a complete, coherent, accessible `DESIGN.md` for a product that has none — sized correctly for its
domain. The failure modes to avoid are equal and opposite: **under-building** (a data-heavy app with no
numeric type, no dense mode, no error states) and **over-building** (a landing page with an enterprise
semantic ramp it will never use). The archetype decides the complexity budget.

## Load the knowledge base

- `${CLAUDE_PLUGIN_ROOT}/references/archetypes.md` — **first**; pick the archetype and its complexity budget.
- `${CLAUDE_PLUGIN_ROOT}/references/design-md-format.md` — the exact output format and token syntax.
- `patterns-color.md`, `patterns-typography.md`, `patterns-space-shape-elevation.md`,
  `patterns-components-theming.md` — the menu of proven patterns to choose from per dimension.
- `${CLAUDE_PLUGIN_ROOT}/references/accessibility.md` — build to AA from the start, not as a fix later.
- `${CLAUDE_PLUGIN_ROOT}/references/expert-panel.md` — validate the result before shipping it.
- `${CLAUDE_PLUGIN_ROOT}/references/exemplars/` — read the closest-archetype exemplar as a worked model.
- `${CLAUDE_PLUGIN_ROOT}/references/codebase-bridge.md` — if emitting to a stack.
- Scaffold: `${CLAUDE_PLUGIN_ROOT}/skills/create-design-system/assets/DESIGN.template.md`.

## Workflow

Copy this checklist into your response and tick items as you go:

```
Create progress:
- [ ] 1. Gather inputs (product, brand, surfaces, constraints)
- [ ] 2. Choose the archetype & write the complexity budget
- [ ] 3. Pick the one signature move
- [ ] 4. Define foundations: color → type → spacing → radius → elevation
- [ ] 5. Build components (core + domain-specific)
- [ ] 6. Write the prose (incl. Do's/Don'ts + Known Gaps)
- [ ] 7. Verify: accessibility sweep + five-lens expert panel
- [ ] 8. Emit tokens to the target stack (optional)
```

### 1. Gather inputs (ask only what you can't infer)
- **What is the product?** (the domain drives the archetype — fintech, dev-tool, marketing site, dashboard,
  consumer app, enterprise suite, creative canvas…)
- **Brand starting points?** existing logo colors, a font, competitors/references, a mood ("calm and
  editorial", "high-energy", "serious and dense").
- **Surfaces?** marketing + product? dark, light, or both? web only or native too?
- **Constraints?** existing codebase/stack, accessibility target (default AA), team size (governance need).
Keep this to a few sharp questions; infer the rest and state your assumptions.

### 2. Choose the archetype & complexity budget
Name the archetype from `archetypes.md` and write the **complexity budget** explicitly — e.g.
"dev-tool-minimal: one accent, tight neutral ramp, single family, no semantic ramp yet, light+dark" or
"fintech-dense: one accent + trading up/down, dual family (copy + tabular numerals), semantic ramp,
light+dark, dense tables." This is the contract for everything below; it prevents both failure modes.

### 3. Pick the signature (one distinctive move)
Every strong system has one: Stripe's gradient mesh, Binance's yellow voltage on near-black, IBM's
thin-300 display on square chrome. Choose ONE and commit — it's what makes the system recognizable rather
than a default. Ration the accent so the signature lands.

### 4. Define foundations, in order
Build the frontmatter dimension by dimension, each choice justified by a pattern from the references:
1. **Color** — brand/accent (+ how it's rationed) → neutral ink ladder (near-black, not `#000`) → surface
   ramp → hairlines → `on-*` tokens → semantic ramp *if the budget calls for it* → domain/dual-code tokens
   *if the domain calls for it* → mode tokens (dark/inverse) if both surfaces exist. Verify every
   text/surface pair for AA as you go.
3. **Typography** — family strategy (single, or dual if numerics/code demand it) → weight signature → the
   semantic role scale (display→micro) with sizes/line-height/tracking → numeric/tabular treatment if data-
   heavy → open-source substitute if a proprietary font is named.
4. **Spacing** — one base unit (4 or 8px) → a regular named scale → section/card/gutter norms.
5. **Radius** — a small scale expressing intent (pill vs square) → radius-per-component.
6. **Elevation** — pick ONE depth strategy suited to the archetype (flat color-block / layered shadow /
   gradient / glass / inverse-tone) → a level table → one focus-ring token.

### 5. Build the components
Start with the core taxonomy (buttons primary/secondary/tertiary, inputs, cards, nav, tags, links,
footer), each as `{token}`-referencing specs with **variants and states as separate entries**. Add the
**domain-specific** components the product actually needs (data table + numeric cells for fintech, pricing
tiers for SaaS, empty/loading/error states for any app). Don't ship components the product won't use.

### 6. Write the prose
Fill every body section (Overview + Key Characteristics, Colors, Typography, Layout, Elevation, Shapes,
Components, **Do's and Don'ts**, Responsive Behavior, Iteration Guide, **Known Gaps**). The Do's/Don'ts
must encode the guardrails specific to *this* system (how the accent is rationed, the weight rule, the
domain-token discipline). Known Gaps must honestly list what you deferred.

### 7. Verify & gate
- **Accessibility:** sweep every component pair in every mode per `accessibility.md`; fix before shipping.
- **Expert panel:** run all five lenses (`expert-panel.md`). The Product Designer checks the domain
  components exist; the Systems Architect checks scales are regular and tokens role-named; the Art Director
  checks the signature is present and consistent.
- If the linter is available: `npx @google/design.md lint DESIGN.md`.

### 8. Emit (optional)
If there's a target codebase, use `codebase-bridge.md` to emit CSS variables / Tailwind theme / Style
Dictionary `tokens.json`, wiring dark mode as a token remap (never a filter).

## Output
- A complete `DESIGN.md` in the user's working directory (canonical format, lints clean, passes AA).
- A short **rationale**: the archetype, the complexity budget, and the signature — so the choices are
  legible and defensible.
- Optional emitted token files for the target stack.

## Handoff
Offer `review-design-system` for an independent scored audit of what you built, and
`optimize-design-system` when the product later needs to evolve (add a mode, a brand, a semantic ramp).
