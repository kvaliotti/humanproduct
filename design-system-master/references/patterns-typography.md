# Typography Patterns

What real systems did. Read with `archetypes.md`: thin-300 display is right for a calm editorial brand and
wrong for a trading platform.

## 1. How many families

No system in the corpus truly uses more than 3.

- **One family — the default.** Hierarchy from size and weight. IBM ("there is no display+body pairing"),
  Notion, Stripe (Söhne across all 15 roles), Airbnb.
- **Sans + mono — essential when there is code.** Vercel (Geist + Geist Mono, "body paragraphs never in
  mono"), Linear, Supabase, MongoDB.
- **Display + text voice split — essential when a serif carries the brand.** Mistral ("the contrast IS the
  brand voice"), Claude, ElevenLabs, Nike (Futura @96px + Helvetica Now).
- **A dedicated numeric family — essential for money, and rare.** Binance sets all prices in BinancePlex
  ("mixing them is a system violation"); Coinbase uses CoinbaseMono for "every numerical value."
- **A fourth family is almost always accidental.** Warp loads four; only two carry load.

## 2. Display weight is the signature

- **Thin display (calm, editorial):** Stripe 300 ("at 400 the editorial air collapses"), IBM 300 ("700
  would look like every other enterprise site"), Coinbase 400 ("a deliberate anti-fintech-urgency signal").
- **Bold display (must compete with data or imagery):** Binance 700 ("numbers must read at a glance,
  headlines must compete with charts"), Uber, Slack 700; Nintendo 900.
- **Engineered mid-weight 500:** Linear, Supabase, Ferrari.
- Most systems live in a 2–3 weight window (Vercel: "400/500/600 are the working set").
- **In-between variable weights add warmth without a new family:** Superhuman 460/540/600 ("warmer, more
  human"); Figma 320–540 ("weight, not size, carries hierarchy"); Mastercard body 450.

## 3. Scale

- 12–18 named roles is the corpus norm. Lean: Tesla 8. Rich: Coinbase 16.
- **Where display tops out signals the archetype.** Restrained SaaS caps small: PostHog 36, Vercel 48,
  Stripe 56. Editorial and consumer go big: Linear 80, Nike 96, Framer 110, Revolut 136.
- Steps are perceptual, not modular: big jumps at the top, 1px steps around body (14/15/16/18). Nike skips
  the middle on purpose (96 → 32 → 16).

## 4. Tracking

- **Negative tracking on display, scaled to size,** is the most consistent signature: Stripe −1.4px@56,
  Linear −3px@80, Framer −5.5px@110 ("don't reduce it for accessibility — reduce the SIZE, keep the
  ratio"). About 0 at body.
- **Positive tracking** only for small all-caps labels (+1–2px) and a deliberate precision dialect
  (IBM +0.16px body, "a Carbon precision detail"; Revolut +0.24px).

## 5. Numbers

`tnum` is rarely used directly. Money legibility is solved two ways:
- `tnum` on dedicated roles. Stripe is the main user ("any money cell uses tnum").
- A numeric family or role. Binance, Coinbase, Ferrari (`number-display`).

The signal is whether *any* dedicated number treatment exists. Don't assume "fintech ⇒ tnum": Revolut
specifies none, and many use a family swap. For a data-heavy product, add one and make it mandatory.

Stylistic sets (`ss01`, `cv05`) are identity, not numerics: Raycast `ss03` ("lose the flag and the chrome
loses its voice").

## 6. Font substitutes

Good specs name an exact open-source substitute **pinned to weight and tracking**: Söhne → Inter 300,
−1.4px, ss01; Circular → Inter 500, −1.92px@64. Give mono and serif their own substitutes. Warn against
lazy fallbacks (Stripe, Supabase: "avoid Helvetica/system-ui — heavier than the brand needs"). With no
brand font yet, Inter, Geist, and IBM Plex Sans (SIL OFL) are safe defaults.

## Don'ts

- Raise display above its signature weight.
- Set body paragraphs in mono or the display face.
- Add a family when neither code, money, nor editorial voice is in play.
- Use weight 300 for small body text (see `accessibility.md` §5).
