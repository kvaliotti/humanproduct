# Typography Patterns

Distilled from the 74-system corpus. Judge a type system (review), know the target (optimize), or choose
a strategy (create). Grounded in real families, sizes, weights, and tracking.

> Calibrate with `archetypes.md`. Thin-300 display is right for calm/editorial brands and *wrong* for a
> trading platform; the correct answer is a function of domain.

---

## Contents
1. Font-family strategy · 2. Weight strategy · 3. The type scale · 4. Line-height & letter-spacing · 5. Numeric / tabular treatment (the data-serious signal) · 6. Font-substitute discipline · 7. Typography Do / Don't

## 1. Font-family strategy — how many families is right?

Complexity ladder, in ascending order of justification. **No product in the corpus truly uses more than 3
families.**

**One family (the default — correct for most).** Hierarchy from size + weight, never a family switch.
IBM (Plex Sans only, *"there is no display+body pairing"*), Notion (Notion Sans, zero mono role), Stripe
(Söhne across all 15 roles), Superhuman, Airbnb, Mastercard, PlayStation, Ferrari.

**Two families = sans + mono — ESSENTIAL when there is code.** The single most common second face: a
monospace for code blocks, terminal mockups, technical labels. Every developer-facing brand has it —
Supabase (Circular + `ui-monospace`), Linear (+ Linear Mono in product/IDs), Vercel (Geist + Geist Mono,
*"body paragraphs never in mono"*), MongoDB (+ Source Code Pro), Figma (mono for uppercase eyebrows only).

**Two families = display + text optical/voice split.** A serif or display-cut face for hero, a workhorse
sans for the rest. ESSENTIAL for an editorial voice (the contrast *is* the brand): Mistral (PP Editorial
Old + Inter, *"the contrast IS the brand voice"*), Claude (Tiempos/Copernicus serif + sans), ElevenLabs
(Waldenburg + Inter), Nike (Futura ND @96px campaign + Helvetica Now for UI). A same-family optical split
(Apple SF Pro Display ≥19px vs Text <20px; Tesla; Linear Display vs Text) is a quieter version.

**The genuinely complex case — financial numerics (ESSENTIAL, rare).** A dedicated family for numbers:
Binance BinanceNova (text) + **BinancePlex** (all prices/volumes/percentages) — *"mixing them is a system
violation"*; Coinbase adds **CoinbaseMono** for *"every numerical value."* A trader reads a table faster
when every digit is tabular and consistent — this is information design, not vanity.

**Rule of thumb:** a second family is essential only for **code** (mono) or **money** (numeric cut), and a
serif display is essential for **editorial voice** and vanity elsewhere. A *fourth* family is almost always
accidental (Warp loads four; only Inter + DM Mono are load-bearing) — flag it.

---

## 2. Weight strategy — the display-weight signature

Two philosophies, mapped to archetype. This is the sharpest essential-complexity contrast in the corpus.

**Thin-display (calm / editorial / marketing):** display renders *lighter* than body-emphasis; the air is
the brand. Stripe display always **300** (*"at 400 the editorial air collapses"*), IBM 42–76px at **300**
(*"700 would look like every other enterprise site"*), ElevenLabs **300**, Claude serif **400** never bold,
Coinbase **400** (*"a deliberate anti-'fintech-urgency' signal"*).

