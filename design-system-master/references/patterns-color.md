# Color System Patterns

Distilled from the 74-system corpus. Use this to judge a color system (review), to know what "good"
looks like per dimension (optimize), and to choose an architecture (create). Every pattern below is
grounded in real systems with real hex values.

> **Read this with `archetypes.md`.** The right color architecture is a function of the archetype. A
> minimal dev-tool with one accent and a dense trading terminal with dual-coded green/red are *both*
> correct — for their domains.

---

## Contents
1. The five color architectures · 2. Neutral & surface ramps · 3. Semantic color · 4. Domain / dual color-coding (the essential-complexity case) · 5. Theming & modes · 6. Accent rationing · 7. On-color text · 8. Anti-patterns to flag · Methodology note

## 1. The five color architectures

| Architecture | Shape | Examples |
|---|---|---|
| **Single-accent** (modal) | 1 saturated hue rationed hard, on an achromatic system | Binance yellow `#fcd535`, IBM blue `#0f62fe`, Linear lavender `#5e6ad2`, Pinterest `#e60023`, Supabase emerald `#3ecf8e` |
| **Restrained-neutral + one accent** | rich neutral ramp, accent scarce as the CTA layer | Vercel (`ink #171717` + reserved gradients), Notion (purple CTA over a pastel decorative layer) |
| **Multi-hue expressive** | many colors as brand voltage or per-category coding | Airtable (8 signature card colors), Notion (9 pastel tints), HashiCorp (7 per-product hues) |
| **Dual-brand / dual-canvas** | two parallel tracks that never blend on one page | Shopify (black marketing / cream transactional), Binance (dark trading / light transactional), Ferrari, Sentry |
| **Gradient-mesh brand** | color as a multi-stop atmospheric device, hero-scale only | Stripe (indigo mesh), Vercel (3 named gradient pairs), Mistral (sunset ramp), PlayStation (PS Plus gold) |

**The default is single-accent.** Reach for more only when the domain earns it (see §4). Two distinct
flavors of "multi-hue" must not be conflated: *decorative voltage* (Airtable/Notion — mnemonic, removing a
color changes personality not legibility) vs. *functional coding* (HashiCorp/MongoDB — the color classifies
something; removing it degrades a real task).

---

## 2. Neutral & surface ramps

**Ink (text) tiers: 2–7 steps.** Shallow (Kraken: near-black `#101114` + silver-blue `#9497a9`, done).
Deep (MongoDB, Notion, Mistral, Revolut each run 6–7 tiers down to a muted floor). More tiers = "room to go
quiet without going invisible." Match depth to how much secondary/tertiary text the product actually has.

