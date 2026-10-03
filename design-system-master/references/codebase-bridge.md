# Codebase Bridge

Map a `DESIGN.md` to a real codebase in both directions: **extract** (code → model, so a repo can be
reviewed or optimized) and **emit** (model → code, so a spec becomes usable).

## Where the system hides

Check in this order:

| Signal | Where |
|---|---|
| CSS custom properties | `:root {}` in `globals.css` / `theme.css`; modes via `[data-theme]` or `.dark` |
| Tailwind | `tailwind.config.{js,ts}` (v3) or `@theme` in CSS (v4) |
| Token pipeline | `tokens.json`, `*.tokens.json`, `style-dictionary.*` (best case) |
| CSS-in-JS theme | `theme.ts`, `ThemeProvider`, `stitches.config` |
| Component kit | `components/ui/*` (shadcn), Radix, MUI / Chakra theme |
| Ad hoc | inline styles, repeated hex/px literals — the literals *are* the de-facto system |

The last row is the usual case for a young product.

### Extraction sweep

```bash
grep -rhoE '#[0-9a-fA-F]{6}\b' src | sort | uniq -c | sort -rn | head -40     # colors
grep -rhoE '(rgba?|hsl)\([^)]*\)' src | sort | uniq -c | sort -rn | head -30  # rgba/hsl
grep -rhoE '\b[0-9]+px\b' src | sort | uniq -c | sort -rn | head -40          # spacing/radius
grep -rhoE 'font-(family|weight|size)[^;]*' src | sort | uniq -c | sort -rn | head -30
grep -rhoE '\-\-[a-z0-9-]+:' src | sort -u | head -60                         # existing CSS vars
```

Cluster the results into the token families in `design-md-format.md`. Frequency tells you the role: the
color used hundreds of times is `canvas` or `ink`; one used 3 times is a candidate to merge or remove.
Near-duplicate hexes are accidental complexity: collapse them and note it. Verify a token by what
components do with it, not by its variable name (a `--button-background-primary` can turn out to be the
link color).

## Emit

Token names stay role-based in every target. Keep one generated source of truth; never hand-maintain two.

- **CSS custom properties** — the safe default. Dark mode is a remap under `:root[data-theme="dark"]`,
  never a CSS `invert()` filter (it breaks photos and shadows). Components consume one variable for both modes.
- **Tailwind v3** — `theme.extend` colors / borderRadius / spacing / fontFamily. Point colors at the CSS
  vars (`primary: 'var(--color-primary)'`) so dark mode stays one remap.
- **Tailwind v4** — `@theme { --color-primary: …; --radius-md: …; --spacing-md: … }`.
- **Style Dictionary / DTCG `tokens.json`** — best for web + native + Figma parity. Frontmatter groups map
  almost 1:1 to DTCG groups (`{ "$value": …, "$type": "color" }`).
- **CSS-in-JS** — a typed `theme` object with the same role names.
- **shadcn / Radix / MUI / Chakra** — map their expected aliases to your tokens instead of inventing
  parallel names: `--background → canvas`, `--foreground → ink`, `--border → hairline`,
  `--ring → focus-ring color`, `--primary → primary`, `--muted → surface-1`. Variants then inherit the system.

## Retrofit procedure (the optimize path)

1. **Extract** the de-facto system and write it up as a draft `DESIGN.md`.
2. **Diff** against the target spec: off-scale literals, off-palette colors, components missing states.
3. **Prioritize** by frequency. Fix the most-used tokens first (change `canvas`/`ink` once, fix every
   screen). Merge near-duplicates. Fill missing states and modes.
4. **Emit** tokens, then **codemod literals to tokens** one family at a time, most frequent first.
5. **Verify** contrast in every mode after each remap (`accessibility.md`). Surface remaps are where AA
   regressions appear.

Never big-bang. Each step replaces one family of literals and leaves the product shippable.
