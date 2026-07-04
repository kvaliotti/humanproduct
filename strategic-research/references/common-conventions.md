# Common Conventions (shared)

Conventions shared by every skill in the strategic-research plugin. Skills point here (`${CLAUDE_PLUGIN_ROOT}/references/common-conventions.md`) instead of restating these blocks. Skill-specific additions stay in each SKILL.md.

## Output location & filenames

All artifacts are written to a **`strategic-research/` subfolder of the user's current working directory** (a relative path — create the folder if it does not exist). Filenames are **fixed and step-numbered** so the orchestrator and any `--from=step-N` resume can find prior artifacts deterministically without guessing a slug:

| Step | Skill | Artifact path |
|---|---|---|
| 1 | industry-process-map | `strategic-research/01-industry-process-map.md` |
| 2 | audience-segment-research | `strategic-research/02-audience-segments.md` |
| 3 | willingness-to-pay-research | `strategic-research/03-willingness-to-pay.md` |
| 4 | competitor-evaluation | `strategic-research/04-competitor-evaluation.md` |
| 5 | strategic-synthesis-report | `strategic-research/05-synthesis-report.html` (+ companion `strategic-research/05-synthesis-report.md`) |

Every downstream skill READS the upstream artifacts from these same fixed paths. Re-running a step overwrites its file in place.

After writing, tell the user the **local relative path** where the file was written (e.g., "Written to `strategic-research/01-industry-process-map.md`"). Do not emit sandbox or share-link URLs — these skills run in the user's own project directory.

## Slug algorithm (for internal IDs)

Artifact filenames are fixed (above), so no slug is needed for them. Where a skill derives a **kebab-case ID** from a name (segment IDs, competitor IDs, matrix cell IDs, canvas element IDs), use this deterministic algorithm so IDs are reproducible across runs and stable on resume:

1. Lowercase the text.
2. Replace every run of non-alphanumeric characters with a single hyphen `-`.
3. Trim leading/trailing hyphens.

Example: `"High-volume Agencies (EU)"` → `high-volume-agencies-eu`.

## Writing style

Shared style for every artifact (each a strategic document a CPO-level reader acts on):

- **No preamble.** Start with the framing table. No "this document aims to…" openers.
- **Tables and structured content over prose.** Prose only where a concept needs explanation.
- **Specific names, not categories.** "Appfigures, AppTweak, SensorTower" beats "ASO tools".
- **Verbs in labels.** "Deciding target audience" beats "Target audience analysis".
- **Source tags on non-obvious claims.** Inline `[src: G2 review 2024-09, behavioral]`.
- **Confidence marks as percentages.** No hedge words ("somewhat", "arguably", "it could be said").
- **Honest gaps.** "Thin evidence — 2 data points, 1 behavioral" beats dressing it up.

Each SKILL.md may add its own emphasis (e.g., dollar-math, skeptical voice on moat claims, Minto ordering).

## Redirecting work outside this plugin

The five skills map the space, the audience, willingness to pay, the competitive set, and the synthesis. When the user actually wants a different deliverable, say so and describe the kind of tool that fits — this plugin does not produce these:

| User actually wants | Redirect to |
|---|---|
| A named-competitor battlecard for sales | a sales-battlecard / competitive-brief tool |
| A positioning canvas or market-category claim | a dedicated positioning skill or workshop (feed it the segments + Leaders + alternatives) |
| To evaluate one specific product idea against this landscape | a product-idea evaluation tool |
| A PRD or working-backwards doc | a PRD / spec-writing tool (feed it the Leaders and proof signals) |
| A sprint plan or roadmap | a roadmap / sprint-planning tool |
| A board or stakeholder update | a stakeholder-update / exec-comms tool (feed it the exec summary) |
| To synthesize a pile of interviews already gathered | a research-synthesis tool |

Route to the sibling skill inside this plugin when the task is one this plugin does cover — those routes stay listed in each SKILL.md.

## Quality-audit discipline

Each skill ends with a skill-specific quality-audit checklist. Run it **explicitly** before writing the final artifact, fix any failure, and loop back to the phase that produced the defect. The checklist items differ per skill; the discipline is the same everywhere.
