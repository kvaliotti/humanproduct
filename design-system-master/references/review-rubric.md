# Review Rubric

The scoring instrument for `review-design-system` (and the target `optimize-design-system` moves toward).
It maps directly onto the three questions a design-system review must answer:

- **A. Coordination** — is each dimension (color, type, space, shape, elevation) internally well-tuned?
- **B. Ease of working with it** — can a contributor use and extend it without fighting it?
- **C. Cohesion** — do the dimensions work *together* as one system, not five parallel ones?

Plus two cross-cutting gates that override a good-looking score: **Accessibility** and **Complexity-fit**.

> **Golden rule of this rubric:** score against the system's *own archetype and domain*, not against a
> generic ideal of "minimal." A dense trading terminal with dual-coded green/red, a dual font stack, and
> two theme surfaces is not "over-complicated" — it is correctly complex. Read
> `references/archetypes.md` and calibrate the bar before scoring. Penalise **accidental** complexity
> (redundant tokens, one-off values, undocumented states); never penalise **essential** complexity the
> domain requires.

---

## Contents
- **Scoring scale (per dimension)** — the 0–4 bands
- **A. Coordination** (A1–A5) — color, type, spacing, shape, elevation
- **B. Ease of working with it** (B1–B6) — naming, scales, component API, docs, mappability, governance
- **C. Cohesion** (C1–C5) — harmony, discipline, mode consistency, prose↔token lockstep, no orphans
- **Cross-cutting gates** — G1 accessibility (hard), G2 complexity-fit (anti-overfit)
- **Overall verdict** — how to synthesize the report

## Scoring scale (per dimension)

| Score | Band | Meaning |
|---|---|---|
| 0 | **Broken** | Actively works against contributors/users; contradictions, illegible pairings, no tokens. |
| 1 | **Weak** | Ad hoc; values repeat as literals; gaps that force one-off decisions on every screen. |
| 2 | **Solid** | Tokenized and mostly consistent; a few holes or inconsistencies; usable but needs care. |
| 3 | **Strong** | Regular scales, disciplined usage, documented; a contributor rarely has to guess. |
| 4 | **Exemplary** | Self-evident, self-enforcing, complete; new work falls into place; peer to the best exemplars. |

Report each dimension's score **with one line of evidence** (a token, a value, a contradiction) — never a
bare number. End with an overall band and the 3 highest-leverage fixes.

---

## A. Coordination (per-dimension quality)

### A1 — Color coordination
- Is there a clear **accent-rationing** logic (one primary that appears sparingly, "one filled thing per band")?
- Neutral ramp: is `ink`/`canvas`/`hairline` a real ladder with even steps, or arbitrary grays?
- Is text near-black (not pure `#000`) and are muted tiers above a legibility floor?
- Do `on-primary` / `on-dark` tokens exist so text-on-fill is deliberate, not accidental?
- **Complex-system check:** if semantic or domain color-coding exists (success/warn/err, trading up/down,
  data-viz), is it *disciplined* (semantic tokens never repurposed, never used as large fills)? See `references/patterns-color.md`.

### A2 — Typography coordination
- Is the scale a **small set of semantic roles** (display/heading/body/caption/button/number), not a size soup?
- Weight strategy coherent (a signature — thin-display or bold-display — held consistently)?
- Line-height & tracking follow a rule (negative tracking on display, ~1.5 body, ~1.0 buttons)?
- **Complex-system check:** if there is a second/third family (numeric/mono/display), is the split
  *functional and rule-bound* (e.g. "all numbers in Plex, all copy in Nova"), not decorative? See `references/patterns-typography.md`.
- Are proprietary fonts given open-source substitutes?

### A3 — Spacing & layout coordination
- One base unit (4 or 8px) with a regular named scale? Any values off the scale?
- Section/card/gutter padding norms stated and followed?
- Grid/container and whitespace philosophy explicit and matched to density (dense vs airy)?

### A4 — Shape coordination
- Radius scale regular, and **radius-per-component consistent** (all buttons one radius, all cards another)?
- Does radius express intent coherently (pill = transactional, square = enterprise) rather than drift?

