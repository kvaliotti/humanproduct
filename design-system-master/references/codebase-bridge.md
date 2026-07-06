# Codebase Bridge

A `DESIGN.md` is implementation-agnostic; a real product is not. This reference maps the token model to
concrete codebases **in both directions**:

- **Extract** (code → model): reverse-engineer a `DESIGN.md` from an existing codebase so it can be
  reviewed or optimized. Used when the input is a repo, not a spec.
- **Emit** (model → code): generate tokens/config for a target stack so a `DESIGN.md` becomes usable.
  Used by `optimize` (apply a system to a product) and `create` (ship the system).

---

## Contents
Where design decisions hide in a codebase (+ fast extraction sweep) · Emit: model → each target (CSS variables / Tailwind v3 / v4 / Style Dictionary / CSS-in-JS / shadcn) · Applying a system to a product codebase (the optimize path)

## Where design decisions hide in a codebase

Before extracting or applying, locate the current source of truth. Check, roughly in this order:

| Signal | Where | What you learn |
|---|---|---|
| CSS custom properties | `:root {}` in global CSS, `theme.css`, `globals.css` | color/space/radius tokens, mode via `[data-theme]` / `.dark` |
| Tailwind config | `tailwind.config.{js,ts}`, `@theme` in CSS (v4) | the scale, extended colors, fontFamily, container |
| Token pipeline | `tokens.json`, `style-dictionary.*`, `*.tokens.json` | a real, exported token layer (best case) |
| CSS-in-JS theme | `theme.ts`, styled-components/emotion `ThemeProvider`, `stitches.config` | tokens as JS objects |
| Component kit | `components/ui/*` (shadcn), Radix, MUI theme, Chakra theme | component API + variant conventions |
| Ad-hoc | inline styles, repeated hex/px literals, `clsx` walls | **no system yet** — the values ARE the (accidental) system |

The last row is the common reality for a "new product." Treat the repeated literals as the *de facto*
design system to be rationalized — grep for them (below) and cluster.

### Fast extraction sweep

```bash
# most-used colors (hex) across the codebase
grep -rhoE '#[0-9a-fA-F]{6}\b' src | sort | uniq -c | sort -rn | head -40
# rgba/hsl usage
grep -rhoE '(rgba?|hsl)\([^)]*\)' src | sort | uniq -c | sort -rn | head -30
# spacing / radius literals
grep -rhoE '\b[0-9]+px\b' src | sort | uniq -c | sort -rn | head -40
# font families & weights
grep -rhoE 'font-(family|weight|size)[^;]*' src | sort | uniq -c | sort -rn | head -30
# existing CSS variables
grep -rhoE '\-\-[a-z0-9-]+:' src | sort -u | head -60
```

Cluster the results into the token families in `references/design-md-format.md`. A color used 400×
is almost certainly `canvas` or `ink`; one used 3× is a candidate for consolidation or removal. Near-
duplicate hexes (small ΔE) are accidental complexity — collapse them and note it.

---

## Emit: model → each target

The token *names* stay role-based; only the syntax changes. Keep one generated source of truth; never
hand-maintain two.

### CSS custom properties (framework-agnostic, safest default)
```css
:root {
  --color-primary: #533afd;
  --color-on-primary: #ffffff;
  --color-ink: #0d253d;
  --color-canvas: #ffffff;
  --color-hairline: #e3e8ee;
  --radius-md: 8px;  --radius-pill: 9999px;
  --space-md: 16px;  --space-lg: 24px;
  --font-body: "Inter", system-ui, sans-serif;
}
:root[data-theme="dark"] {         /* mode = token remap, not a filter */
  --color-canvas: #0b0e11;
  --color-ink: #eaecef;
  --color-hairline: #2b3139;
}
```
Components consume `var(--color-primary)` — one variable, both modes.

### Tailwind (v3 `theme.extend`)
```js
// tailwind.config.js
theme: { extend: {
  colors: { primary: '#533afd', 'on-primary': '#fff', ink: '#0d253d', canvas: '#fff', hairline: '#e3e8ee' },
  borderRadius: { md: '8px', pill: '9999px' },
  spacing: { md: '16px', lg: '24px' },
  fontFamily: { body: ['Inter','system-ui','sans-serif'] },
}}
```
Prefer wiring Tailwind colors to CSS vars (`primary: 'var(--color-primary)'`) so dark mode is one remap.

### Tailwind v4 (`@theme` in CSS)
```css
@theme {
  --color-primary: #533afd;
  --radius-md: 8px;
  --spacing-md: 16px;
}
```

### Style Dictionary / DTCG `tokens.json` (best for multi-platform / handoff)
```json
{ "color": { "primary": { "$value": "#533afd", "$type": "color" } },
  "space": { "md": { "$value": "16px", "$type": "dimension" } } }
```
This is the ideal target when the product needs web + native + Figma parity; the `DESIGN.md` frontmatter
maps almost 1:1 to DTCG groups.

### CSS-in-JS theme object
```ts
export const theme = {
  colors: { primary: '#533afd', onPrimary: '#fff', ink: '#0d253d', canvas: '#fff', hairline: '#e3e8ee' },
  radius: { md: '8px', pill: '9999px' },
  space:  { md: '16px', lg: '24px' },
} as const
```

### Component libraries (shadcn/Radix, MUI, Chakra)
Map the semantic aliases these expect (`--background`, `--foreground`, `--primary`, `--muted`,
`--border`, `--ring`) to the `DESIGN.md` tokens rather than inventing parallel names — e.g.
`--background → {colors.canvas}`, `--foreground → {colors.ink}`, `--border → {colors.hairline}`,
`--ring → {colors.info-ring}`. Then component variants inherit the system for free.

---

## Applying a system to a product codebase (the `optimize` path)

1. **Extract** the de-facto system (sweep above) and reverse it into a draft `DESIGN.md` model.
2. **Diff** it against the target `DESIGN.md` (or the intended direction): which literals violate the
   scale, which colors are off-palette, which components lack states.
3. **Prioritize** by blast radius: fix the tokens that appear most first (change `canvas`/`ink` once,
   fix a thousand screens). Consolidate near-duplicates. Fill missing states/modes.
4. **Emit** the tokens to the target medium and **codemod the literals to tokens** incrementally —
   highest-frequency values first, so each step removes the most drift.
5. **Verify** contrast in every mode after the remap (`references/accessibility.md`) — remapping
   surfaces is exactly when AA regressions sneak in.

Never do a big-bang rewrite. Each step should replace one family of literals with one set of tokens and
leave the product shippable.
