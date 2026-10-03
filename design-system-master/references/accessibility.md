# Accessibility Checks

The review's hard gate. These checks are deterministic: do the math, report the numbers.

## 1. Contrast

WCAG 2.x contrast ratio:

```
linearize each channel c (0–1): c ≤ 0.03928 ? c/12.92 : ((c+0.055)/1.055)^2.4
L = 0.2126·R + 0.7152·G + 0.0722·B
ratio = (L_lighter + 0.05) / (L_darker + 0.05)
```

| Content | AA | AAA |
|---|---|---|
| Body text (< 18pt, or < 14pt bold) | **4.5:1** | 7:1 |
| Large text (≥ 18pt, or ≥ 14pt bold) | **3:1** | 4.5:1 |
| UI boundaries, focus indicators, meaningful graphics | **3:1** | — |
| Disabled elements | exempt, but keep ~3:1 so they stay perceivable | |

For every component with `textColor` + `backgroundColor`, resolve both tokens to hex and compute the
ratio, **in every mode** (a pair that passes on light can fail on dark). Usual offenders: muted text on
tinted surfaces, white `on-primary` on a mid-tone accent, placeholder text. Over ~10 components, write a
small script to sweep all pairs.

Report as: `button-secondary — ink-muted #525252 on surface-1 #f4f4f4 = 4.1:1 ✗ (needs 4.5:1) [light]`.

Any body-text pair below AA, or an interactive element with no visible focus state, **blocks**: it goes
first in the fix list regardless of anything else.

## 2. Color is never the only signal

- Up/down (trading green/red, diffs) must also carry an arrow, a `+`/`−`, or a word.
- Status needs icon + text, not just a colored dot.
- Required fields, errors, and selection need a non-color cue (asterisk, border, checkmark).

Flag any component whose state differs only by color.

## 3. Focus and targets

- Every interactive component has a visible focus state, ideally one reused focus-ring token at ≥ 3:1
  against its background. Never `outline: none` without a replacement.
- Targets ≥ 44×44px (WCAG 2.5.5). Dense trading rows and table row actions may go smaller: allow it, flag
  it, and require the whole row or cell to be the target.

## 4. Motion and modes

- Motion tokens need a `prefers-reduced-motion` story, even if it is "disable non-essential motion".
- Dark mode is a token remap, never a CSS `invert()` filter.

## 5. Thin small text

Thin + small + low contrast is the classic illegibility trap. A thin-300 display system must still use
≥ 400 for body text.

## Honesty note

The corpus this plugin was distilled from is machine-reconstructed from live marketing sites and cites
**no** numeric contrast ratios. Never call a system "accessibility-audited" because it resembles a
reference system. Always run the math.
