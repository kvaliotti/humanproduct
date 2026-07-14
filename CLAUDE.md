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
design-system-master/             # plugin — orchestrator + three skills (review/optimize/create design systems)
  .claude-plugin/plugin.json
  skills/<skill-name>/SKILL.md    # design-system-master (router), review-/optimize-/create-design-system
  skills/create-design-system/assets/DESIGN.template.md  # scaffold the create skill writes out
  references/                     # plugin-root shared refs (format, rubric, panel, a11y, patterns, archetypes, codebase-bridge)
  references/exemplars/           # 5 curated real DESIGN.md specs spanning the archetype range
designing-for-behaviour/          # plugin — orchestrator skill + FOUR analyst AGENTS (the marketplace's only agents-based plugin)
  .claude-plugin/plugin.json
  skills/designing-for-behaviour/SKILL.md   # orchestrator + /designing-for-behaviour entry point
  agents/<lens>-analyst.md        # behavioural-loop / cognitive-ease / capability-results / control-autonomy (read-only inspection)
  references/                     # plugin-root shared refs (foundations, scoring-rubric, 4 lens-*.md, ethics, coherence-and-anti-bloat, report-template)
user-story-review/                # plugin — one skill; user-story reviewer with a hard one-page output budget
  .claude-plugin/plugin.json
  skills/user-story-review/SKILL.md
  skills/user-story-review/references/   # review-rubric, output-contract, splitting-patterns (single-skill → per-skill, not plugin-root)
