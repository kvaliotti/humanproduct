# Design System Master

**Review** a design system, **optimize** one (including retrofitting it into a product codebase), or
**create** one from scratch. Everything reads or writes a single lintable `DESIGN.md` (the
token-referencing `getdesign.md` format).

Distilled from 74 real-world design systems, from minimal dev-tools (Linear, Vercel) to dense fintech
(Binance, Coinbase) and enterprise (IBM Carbon). That grounding is what stops it from "simplifying"
complexity a domain needs: dual-coded green/red, a numeric font, multi-surface theming, semantic ramps.

## Skills

| Skill | What it does | Say |
|---|---|---|
| **design-system-master** | Router. Works out review vs optimize vs create, and what input you have (DESIGN.md, codebase, nothing). | "help with my design system", "our UI is inconsistent" |
| **review-design-system** | Accessibility gate (real contrast math), complexity-fit gate (judged against the archetype), then the top fixes and what to keep. About one page, no scores. | "review my design system", "audit our tokens" |
| **optimize-design-system** | Consolidates tokens, regularizes scales, fills gaps, fixes contrast, and/or rolls the system into a codebase (CSS vars / Tailwind / Style Dictionary) one literal family at a time. Protects the signature. | "clean up our tokens", "apply this system to our app", "add dark mode properly" |
| **create-design-system** | Builds a complete `DESIGN.md` sized to the product's archetype, with one chosen signature. | "create a design system", "we have nothing — set one up" |

## The one rule

**Calibrate to the archetype; never impose generic minimalism.** Every skill classifies the product's
archetype first (`references/archetypes.md`) and judges each piece of complexity as **essential** (the
domain needs it: keep it) or **accidental** (redundant, one-off, undocumented: remove it).

## References (plugin root)

- `design-md-format.md` — the artifact format and token syntax
- `archetypes.md` — archetypes and the essential-vs-accidental test (the load-bearing file)
- `accessibility.md` — WCAG contrast math and non-color-signal checks
- `codebase-bridge.md` — extract a system from code, emit tokens, retrofit procedure
- `patterns-color.md` · `patterns-typography.md` · `patterns-space-shape-elevation.md` ·
  `patterns-components-theming.md` — what real systems did, with their stated rules
- `exemplars/` — two complete real specs at opposite ends of the range: Linear (minimal dev-tool) and
  Binance (dense fintech)

Validate output with `npx @google/design.md lint DESIGN.md` if available.
