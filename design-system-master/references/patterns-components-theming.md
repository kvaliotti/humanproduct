# Component, State & Theming Patterns

What real systems did with components, states, variants, and modes. Color-side theming is in
`patterns-color.md` §5.

## 1. Domain components

Every system documents a common core (buttons, inputs, cards, nav, tags, links). Strong systems also ship
the components their product actually renders:

- **Finance/trading:** markets table, `price-up-cell` / `price-down-cell`, amount input (Binance, Coinbase).
- **SaaS/marketing:** pricing tiers with an inverted featured tier, stat callouts, product-UI mockups.
- **Dev tools:** code block, terminal mockup.
- **Any app:** empty / loading / error states. Often missing; a common under-built gap.

Missing domain components is a gap. Components the product never renders is bloat.

## 2. Buttons

- One filled primary per band or viewport (accent rationing).
- On-dark / on-light variants are separate entries in multi-theme systems
  (Binance `button-secondary-on-dark` / `-on-light`).
- Domain action buttons stay out of generic flows. Binance's green/red trading buttons are only for
  Buy/Sell: "never for generic confirm/cancel."

## 3. States — document what matters

The corpus is minimal about states. Binance: "Never document hover. The system documents Default and
Active/Pressed states only." Raycast states the same as policy.

Document: **default**, **active/pressed** (an `-active` token), **disabled** (keep ~3:1), **focus** (one
reused focus-ring token on every interactive element), **error** (where there are forms).

- **Declared policy vs silent gap.** "No hover, by policy" is discipline. A component missing focus or
  error with no stated reason is a hole.
- **Focus styles vary, but must exist.** Linear: 2px accent at 50%. Sentry: "the only blue in the system."
  Framer: "selected = lift, not color." Raycast and HP avoid a colored ring, which is fine if the state is
  visible at ≥3:1. **A system with no focus token at all (Superhuman, Warp, Wired) has a real gap.**
- **Inverted priorities are a flag:** 8 hover shades and no focus or error state.

## 4. Variants as separate entries

Binance: "variants of a component live as separate entries in `components:` — never as nested state
objects." Color variants too: Notion ships seven `card-feature-{peach,rose,…}` entries; Webflow's five
`category-card-*` each carry their own text color (green uses ink for legibility, the rest white). Verbose
but honest: each real combination is explicit and contrast-checkable. It is bloat only when variants are
unused or differ by nothing.

## 5. Density and touch targets

State the density and hold it. Dense products separate content with contrast and hairlines; comfortable
ones with whitespace. Sub-44px targets are legitimate in dense UIs (Binance 28px buttons "match industry
trading-platform norms") only when the whole row is the target. Flag them.

## 6. Multi-surface structure

- **Inverse tokens + one component set** (IBM). A mode swap remaps tokens; one definition serves both.
  Cleanest.
- **Parallel component pairs** (`top-nav-on-dark` / `-on-light`). Common in extracted rather than designed
  systems. Works, but costs more to maintain.
- **Polarity-flip pages** (Binance, Claude, Ferrari): components must exist for each surface they land on,
  and the spec should state the band rhythm.

Flag accent drift between modes and components that exist in only one mode with no reason.
