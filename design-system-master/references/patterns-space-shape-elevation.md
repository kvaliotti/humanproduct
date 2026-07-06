# Spacing, Shape & Elevation Patterns

Distilled from the 74-system corpus. The quieter foundations — but the ones that make a system feel
coordinated or chaotic. Grounded in real px values.

---

## Contents
1. Spacing — base unit & scale · 2. Shape — the border-radius scale · 3. Elevation & depth — pick ONE strategy and hold it

## 1. Spacing — base unit & scale

**4px vs 8px base is a near-even split, and it tracks density.**
- **8px base** — airy / marketing / brand: IBM, Apple, Shopify, Stripe, Coinbase, Nike, Figma, Supabase.
- **4px base** — compact UI / dense / developer: Binance, Linear, Vercel, MongoDB, Notion, Claude, Airbnb,
  Ferrari, Uber, Cursor.
- Most 8px systems still keep 2/4/12px sub-tokens "for fine work," so the practical gap between the camps
  is small. **Default to 8px with 2/4/12 sub-tokens** unless the product is dense/data-heavy (then 4px).
- **Outlier to flag:** Framer's 5px base (5/10/15/20/30) is genuinely non-standard — accidental idiosyncrasy.

**Naming & step count.** Two conventions: **t-shirt** (`xxs…xxl` + a top `section`/`huge`/`hero`) and
**numeric** (`space-1…space-12`). Typical **8 steps** (Stripe & Supabase: 2/4/8/12/16/24/32/64). Dense
systems extend to 10–13 by adding large top-end tokens (Vercel to `section:192px`, MongoDB/Notion to
`hero:120px`). Prefer t-shirt names — they're more guessable (a B1 ergonomics win in the rubric).

**Section padding is the density tell** (vertical gap between major bands):
- **Dense 48–80px** — Binance 80 (*"tighter because pages mix marketing with dense product surfaces"*),
  Airbnb 64 (*"marketplace pages need higher card density"*), Nike 48.
