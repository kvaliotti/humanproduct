---
name: review-design-system
description: |
  Audit an existing design system and say what to fix first. Use when the user says "review my design
  system", "audit our design tokens", "critique our colors/typography/spacing", "is our design system any
  good", "why does our UI feel inconsistent", "grade our DESIGN.md", or hands over a DESIGN.md, a codebase,
  a Tailwind config, or screenshots for a quality judgment. Runs an accessibility gate (real WCAG contrast
  math) and a complexity-fit gate (judged against the product's archetype, not generic minimalism), then
  returns the top fixes and what to protect. Keywords: design system review, design audit, design token
  review, design critique, UI consistency.
user-invocable: true
argument-hint: "[path to DESIGN.md / codebase / or description of the system]"
---

# Review a Design System

Say what is wrong, what to fix first, and what to leave alone. Every finding points at a real token,
component, or section. No vibes, no scores.

Read first:
- `${CLAUDE_PLUGIN_ROOT}/references/archetypes.md` — sets the bar. Read before judging anything.
- `${CLAUDE_PLUGIN_ROOT}/references/accessibility.md` — the contrast math and checks.
- The `patterns-*.md` file for whatever you flag, and the nearest exemplar in
  `${CLAUDE_PLUGIN_ROOT}/references/exemplars/` (Linear = minimal dev-tool, Binance = dense fintech).

## Steps

1. **Get the system.** A DESIGN.md: read it. A codebase: extract the de-facto system with
   `${CLAUDE_PLUGIN_ROOT}/references/codebase-bridge.md`. Screenshots or Figma: capture the observable
   colors, type roles, spacing, radii, components. Say what you could not see.
2. **Name the archetype.** One sentence: "Judged as a **<archetype>**, so I expect <its complexity budget>."
3. **Accessibility gate.** Resolve every component's text/background pair to hex and compute the ratio in
   every mode. Over ~10 components, write a script. Also check color-only signals and missing focus.
   Any AA failure blocks: it is fix #1 regardless of anything else.
4. **Complexity-fit gate.** Judge both ways against the archetype budget. *Under-built*: the domain needs
   tokens it lacks (no error states in an app with forms, no up/down in a trading UI). *Over-built*:
   near-duplicates, one-offs, orphans, ceremony with no payoff. Before calling anything bloat, run the
   essential-vs-accidental test. If unsure, ask.
5. **Find the top fixes.** Use the lookup list below. Rank by how many screens a fix touches times how easy
   it is. Keep at most 5; 3 is the default.
6. **Write the Keep list.** The signature and real strengths an optimize pass must not sand off.

## What to look for (lookup, not output)

- **Color:** one accent, rationed; a real ink ladder (near-black, not drifting); explicit `on-*` tokens;
  semantic/domain colors used as signals, never fills; no near-duplicate inks or hairlines.
- **Type:** a small set of semantic roles, not a size soup; one weight signature held everywhere; extra
  families only for code, money, or editorial voice; open-source substitutes for proprietary fonts.
- **Space and shape:** one base unit, a regular scale, no off-scale values; one radius per component type.
- **Elevation:** one depth strategy, not a mix; one focus-ring token reused everywhere.
- **Components:** variants and states as separate flat entries; the domain components the product
  actually renders (tables, number cells, empty/loading/error); no hover shades while focus/error is missing.
- **Docs:** Do's/Don'ts that stop the likely mistakes; honest Known Gaps; every token the prose names
  exists, and every token is explained. Prose that promises what the tokens can't express is a finding.
- **Modes:** accent and domain colors stay identical across modes; only surface and ink flip.
- **Absence:** absence with a stated rule is discipline; absence without one is a hole.

## Output

Keep it to about one page:

```
# Design System Review — <name>

**Archetype:** <archetype> — judged against <what this domain warrants>
**Verdict:** <one or two sentences: the state of the system and the single biggest problem>

## Accessibility — <PASS / BLOCK>
- <component> — <fg hex> on <bg hex> = <ratio> ✗ (needs <min>) [<mode>]
- Color-only signals / missing focus: <list or "none">

## Complexity fit — <well-fit / under-built / over-built>
<1–3 lines, each naming the token or component>

## Top fixes
1. **<anchor: token / component / section>** — <why it matters> → <smallest change that fixes it>
2. …

## Keep
- <signature or strength, with the token that carries it>

_Not shown: <e.g. per-dimension notes, the full contrast table, N minor findings>. Ask for any of them._
```

List at most 5 contrast failures (worst first) and give a count for the rest. If the user wants the fixes
applied, hand off to `optimize-design-system` with the archetype, the fixes, and the Keep list.
