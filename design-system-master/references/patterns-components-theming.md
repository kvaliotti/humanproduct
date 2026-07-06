# Component, State & Theming Patterns

Distilled from the 74-system corpus. How components are structured, which states get documented, how
variants and modes are modeled, and how density is chosen. Grounded in real specs.

---

## Contents
1. Component taxonomy · 2. Button hierarchy · 3. State model (document what matters) · 4. Variants & states as separate entries · 5. Density & touch targets · 6. Theming & mode structure · 7. Component-side Do / Don't

## 1. Component taxonomy

Every system documents a **common core**; strong systems add the **domain-specific** components their
product actually renders. Don't ship components the product won't use, and don't omit the domain ones it
needs (both are rubric findings — bloat and gap respectively).

**Common core (nearly universal):**
- **Buttons** — primary / secondary / tertiary(text/ghost), plus on-dark / on-light variants.
- **Inputs & forms** — text input (+ focused/error states), select, search.
- **Cards & containers** — feature card, pricing card, generic surface card.
- **Navigation** — top nav (on-dark / on-light), footer, tabs.
- **Tags / pills / chips** — status pills, category tags, eyebrows.
- **Links** — inline text links.

**Domain-specific (present when the product needs them):**
- **Finance/trading** — markets table, `price-up-cell` / `price-down-cell`, amount input, conversion cell,
  trader/subscribe rows (Binance, Coinbase). These carry the dual-code discipline (§color patterns §4).
- **SaaS/marketing** — pricing tiers (incl. an inverted "featured" tier), trust badges, stat callouts,
  composited product-UI mockups, CTA bands, FAQ accordions.
- **Any app** — empty / loading / error states (frequently missing — a common under-built gap).
- **Dev tools** — code block, terminal mockup, API/status tokens.

---

## 2. Button hierarchy conventions

- **Primary is rationed** — one filled primary per band/viewport (the accent-rationing rule from
  `patterns-color.md` §6). Everything else is secondary/tertiary.
- **Secondary** is outline or low-emphasis fill; **tertiary/text** has no background (inline "Log in",
  "Read more").
- **On-dark / on-light variants are separate entries** because the same button appears on both surfaces in
  multi-theme systems (Binance `button-secondary-on-dark` vs `-on-light`).
- **Shape signals intent** — pill (transactional/consumer), rounded-rect 8px (sober/technical), 0px square
  (enterprise/precision). Hold it per system (`patterns-space-shape-elevation.md` §2).
- **Domain action buttons carry semantics** — Binance's green `button-trading-up` / red `button-trading-down`
  are *only* for Buy/Sell; *"never for generic confirm/cancel."* Keep semantic buttons out of generic flows.

---

## 3. State model — document the states that matter, skip the ones that don't

The corpus is disciplined and, importantly, **minimal** about states. Binance's iteration guide states the
convention bluntly: *"Never document hover. The system documents Default and Active/Pressed states only."*

