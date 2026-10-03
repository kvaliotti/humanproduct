# Color Patterns

What real systems did, with their own words where they state a rule. Read with `archetypes.md`: the right
color architecture depends on the archetype.

## 1. Architectures

| Architecture | Shape | Examples |
|---|---|---|
| **Single-accent** (the default) | one saturated hue rationed hard on an achromatic system | Binance `#fcd535`, IBM `#0f62fe`, Linear `#5e6ad2`, Supabase `#3ecf8e` |
| **Restrained neutral + one accent** | rich neutral ramp, accent only as the CTA layer | Vercel, Notion |
| **Multi-hue** | many colors as brand voltage *or* per-category coding | Airtable (8 card colors), Notion (9 tints), HashiCorp (7 product hues) |
| **Dual-canvas** | two tracks that never blend on one page | Binance (dark trading / light transactional), Shopify, Ferrari |
| **Gradient-mesh brand** | multi-stop atmosphere, hero-scale only | Stripe, Vercel, Mistral |

Don't conflate the two kinds of multi-hue. *Decorative* (Airtable, Notion): removing a color changes
personality, not legibility. *Functional* (HashiCorp, MongoDB): the color classifies something, and
removing it breaks a task.

## 2. Neutrals and surfaces

- **Ink tiers: 2–7.** Kraken uses two; MongoDB, Notion, Revolut run 6–7. Match depth to how much
  secondary text the product actually has.
- **Near-black, not `#000`, is the dominant convention** (Supabase `#171717` "never pure black"; Claude
  `#141413` on cream `#faf9f5`). Pure black is a deliberate minority (Revolut: "the brand is #000000, not
  #0a0a0a"; BMW-M, Uber). There is no correct canvas value, but a system must pick one and hold it. A
  drifting canvas value is a real flag.
- **Surface ladders: 2–4 steps.** Linear's `#010102 → #0f1011 → #141516 → …` "carries hierarchy without
  shadow."
- **Hairlines sit one elevation step from their surface.** Binance's `hairline-on-dark #2b3139` is the same
  hex as its elevated surface: "borders feel like surface steps."

## 3. Semantic color

- Full success/warning/error/info ramps appear where users judge validity or severity fast: IBM, Wise
  (each state with pressed + content variants because money movement demands unambiguous states).
- HashiCorp double-duties product hues as semantics (`success` = Nomad green) to keep the count down.
- **Omission is legitimate on marketing surfaces.** Stripe: "error/success live in the dashboard product."
- **An app with forms but no error tokens is under-built**, not minimal.

## 4. Domain color-coding — never "simplify" this away

Here color is information, not decoration. The rule across the corpus: domain color is a **signal**
(text, small badge), never a **fill**.

- **Trading up/down.** Binance `trading-up #0ecb81` / `trading-down #f6465d`: "text color in tables,
  charts, ticker arrows. Never a button background." Coinbase: "color only, no background fill."
  A trader scanning 40 assets resolves direction in peripheral vision. Removing it breaks the core task.
- **Wall domain color off from semantics.** "Never repurpose price green/red for success/error."
  "Market up" and "form valid" are different meanings. Pair up/down with an arrow or sign
  (`accessibility.md` §2).
- **Per-product suites.** HashiCorp's 7 hues tell an engineer which product's docs they are in. Rule:
  "never combine multiple product accents in one viewport."
- **Scoped functional palettes.** Cursor's 5 AI-timeline state colors: "only in product UI, never as
  system action colors," fenced off from the brand CTA.
- **Check scope before calling it missing.** Kraken and Revolut show no up/down tokens because only their
  marketing surface was captured.

## 5. Modes

- **Light-only** where dark adds nothing (Airbnb: "no dark mode on the public web").
- **Dark-only** where identity is nocturnal or precise (Linear: "don't ship a light marketing page").
- **Toggle** — a token remap, never `invert()`.
- **Polarity-flip by section** — the most common pattern. Dark and light bands coexist on one page,
  chosen by section intent (Binance: "choose canvas mode by surface intent"; Claude: "don't repeat the same
  surface mode in two consecutive bands").

**The mark of a good multi-theme system:** accent and domain colors don't change when the canvas flips.
Binance's yellow and green/red are identical on dark and light; only surface and ink change.

**Inverse tokens** formalize this. IBM `inverse-canvas #161616` / `inverse-ink #ffffff`, scoped narrowly
("invert only at the footer"). IBM's ink `#161616` *is* its inverse-canvas: one token, two jobs.

## 6. Accent rationing — the most consistent rule in the corpus

Stripe: "one filled button per band." Revolut, Nike: "if more than one accent element appears per
viewport, drop one to a neutral surface." Sentry: "the signature only works because it's rare." When a
second instance is needed, demote it to a neutral surface; don't repeat the hue.

## 7. On-color is a brand decision

The text color on a filled accent is chosen, not defaulted to white: Binance `#181a20` on `#fcd535`
("white on yellow loses contrast and recognition"), MongoDB `#001e2b` on `#00ed64`, Wise dark ink on lime.
Always define explicit `on-*` tokens and check their contrast.

## 8. Flags for a review

1. A second brand accent (the most repeated Don't in the corpus). Systems with many legitimate hues scope
   each to one role.
2. A signal color used as a fill (trading green card, timeline pastel as a button).
3. The accent used as body text or a large fill.
4. A half-committed gradient. A signature gradient is hero-scale or absent.
5. Trusting a token's *name* over its use (Airtable's `--…button-background-primary` is its link color;
   the real primary is near-black).