**Near-black, not pure black — the dominant convention for ink**, and brands argue it explicitly: Binance
body `#eaecef` ("slightly cooler, never pure white"), Claude ink `#141413` ("warm, off-pure-black") on
cream `#faf9f5`, Supabase `#171717` ("near-black, never pure black"), Tesla `#171A20` (warm near-black,
blue undertone). **Pure `#000000` is a deliberate minority** signaling authority/void — Revolut (*"the brand
is #000000, not #0a0a0a"*), BMW-M, Lamborghini, Uber, HashiCorp. Linear goes to `#010102` and still bans
true black. **Lesson:** there is no universally correct dark canvas — but each system must *pick one and
defend it everywhere.* A drifting canvas value is a real flag.

**Surface elevation ladders: 2–4 steps, rarely more.** Linear documents a clean 4-step ladder
(`canvas #010102` → `surface-1 #0f1011` → `surface-2 #141516` → `surface-3/4`) that "carries hierarchy
without shadow." Many systems (Supabase, Sentry, Nike) collapse to a 2-pole white/near-black system —
flatness as restraint. Elevation-by-tone is a legitimate alternative to shadow (see `patterns-space-shape-elevation.md`).

**Hairlines usually sit one elevation step from their surface, not as ink lines.** Binance's
`hairline-on-dark #2b3139` *is the same hex* as `surface-elevated-dark` — "borders feel like surface steps."
Some minimal systems (Wise, Kraken) omit a dedicated hairline token and reuse `ink` at 1px.

---

## 3. Semantic color (success / warning / error / info)

**Full 4-part palettes appear in enterprise and fintech systems** where users make fast binary/ranked
judgments: IBM (`success #24a148` / `warning #f1c21b` / `error #da1e28` / `info #0f62fe`), Wise (the richest
— positive/warning/negative each with pressed + content variants, because money movement demands
unambiguous states). HashiCorp cleverly double-duties its per-product hues as semantics to keep the count
down (`success` = Nomad green, `error` = Consul red).

**Deliberate omission is legitimate on pure-brand/marketing surfaces.** Stripe states it best: *"the brand
does not use a separate semantic palette in the marketing system — error/success live in the dashboard
product."* The semantic need is real but scoped to a different surface. Supabase omits them so they don't
compete with its single green.

**Judgment (review/create):** a full semantic ramp is *warranted* wherever the UI asks the user to judge
validity/severity/direction quickly (forms, dashboards, fintech). It's *reasonably absent* on editorial/
marketing/luxury surfaces with no such judgment. If an app has forms but no error tokens, that's an
**under-built gap**, not admirable minimalism.

---

## 4. Domain / dual color-coding — the essential-complexity case

**This is the pattern the tool must never naively "simplify" away.** Here color is information
architecture, not decoration. The corpus draws a sharp, repeated line: domain color is a **signal**
(text/small badge), never a **surface** (fill).

**Trading up/down (fintech/crypto) — the canonical example.**
- Binance `trading-up #0ecb81` / `trading-down #f6465d` — *"text color in tables, charts, ticker arrows.
  Never a button background."*
- Coinbase `semantic-up #05b169` / `semantic-down #cf202f`, wired to `price-up-cell` / `price-down-cell`,
  *"color only, no background fill."*
- **Why essential:** a trader scanning 40 assets needs up/down to resolve in peripheral vision, faster than
  reading a sign. Removing it degrades the product's core task.
- **The discipline that keeps it clean:** these tokens are *walled off from generic success/error* —
  *"never repurpose price green/red for 'success'/'error'."* Conflating "market up" with "form valid" is a
  comprehension bug, not a nitpick. **And** because color-blind users can't see hue, up/down must *also*
  carry an arrow/sign (see `accessibility.md` §2).

**Per-product identity coding — essential when the "product" is a suite.** HashiCorp's 7 hues (Terraform
purple, Vault yellow, Consul red, Waypoint cyan, Vagrant blue, Nomad green, Boundary coral) are wayfinding:
the color tells an engineer which product's docs they're in. Rule: *"never combine multiple product accents
in one viewport."* The naive "just use one HashiCorp blue" would make seven products indistinguishable.

**Scoped functional palettes.** Cursor's 5 AI-timeline states (`timeline-thinking #dfa88f`, `-grep`,
`-read`, `-edit`, `-done`) solve "which of 5 states is this row?" by hue — *"only in product UI, never as
system action colors,"* fenced off from the brand CTA (`#f54e00`). MongoDB's course-category tags are
borderline (aid scanning, but text/icon could also do it).

**Contrast with decorative color-coding** (Airtable's 8 cards, Notion's 9 tints): nothing is *classified*
by these; they're mnemonic brand punctuation. Both are legitimate, but only the functional kind is
essential complexity — know which you're looking at before judging.

**Scope-gap caution:** absence of domain tokens isn't proof the domain doesn't need them — Kraken and
Revolut (both crypto) show no up/down tokens *because the captured surface was marketing-only.* Check scope
before concluding "missing."

---

## 5. Theming & modes

Four patterns, chosen by product need, not fashion:

- **Light-only** — consumer-luxury / B2C marketing where dark adds no function (Airbnb *"no dark mode on
  the public web,"* Mistral, Pinterest, Mastercard).
- **Dark-only** — brands whose identity is nocturnal/precision (Linear *"don't ship a light marketing
  page,"* The Verge, BMW-M, HashiCorp, Spotify).
- **Light + dark toggle** — the app-preference case; wire as a **token remap**, never a CSS `invert()`.
- **Compositional polarity-flip** (the corpus's dominant pattern) — dark and light bands *coexist on one
  page*, chosen by section intent, not a user toggle. Binance (dark trading / light transactional,
  *"choose canvas mode by surface intent"*), Claude (cream→cream→dark-navy→coral→dark footer,
  *"don't repeat the same surface mode in two consecutive bands"*), Ferrari, Sentry, MongoDB, Coinbase.

**The sophisticated part of multi-surface theming:** identity and domain semantics **don't reset** when the
canvas polarity flips. Binance's yellow CTA and its trading green/red look identical on dark and light —
only surface and ink tones flip. That is the mark of a well-structured multi-theme system.

**Inverse-token pairs** are the formal mechanism. IBM: `inverse-canvas #161616` / `inverse-surface-1
#262626` / `inverse-ink #ffffff` / `inverse-ink-muted #c6c6c6`, scoped narrowly (*"invert only at the
footer"*). Elegant reuse: IBM's charcoal ink `#161616` *is* its inverse-canvas — one token serves "near-
black text" and "dark surface." Systems that don't name `inverse-*` tokens instead ship parallel component
pairs (`nav-on-dark` / `nav-on-light`) — functionally equivalent, less systematized.

---

## 6. Accent rationing — the most consistent rule in the corpus

Stated near-verbatim by unrelated brands: *"reserve the primary for filled CTAs — one filled button per
band"* (Stripe); *"if more than one accent element appears per viewport, drop one to a neutral surface"*
(Revolut, Nike); *"the signature only works because it's rare"* (Sentry); *"one full-bleed blue band per
page"* (PlayStation). **Scarcity is what makes the accent read as "the one thing to click."** When a second
instance is needed, demote it to a secondary/neutral surface — don't duplicate the hue. This is the same
discipline as domain-coding (§4): never let a signal color become ambient decoration.

---

## 7. On-color text is a brand decision, not a black/white default

The "correct" text color on a filled accent is chosen, and getting it wrong breaks the signature:
Binance black-on-yellow (`#181a20` on `#fcd535`, *"white on yellow loses contrast and recognition"*),
Supabase near-black on emerald (*"reads as a lit surface with dark type, not a colored chip"*), MongoDB
deep-navy on green (`#001e2b` on `#00ed64`), Wise dark ink on lime. **Always define explicit `on-primary`
/ `on-dark` tokens and verify each for contrast** (`accessibility.md`) — don't let text-on-fill be accidental.

---

## 8. Color anti-patterns (Don'ts) to flag in a review

1. **A second brand accent** — the corpus's most repeated Don't. When a system legitimately carries many
   hues (gradient family, per-product suite), the rule becomes *"never use them outside their scoped role."*
2. **A domain/semantic signal used as a surface fill** — trading green as a card background, timeline
   pastels as system actions, sale-red on chrome. Signal = text/small badge only.
3. **The accent as body text or a large fill** — it's a CTA/link color, not a type color.
4. **A drifting canvas value** — pick pure-black *or* warm-near-black and hold it everywhere.
5. **Near-duplicate tokens** — two inks a couple % apart (`ink-mute` vs `ink-mute-2`) doing one job =
   accidental complexity; consolidate.
6. **Half-committed gradients** — a signature gradient is hero-scale and brand-critical *or* absent; a
   timid decorative gradient reads as noise.
7. **Trusting a CSS variable *name* over its role** — Airtable's `--...button-background-primary` is
   actually its link color; the real primary is near-black. Verify tokens against *component usage*, not names.

---

## Methodology note (for honest reviews)

The corpus specs are machine-reconstructed from live sites. **No spec cites a numeric contrast ratio**, and
a few lines are extraction boilerplate (a generic "44×44px WCAG" touch-target note; a "don't sample a
cookie-widget's CTA color" warning). Therefore: **do not claim a real system is "accessibility-audited"
just because it resembles the corpus.** Accessibility is *this tool's* contribution — always run the real
contrast math in `accessibility.md` rather than assuming the reference systems already did.