**Bold-display (trading / consumer / sport):** heavier because it must compete with dense data or loud
imagery. Binance hero **700** (*"numbers must read at a glance, headlines must compete with charts… 400
reads as design-portfolio, not trading platform"*), Uber **700**, Slack **700**, Nintendo **900**.

**Body is near-universally 400**, with **500–600** for emphasis/labels/buttons. The whole system usually
lives in a **2–3 weight window** (Vercel *"400/500/600 are the working set; 600 is the display ceiling"*).
Mid-weight-500 "engineered" display is a third camp (Linear, Supabase, Ferrari, Nike).

**Variable sub-default weights — cheap warmth without adding a family (ESSENTIAL nuance):** Superhuman picks
**460/540/600** instead of 400/500/700 (*"warmer, more human"*); Figma flexes **320/330/340/480/540**
(*"one voice that flexes; weight, not size, carries hierarchy"*); Mastercard body **450**. When a system
wants more warmth, reach for in-between weights before reaching for another typeface.

---

## 3. The type scale

- **Role count:** 12–18 named roles is the norm; ~14 is a good default (4–5 display/heading, 3–4 body,
  2–3 caption/micro, 1–2 button). Lean: Tesla 8, PostHog 11. Rich: Stripe 15, Coinbase 16.
- **Where display tops out is the clearest archetype signal.** Restrained SaaS caps small and lets imagery
  carry the page: PostHog 36, Vercel 48, Stripe 56. Editorial/consumer go big: Linear/Notion 80, Mistral
  84, Figma 86, Nike/Shopify 96, The Verge 107, Framer 110, Revolut 136 (corpus max).
- **Smallest legible sizes:** floor 10–12px for micro/legal; body never below 13–16px (14px only in dense
  systems like Binance/Ferrari).
- **Step logic is perceptual, not strictly modular:** larger jumps at the top (~1.4×), tight steps at body
  (body variants often 1px apart, clustering at 14/15/16/18px). Nike deliberately omits the middle
  (96→32→16) for a "billboard above, catalog below" effect.

---

## 4. Line-height & letter-spacing

**Negative tracking on display — the most consistent signature in the corpus, and it scales with size.**
Stripe −1.4px@56px → −0.2px@20px; Linear −3.0px@80px; Framer −5.5px@110px (*"don't reduce it 'for
accessibility' — reduce the SIZE, keep the ratio"*). Rule: **tracking is negative and proportional above
~24px, ~0 at body.**

**Positive tracking is reserved for two things:** (1) small all-caps eyebrows/labels open up 1–2px (The
Verge, Ferrari, Spotify, Claude); (2) a deliberate "precision/mechanical" body dialect — IBM **+0.16px**
body / +0.32px caption (*"a Carbon precision detail"*), Revolut +0.24px (*"fintech precision"*). IBM is the
only system with positive body tracking as a rule.

**Line-height ladder:** buttons **≈1.0** (a single-line label needs no leading); display **0.85–1.15**,
tightening as size grows; body **1.4–1.55** (docs-heavy systems like MongoDB/Notion/Mistral push 1.55 for
readability). Note: some specs give line-height in px (Vercel, Warp), most as unitless ratios.

---

## 5. Numeric / tabular treatment — the "data-serious" signal

The sharpest essential-vs-accidental divider, with a surprising corpus truth: **OpenType `tnum` is almost
never used directly** — money-legibility is solved two ways.

- **Path 1 — `tnum` (rare).** Stripe is essentially the only first-class user: `body-tabular` + `caption`
  carry `font-feature-settings:"tnum"` (*"any money cell uses tnum… don't render money without it"*).
- **Path 2 — a dedicated numeric role / family (the more common serious solution).** Binance forces all
  numbers into BinancePlex; Coinbase renders prices in CoinbaseMono; Ferrari has a `number-display` role
  for spec cells and race positions.

**The signal isn't `tnum` specifically — it's whether a dedicated number treatment exists at all.** Its
presence marks Stripe/Binance/Coinbase/Ferrari as data-serious. **Do not over-generalize "fintech ⇒ tnum":**
Revolut (a bank) specifies no numeric feature; serious-numbers brands often use a *family swap* instead.
When you create a data-heavy system, add a number treatment and make it non-negotiable.

**Stylistic sets (`ss0x`, `cvXX`) are a brand-identity signal, not a numeric one.** Raycast `ss03`
universally (*"lose the flag and the chrome loses its voice"*), Stripe `ss01` globally, Framer a rich
`cv01/cv05/ss03/ss07/dlig` set. These are cosmetic character alternates — legitimate identity, but don't
confuse them with tabular-figure handling.

---

## 6. Font-substitute discipline

Well-authored specs treat a proprietary face as swappable and name an **exact open-source analogue with the
settings to match it** — not just "use Inter." The discipline has three parts:

1. **Pin the substitute to a weight + tracking**, e.g. Söhne → *Inter wt 300, letter-spacing −1.4px, ss01*;
   BinanceNova → *Inter (−3% line-height to match cap height)*; Circular → *Inter wt 500, −1.92px@64px*.
2. **Give mono and serif their own substitutes** — JetBrains/Geist Mono for code; EB Garamond / Cormorant
   Garamond for serif display.
3. **Warn against the lazy fallback** — Stripe/Supabase *"avoid Helvetica/system-ui — heavier than the
   brand needs"*; Superhuman *"avoid fixed 400/500/600 Inter — the brand picks in-between weights."*

IBM Plex Sans is itself open-source (SIL OFL) — a strong default when there is no brand font yet, alongside
Inter and Geist.

---

## 7. Typography Do / Don't

**Do**
- Match display weight to archetype: **300** calm/editorial, **500** engineered, **700** only when it must
  fight data or imagery.
- Apply **negative tracking on display scaled to size** (−1 to −5px), ~0 at body.
- Reserve positive tracking for small all-caps labels (1–2px) and an optional precision body nudge (+0.16px).
- Keep a 2–3 weight window; use variable sub-default weights for warmth before adding a family.
- Line-height: ~1.0 buttons, 0.85–1.15 display, 1.4–1.55 body.
- Add a dedicated number treatment only if money/data is central — then make it mandatory.
- Name an exact open-source substitute *with weight + tracking*; give mono/serif their own.

**Don't**
- Bump display above its signature weight — *"the air collapses"* (universal warning).
- Reduce display negative tracking "for accessibility" — shrink the size, keep the ratio.
- Set body paragraphs in the mono or display face — mono is code + labels only.
- Add a face for vanity — if code and money aren't in play, one family + weight suffices.
- Rely on `font-weight:300` for small body text — thin + small + low-contrast is the illegibility trap;
  a thin-display system still uses ≥400 for body (see `accessibility.md`).
