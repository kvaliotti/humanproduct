# Design System Master

Your design-system master. **Review** an existing design system, **optimise** one (including retrofitting
it into a real product codebase), or **create** one from scratch — all producing or working against a
single lintable `DESIGN.md` (the token-referencing `getdesign.md` format).

Grounded in a corpus of **74 real-world design systems** — from minimal dev-tools (Linear, Vercel, Notion)
to dense financial/trading platforms (Binance, Coinbase) to enterprise systems (IBM Carbon, MongoDB) to
expressive consumer and automotive brands (Airtable, Nike, Ferrari). That grounding is what stops it from
naively "simplifying" complexity a domain legitimately needs (dual-coded green/red, dual font stacks,
multi-surface theming, semantic ramps).

## Skills

| Skill | What it does | Trigger phrases |
|---|---|---|
| **design-system-master** | Entry point / router. Diagnoses whether you need review, optimize, or create, and what input you have (a DESIGN.md, a codebase, or nothing yet). | "help with my design system", "look at our design tokens", "our UI is inconsistent" |
| **review-design-system** | Scored audit across coordination (color/type/space/shape/elevation), ease of working with it, and cohesion — gated by accessibility (real contrast math) and complexity-fit, then a five-lens expert panel. | "review my design system", "audit our tokens", "is our design system any good" |
| **optimize-design-system** | Improves a system: consolidates tokens, regularizes scales, fills gaps, fixes contrast — and/or rolls it into a codebase (CSS variables / Tailwind / Style Dictionary), codemodding literals → tokens incrementally. Protects the signature. | "clean up our tokens", "make our UI consistent", "apply this system to our app", "add dark mode properly" |
| **create-design-system** | Builds a system from scratch as a complete `DESIGN.md`, sized to the product's archetype (a fintech gets up/down tokens + tabular numerals; a dev-tool stays minimal), with one chosen signature. | "create a design system", "define our colors/typography/spacing", "we have nothing — set one up" |

## The one rule

**Calibrate to the archetype; never impose generic minimalism.** The plugin classifies the product's
archetype first (`references/archetypes.md`) and judges every piece of complexity as either **essential**
(the domain requires it — keep and discipline it) or **accidental** (redundant tokens, one-off values,
undocumented states — remove it). A trading terminal and a landing page are held to different bars, on
purpose.

## The DESIGN.md artifact

Everything reads/writes a `DESIGN.md`: YAML frontmatter of tokens (`colors`, `typography`, `rounded`,
`spacing`) + component specs that reference tokens via `{group.token}`, plus prose sections (Overview,
Colors, Typography, Layout, Elevation, Shapes, Components, Do's/Don'ts, Responsive, Iteration Guide, Known
Gaps). See `references/design-md-format.md`. Validate with `npx @google/design.md lint DESIGN.md`.

## Knowledge base (plugin-root `references/`)

- `design-md-format.md` — the canonical artifact format & token syntax
- `archetypes.md` — product archetypes + the essential-vs-accidental complexity calibration
- `patterns-color.md` · `patterns-typography.md` · `patterns-space-shape-elevation.md` · `patterns-components-theming.md` — corpus-distilled pattern libraries
- `review-rubric.md` — the scoring instrument · `expert-panel.md` — the five-lens gate
- `accessibility.md` — WCAG contrast math & non-color-signal checks
- `codebase-bridge.md` — extract a system from a codebase / emit tokens to CSS vars, Tailwind, Style Dictionary
- `exemplars/` — five complete real specs spanning the archetype range (Binance, IBM, Linear, Stripe, Airtable)

Skills are callable standalone (`/review-design-system`, `/optimize-design-system`, `/create-design-system`)
or routed via `/design-system-master`.
