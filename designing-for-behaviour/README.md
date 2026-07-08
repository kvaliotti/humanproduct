# designing-for-behaviour

Evaluate how well a product experience drives user **behaviour**, **adoption**, and **engagement** — then get an integrated set of fixes that strengthen a single coherent core experience instead of bloating it with bolted-on mechanisms.

Point it at either:
- **an existing product / codebase** — it reconstructs the experience users actually get, from the code, or
- **an idea, PRD, or feature description** — it reconstructs the *intended* experience from the doc.

```
/designing-for-behaviour <path to code / PRD file, or a feature description>
```

## The pipeline

```
intake (codebase OR PRD) → 4 lenses in parallel → score (3 dimensions)
   → rank gaps → coherence & anti-bloat review → report
```

1. **Intake** — reconstruct the specific experience, its target behaviour(s), users, and why it matters. Done once and shared with every lens.
2. **Four lenses, in parallel** — a board of independent analysts, each reading the real artifact through one frame and returning scored, anchored findings.
3. **Score** — roll up **behaviour / adoption / engagement** percentages (+ overall, per-lens, confidence).
4. **Rank gaps** — biggest blocker first, each with a concrete anchor.
5. **Coherence & anti-bloat review** *(the point of the tool)* — consolidate recommendations, resolve conflicts, enforce a complexity budget, prefer embedding over adding, find the root fix that dissolves several recs, run a subtraction pass, and gate everything for ethics. Output: **core moves** (sequenced), **fold-ins** (embedded, not bolted on), and **deliberately NOT adding** (what was cut, and why).
6. **Report** — a `behaviour-review-[target].md` file plus a tight inline summary.

It **evaluates and recommends** — it does not implement. Hand the core moves to your own dev flow (e.g. `/ship`) to build.

## The four lenses (six books, de-duplicated)

The six source books overlap heavily — each repeats behaviour-definition, adoption, engagement, metrics, and ethics. Those shared sections are factored out **once** into cross-cutting references; the three habit books (which overlap ~70%) merge into a single loop lens. What remains are four genuinely distinct lenses:

| Lens (agent) | Distilled from | Owns |
|---|---|---|
| **behavioural-loop** | Atomic Habits · Tiny Habits · Hooked | Trigger → action → reward → investment; B=MAP; the return/habit loop |
| **cognitive-ease** | Thinking, Fast and Slow | Decision points: System 1/2, fluency, friction, framing, anchoring, defaults, loss aversion, memory |
| **capability-results** | Badass: Making Users Awesome | Does the *user* get better — compelling context, progress curve, meaningful vs. empty engagement |
| **control-autonomy** | Making Sense of Behavior (PCT) | What the user is trying to *control*; disturbances; conflict; autonomy; anti-manipulation |

## Why the anti-bloat step exists

Four lenses each generate good recommendations. Concatenated, they produce a product with streaks *and* badges *and* a tour *and* five nudges *and* a goal wizard — each defensible, collectively unusable. The coherence review is the editorial pass that turns the pile into the **smallest set of changes that most improves behaviour while keeping the experience light** — and it's willing to recommend *removing* mechanisms, not just adding them. A behavioural checklist without this step actively makes products worse.

## Components

| Component | Role |
|---|---|
| `skills/designing-for-behaviour` | Orchestrator — the `/designing-for-behaviour` entry point; runs the pipeline and the anti-bloat review |
| `agents/*-analyst.md` | The four parallel lens-analysts (read-only inspection — they read/search the product, never modify it) |
| `references/foundations.md` | Shared definitions + intake protocol (the de-duplicated common header) |
| `references/scoring-rubric.md` | Unified 0/1/2/N-A scale + dimension roll-up |
| `references/lens-*.md` | The four de-duplicated lens checklists |
| `references/coherence-and-anti-bloat.md` | The integration review |
| `references/ethics-and-dark-patterns.md` | The manipulation gate applied to recommendations |
| `references/report-template.md` | Fixed report structure + inline-summary spec |

## Design notes

- **Anti-slop by contract** — every score, gap, and recommendation must carry a concrete anchor (screen/flow/`file:line`/quoted copy/PRD section/moment). Unanchored claims don't ship.
- **Right-sized machinery** — items irrelevant to a product's archetype are marked N/A, not scored 0. The tool never tells a focused utility to become a cluttered one.
- **Autonomy wins** — where a mechanism-lens fix would be manipulative, the ethics gate reframes or cuts it.

Grounded in *Atomic Habits*, *Tiny Habits*, *Hooked*, *Badass: Making Users Awesome*, *Thinking, Fast and Slow*, and *Making Sense of Behavior* (Perceptual Control Theory).
