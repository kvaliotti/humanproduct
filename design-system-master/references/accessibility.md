# Accessibility Checks

A design system is a promise that anything built from it will be usable. These are the checks the
**Accessibility Specialist** lens runs and that rubric gate **G1** enforces. They are deterministic — do
the math, report the numbers, don't guess.

---

## 1. Contrast (the hard gate)

WCAG 2.x contrast ratio between foreground and background:

```
L = 0.2126·R + 0.7152·G + 0.0722·B      (linearized sRGB channels)
ratio = (L_lighter + 0.05) / (L_darker + 0.05)
```

**Linearize each channel** `c` (R,G,B as 0–1): `c ≤ 0.03928 ? c/12.92 : ((c+0.055)/1.055)^2.4`.

| Content | Minimum (AA) | Enhanced (AAA) |
|---|---|---|
| Body text (< 18pt / < 14pt bold) | **4.5:1** | 7:1 |
| Large text (≥ 18pt / ≥ 14pt bold) | **3:1** | 4.5:1 |
| UI component boundaries, focus indicators, meaningful graphics | **3:1** | — |
| Disabled elements | exempt (but keep ~3:1 so they're still perceivable) |

**What to check in a `DESIGN.md`:** for every component with `textColor` + `backgroundColor`, resolve both
tokens to hex and compute the ratio. Do this for **every mode** (a pair that passes on light can fail on
dark). Common offenders: muted text on tinted surfaces, `on-primary` white on a mid-tone accent, hairline
text, placeholder text.

Report failures as: `button-secondary — ink-muted #525252 on surface-1 #f4f4f4 = 4.1:1 ✗ (needs 4.5:1)`.

You can compute ratios by hand for a few pairs, or write a tiny script (Bash/Python) to sweep every
`components:` pair when a system is large. Prefer the script for anything over ~10 components.

---

## 2. Color is never the only signal

Meaning carried by hue alone is invisible to color-blind users (~8% of men) and in grayscale.

- **Dual-coded up/down** (trading green/red, diffs) MUST also carry a **shape or sign**: a ▲/▼ arrow, a
  `+`/`−`, a word. Green/red is the accelerator, not the only cue. (This is why disciplined finance
  systems pair the color with an arrow — see `references/patterns-color.md`.)
- **Status** (success/warning/error) needs an **icon + text**, not just a colored dot.
- **Required fields, errors, selection** need a non-color affordance (asterisk, border, checkmark).

Flag any component whose state is distinguishable *only* by color.

---

## 3. Focus & operability

- **Every** interactive component has a **visible focus state** — ideally one reused focus-ring token
  (`0 0 0 2px {colors.info-ring}` or a 2px offset outline) with ≥ 3:1 against its background.
- Focus is never removed (`outline: none`) without a replacement.
- Hit targets ≥ **44×44px** (WCAG 2.5.5). Domain exceptions exist (dense trading rows at ~28px, data-table
  row actions) — allow them but **flag them explicitly** and require the whole row/cell to be the target.

---

## 4. Motion & preference

- Any motion/transition tokens should have a `prefers-reduced-motion` story (documented, even if "disable
  non-essential motion").
- Dark mode should be a real token remap (see theming in `references/patterns-components-theming.md`), not
  a CSS `invert()` filter — inverted photos and shadows break.

---

## 5. Typographic legibility floors

- Body text ≥ 14px (16px preferred); anything smaller (captions, micro) reserved for genuinely secondary
  content and never for essential instructions.
- Line-height ≥ 1.4 for body copy; line length target 45–75 characters.
- Don't rely on `font-weight: 300` for small body sizes on low-contrast pairings — thin + small + low
  contrast is the classic illegibility trap (a thin-display system must still use ≥ 400 for body).

---

## Output

When the accessibility lens runs, produce a short block:

```
### Accessibility
Contrast failures (AA):
- <component> — <fg hex> on <bg hex> = <ratio> ✗ (needs <min>)   [mode: <light/dark>]
Color-only signals: <list or none>
Missing/insufficient focus: <list or none>
Touch targets < 44px: <list, with whether the row/cell compensates>
Verdict: <PASS / BLOCK> — <one line>
```

A contrast or focus failure is a **BLOCK** (rubric G1): it caps the system's overall band until fixed.
