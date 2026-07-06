# The DESIGN.md Format (the canonical artifact)

Every skill in this plugin reads, reviews, produces, or refactors a **`DESIGN.md`** file. It is the
single source of truth for a design system: a token-referencing spec that is both human-readable
prose and machine-lintable structured data. It is the format used by all 74 exemplars this plugin is
grounded in (see `references/exemplars/`), and it is what `create-design-system` outputs, what
`review-design-system` audits against, and what `optimize-design-system` refactors.

> A `DESIGN.md` is **not** a stylesheet. It is the *contract* a stylesheet, Tailwind config, or
> token pipeline is generated from. Keep it implementation-agnostic; the codebase bridge
> (`references/codebase-bridge.md`) handles the mapping to CSS/Tailwind/Style Dictionary.

---

## Contents
Anatomy · The token-reference syntax · Frontmatter layer (colors / typography / rounded / spacing / components) · Body layer (required sections & what belongs in each) · Validation · Minimal skeleton

## Anatomy

```
DESIGN.md
├── YAML frontmatter  ← the machine-readable token + component layer
│   ├── version / name / description
│   ├── colors:        (token name → hex)
│   ├── typography:     (role → { fontFamily, fontSize, fontWeight, lineHeight, letterSpacing, fontFeature })
│   ├── rounded:        (token → radius)
│   ├── spacing:        (token → length)
│   └── components:     (component → spec, referencing tokens via {group.token})
└── Markdown body      ← the human-readable design intent + usage rules
    ├── ## Overview  (+ Key Characteristics)
    ├── ## Colors
    ├── ## Typography
    ├── ## Layout
    ├── ## Elevation & Depth
    ├── ## Shapes
    ├── ## Components
    ├── ## Do's and Don'ts
    ├── ## Responsive Behavior
    ├── ## Iteration Guide
    └── ## Known Gaps        (optional but recommended)
```

The frontmatter is the **tokens**; the body is the **why and when**. A good `DESIGN.md` keeps the two in
lockstep — every color/role/component the prose mentions exists as a token, and every token is
explained in the prose.

---

## The token-reference syntax

Anywhere a value repeats, reference a token instead of hardcoding it. This is the single most important
rule of the format — it is what makes the system *a system* rather than a list of one-off values.

- `{colors.primary}` → the `primary` entry under `colors:`
- `{typography.body-md}` → the `body-md` role under `typography:`
- `{rounded.pill}` · `{spacing.lg}`
- `{component.button-primary}` → reference another component (used in prose)

In `components:`, fields point at tokens:

```yaml
components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.button}"
    rounded: "{rounded.md}"
    padding: 12px 24px
    height: 40px
```

Raw hex or px inside `components:` (instead of a `{token}`) is a smell — it means the value escaped the
token layer. The one legitimate exception is a genuinely component-local value that will never repeat
(e.g. a specific `padding: 12px 24px`); even then, prefer `{spacing.*}` composition.

---

## Frontmatter layer, in detail

### `colors:`
Flat map of `token-name: "#hex"`. Group *conceptually in the prose*, not by nesting. Typical token
families (name them by **role**, not by hue — `ink`, `canvas`, `hairline`, not `gray-900`):

- **Brand / accent**: `primary`, `primary-active` (press), `primary-disabled`, optional `primary-soft`/`-subdued`.
- **Text (ink)**: `ink` (strongest), `ink-muted`, `ink-subtle` — a legibility ladder, near-black not pure `#000`.
- **Surface**: `canvas` (page floor), `surface-1`, `surface-2` (elevation-by-tone), plus `-dark`/`inverse-*` for modes.
- **Hairline / border**: `hairline`, `hairline-strong`.
- **On-color**: `on-primary`, `on-dark` — the text color that sits *on* a filled surface.
- **Semantic** (when warranted): `semantic-success`, `-warning`, `-error`, `-info`.
- **Domain** (when the domain demands it): e.g. `trading-up` / `trading-down`, data-viz categoricals.

See `references/patterns-color.md` for which of these a given system actually needs.