- **Standard 96px** — IBM, Linear, Raycast, Claude.
- **Airy 96–192px** — Mastercard, Revolut, Superhuman, Vercel (hero 192).
- Common move: **pricing/product pages tighten** vs marketing (Stripe 96→32px *"where users compare and
  act"*). A system should state both its marketing and its product density.

**Card internal padding** clusters at **24–32px** for feature/pricing cards, dropping to **16px** for dense
grid cards. Raycast warns the other way: *"don't pad cards 32px+ — the system runs tight at 16–24px."* The
rule is *consistency per card type*, not a universal number.

---

## 2. Shape — the border-radius scale

Radius is the most explicit **brand-signal** token — the corpus repeatedly ties corner shape to identity.
Three archetypes:

| Camp | Range | Reads as | Examples |
|---|---|---|---|
| **Flat / square** | 0–4px | enterprise gravitas, editorial, precision | IBM (`none:0`, *"even 4px breaks the Carbon look; pills read as a different brand"*), Wired (only `0` + `9999`), Ferrari (`0`), Tesla (4px), Warp (3–4px) |
| **Moderate rounded-rect** | 6–12px | sober / technical SaaS (the anti-pill camp) | Linear (8px, *"don't pill-round CTAs"*), Notion (8px, *"NOT pills"*), Mistral (8px, *"not playful"*), Supabase (6px), Superhuman (8px, pill only on hero) |
| **Pill** | 9999px | transactional / consumer / playful | Stripe (*"all buttons pills… don't replace with rounded-rects"*), MongoDB (*"the pill is a brand signature"*), Nike (30px pill, *"pill or icon-circle is the entire button vocabulary"*), Framer, Spotify, Revolut |

**Radius-per-component is near-universal:** inputs get the smallest real radius (4–8px), cards a middle
tier (8–16px), buttons either the smallest (anti-pill camp) *or* pill, avatars/icon-buttons a full circle.
Consistency here (all buttons one radius, all cards another) is exactly what rubric A4 scores.

**Nuances worth knowing:**
- **Two pill scales by surface (ESSENTIAL):** Vercel runs `pill:100px` for marketing CTAs + `sm:6px` for
  in-app buttons — *"don't pair the 100px pill with the 6px nav radius on the same screen; pick a scale and
  stay there."* Marketing and product are different surfaces.
- **Finite pills (90/100/999px) instead of 9999px (usually ACCIDENTAL):** Slack 90, Coinbase 100, Uber
  999 — a true `9999px` behaves identically and is simpler; collapse unless there's a reason.
- **Forbidden-middle / bimodal scales (deliberate):** Mastercard (*"3–6px OR 20–40px OR pill — the 8–16px
  middle is absent"*), Sanity (*"jumps 12px straight to pill"*). A gap can be intentional identity, not a hole.

**Radius as brand signal, one line:** pill button ⇒ transactional/consumer · rounded-rect 8px ⇒
sober/technical · 0px square ⇒ enterprise/editorial/precision.

**But don't over-map it — the corpus is genuinely mixed, and the exceptions are informative:**
- **"Consumer = pill" doesn't hold.** Airbnb, Nike, and Pinterest *reject* the full pill for CTAs (soft
  8–16px rectangles; Nike's 30px pill is paired with a hard rule that pill-or-icon-circle is the *entire*
  vocabulary; Pinterest is 16px, *"not full pill"*). Pills there are reserved for search bars and chips.
- **Fintech splits by register:** crypto *exchanges* reject the pill (Binance 6px; Kraken *"12px max, don't
  use pill buttons"*) to read as "engineered," while consumer *banking* apps embrace it (Wise, Revolut,
  Coinbase all full-pill) to read as "friendly." Same industry, opposite radius — driven by register, not
  domain. Read the brand's own stated intent, don't assume from the sector.

---

## 3. Elevation & depth — pick ONE strategy and hold it

A coordinated system uses a single depth medium; a mix reads as noise (rubric A5). Five strategies:

**(a) Flat color-block separation — no shadow.** Depth comes from the tone jump between canvas and surface,
plus hairlines. Binance (*"flat surfaces with color-block separation… the 12-step lightness jump between
`canvas-dark #0b0e11` and `surface-card-dark #1e2329` reads as a clear elevation boundary; no heavy shadows
or glass"*), IBM (thin-bordered tiles, no shadow), Nike (*"no drop-shadow elevation in the retail chrome at
all"*). Right for dense/enterprise/precision brands.

**(b) Elevation-by-tone (dark-mode ladder).** A stepped surface ramp carries hierarchy without shadow.
Linear (`canvas #010102` → `surface-1 #0f1011` → `surface-2 #141516` → `surface-3/4`, *"carries hierarchy
without shadow… the dark canvas IS the whitespace; sections lift onto surface-1 panels"*). The dark-native
counterpart of (a).

**(c) Subtle layered shadow.** Soft, low-alpha, tinted to the brand — for cards floating on light. Stripe
(Level 1 `rgba(0,55,112,0.08) 0 1px 3px`; Level 2 `0 8px 24px` + `0 2px 6px`; *"literal shadows are
reserved for product-UI mockups and stay subtle"*). Note the shadow is tinted with the brand's blue, not
neutral black — a coordination detail. Right for light-surface product/marketing UI.

**(d) Gradient / atmospheric depth as the primary medium.** The lift is color, not shadow. Stripe's gradient
mesh (*"the gradient mesh IS the depth system… atmospheric color rather than literal shadow"*), Vercel's
mesh, Mistral's sunset band. This is a *signature* commitment — hero-scale and brand-critical, or absent;
a timid decorative gradient reads as noise (see `patterns-color.md` §8).

**(e) Glass / blur.** Translucent surfaces with backdrop-blur over content — used sparingly for floating
chrome (nav, command palettes). **Genuinely rare in the corpus** — despite glassmorphism being common in
contemporary UI, Tesla's frosted nav (`rgba(255,255,255,0.75)` + `backdrop-filter` on scroll) is the only
unambiguous instance across 48 systems. Easy to overuse; if you reach for it, verify text contrast over the
blurred surface in every case, and don't let it become a second depth strategy alongside another.

**What actually drives the choice is canvas color + brand register, more than archetype.** Dark-canvas
dev-tool/AI brands go flat/tone-ladder because shadows physically don't read against near-black (Linear,
Raycast, Cursor, HashiCorp — a constraint, not a preference; Lamborghini states it best: *"on a black
canvas traditional drop shadows are invisible — elevated elements are literally lighter, inverting the
shadow model"*). Light-canvas broad-catalog marketing sites (Vercel, Webflow, Miro, Starbucks) engineer
real multi-stop shadows because they must lift many panels off white. Storytelling/infra brands (Stripe,
Mistral) reach for gradient-as-atmosphere. One brand can even make the shadow *colored*: Sentry's glow-halo
`rgb(21,15,35) 0 0 8px 6px` turns the dark canvas color itself into a vignette rather than a black drop.

**Focus ring is part of elevation and must be specified once and reused.** Binance
`0 0 0 2px {info-ring}` at 50% alpha. A system with per-component ad-hoc focus states fails both A5 and the
accessibility gate. Define one focus-ring token; every interactive element uses it.

**Choosing:** dense/enterprise/precision → (a) or (b). Light product/marketing → (c). Strong atmospheric
brand → (d) as the signature, with (c) for literal cards. Never run three of these at once — that's the
most common elevation incoherence.
