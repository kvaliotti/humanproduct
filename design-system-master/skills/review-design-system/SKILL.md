---
name: review-design-system
description: |
  Audit an existing design system and report how good it is. Use when the user says "review my design
  system", "audit our design tokens", "critique our colors/typography/spacing", "is our design system
  any good", "why does our UI feel inconsistent", "grade our DESIGN.md", or hands over a DESIGN.md, a
  codebase, a Tailwind config, or screenshots for a quality judgment. Scores three lenses — coordination
  (color, type, spacing, shape, elevation), ease of working with it (naming, scale regularity, component
  API, docs), and cohesion — gated by accessibility and complexity-fit, then runs a five-lens expert
  panel. Produces a scorecard, contrast findings, the highest-leverage fixes, and what to protect.
  Grounded in 74 real systems so it judges against the product's archetype, not generic minimalism.
  Keywords: design system review, design audit, design token review, design critique, UI consistency.
user-invocable: true
argument-hint: "[path to DESIGN.md / codebase / or description of the system]"
---

# Review a Design System

Produce an honest, evidence-backed judgment of a design system across the three questions that matter:
is each dimension well-**coordinated**, is it **easy to work with**, and does it all **cohere**. Every
claim is anchored to a real token, value, or contradiction — never a vibe.

## Load the knowledge base

Read before scoring (these are the instrument):
- `${CLAUDE_PLUGIN_ROOT}/references/archetypes.md` — **first**, to set the bar correctly.
- `${CLAUDE_PLUGIN_ROOT}/references/review-rubric.md` — the dimensions and scoring scale you'll apply.
- `${CLAUDE_PLUGIN_ROOT}/references/accessibility.md` — the hard contrast/focus gate.
- `${CLAUDE_PLUGIN_ROOT}/references/expert-panel.md` — the five-lens adversarial pass.
- The pattern files (`patterns-color.md`, `patterns-typography.md`, `patterns-space-shape-elevation.md`,
  `patterns-components-theming.md`) — read the ones relevant to what you're flagging, for the "what good
  looks like" comparison.
- `${CLAUDE_PLUGIN_ROOT}/references/exemplars/` — reach for a same-archetype exemplar to calibrate.

## Workflow

For a full audit, copy this checklist into your response and tick items as you go:

```
Review progress:
- [ ] 1. Ingest & normalize the input (or extract it from the codebase)
- [ ] 2. Classify the archetype (sets the bar)
- [ ] 3. Score dimensions A1–C5 (each: score + one line of evidence)
- [ ] 4. Accessibility gate — contrast every pair, every mode
- [ ] 5. Complexity-fit gate — under-built vs over-built
- [ ] 6. Expert panel — five lenses
- [ ] 7. Synthesize verdict + top 3 fixes + Keep list
```

### 1. Ingest & normalize the input
- **DESIGN.md** → read it as-is.
- **Codebase** → extract the de-facto system using `${CLAUDE_PLUGIN_ROOT}/references/codebase-bridge.md`
  (grep colors/spacing/type, find CSS vars / Tailwind / tokens.json). Build a working token model.
- **Screenshots / live / Figma** → capture observable colors, type roles, spacing, radius, components.
- If the system is thin or you're inferring a lot, say so — a review of an extracted model is only as
  good as the extraction. List what you couldn't see (feeds "Known Gaps").

### 2. Classify the archetype (sets the bar)
Name the archetype and domain from `archetypes.md` (dev-tool minimal / financial-dense / enterprise /
consumer-brand / AI-product / creative-canvas / automotive-luxury / media / gaming). Write one sentence:
"Judged as a **<archetype>** system, so I expect <the complexity this domain warrants>." This is what
stops you from scoring correct complexity as a flaw.

### 3. Score the dimensions
Walk **A1–A5** (coordination), **B1–B6** (ease), **C1–C5** (cohesion) from the rubric. For each: a 0–4
score **and one line of evidence**. Be specific — `A1 Color: 2 — "ink-mute #64748d and ink-mute-2 #61718a
are near-duplicates doing the same job"`. Compare against the same-archetype exemplar and the pattern
files, not against an abstract ideal.

### 4. Run the accessibility gate (G1)
Compute contrast for every text/background component pair, **in every mode**, per `accessibility.md`. For
>10 components, write a small script to sweep them. Report each failure with its measured ratio. Check for
color-only signals and missing focus states. Any AA failure caps the overall band.

### 5. Run the complexity-fit gate (G2)
Judge both directions: **under-built** (domain needs tokens it lacks — no dark mode, no up/down tokens, no
error states) and **over-built** (redundant/orphan tokens, one-off values, ceremony without payoff). Only
the second is "too complex."

### 6. Run the expert panel
Do the five-lens pass from `expert-panel.md` (inline for a normal system; parallel subagents for a large
one). Surface each panelist's one concrete point and any blocking objection.

### 7. Synthesize the verdict
Assemble the report (template below). Do not average scores blindly — weight cohesion and the gates. End
with the **top 3 highest-leverage fixes** and, crucially, **what to keep** (the strengths and signature an
optimize pass must not destroy).

## Report structure

ALWAYS use this template:

```
# Design System Review — <name>

**Archetype:** <archetype> · judged against <what this domain warrants>
**Headline:** <Broken / Weak / Solid / Strong / Exemplary> — <one-sentence why>

## Scorecard
| Dim | Area | Score | Evidence |
|-----|------|-------|----------|
| A1 | Color coordination | x/4 | … |
| A2 | Typography | x/4 | … |
| A3 | Spacing & layout | x/4 | … |
| A4 | Shape | x/4 | … |
| A5 | Elevation & depth | x/4 | … |
| B1 | Token naming | x/4 | … |
| B2 | Scale regularity | x/4 | … |
| B3 | Component API | x/4 | … |
| B4 | Docs & guardrails | x/4 | … |
| B5 | Codebase mappability | x/4 | … |
| B6 | Extensibility/governance | x/4 | … |
| C1 | Cross-dimension harmony | x/4 | … |
| C2 | Usage discipline | x/4 | … |
| C3 | Mode/theme consistency | x/4 | … |
| C4 | Prose↔token lockstep | x/4 | … |
| C5 | No orphans/redundancy | x/4 | … |

## Gates
- **Accessibility (G1):** <PASS/BLOCK> — <failing pairs with ratios, color-only, focus>
- **Complexity-fit (G2):** <under-built gaps | over-built bloat | well-fit>

## Expert Panel
<the five verdicts + panel outcome>

## Top 3 fixes (highest leverage)
1. <fix> — <why it moves the most, and roughly how>
2. …
3. …

## Keep (protect these)
- <the signature / strengths an optimize pass must not sand off>
```

## Handoff
If the user wants the fixes applied, hand off to **`optimize-design-system`** — pass along the archetype,
the top fixes, and especially the "Keep" list so improvement doesn't erase the system's identity.

## Scale the effort
A quick "gut check" ask → score the five A-dimensions + the accessibility gate + top 3 fixes, skip the
full scorecard and panel. A formal audit → the whole workflow. Say which mode you're running.
