# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A Claude Code plugin marketplace (not an application). No build, lint, or test step — it ships content (skills and slash commands) consumed by Claude Code when a user installs a plugin from it. Published at `kvaliotti/humanproduct` and installed via `/plugin marketplace add kvaliotti/humanproduct`.

## Structure

```
.claude-plugin/marketplace.json   # marketplace manifest — lists every plugin in the repo
prd-workflow/                     # plugin (directory referenced by marketplace.json)
  .claude-plugin/plugin.json      # plugin manifest (name, version, description, keywords)
  skills/<skill-name>/SKILL.md    # each skill: YAML frontmatter + markdown body
  skills/<skill-name>/references/ # optional supporting docs the skill reads at runtime
strategic-research/               # plugin — also ships a slash command
  .claude-plugin/plugin.json
  commands/<command>.md           # optional: slash commands with frontmatter (description, argument-hint)
  skills/<skill-name>/SKILL.md
  skills/<skill-name>/assets/     # optional: templates the skill writes out (HTML, md scaffolds)
  skills/<skill-name>/references/
pmm-define-and-review-positioning/ # plugin — six skills, no slash commands
  .claude-plugin/plugin.json
  skills/<skill-name>/SKILL.md
  skills/<skill-name>/references/
user-research/                    # plugin — six skills, no slash commands
  .claude-plugin/plugin.json
  skills/<skill-name>/SKILL.md
  skills/<skill-name>/references/
plg-growth/                       # plugin — fourteen skills, no slash commands
  .claude-plugin/plugin.json
  skills/<skill-name>/SKILL.md
  skills/<skill-name>/references/
```

Adding a plugin: create `<plugin>/.claude-plugin/plugin.json` and `<plugin>/skills/...` (plus `<plugin>/commands/...` if it exposes slash commands), then register it in the root `marketplace.json` `plugins` array with `name`, `source` (relative path), `description`, `version`.

## Skill contract

Every `SKILL.md` starts with YAML frontmatter:

- `name` — must match the directory name
- `description` — trigger phrases; this is what Claude Code matches against user intent to decide when to activate the skill. Be generous with phrasings.
- `user-invocable: true` — exposes the skill as `/skill-name` (optional — skills can also activate purely from description matching)
- `argument-hint` — shown in the slash-command picker

Skill bodies are prose instructions the model follows at activation time. They can reference sibling files via relative paths (e.g., `references/prd-template.md`, `assets/html-template.html`).

## Command contract

Slash commands live in `<plugin>/commands/<name>.md` with frontmatter:

- `description` — shown in the command picker and used for matching
- `argument-hint` — placeholder text for the argument field

The body is the prompt the command runs. `strategic-research/commands/strategic-research.md` is the working example.

## prd-workflow architecture

The three skills form a sequential pipeline that enriches a single `PRD-[feature-name].md` file in the user's working directory:

1. `prd-draft` — writes the initial PRD from messy input, using `references/prd-template.md`
2. `prd-evaluate` — runs gap analysis against `references/evaluation-checklist.md`; the user accepts/rejects findings, PRD is updated
3. `sit-beh` — runs Situation/Behaviour analysis on the PRD's situations section, adds new user stories and acceptance criteria; also writes to `.sitbeh/` in the user's working directory

Each skill's SKILL.md describes the handoff to the next. When editing one, keep the chaining instructions at the end of the file consistent with the others.

## strategic-research architecture

Five skills chained by YAML handoffs, orchestrated by the `/strategic-research` command. Each skill emits a markdown artifact plus a YAML handoff block the next skill parses:

1. `industry-process-map` — process tree + matrix of what end users do in the space
2. `audience-segment-research` — segments, stakeholders, tensions
3. `willingness-to-pay-research` — per-segment value, drivers, proof signals
4. `competitor-evaluation` — 7 Powers grid, strategy canvases
5. `strategic-synthesis-report` — consumes all four handoffs, renders a self-contained HTML report (plus a one-page markdown companion) using `assets/html-template.html`

The YAML handoff schemas are the contract between skills — they live under each skill's `references/handoff-schema.md`. Breaking a schema breaks the pipeline, so treat those files as load-bearing and bump `version` in `plugin.json` + `marketplace.json` when changing one.

Skills are also callable individually. The orchestrator command supports `--from=step-N` to resume mid-pipeline when upstream artifacts already exist.

## pmm-define-and-review-positioning architecture

Six skills forming a positioning toolkit based on the 5+1 framework (Competitive Alternatives → Unique Attributes → Value Themes → Target Market → Market Category → optional Trends):