**Document:**
- **Default** — the base.
- **Active / pressed** — a distinct token (usually the accent's darker `-active` step).
- **Disabled** — a desaturated variant (Binance `primary-disabled #3a3a1f`); keep it ~3:1 so it's still
  perceivable (`accessibility.md`).
- **Focus** — a **single reused focus-ring token** (`0 0 0 2px {info-ring}`), on *every* interactive
  element. Never `outline:none` without a replacement. This is a hard accessibility requirement, not a nicety.
- **Error / validation** — for inputs, where the product has forms (often an under-built gap).

**Often deliberately skipped:** hover — 15+ systems *declare a policy* (Raycast: *"no hover states
documented per system policy; each spec covers Default and Active/Pressed only"*). A few systems document
rich hover+focus anyway (Lamborghini, Tesla, The Verge — the last has the corpus's richest state matrix
with a dedicated Focus Cyan `#1eaedb` *"never shown outside a keyboard-focus state"*); that's fine too.

**The distinction that matters for review — declared policy vs. silent gap.** "No hover, by policy" is a
deliberate discipline; a component simply missing hover/focus/error with *no stated reason* is a
documentation hole. Absence-with-a-rule is fine; absence-without-one is the flag. Same logic for a color
used once (bounded in prose = fine; unbounded = a smell).

**Focus-ring values vary but must exist and be reused:** Linear (2px accent at 50% opacity, its own
elevation Level 4), Sentry (`rgba(59,130,246,0.5)` — *"the only blue in the system"*), Framer (a 1px ring,
*"selected = lift, not color"*), or simple 2px-border thickening (Notion, Binance). Some systems
deliberately avoid a colored ring (Raycast "subtle brightening"; HP "1px border, no halo") — legitimate, as
long as the state is visible and ≥3:1. **A system with *no* focus token at all (Superhuman, Warp, Wired) is
a real accessibility gap**, not a stylistic choice.

**Why this matters for review:** a system that documents 8 hover shades but has no focus or error state is
inverted — ceremony where it doesn't matter, a gap where it does.

---

## 4. Variants & states are SEPARATE entries, not nested objects

The corpus convention (Binance: *"variants of a component live as separate entries in `components:` — never
as nested state objects"*):

```yaml
button-primary:            { ... }
button-primary-active:     { ... }   # pressed
button-primary-disabled:   { ... }
button-secondary-on-dark:  { ... }   # mode variant
button-trading-up:         { ... }   # domain variant
```

This keeps each spec flat and `{token}`-referencing, and makes the component list a complete enumeration of
what actually exists. Nested state objects hide variants and drift out of sync. A review should flag nested
state modeling as a B3 (component-API-consistency) problem.

**Color/tint variants get the same treatment — as separate keys, not one component + a color prop.** Notion
ships seven `card-feature-{peach,rose,mint,sky,lavender,cream,yellow}` entries; Webflow's five
`category-card-{purple,blue,orange,green,pink}` each carry their *own* text-color override (green uses ink
text for legibility, the rest white — genuine per-variant divergence, not copy-paste). This is verbose but
honest: it makes each real combination explicit and lets per-variant contrast be verified. It's only bloat
when the variants are never used or differ by nothing meaningful.

---

## 5. Density & touch targets

- **Density is chosen by domain.** Dense (trading tables, dashboards, dev tools) trusts contrast and
  hairlines to separate content; comfortable (marketing, consumer) uses whitespace
  (`patterns-space-shape-elevation.md` §3). A system should state its density and hold it.
- **Touch targets ≥ 44×44px** is the baseline (WCAG 2.5.5). **Domain exceptions exist and are legitimate
  but must be flagged:** Binance's subscribe buttons at 28px and dense trading rows *"match industry
  trading-platform norms"* — allowed *because the whole row is tappable* (44px+ effective target). When you
  see a sub-44px target, require that the surrounding row/cell compensates, and note it.

---

## 6. Theming & mode structure (component side)

Two mechanisms for supporting multiple surfaces (see `patterns-color.md` §5 for the color side):

**(a) Inverse tokens + one component set.** Define `inverse-canvas` / `inverse-ink` / `inverse-surface-*`
and let components consume `var(--canvas)` etc.; a mode swap remaps the tokens. IBM's approach (scoped to
the footer). Cleanest — one component definition, both modes. **Dark mode is a token remap, never a CSS
`invert()` filter** (which breaks photos and shadows).

**(b) Parallel component pairs.** Ship `top-nav-on-dark` / `top-nav-on-light`, `card-feature-light` /
`card-feature-dark` as separate entries. More explicit, less systematized; common when a system was
extracted rather than designed top-down. Functionally equivalent to (a) at more maintenance cost.

**The mark of a well-structured multi-theme system:** identity and domain semantics **don't reset** across
modes. Binance's yellow CTA and trading green/red are byte-identical on dark and light — only surface and
ink tones flip. If a review finds mode-specific accent drift or orphaned single-mode components, that's a
C3 (mode/theme consistency) failure.

**Compositional polarity-flip** (dark and light bands on one page, chosen by section intent — Binance,
Claude, Ferrari, Sentry) is a theming pattern too: components must be defined for the surface they land on,
and the spec should state the band rhythm (*"don't repeat the same surface mode in two consecutive bands"*).

---

## 7. Component-side Do / Don't

**Do**
- Enumerate variants and states as separate flat `{token}`-referencing entries.
- Ration the primary; give secondary/tertiary clear, lower-emphasis roles.
- Define one focus-ring token and apply it to every interactive element.
- Ship the domain components the product actually renders — including empty/loading/error.
- Keep semantic/domain action buttons (trading up/down, destructive) out of generic confirm/cancel flows.

**Don't**
- Model states as nested objects, or invent state per-component instead of reusing tokens.
- Document hover shades while leaving focus/error states unspecified.
- Duplicate a whole component per mode when inverse tokens would let one definition serve both.
- Let a mode-specific accent or orphan component break cross-mode consistency.
- Ship components (or a semantic ramp, or a second theme) the product has no use for — that's bloat.
