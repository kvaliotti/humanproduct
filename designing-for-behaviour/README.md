# designing-for-behaviour

Review how well a product experience drives user **behaviour**, **adoption**, and **engagement**, then get the smallest integrated set of fixes that strengthens one coherent core experience instead of bloating it with bolted-on mechanisms.

Point it at either:
- **an existing product / codebase** — it reconstructs the experience users actually get, from the code, or
- **an idea, PRD, or feature description** — it reconstructs the *intended* experience from the doc.

```
/designing-for-behaviour <path to code / PRD file, or a feature description>
```

## The pipeline

```
intake → 4 lenses in parallel → rank gaps → coherence & anti-bloat review + ethics gate → report
```

1. **Intake** — reconstruct the experience, its target behaviour, users, and why it matters. Done once and shared with every lens.
2. **Four lenses, in parallel** — independent analysts, each reading the real artifact through one frame and returning anchored findings, candidate fixes, what's already strong, and what's N/A.
3. **Rank gaps** — biggest blocker first; convergence across lenses raises priority. Names the bottleneck dimension in words.
4. **Coherence & anti-bloat review** *(the point of the tool)* — consolidate, resolve conflicts, enforce a complexity budget, prefer embedding over adding, find the root fix, run a subtraction pass, then gate everything for ethics.
5. **Report** — `behaviour-review-[target].md`, capped at two pages, leading with at most three sequenced core moves and a **deliberately NOT adding** list. Plus a short inline summary.

**No score.** The report has no percentages, bands, or confidence labels. Lenses rate items 0/1/2/N-A internally only to rank gaps and keep irrelevant machinery out.

It **evaluates and recommends**; it does not implement.

## The four lenses

| Lens (agent) | Source | Owns |
|---|---|---|
| **behavioural-loop** | Atomic Habits · Tiny Habits · Hooked | Trigger → action → reward → investment; the return loop; recovery after a lapse |
| **cognitive-ease** | Thinking, Fast and Slow | Decision points: fluency, friction, framing, anchoring, defaults, memory of the experience |
| **capability-results** | Badass: Making Users Awesome | Does the *user* get better; progress curve; meaningful vs. empty engagement; attention drain |
| **control-autonomy** | Making Sense of Behavior (PCT) | What the user is trying to *control*; disturbances; conflict; anti-manipulation |

## Why the anti-bloat step exists

Four lenses each generate good recommendations. Concatenated, they produce streaks *and* badges *and* a tour *and* five nudges *and* a goal wizard: each defensible, together unusable. The coherence review turns the pile into the smallest set of changes that most improves behaviour while keeping the experience light, and it will recommend *removing* mechanisms.

## Components

| Component | Role |
|---|---|
| `skills/designing-for-behaviour` | Orchestrator and `/designing-for-behaviour` entry point |
| `agents/*-analyst.md` | The four parallel lens-analysts (read-only) |
| `references/foundations.md` | Definitions, anti-slop contract, internal 0/1/2/N-A rating, intake, lens carve-up, lens-analyst protocol |
| `references/lens-*.md` | The four lens checklists |
| `references/coherence-and-anti-bloat.md` | The integration review |
| `references/ethics-and-dark-patterns.md` | The manipulation gate applied to recommendations |
| `references/report-template.md` | Report structure, caps, and inline summary |

## Design notes

- **Anchor everything** — every gap and recommendation points at a screen, flow, `file:line`, quoted copy, PRD section, or moment.
- **Right-sized machinery** — items irrelevant to the product's archetype are N/A, not 0. The tool never tells a focused utility to become a cluttered one.
- **Autonomy wins** — where a mechanism-lens fix would be manipulative, the ethics gate reframes or cuts it.