### `typography:`
Map of `role: { fontFamily, fontSize, fontWeight, lineHeight, letterSpacing, fontFeature }`. Name roles
**semantically** (`display-xl`, `heading-md`, `body-md`, `caption`, `button`, `number-md`), never by size
(`text-56`). `fontFeature` carries OpenType settings like `tnum` (tabular figures) or `ss01`.

### `rounded:` / `spacing:`
Ordered scales with named steps (`xs…xl`, `pill`/`full`; `xxs…section`/`huge`). Keep them small and
regular — a scale with a value used once is a scale with a hole in it.

### `components:`
Each component is a flat spec of token references plus any component-local geometry. **Variants and
states are separate top-level entries**, not nested objects:

```yaml
button-primary:            { ... }
button-primary-active:     { ... }   # pressed state = its own entry
button-primary-disabled:   { ... }
button-secondary-on-dark:  { ... }   # mode variant = its own entry
```

---

## Body layer — required sections & what belongs in each

| Section | Purpose | Must contain |
|---|---|---|
| **Overview** | The one-paragraph thesis of the system + a "Key Characteristics" bullet list | The single sentence that captures the brand's design DNA |
| **Colors** | Every token grouped by role, each with its hex, name, and *usage* | Brand/Accent · Surface · Text · Hairlines · Semantic · Domain (as applicable) |
| **Typography** | Font family strategy, the full scale table, principles, font-substitute note | A `\| role \| size \| weight \| line-height \| tracking \| use \|` table |
| **Layout** | Spacing system, grid/container, whitespace philosophy | Base unit, token list, section/card padding norms |
| **Elevation & Depth** | The depth *strategy* (flat color-block / shadow / gradient / glass / inverse-tone) | A level table + focus-ring spec |
| **Shapes** | Radius scale + photography/icon geometry | Radius-per-component table |
| **Components** | Prose spec of each component grouped by kind | Buttons, Cards, Inputs, Nav, Pills/Tags, Signature, Footer |
| **Do's and Don'ts** | The guardrails that keep contributors on-system | Rationed-accent rules, weight rules, domain-token discipline |
| **Responsive Behavior** | Breakpoints, touch targets, collapsing strategy | A breakpoint table + 44px touch-target note |
| **Iteration Guide** | How to extend the system without breaking it | "one component at a time", "reference tokens", "variants as new entries" |
| **Known Gaps** | Honest list of what is *not* specified yet | The states/surfaces/flows not yet extracted |

The **Do's and Don'ts** and **Known Gaps** sections are what separate a living design system from a
static screenshot. Never omit them.

---

## Validation

The upstream tooling ships a linter:

```bash
npx @google/design.md lint DESIGN.md
```

If it is available, run it after any edit. Independently of the linter, this plugin's own checks
(`references/review-rubric.md`) verify token-reference integrity, contrast (`references/accessibility.md`),
and prose/token lockstep. A `DESIGN.md` that lints clean can still fail the rubric — the linter checks
*form*, the rubric checks *coherence*.

---

## Minimal skeleton

`create-design-system` ships a fuller scaffold at
`skills/create-design-system/assets/DESIGN.template.md`. The irreducible minimum is:

```markdown
---
version: alpha
name: <Product>-design-system
description: <one-sentence design DNA — the thesis a reader should walk away with>
colors:
  primary: "#____"
  on-primary: "#ffffff"
  ink: "#____"
  ink-muted: "#____"
  canvas: "#ffffff"
  surface-1: "#____"
  hairline: "#____"
typography:
  display-lg: { fontFamily: Inter, fontSize: 48px, fontWeight: 600, lineHeight: 1.1, letterSpacing: -0.5px }
  body-md:    { fontFamily: Inter, fontSize: 15px, fontWeight: 400, lineHeight: 1.5, letterSpacing: 0 }
  button:     { fontFamily: Inter, fontSize: 14px, fontWeight: 600, lineHeight: 1,   letterSpacing: 0 }
rounded: { sm: 4px, md: 8px, lg: 12px, pill: 9999px }
spacing: { xs: 4px, sm: 8px, md: 16px, lg: 24px, xl: 32px }
components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.button}"
    rounded: "{rounded.md}"
    padding: 8px 16px
---

## Overview
...
```
