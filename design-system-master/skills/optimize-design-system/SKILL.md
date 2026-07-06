---
name: optimize-design-system
description: |
  Improve an existing design system and/or roll it into a product codebase. Use when the user says
  "optimize/improve our design system", "clean up our tokens", "our styles are inconsistent",
  "consolidate our colors", "apply this design system to our app", "retrofit these tokens", "reduce token
  bloat", or "add dark mode / semantic colors properly". Works on the spec (consolidate and rationalize
  tokens, fill gaps, fix contrast) and on the codebase (extract the de-facto system, map tokens to CSS
  variables / Tailwind / Style Dictionary, codemod literals to tokens incrementally). Prioritizes by
  blast radius and protects the system's signature; grounded in 74 real systems so it removes accidental
  complexity without touching complexity the domain needs. Keywords: optimize design system, consolidate
  design tokens, design consistency, retrofit tokens, dark mode, semantic colors, Tailwind, CSS variables.
user-invocable: true
argument-hint: "[path to DESIGN.md and/or codebase] [what to improve, or 'audit + fix']"
---

# Optimize a Design System

Make an existing system measurably better — tighter coordination, easier to work with, more cohesive —
and/or make a product codebase actually implement it. The prime directive: **remove accidental
complexity, preserve essential complexity, and never destroy the signature.**

## Load the knowledge base

- `${CLAUDE_PLUGIN_ROOT}/references/archetypes.md` — **first**; it defines what complexity to protect.
- `${CLAUDE_PLUGIN_ROOT}/references/review-rubric.md` — the dimensions you're moving upward.
- The pattern files — the "what good looks like" target for each dimension you touch.
- `${CLAUDE_PLUGIN_ROOT}/references/codebase-bridge.md` — for the code-facing path (extract & emit).
- `${CLAUDE_PLUGIN_ROOT}/references/accessibility.md` — re-run after every color/mode change.
- `${CLAUDE_PLUGIN_ROOT}/references/expert-panel.md` — gate the proposed changes before applying.
- `${CLAUDE_PLUGIN_ROOT}/references/design-md-format.md` — keep the spec canonical as you edit.

## Two paths (often both)

**Path S — improve the spec (`DESIGN.md`).** Consolidate near-duplicate tokens, regularize scales, name
things by role, fill missing states/modes, fix contrast, tighten the prose↔token lockstep, add Do's/Don'ts
and Known Gaps.

**Path C — apply it to a codebase.** Extract the de-facto system, diff it against the intended direction,
emit tokens to the target medium, and codemod literals → tokens incrementally. This is the common "new
product" case.

Decide which path(s) apply from the input, and say so.

## Workflow

Copy this checklist into your response and tick items as you go:

```
Optimize progress:
- [ ] 1. Know the current state (archetype, top problems, Keep list)
- [ ] 2. Set the direction (polish spec / roll into codebase / evolve)
- [ ] 3. Build the prioritized plan (blast radius × ease)
- [ ] 4. Anti-overfit guard — essential vs accidental on every removal
- [ ] 5. Apply changes in small reviewable batches
- [ ] 6. Gate & verify — expert panel + accessibility recheck
```

### 1. Know the current state (don't optimize blind)
If a review hasn't just been done, run a fast pass of `review-design-system` (or at least: classify the
archetype, score the five coordination dimensions, run the accessibility gate). You need three things
before changing anything:
- the **archetype** (what complexity is legitimate),
- the **top problems** (where the leverage is),
- the **Keep list** (the signature + strengths that are off-limits to "improvement").

### 2. Set the direction
Confirm the target with the user in one line: are we (a) polishing the spec, (b) rolling it into a
specific codebase/stack, (c) evolving it (add dark mode, add a semantic ramp, support a second brand)?
For a codebase, identify the stack (CSS vars / Tailwind v3 / v4 / Style Dictionary / CSS-in-JS / shadcn)
from `codebase-bridge.md`.

### 3. Build the prioritized improvement plan
Classify every proposed change and rank by **blast radius × ease**:

- **Consolidations** — merge near-duplicate tokens (small ΔE), collapse redundant radii/spacings, delete
  orphans. Highest-frequency tokens first: fixing `canvas`/`ink` once fixes thousands of screens.
- **Regularizations** — snap off-scale values onto the scale; make radius-per-component consistent.
- **Gap fills** — missing states (disabled/focus/error), missing modes (dark), missing semantic/domain
  tokens the domain actually needs, missing docs (Do's/Don'ts, Iteration Guide).
- **Accessibility fixes** — every AA failure from the gate; add/repair focus rings; add non-color signals.
- **Naming** — literal → role-based names, kill near-synonyms.

Present the plan as a ranked table (change · type · blast radius · effort · risk to signature) and get a
go-ahead before large edits. **Flag anything that touches the Keep list and require explicit sign-off.**

### 4. The anti-overfit guard (do NOT skip)
Before proposing to remove any complexity, ask for each item: *is this accidental or essential?*
- A second font family → vanity, or is it carrying numerics/code? (essential — keep)
- Green/red tokens → decorative, or semantic price/diff signals? (essential — keep, just discipline them)
- A second theme → redundant, or marketing-dark + product-light like Binance? (essential — keep)
- A wide semantic ramp → bloat, or enterprise breadth like IBM/Carbon? (essential — keep)
- Many colors → noise, or functional object-coding in a canvas tool like Airtable/Figma? (essential — keep)
Only propose removing what fails this test. When unsure, ask the user rather than assume.

### 5. Apply changes
- **Path S:** edit the `DESIGN.md` — keep frontmatter tokens and prose in lockstep; represent variants/
  states as separate `components:` entries; update Do's/Don'ts and Known Gaps to match.
- **Path C:** emit tokens to the target medium, then codemod literals → tokens **incrementally**, highest-
  frequency family first, leaving the product shippable after each step. Never big-bang rewrite.
- Make changes in small, reviewable batches; show diffs; explain each in one line.

### 6. Gate & verify
- Run the **expert panel** on the changed system — the Art Director watches that the signature survived,
  the Accessibility lens re-checks contrast in every mode, the DX Engineer confirms it's still buildable.
- Re-run the **accessibility** contrast sweep — surface remaps are exactly when AA regressions appear.
- If the linter is available, `npx @google/design.md lint DESIGN.md`.

## Output
- The updated `DESIGN.md` (and/or emitted token files + codemod diffs).
- A **change log**: what changed, why, blast radius, and explicit confirmation the Keep list survived.
- Any remaining items deferred, with rationale (added to Known Gaps).

## Scale the effort
"Just consolidate the colors" → do the consolidation + accessibility recheck, skip the full plan. "Roll
our system into this app" → the full Path-C workflow. Match the ceremony to the ask.