### A5 — Elevation & depth coordination
- Is there ONE depth strategy (flat color-block / layered shadow / gradient / glass / inverse-tone),
  applied consistently — or a mix that reads as noise?
- Focus-ring specified once and reused?

---

## B. Ease of working with it (ergonomics / DX)

### B1 — Token naming & discoverability
- Role-based names (`ink`, `canvas`, `hairline`) beat literal names (`gray-900`)? Could a new contributor
  guess the right token in <5s? Are there near-synonyms that force a coin-flip (`ink-mute` vs `ink-mute-2`)?

### B2 — Scale regularity & predictability
- Are spacing/type/radius scales evenly stepped so "the next size up" is obvious? Holes and one-offs
  each cost a decision.

### B3 — Component API consistency
- Do components share a consistent shape (same fields, `{token}` refs, variants-as-entries)? Is state
  modeled the same way everywhere? Inconsistent component specs are the #1 velocity tax.

### B4 — Documentation & guardrails
- Do **Do's/Don'ts** exist and actually prevent the likely mistakes? Is there an **Iteration Guide**?
  Are **Known Gaps** honest? Undocumented systems get re-litigated on every PR.

### B5 — Codebase mappability
- Do tokens translate cleanly to the target's medium (CSS vars / Tailwind theme / Style Dictionary /
  CSS-in-JS)? See `references/codebase-bridge.md`. Systems that don't map get bypassed with inline styles.

### B6 — Extensibility & governance
- Can you add a component/mode without breaking existing ones? Is there a stated way to propose changes?
  (Weight this up for enterprise archetypes, down for a solo-founder MVP.)

---

## C. Cohesion (does it work *together*)

### C1 — Cross-dimension harmony
- Do color + type + space + shape read as one voice (e.g. thin type + generous space + square chrome =
  enterprise gravitas), or as four unrelated decisions bolted together?

### C2 — Usage discipline
- Is the accent actually rationed in practice? Is the signature (the one distinctive move) held
  everywhere, or abandoned on half the surfaces?

### C3 — Mode / theme consistency
- If multi-theme, do the *same* tokens/components flip cleanly (shared accent, shared semantics, only
  surface/ink tones change)? Are there mode-specific orphans?

### C4 — Prose ↔ token lockstep
- Does every token the prose names exist in frontmatter, and is every token explained in prose? Drift
  here means the doc is already lying about the system.

### C5 — No orphans / no redundancy
- Tokens defined but never referenced? Components with no usage rule? Near-duplicate colors (ΔE tiny)?
  Two radii that do the same job? Each is accidental complexity to flag.

---

## Cross-cutting gates (can cap the overall score)

### G1 — Accessibility (hard gate)
Run the checks in `references/accessibility.md`. Any **body-text/background pair below WCAG AA (4.5:1)**,
or an interactive target with no visible focus state, caps the overall band at **"Solid" (2)** regardless
of aesthetics until fixed. Report each failing pair with its measured ratio.

### G2 — Complexity-fit (the anti-overfit gate)
Classify the archetype (`references/archetypes.md`). Then judge complexity **both ways**:
- *Under-built:* a system whose domain needs semantic/domain/mode tokens but lacks them (e.g. a fintech
  with no up/down tokens, an app with no dark mode) — this is a **gap**, not virtue.
- *Over-built:* redundant tokens, one-off values, ceremony with no payoff — this is **bloat**.
A system is complexity-fit when every piece of its complexity is traceable to a real domain need.

---

## Overall verdict

Synthesize, don't average blindly. Produce:

1. **Headline band** (Broken / Weak / Solid / Strong / Exemplary) with the archetype it's judged against.
2. **Scorecard table** — each dimension A1–C5 with score + one-line evidence.
3. **Gate results** — accessibility failures (with ratios) and complexity-fit judgment.
4. **Top 3 highest-leverage fixes** — ranked by (impact on cohesion/usability × ease of doing).
5. **What to keep** — the strengths worth protecting (so an "optimize" pass doesn't destroy them).

Item 5 is not optional. The fastest way to ruin a good system is to "improve" its signature away.
