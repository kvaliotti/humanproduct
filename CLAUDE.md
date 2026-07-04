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
event-tracking/                   # plugin — five skills, no slash commands
  .claude-plugin/plugin.json
  skills/<skill-name>/SKILL.md
  skills/<skill-name>/references/
feature-flow/                     # plugin — four skills; engineering-delivery workflow
  .claude-plugin/plugin.json
  skills/<skill-name>/SKILL.md    # ship, storm, verify, debug (ship = /ship entry point)
  references/                     # plugin-root references (NOT per-skill): stop-conditions, test-policy, squash-safe-finish
  config/feature-flow.config.example.md  # copied into a target repo as .claude/feature-flow.local.md
cro-engine/                       # plugin — one skill; conversion-rate-optimization reviewer
  .claude-plugin/plugin.json
  skills/cro-engine/SKILL.md
  skills/cro-engine/references/   # CRO pattern libraries + expert-panel-review
```

Adding a plugin: create `<plugin>/.claude-plugin/plugin.json` and `<plugin>/skills/...` (plus `<plugin>/commands/...` if it exposes slash commands), then register it in the root `marketplace.json` `plugins` array with `name`, `source` (relative path), `description`, `version`.

## Skill contract

Every `SKILL.md` starts with YAML frontmatter:

- `name` — must match the directory name
- `description` — trigger phrases; this is what Claude Code matches against user intent to decide when to activate the skill. Be generous with phrasings.
- `user-invocable: true` — exposes the skill as `/skill-name` (optional — skills can also activate purely from description matching)
- `argument-hint` — shown in the slash-command picker

Skill bodies are prose instructions the model follows at activation time. They can reference sibling files via relative paths (e.g., `references/prd-template.md`, `assets/html-template.html`).

**Shared references (cross-skill).** When a reference is used by more than one skill in a plugin, it lives once at the plugin root (`<plugin>/references/…`) and skills point to it with the absolute plugin variable `${CLAUDE_PLUGIN_ROOT}/references/<file>.md` — not a per-skill copy. This is the standard for de-duplicated content across the marketplace (e.g. `plg-growth/references/problem-solving-backbone.md`, `user-research/references/behavioral-frameworks.md`, `strategic-research/references/tension-taxonomy.md`, `event-tracking/references/platform-constraints.md`, and all of `feature-flow/references/`). Keep single-skill references under that skill's own `references/`. When you delete or move a reference, grep the whole plugin for its path (both `references/…` and `${CLAUDE_PLUGIN_ROOT}/…` forms) and fix every pointer.

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

Artifacts are written to a `strategic-research/` subfolder of the user's current working directory under **fixed step-numbered filenames** (`01-industry-process-map.md` … `05-synthesis-report.html`), so each skill reads the prior one's output and `--from` resume is deterministic. Do not reintroduce derived/slug filenames or absolute sandbox paths here — that broke the chain historically. The synthesis HTML is genuinely self-contained: Chart.js is vendored inline in `assets/html-template.html` (no CDN/network), and shared prose (tension taxonomy, writing conventions) lives in `references/tension-taxonomy.md` and `references/common-conventions.md`.

## pmm-define-and-review-positioning architecture

Six skills forming a positioning toolkit based on the 5+1 framework (Competitive Alternatives → Unique Attributes → Value Themes → Target Market → Market Category → optional Trends):

1. `positioning-workshop` — full guided 10-step process producing a filled 5+1 canvas, narrative, and pressure test results
2. `positioning-review` — audits existing positioning against the 9-question pressure test; scores each component and prescribes fixes
3. `competitive-alternatives` — deep dive into Steps 4-6 (alternatives → attributes → value themes); produces YAML handoff for downstream skills
4. `market-frame-selector` — Step 8 decision tool: Head to Head vs Big Fish Small Pond vs Create a New Game
5. `sales-story-builder` — translates a completed canvas into a 7-stage sales narrative plus story-on-a-page
6. `positioning-orchestrator` — runs all skills in sequence (workshop → market frame → capture → sales story) with phase-boundary confirmations

Skills pass structured YAML between phases. Each skill is also callable standalone. Reference files provide methodology detail, case studies, and scoring rubrics; content shared across skills (the three positioning styles, the case-study set, the 9-question pressure test) is consolidated into plugin-root `references/` (`three-styles.md`, `case-studies.md`, `pressure-test.md`) rather than duplicated per skill. When run under `positioning-orchestrator`, `positioning-workshop` stops after Step 7 and emits the `phase_1_output` YAML the orchestrator consumes.

## user-research architecture

Six skills forming a paired build/evaluate pipeline for qualitative user research. Each phase produces a markdown artifact; the evaluate skill stress-tests it before the next phase begins:

1. `build-research-brief` — defines what to learn, from whom, and why; auto-detects research type (general, behavioral, or mixed)
2. `evaluate-research-brief` — scored evaluation with fatal-flaw gate, anti-pattern detection, and Mom Test check; verdict gates fieldwork
3. `build-research-guide` — translates brief into tactical interview guide with probes, timing, and dig triggers
4. `evaluate-research-guide` — validates guide quality, question phrasing, and structural coverage; verdict gates fieldwork
5. `analyze-research` — processes transcripts/notes into coded findings; behavioral mode adds COM-B coding and B=MAP analysis
6. `review-research-analysis` — evaluates analysis rigor, evidence backing, and failure patterns before the team acts on findings

Each skill loads methodology-specific references from its `references/` directory (`behavioral-*.md` and `general-*.md`); the shared COM-B/B=MAP primer and the research-type signal list are factored into plugin-root `references/behavioral-frameworks.md` and `references/research-type-detection.md`. No YAML handoff schema between skills, so chaining relies on **filename convention**: producers write `research-brief-[topic].md` / `research-guide-[topic].md` / `research-analysis-[topic].md` and stamp a `Research Type:` field into the artifact; consumers discover the input by that glob (newest first) and trust the stamped type rather than re-detecting. Keep those filename patterns and the type stamp stable — they are the de-facto contract. Skills are callable standalone or in sequence.

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

All skills share a unified structured problem-solving backbone: issue trees (MECE), hypothesis trees, driver disaggregation, 80/20 prioritization, Minto Pyramid synthesis, and hypothesis-driven work plans. That backbone lives once in `references/problem-solving-backbone.md` (each skill carries a one-line summary + a `${CLAUDE_PLUGIN_ROOT}` pointer, not a verbatim copy); the shared work-plan skeleton (`references/work-plan-template.md`) and team-structuring guidance (`references/team-structuring.md`) are likewise plugin-root references, while each domain skill keeps its own `references/work-plan-examples.md`. `plg-orchestrator` must route to all 13 spokes by their real skill names (no "[future skill]" placeholders). The heavyweight domain skills expose a "Quick Answer Mode" so a simple question doesn't force the full ritual. Skills are callable standalone or via the orchestrator. No YAML handoff schemas between skills — the orchestrator routes by reading diagnostic context.

## event-tracking architecture

Five skills forming a four-stage pipeline for analytics event tracking. The orchestrator assesses current state and routes to the appropriate stage — users can enter at any point:

1. `tracking-orchestrator` — entry point: gathers product context, detects existing naming conventions (from analytics tools or codebase), and routes to the right stage
2. `analytics-use-cases` — defines stakeholder questions, analysis types (funnel, retention, segmentation, etc.), dashboard specs, and conceptual event requirements before any events are named
3. `event-definition` — converts use cases into concrete event specs: names, properties, firing conditions, user/group properties, PII classification, and sample payloads. Uses `references/naming-conventions.md`, `references/property-patterns.md`, `references/decision-framework.md`, and the shared `${CLAUDE_PLUGIN_ROOT}/references/platform-constraints.md`
4. `tracking-plan-review` — audits existing tracking across 7 dimensions (naming consistency, coverage, redundancy, property quality, platform compliance, user properties, firing clarity) with a scored report. Uses the shared `${CLAUDE_PLUGIN_ROOT}/references/platform-constraints.md`
5. `platform-formatter` — generates platform-specific event names, property formats, sample payloads, and SDK code snippets for Amplitude, Mixpanel, PostHog, Segment, and GA4. Uses `references/platform-formats.md`

Key design decisions: events must trace to analytical use cases; parameterization test (one event with properties vs. multiple events) is the primary design tool; platform constraints are validated during event definition, not just at formatting time; naming conventions are detected from existing tracking and matched, not imposed. Vendor limits live in ONE place — the shared plugin-root `references/platform-constraints.md` (single source of truth; carries a "verify against current vendor docs" hedge because these change). `event-definition` and `tracking-plan-review` each offer a quick mode for small/ad-hoc scope. No YAML handoff schemas between skills — artifacts are markdown files the next skill reads directly.

## feature-flow architecture

The one engineering-delivery plugin (the others are product-strategy). Four skills orchestrated by `/ship`, which sequences a feature from a rough description to an open PR:

1. `ship` — the orchestrator and `/ship` entry point. Stages: branch/isolation → design (calls `storm`) → plan (strong model) → **approval gate** → implement → verify (calls `verify`) → review/simplify → PR → finish. Reuses native capabilities (plan approval, `/code-review`, `/simplify`, `commit-commands`) rather than reimplementing them.
2. `storm` — Stage-1 design: brainstorm spine + a compact product lens (situation, target behaviour, don't-know/don't-want/can't barriers, edge cases). Micro and big modes. Reads a `.sitbeh/` dir as the product lens if present.
3. `verify` — read-only evidence-based gate. Runs the right subset (typecheck / lint / targeted tests / arch-checks / build) by what changed and pastes real output. Diagnoses nothing itself; a failure hands off to `debug`.
4. `debug` — root-cause debugging (Iron Law: no fix without confirmed intended behaviour AND root cause). Invoked by `ship` when verify fails; also standalone. Ships supporting technique files (`root-cause-tracing.md`, `defense-in-depth.md`, `condition-based-waiting.*`, `find-polluter.sh`) under `skills/debug/`.

Distinctive design vs. the other plugins:

- **References live at the plugin root** (`references/`, `config/`, `scripts/`), not under each skill — because `ship`, `verify`, and `storm` all read the same `stop-conditions.md`, `test-policy.md`, and `squash-safe-finish.md`. Skills reference them via `${CLAUDE_PLUGIN_ROOT}/references/...`.
- **Generic spine, per-repo config**: no project specifics are hardcoded. Behaviour (verify commands, model tiers, test policy, stop-conditions, PR settings) comes from a `.claude/feature-flow.local.md` the target repo owns (gitignored there). `config/feature-flow.config.example.md` is the template `/ship` offers to copy on first run. When editing the plugin, keep example config keys, the `ship` Stage-0 parser, and the `verify`/`stop-conditions`/`test-policy` references in sync — they are the contract.
- **Autonomy is gated by stop-conditions**: `auto` mode runs implement→PR without pausing except on a stop-condition (`references/stop-conditions.md`), which are always *added to*, never replaced by, the repo's list. The plan-approval gate (Stage 4) is the one mandatory checkpoint in both modes.
- **Subagent-driven implementation (no Workflow tool)**: Stage 5 hands all writing to implementer subagents via the `Task` tool — parallel Task calls (multiple in one message) for independent disjoint-file tasks, one subagent for coupled tasks — to keep the orchestrator's context clean for gating and debugging. Inline editing is reserved for the rare truly-trivial change; when in doubt, dispatch a subagent. There is deliberately **no dependency on the `Workflow` tool** (it over-spawns) — do not reintroduce it.
- **External dependencies** (unlike the strategy plugins, which are self-contained prose): `git` + `gh` for the PR/finish stages (both degrade gracefully if `gh` is absent — push + print a compare URL). Verify's fallback defaults assume a Node/npm/Jest toolchain and are guarded so non-Node repos are detected or the user is asked, rather than running `npm` blindly.

## Distribution

`main` is the published branch — pushing updates it live for anyone who has added the marketplace. Bump `version` in both the plugin's `plugin.json` and the matching entry in `marketplace.json` when shipping breaking changes to a skill or handoff schema.

## Ignored paths

`.remember/` is Claude session state (logs, tmp). Never commit it. `.DS_Store` is also gitignored. `strategic-research/working/` holds local draft artifacts and should stay out of commits.