1. `positioning-workshop` — full guided 10-step process producing a filled 5+1 canvas, narrative, and pressure test results
2. `positioning-review` — audits existing positioning against the 9-question pressure test; scores each component and prescribes fixes
3. `competitive-alternatives` — deep dive into Steps 4-6 (alternatives → attributes → value themes); produces YAML handoff for downstream skills
4. `market-frame-selector` — Step 8 decision tool: Head to Head vs Big Fish Small Pond vs Create a New Game
5. `sales-story-builder` — translates a completed canvas into a 7-stage sales narrative plus story-on-a-page
6. `positioning-orchestrator` — runs all skills in sequence (workshop → market frame → capture → sales story) with phase-boundary confirmations

Skills pass structured YAML between phases. Each skill is also callable standalone. Reference files under each skill's `references/` directory provide methodology detail, case studies, and scoring rubrics.

## user-research architecture

Six skills forming a paired build/evaluate pipeline for qualitative user research. Each phase produces a markdown artifact; the evaluate skill stress-tests it before the next phase begins:

1. `build-research-brief` — defines what to learn, from whom, and why; auto-detects research type (general, behavioral, or mixed)
2. `evaluate-research-brief` — scored evaluation with fatal-flaw gate, anti-pattern detection, and Mom Test check; verdict gates fieldwork
3. `build-research-guide` — translates brief into tactical interview guide with probes, timing, and dig triggers
4. `evaluate-research-guide` — validates guide quality, question phrasing, and structural coverage; verdict gates fieldwork
5. `analyze-research` — processes transcripts/notes into coded findings; behavioral mode adds COM-B coding and B=MAP analysis
6. `review-research-analysis` — evaluates analysis rigor, evidence backing, and failure patterns before the team acts on findings

Each skill loads methodology-specific references from its `references/` directory (`behavioral-*.md` and `general-*.md`). Skills are callable standalone or in sequence. No YAML handoff schema between skills — artifacts are markdown files the next skill reads directly.

## plg-growth architecture

Fourteen skills forming a comprehensive Product-Led Growth toolkit. A hub-and-spoke model with `plg-orchestrator` as the entry point that diagnoses current state and routes to specialized skills:

**Orchestration & Assessment:**
1. `plg-orchestrator` — entry point: diagnoses PLG maturity, builds issue tree, routes to the right skill(s)
2. `plg-readiness` — deep PLG fit assessment: suitability criteria, pillar maturity, PMF signals, competitive moats, decision-driver research
3. `plg-revenue-analysis` — revenue driver tree decomposition, sensitivity analysis, opportunity sizing

**Acquisition & Model Selection:**
4. `acquisition-domain` — product-led acquisition analysis: viral growth, product-driven SEO, sidecar products, signup optimization
5. `acquisition-model-selector` — choose between freemium, free trial, ungated, reverse trial, or self-service demo

**Core AARMS Domains (Analysis / Data Analysis / Work Plan modes):**
6. `activation-domain` — activation metric definition, aha moment identification, time-to-value optimization
7. `retention-domain` — 4-component retention model (activation, adoption, engagement, resurrection) with B=MAT and COM-B
8. `monetisation-domain` — pricing strategy, packaging, freemium conversion, ARPA growth, expansion revenue
9. `satisfaction-domain` — NPS/CSAT/CES analysis, PMF survey, satisfaction-to-retention correlation

**Cross-cutting Skills:**
10. `growth-loops` — design viral, content, paid, and sales loops with k-factor math and network effects analysis
11. `product-led-sales` — PQA/PQL scoring, sales pipeline from product signals, land-and-expand playbooks
12. `plg-experimentation` — experiment design with B=MAT behavioral science, sample size calculation, backlog prioritization
13. `plg-data-setup` — TASE framework (Track, Analyse, Sync, Experiment) for PLG data infrastructure design
14. `plg-transformation` — org transformation planning: strategic alignment, team design (OST), process design (Freedom Within Frame)

All skills share a unified structured problem-solving backbone: issue trees (MECE), hypothesis trees, driver disaggregation, 80/20 prioritization, Minto Pyramid synthesis, and hypothesis-driven work plans. Skills are callable standalone or via the orchestrator. No YAML handoff schemas between skills — the orchestrator routes by reading diagnostic context.

## Distribution

`main` is the published branch — pushing updates it live for anyone who has added the marketplace. Bump `version` in both the plugin's `plugin.json` and the matching entry in `marketplace.json` when shipping breaking changes to a skill or handoff schema.

## Ignored paths

`.remember/` is Claude session state (logs, tmp). Never commit it. `.DS_Store` is also gitignored. `strategic-research/working/` holds local draft artifacts and should stay out of commits.
