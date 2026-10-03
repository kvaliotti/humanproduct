# Spacing, Shape & Elevation Patterns

What real systems did, in px.

## 1. Spacing

- **Base unit tracks density.** 8px for airy marketing/brand (IBM, Stripe, Apple, Nike, Supabase); 4px for
  dense UI and dev tools (Binance, Linear, Vercel, Notion, Cursor). Most 8px systems keep 2/4/12px
  sub-tokens, so the gap is small. Default to 8 with 2/4/12 sub-tokens; use 4 when the product is dense.
- **Flag non-standard bases.** Framer's 5px (5/10/15/20/30) is idiosyncrasy, not design.
- **Prefer t-shirt names** (`xxs…xxl` + `section`) over numeric ones; they are easier to guess. About 8
  steps is typical (Stripe, Supabase: 2/4/8/12/16/24/32/64).
- **Section padding is the density tell.** Dense 48–80px (Binance 80: "pages mix marketing with dense
  product surfaces"). Standard 96 (IBM, Linear). Airy up to 192 (Vercel hero).
- **Product pages tighten vs marketing** (Stripe 96 → 32px "where users compare and act"). A spec should
  state both densities.
- **Card padding:** consistency per card type matters more than the number. Raycast: "don't pad cards
  32px+ — the system runs tight at 16–24px."

## 2. Shape

Radius is the most explicit brand signal in the corpus.

| Camp | Range | Reads as | Examples |
|---|---|---|---|
| Square | 0–4px | enterprise, editorial, precision | IBM 0 ("even 4px breaks the Carbon look"), Wired, Ferrari |
| Rounded-rect | 6–12px | sober, technical (the anti-pill camp) | Linear 8 ("don't pill-round CTAs"), Notion 8, Supabase 6 |
| Pill | 9999px | transactional, friendly | Stripe ("all buttons pills"), MongoDB ("the pill is a brand signature"), Revolut |

- **One radius per component type** (inputs smallest, cards middle, buttons either smallest or pill).
- **Two scales by surface can be essential.** Vercel: `pill:100px` for marketing CTAs, `sm:6px` in-app,
  "don't pair the 100px pill with the 6px nav radius on the same screen."
- **Finite pills are usually accidental.** Slack 90, Coinbase 100, Uber 999: a true `9999px` does the same.
- **A gap in the scale can be intentional.** Mastercard: "3–6px OR 20–40px OR pill — the 8–16px middle is
  absent."
- **Don't map radius from the sector.** Airbnb, Nike, Pinterest reject full pills for CTAs. Crypto
  exchanges reject pills (Binance 6px; Kraken "12px max") to read engineered, while consumer banks embrace
  them (Wise, Revolut) to read friendly. Read the brand's stated intent.

## 3. Elevation — pick one strategy

1. **Flat color-block** — depth from the tone jump plus hairlines. Binance ("no heavy shadows or glass"),
   IBM, Nike. Dense, enterprise, precision brands.
2. **Tone ladder** — the dark-mode version. Linear ("the dark canvas IS the whitespace").
3. **Subtle layered shadow** — light surfaces. Stripe tints its shadow with brand blue
   (`rgba(0,55,112,0.08) 0 1px 3px`), not neutral black.
4. **Gradient as depth** — Stripe ("the gradient mesh IS the depth system"), Mistral. Hero-scale and
   brand-critical, or absent.
5. **Glass/blur** — rare in the corpus (Tesla's nav is the only clear case). Easy to overuse; check text
   contrast over the blur.

What drives the choice is **canvas color and brand register** more than archetype. On near-black,
shadows don't read (Lamborghini: "on a black canvas traditional drop shadows are invisible — elevated
elements are literally lighter"), so dark brands go flat or tone ladder. Light catalog sites need real
shadows to lift many panels.

Never run two or three strategies at once. That is the most common elevation incoherence.

**Focus ring belongs here.** Define one token (Binance `0 0 0 2px {info-ring}` at 50% alpha) and reuse it
on every interactive element. Per-component ad-hoc focus fails both coherence and accessibility.
