<!--
  DESIGN.md scaffold — fill every <…>, delete guidance comments as you go.
  Sections/tokens marked [OPTIONAL — <archetype>] are ESSENTIAL for that domain and OMITTABLE otherwise.
  Decide your archetype + complexity budget first (references/archetypes.md), then keep only what the budget calls for.
  Keep frontmatter tokens and prose in lockstep; reference tokens via {group.token}; verify every text/bg pair for AA.
-->
---
version: alpha
name: <Product>-design-system
description: <one sentence capturing the design DNA — the thesis a reader walks away with. Name the signature.>

colors:
  # Brand / accent — ration it hard (one filled thing per band)
  primary: "#______"
  primary-active: "#______"          # pressed/hover-darker
  on-primary: "#______"              # text ON primary — a deliberate choice, verify contrast (not auto white)
  # Ink (text) ladder — near-black, not pure #000
  ink: "#______"                     # strongest text
  ink-muted: "#______"               # secondary
  ink-subtle: "#______"              # tertiary / captions (keep above the legibility floor)
  # Surface ramp — 2–4 steps
  canvas: "#______"                  # page floor
  surface-1: "#______"
  hairline: "#______"                # ~one elevation step from its surface
  # [OPTIONAL — any app with forms/dashboards] Semantic ramp
  # semantic-success: "#______"
  # semantic-warning: "#______"
  # semantic-error: "#______"
  # semantic-info: "#______"
  # [OPTIONAL — fintech/trading] Domain dual-code — text/badge only, NEVER a fill; pair with an arrow/sign
  # trading-up: "#______"
  # trading-down: "#______"
  # [OPTIONAL — both light & dark surfaces] Inverse/mode tokens (or ship parallel component pairs)
  # inverse-canvas: "#______"
  # inverse-ink: "#______"
  # info-ring: "#______"             # the single reused focus-ring color

typography:
  # Name roles semantically, never by size. ~14 roles is a good default.
  display-lg: { fontFamily: <Family>, fontSize: __px, fontWeight: ___, lineHeight: _._, letterSpacing: -_._px }
  heading-md: { fontFamily: <Family>, fontSize: __px, fontWeight: ___, lineHeight: _._, letterSpacing: -_._px }
  body-md:    { fontFamily: <Family>, fontSize: __px, fontWeight: 400, lineHeight: 1.5, letterSpacing: 0 }
  caption:    { fontFamily: <Family>, fontSize: __px, fontWeight: 400, lineHeight: 1.4, letterSpacing: 0 }
  button:     { fontFamily: <Family>, fontSize: __px, fontWeight: 600, lineHeight: 1,   letterSpacing: 0 }
  # [OPTIONAL — dev tools] mono role for code/terminal; [OPTIONAL — data/money] a numeric role (tnum or a numeric family)
  # code:       { fontFamily: <Mono>, fontSize: __px, fontWeight: 400, lineHeight: 1.5, letterSpacing: 0 }
  # number-md:  { fontFamily: <Family>, fontSize: __px, fontWeight: 500, lineHeight: 1.4, letterSpacing: 0, fontFeature: tnum }

rounded:
  # 0–4px = enterprise/precision · 6–12px = sober/technical · 9999px pill = transactional/consumer. Pick intent.
  sm: __px
  md: __px
  lg: __px
  pill: 9999px

spacing:
  # One base unit (8px airy / 4px dense). Regular, guessable, t-shirt-named.
  xs: 4px
  sm: 8px
  md: 16px
  lg: 24px
  xl: 32px
  section: __px                      # 48–80 dense · 96 standard · 96–192 airy

components:
  # {token}-referencing specs. Variants & states are SEPARATE entries, not nested objects.
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.button}"
    rounded: "{rounded.md}"
    padding: 8px 16px
    height: 40px
  button-primary-active:   { backgroundColor: "{colors.primary-active}", textColor: "{colors.on-primary}", rounded: "{rounded.md}" }
  button-secondary:        { backgroundColor: "{colors.canvas}", textColor: "{colors.ink}", typography: "{typography.button}", rounded: "{rounded.md}", padding: 8px 16px }
  text-input:              { backgroundColor: "{colors.canvas}", textColor: "{colors.ink}", typography: "{typography.body-md}", rounded: "{rounded.sm}", padding: 8px 12px }
  card:                    { backgroundColor: "{colors.canvas}", textColor: "{colors.ink}", typography: "{typography.body-md}", rounded: "{rounded.lg}", padding: 24px }
  # Add the DOMAIN components your product actually renders (data table + number cells, pricing tiers,
  # empty/loading/error states…). Don't ship components the product won't use.
---

## Overview
<One paragraph: the thesis of the system + the signature move.>

**Key Characteristics:**
- <the single distinctive move, held everywhere>
- <accent-rationing rule>
- <type/weight signature>
- <density / whitespace philosophy>

## Colors
### Brand & Accent
### Surface
### Text
### Hairlines & Borders
### Semantic        <!-- [OPTIONAL] keep only if present in frontmatter -->
### Domain          <!-- [OPTIONAL — e.g. trading up/down] state the discipline: signal only, never a fill -->

## Typography
### Font Family     <!-- strategy + why; open-source substitute with weight + tracking -->
### Hierarchy       <!-- | role | size | weight | line-height | tracking | use | table -->
### Principles

## Layout
### Spacing System
### Grid & Container
### Whitespace Philosophy

## Elevation & Depth
<!-- pick ONE strategy: flat color-block / elevation-by-tone / layered shadow / gradient / glass. + a level table + the one focus-ring token -->

## Shapes
### Border Radius Scale   <!-- radius-per-component table -->

## Components
### Buttons
### Cards & Containers
### Inputs & Forms
### Navigation
### <Domain components>

## Do's and Don'ts
### Do
### Don't            <!-- encode THIS system's guardrails: accent rationing, weight rule, domain-token discipline -->

## Responsive Behavior
### Breakpoints      <!-- table -->
### Touch Targets    <!-- ≥44px, note any dense-mode exceptions -->
### Collapsing Strategy

## Iteration Guide
1. One component at a time.
2. Reference tokens directly; never hardcode a value that has a token.
3. Variants/states as new entries, not nested objects.
4. <system-specific extension rule>

## Known Gaps
- <what you deliberately did not specify yet>
