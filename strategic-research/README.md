# strategic-research

A five-skill Claude Code / Cowork plugin that turns a product, category, or industry name into a full strategic picture — ending in a self-contained HTML report a CPO can read in one sitting.

## The pipeline

```
┌─────────────────────────┐
│ 1. industry-process-map │  What do end users actually do? (process tree + matrix)
└────────────┬────────────┘
             ▼  YAML handoff
┌───────────────────────────────┐
│ 2. audience-segment-research  │  Who are they? Segments, stakeholders, tensions
└──────────────┬────────────────┘
               ▼  YAML handoff
┌─────────────────────────────────┐
│ 3. willingness-to-pay-research  │  What do they pay for, why, and how do they know it's working?
└───────────────┬─────────────────┘
                ▼  YAML handoff
┌──────────────────────────────┐
│ 4. competitor-evaluation     │  Who else plays, how, and what's their moat?
└──────────────┬───────────────┘
               ▼  YAML handoff (of all four)
┌────────────────────────────────────┐
│ 5. strategic-synthesis-report      │  Executive summary + per-section analysis + cross-skill insights
│    → strategic-synthesis-[slug].html │  Self-contained HTML with tables, heatmaps, radar charts
└────────────────────────────────────┘
```

Every skill has a markdown body artifact (readable standalone) and a YAML handoff block at the end (machine-parseable). The final skill consumes all four YAML handoffs and renders the HTML report.

## Book spine

Each skill is grounded in specific books, integrated rather than cited:

| Skill | Book spine |
|---|---|
| industry-process-map | Christensen (JTBD); MECE discipline (Minto) |
| audience-segment-research | Dunford (Obviously Awesome); The Mom Test (Fitzpatrick); Thinking in Systems |
| willingness-to-pay-research | Monetizing Innovation (Ramanujam & Tacke); Kano; Bain 30 Elements of Value; Ulwick (ODI); EVC (Anderson-Narus) |
| competitor-evaluation | 7 Powers (Helmer); Blue Ocean Strategy; Dunford; Christensen; The Mom Test |
| strategic-synthesis-report | Minto Pyramid; Working Backwards (for the recommendation shape) |

## Usage

### Full pipeline

```
/strategic-research SplitMetrics
```

Runs all five skills in sequence, ending with the HTML report.

### Resume from a step

```
/strategic-research "Mobile ad optimization" --from=step-4
```

Resumes from step 4, assuming steps 1–3 already produced artifacts.

### Individual skills

Each skill is callable independently:

- `industry-process-map` — when you need the space mapped but not yet the users
- `audience-segment-research` — consumes a process map handoff if present, else bootstraps
- `willingness-to-pay-research` — consumes segments; produces per-segment value/drivers/proof-signals
- `competitor-evaluation` — consumes all three upstream handoffs; produces 7 Powers grid and strategy canvases
- `strategic-synthesis-report` — consumes all four; produces the HTML artifact

## Design principles (plugin-wide)

1. **Verbs, not nouns, everywhere.** Axis labels, segment names, Leader outcomes — all are user verbs, not vendor categories.
2. **Behavior beats stated preference.** Every claim is tagged behavioral or stated; behavioral weights ~3× higher.
3. **Tensions held, not resolved.** Contradictions live in a dedicated log. Premature resolution is a feature loss.
4. **Singletons preserved.** Per-segment and global outlier sections. 1–2 data points can foreshadow a nascent pattern.
5. **Confidence as a percentage.** No hedge words. Every claim carries a %.
6. **YAML handoffs are the contract.** Breaking the schema breaks the pipeline. Schemas live under `references/handoff-schema.md` in each skill.

## Structure

```
strategic-research/
├── .claude-plugin/
│   └── plugin.json
├── README.md
├── commands/
│   └── strategic-research.md         ← /strategic-research orchestrator
└── skills/
    ├── industry-process-map/
    │   ├── SKILL.md
    │   ├── assets/
    │   └── references/
    ├── audience-segment-research/
    ├── willingness-to-pay-research/
    ├── competitor-evaluation/
    └── strategic-synthesis-report/
        ├── SKILL.md
        ├── assets/
        │   ├── html-template.html    ← single-file HTML scaffold
        │   └── output-template.md    ← companion 1-page markdown
        └── references/
            ├── html-template-guide.md
            ├── synthesis-patterns.md  ← the cross-skill joins that matter
            └── visualization-catalog.md
```

## Outputs

For anchor `[slug]`, the pipeline produces in `/sessions/adoring-cool-cray/mnt/tempSkills/`:

- `industry-process-map-[slug].md`
- `audience-segment-research-[slug].md`
- `willingness-to-pay-research-[slug].md`
- `competitor-evaluation-[slug].md`
- `strategic-synthesis-[slug].html`  ← the final deliverable
- `strategic-synthesis-[slug].md`    ← 1-page companion summary

## When to use this plugin

- Entering a new product category or industry and need the whole picture
- Evaluating a new market for an existing product
- Preparing a strategic bet memo or investment thesis
- Refreshing strategic context before a planning cycle
- Replacing a Gartner quadrant briefing with something grounded in buyer behavior

## When NOT to use this plugin

- You only need one of the outputs — call the individual skill
- You already have the research and just need a PRD → `pm-sage:write-prd`
- You need positioning work → `pm-sage:position-product` (feed it the skill #2 + skill #3 handoffs)
- You need a sprint plan or roadmap → `product-management:sprint-planning`, `product-management:roadmap-update`

## License

MIT.