```

Note: `design-md-corpus/` at the repo root (74 product `DESIGN.md` files) is **grounding data, not a plugin** — it is untracked and must not be registered in `marketplace.json` or shipped. The `design-system-master` plugin distills it into `references/` + 5 curated `references/exemplars/`; it does not ship the full corpus.

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

## design-system-master architecture

An orchestrator + three capability skills that all read, write, or refactor a single canonical artifact — a **`DESIGN.md`** (the token-referencing `getdesign.md` format: YAML frontmatter of `colors`/`typography`/`rounded`/`spacing`/`components` with `{group.token}` refs, plus prose sections). The three capabilities map to the user's three asks:

1. `design-system-master` — router / `/design-system-master` entry point. Classifies intent (review / optimize / create) and input (a DESIGN.md / a codebase / nothing yet), then routes.
2. `review-design-system` — scored audit across three lenses (coordination A1–A5, ease-of-use B1–B6, cohesion C1–C5) gated by accessibility (real WCAG contrast math) and complexity-fit, then a five-lens expert panel. Produces a scorecard + top fixes + a "Keep" list.
3. `optimize-design-system` — improves the spec (consolidate/regularize/fill/fix) and/or retrofits it into a product codebase (extract de-facto tokens → emit CSS vars / Tailwind / Style Dictionary → codemod literals→tokens incrementally). Protects the signature.
4. `create-design-system` — builds a complete DESIGN.md from scratch, sized to the product's archetype, using `skills/create-design-system/assets/DESIGN.template.md`.

Distinctive design:

- **References live at the plugin root** (`references/`), not per-skill — all three capabilities share them (à la feature-flow / plg-growth). Skills point to them via `${CLAUDE_PLUGIN_ROOT}/references/...`. The set: `design-md-format.md`, `archetypes.md`, `patterns-{color,typography,space-shape-elevation,components-theming}.md`, `review-rubric.md`, `expert-panel.md`, `accessibility.md`, `codebase-bridge.md`, plus `exemplars/` (5 curated real specs). When moving/deleting a reference, grep the whole plugin for both `references/…` and `${CLAUDE_PLUGIN_ROOT}/…` forms and fix every pointer.
- **The anti-overfit invariant** — the load-bearing idea. Every skill classifies the product **archetype** first (`archetypes.md`) and judges complexity as **essential** (domain-required — keep) vs **accidental** (redundant/one-off/undocumented — remove). This is what stops the plugin from naively "simplifying" legitimate complexity (dual-coded green/red, dual font stacks, multi-surface theming, semantic ramps). `archetypes.md` is the most load-bearing reference; keep the essential-vs-accidental guide and the complexity budgets intact when editing.
- **Grounding, not shipped data** — `references/` and `exemplars/` are distilled from the `design-md-corpus/` (74 specs, untracked, repo root). Do not ship the full corpus in the plugin. The corpus specs are machine-reconstructed marketing-surface extractions with **no numeric contrast ratios** — so accessibility (real contrast math in `accessibility.md`) is the tool's own contribution, never something to claim the corpus already did.
- **Self-contained prose** (like the strategy plugins): no external runtime deps. It references an optional upstream linter (`npx @google/design.md lint`) and, when applying to a codebase, reads/writes real files — but degrades to prose guidance if neither is present.

## designing-for-behaviour architecture

A behavioural-design **reviewer** (evaluate + recommend, does NOT implement). One orchestrator skill drives a board of **four read-only lens-analyst agents** — this is the marketplace's only plugin that ships an `agents/` directory (all others are skills-only). It reviews either an existing product/codebase OR an idea/PRD, and answers: how well does this drive **behaviour, adoption, engagement**, where are the gaps, and what integrated set of fixes strengthens one coherent core experience rather than bloating it.

Pipeline (in `skills/designing-for-behaviour/SKILL.md`): intake (codebase or PRD, once, shared) → dispatch 4 lenses **in parallel** (one message, 4 `Task` calls) → roll up score across 3 dimensions → rank gaps → **coherence & anti-bloat review** → report (`behaviour-review-[target].md` + inline summary).

Distinctive design:

- **Six books → four de-duplicated lenses.** The six source books (Atomic Habits, Tiny Habits, Hooked, Badass, Thinking Fast and Slow, Perceptual Control Theory) each repeated the same surface sections (behaviour-definition, adoption, engagement, metrics, ethics). Those are factored out **once** into cross-cutting refs; the three habit books (~70% overlap) merge into one loop lens. The four lenses are: `behavioural-loop-analyst` (Atomic/Tiny/Hooked), `cognitive-ease-analyst` (Kahneman), `capability-results-analyst` (Badass), `control-autonomy-analyst` (PCT + anti-manipulation). When editing a lens, keep it in its lane — the `foundations.md` "what each lens owns / not your lens" carve-up is what prevents the redundant 6× analysis the plugin exists to avoid.
- **References at the plugin root** (à la feature-flow / plg-growth), shared by the skill AND the agents via `${CLAUDE_PLUGIN_ROOT}/references/...`: `foundations.md` (defs + intake), `scoring-rubric.md` (unified 0/1/2/N-A scale), `lens-{behavioural-loop,cognitive-ease,capability-results,control-autonomy}.md`, `ethics-and-dark-patterns.md`, `coherence-and-anti-bloat.md`, `report-template.md`. Agents stay thin and read their one lens ref at runtime. When moving/deleting a ref, grep the whole plugin for both `references/…` and `${CLAUDE_PLUGIN_ROOT}/…` forms.
- **The anti-bloat coherence review is the load-bearing idea** (`coherence-and-anti-bloat.md`) — the editorial pass that turns four lenses' worth of good-but-additive recommendations into the smallest integrated set, enforces a complexity budget calibrated to the archetype, prefers embedding over adding, runs a subtraction pass, and emits an explicit "deliberately NOT adding" list. Without it a behavioural checklist makes products worse. Keep it, and the N/A scoring discipline that feeds it, intact.
- **Anti-slop + ethics by contract.** Every score/gap/rec must carry a concrete anchor (screen/flow/`file:line`/quoted copy/PRD section); the ethics gate (`ethics-and-dark-patterns.md`) reframes or cuts any manipulative recommendation, and autonomy wins conflicts. Self-contained prose, read-only agents, no external runtime deps.

## user-story-review architecture

One skill (`/user-story-review`) that reads a PRD/backlog and reviews its user stories. Deliberately the smallest plugin here — its design is mostly about what it *refuses* to emit.

Pipeline in `skills/user-story-review/SKILL.md`: find input (arg → newest `PRD-*.md` → any backlog-shaped file → ask) → read PRD context → classify every item into one of five verdicts (READY / NEEDS CONVERSATION / REFRAME / SPLIT-EXPERIMENT / NOT A USER STORY) against the six gates → **triage** → emit.

- **The output budget is the load-bearing idea.** `references/output-contract.md` caps the review at ~1 page: verdict + at most **three** systemic issues + one table row per story + rewrites for the **worst three only**, then a footer naming what's being withheld (splitting options, full question list, non-story work). Depth is pull, never push. The original skill mandated 8 sections including chapter citations, which on a 30-story PRD produced ~10 pages — i.e. it moved the work instead of doing it. **Do not reintroduce sections, raise the caps, or let the rubric be transcribed into the output.** If editing makes the review longer, it is a regression.
- **Substance over syntax.** The reviewer judges whether a story is true and useful, never template compliance; nonstandard syntax is explicitly not a finding, and wording is not reportable unless it causes real misunderstanding.
- **The causal chain is the analytical spine** (`references/review-rubric.md`): observable system change (team's *zone of control*) → user behaviour change (*sphere of influence*) → business impact. Most findings are a symptom of collapsing it. The rubric is a lookup keyed by gate, not a script to walk aloud.
- **No numeric score, ever** — the pattern of failure matters more than arithmetic, and a score hides the failure *type*. Same reason the plugin refuses to force tasks, NFRs, research, or cross-cutting work into fake user stories.
- **Missing context is a finding, not a blank to fill.** Verdict becomes "Not reviewable yet"; never invent a segment or metric to enable a rewrite.
- References are **per-skill** (`skills/user-story-review/references/`), not plugin-root — correct here because there is only one skill (à la cro-engine). If a second skill lands and shares them, move them to the plugin root and switch pointers to `${CLAUDE_PLUGIN_ROOT}/references/…`.
- Grounding: *Fifty Quick Ideas to Improve Your User Stories* (Adzic/Evans/Korac). Distilled into the rubric and splitting patterns; the book's chapter list and per-finding chapter citations were **deliberately cut** (they consumed output space and helped no reader). Don't re-add a traceability file or chapter numbers.
- Chains off `prd-workflow` by **filename convention** — it auto-discovers the `PRD-[feature-name].md` that `prd-draft` writes, as the last gate before engineering. Keep that glob working if the PRD filename convention changes.

## Distribution

`main` is the published branch — pushing updates it live for anyone who has added the marketplace. Bump `version` in both the plugin's `plugin.json` and the matching entry in `marketplace.json` when shipping breaking changes to a skill or handoff schema.

## Ignored paths

`.remember/` is Claude session state (logs, tmp). Never commit it. `.DS_Store` is also gitignored. `strategic-research/working/` holds local draft artifacts and should stay out of commits. `design-md-corpus/` (74 real `DESIGN.md` specs) is gitignored grounding data for the `design-system-master` plugin — it is not a plugin and must not be committed or shipped; the plugin distills it into `design-system-master/references/` + `references/exemplars/`. (The `designing-for-behaviour` plugin was similarly distilled from 6 behavioural-science books into its `references/`; that raw grounding was consumed during authoring and is not retained in the repo.)
