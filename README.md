# Human-Led Product Claude Plugins

A Claude Code plugin marketplace for product work — turning messy input into engineering-ready specs, scoping new markets into boardroom-ready strategy, shipping features from description to PR, and reviewing, optimising, or building design systems, all grounded in real user behaviour.

## Install the marketplace

In Claude Code:

```
/plugin marketplace add kvaliotti/humanproduct
```

Then browse and install plugins:

```
/plugin install prd-workflow@human-led
/plugin install strategic-research@human-led
/plugin install pmm-define-and-review-positioning@human-led
/plugin install user-research@human-led
/plugin install plg-growth@human-led
/plugin install event-tracking@human-led
/plugin install feature-flow@human-led
/plugin install cro-engine@human-led
/plugin install design-system-master@human-led
/plugin install designing-for-behaviour@human-led
/plugin install user-story-review@human-led
```

## Plugins

### prd-workflow

End-to-end PRD pipeline: draft from messy input, evaluate for gaps, then run Situation/Behaviour analysis to ground the spec in real user moments.

Three skills:
- **prd-draft** — structured PRD from unstructured input
- **prd-evaluate** — gap analysis across 12 categories
- **sit-beh** — situation/behaviour framework with product-led mechanisms

See [prd-workflow/README.md](./prd-workflow/README.md) for details.

### strategic-research

Five-skill strategic research pipeline that turns a product, category, or industry name into a full strategic picture — ending in a self-contained HTML report a CPO can read in one sitting.

Run the whole pipeline with `/strategic-research <anchor>`, or call any skill standalone:

1. **industry-process-map** — what end users actually do (process tree + matrix)
2. **audience-segment-research** — segments, stakeholders, tensions
3. **willingness-to-pay-research** — per-segment value, drivers, proof signals
4. **competitor-evaluation** — 7 Powers grid and strategy canvases
5. **strategic-synthesis-report** — cross-skill synthesis as a self-contained HTML report

Skills chain via YAML handoffs, so they compose cleanly and you can resume the pipeline mid-way with `--from=step-N`.

See [strategic-research/README.md](./strategic-research/README.md) for details.

### pmm-define-and-review-positioning

Product positioning toolkit grounded in the 5+1 positioning framework. Define positioning through a guided workshop, audit existing positioning, or go deep on specific steps.

Six skills:
- **positioning-workshop** — full guided 10-step positioning process
- **positioning-review** — audit and stress-test existing positioning
- **competitive-alternatives** — deep dive into alternatives, attributes, and value themes
- **market-frame-selector** — choose between Head to Head / Big Fish Small Pond / Create a New Game
- **sales-story-builder** — 7-stage sales narrative from completed positioning
- **positioning-orchestrator** — end-to-end pipeline running all skills in sequence

See [pmm-define-and-review-positioning/README.md](./pmm-define-and-review-positioning/README.md) for details.

### user-research

End-to-end user research workflow — from scoping what to learn, through fieldwork prep, to analysis and review. Supports both general research (discovery, validation, exploratory) and behavioral research (COM-B, B=MAP) methodologies.

Six skills in three paired build/evaluate phases:
- **build-research-brief** — structured research brief from a business problem
- **evaluate-research-brief** — stress-test the brief before fieldwork
- **build-research-guide** — convert brief into interview guide with probes and timing
- **evaluate-research-guide** — validate guide quality and Mom Test compliance
- **analyze-research** — process transcripts into coded findings and recommendations
- **review-research-analysis** — evaluate analysis rigor and evidence before decisions

See [user-research/README.md](./user-research/README.md) for details.

### plg-growth

Product-Led Growth toolkit — assess readiness, decompose revenue, choose acquisition models, run domain-specific analysis across the full AARMS funnel, design growth loops, operationalize product-led sales, and plan org transformation. All grounded in structured problem solving and proven PLG frameworks.

Fourteen skills organized as a hub-and-spoke model:

**Orchestration & Assessment:**
- **plg-orchestrator** — entry point: diagnoses PLG maturity and routes to the right skill(s)
- **plg-readiness** — deep PLG fit assessment with suitability criteria, pillar maturity, and PMF signals
- **plg-revenue-analysis** — revenue driver tree decomposition with sensitivity analysis

**Acquisition & Model Selection:**
- **acquisition-domain** — product-led acquisition analysis (viral, SEO, sidecar products, signup optimization)
- **acquisition-model-selector** — choose between freemium, free trial, ungated, reverse trial, or self-service demo

**Core AARMS Domains:**
- **activation-domain** — activation metric definition, aha moment identification, time-to-value optimization
- **retention-domain** — 4-component retention model with behavioral science (B=MAT, COM-B)
- **monetisation-domain** — pricing strategy, packaging, freemium conversion, ARPA growth
- **satisfaction-domain** — NPS/CSAT/CES analysis, PMF survey, satisfaction-to-retention correlation

**Cross-cutting:**
- **growth-loops** — viral, content, paid, and sales loops with k-factor math
- **product-led-sales** — PQA/PQL scoring, pipeline from product signals, land-and-expand
- **plg-experimentation** — experiment design with B=MAT behavioral science
- **plg-data-setup** — TASE framework for PLG data infrastructure design
- **plg-transformation** — org transformation: strategic alignment, team design, process design

### event-tracking

Analytics event tracking toolkit — define what to track, how to name it, and how to ship it to your analytics platform. Four-stage pipeline from analytical questions to platform-ready implementation specs.

Five skills:
- **tracking-orchestrator** — entry point: assesses current state and routes to the right stage
- **analytics-use-cases** — define stakeholder questions, dashboards, and analysis types before naming any events
- **event-definition** — concrete event specs with names, properties, firing conditions, and user properties
- **tracking-plan-review** — audit existing tracking for naming consistency, coverage gaps, redundancy, and platform compliance
- **platform-formatter** — generate platform-specific names, payloads, and SDK code for Amplitude, Mixpanel, PostHog, Segment, or GA4

See [event-tracking/README.md](./event-tracking/README.md) for details.

### feature-flow

The one engineering-delivery plugin in the set. An end-to-end feature workflow — one command takes a rough description to an open PR, sequencing the pieces you already have (plan approval, subagents, `/code-review`, `/simplify`, commit/PR) behind a lean, consistent spine.

```
/ship <feature description> [--step] [--auto] [--micro|--big]
```

Four skills:
- **ship** — orchestrator: branch → design → plan → ⛱ approval gate → implement → verify → review/simplify → PR
- **storm** — Stage-1 design: brainstorm spine + a compact product lens (situation, behaviour, barriers, edge cases)
- **verify** — evidence-based gate that runs the right subset of checks by what changed and pastes real output
- **debug** — root-cause debugging: confirm intended behaviour, find the root cause, then fix at the source

Autonomous after plan approval by default (halting only on a stop-condition), or `--step` to pause at each stage. The spine is generic; per-repo behaviour (verify commands, test policy, stop-conditions, PR settings) comes from a `.claude/feature-flow.local.md` config the plugin offers to create on first run.

Requires: `git` and the GitHub CLI (`gh`, authenticated) for the PR stage. Verify commands default to a Node/npm toolchain if you don't provide a config — set your own in `.claude/feature-flow.local.md` for non-Node projects.

See [feature-flow/README.md](./feature-flow/README.md) for details.

### cro-engine

A conversion-rate-optimization reviewer — audits and improves landing pages, signup flows, paywalls, popups, onboarding, and forms against a library of CRO best-practice patterns and an expert-panel review gate.

One skill (`cro-engine`) backed by pattern references for pages, signup, paywalls, popups, onboarding, and forms.

### design-system-master

Your design-system master — review an existing design system, optimise one (including retrofitting it into a product codebase), or build one from scratch as a lintable `DESIGN.md`. Grounded in a corpus of 74 real-world design systems (minimal dev-tools → dense financial/enterprise → expressive consumer/automotive), with a complexity-calibration gate so it never naively simplifies complexity a domain legitimately needs (dual-coded green/red, dual font stacks, multi-surface theming, semantic ramps).

An orchestrator plus three skills:
- **design-system-master** — entry point / router: diagnoses whether you need review, optimize, or create, and what input you have
- **review-design-system** — scored audit across coordination, ease-of-use, and cohesion, gated by real WCAG contrast math and complexity-fit, then a five-lens expert panel
- **optimize-design-system** — consolidate tokens, fill gaps, fix contrast, and/or roll the system into a codebase (CSS variables / Tailwind / Style Dictionary), protecting the signature
- **create-design-system** — build a complete `DESIGN.md` from scratch, sized to the product's archetype

Run the router with `/design-system-master`, or call any skill standalone. See [design-system-master/README.md](./design-system-master/README.md) for details.

### designing-for-behaviour

A behavioural-design reviewer — point it at a codebase or at an idea/PRD and it answers: how well does this drive behaviour, adoption, and engagement, where are the gaps, and what integrated set of fixes strengthens one coherent core experience rather than bloating it.

An orchestrator skill driving four read-only analyst agents in parallel (the only agents-based plugin here):
- **behavioural-loop-analyst** — trigger → action → reward → investment (Atomic Habits, Tiny Habits, Hooked)
- **cognitive-ease-analyst** — System 1/2, friction, framing, defaults, peak-end (Thinking, Fast and Slow)
- **capability-results-analyst** — does the user get more capable and get results they care about (Badass)
- **control-autonomy-analyst** — what the user is trying to control, plus the anti-manipulation backbone (Perceptual Control Theory)

Six books collapse into four de-duplicated lenses, then an **anti-bloat coherence review** turns four lenses' worth of additive suggestions into the smallest integrated set — with an explicit "deliberately NOT adding" list. Run with `/designing-for-behaviour`.

### user-story-review

Reviews the user stories in a PRD or backlog and hands back **one page**: the few things that will sink the milestone, a verdict per story, and rewrites for the worst offenders. Depth on request — a review you have to work through is not a review, it's a new task.

One skill (`user-story-review`), backed by a six-gate rubric and ten value-oriented splitting patterns.

It reads the whole PRD before judging any story, doesn't reward template compliance, separates the causal chain (system change the team *controls* → behaviour change it *influences* → business impact it *contributes to*), names the work that shouldn't be a user story at all, and refuses to emit a quality score. Grounded in *Fifty Quick Ideas to Improve Your User Stories*.

```
/user-story-review              # auto-discovers the newest PRD-*.md
```

Pairs with `prd-workflow` as the last gate before engineering. See [user-story-review/README.md](./user-story-review/README.md) for details.

## Repository layout

```
.claude-plugin/marketplace.json   # marketplace manifest
prd-workflow/                     # plugin
  .claude-plugin/plugin.json
  skills/
strategic-research/               # plugin
  .claude-plugin/plugin.json
  commands/strategic-research.md  # /strategic-research orchestrator
  skills/
pmm-define-and-review-positioning/ # plugin
  .claude-plugin/plugin.json
  skills/
user-research/                    # plugin
  .claude-plugin/plugin.json
  skills/
plg-growth/                       # plugin
  .claude-plugin/plugin.json
  skills/
event-tracking/                   # plugin
  .claude-plugin/plugin.json
  skills/
feature-flow/                     # plugin
  .claude-plugin/plugin.json
  skills/                         # ship, storm, verify, debug
  references/                     # stop-conditions, test-policy, squash-safe-finish
  config/                         # feature-flow.config.example.md
cro-engine/                       # plugin
  .claude-plugin/plugin.json
  skills/cro-engine/              # SKILL.md + CRO pattern references
design-system-master/             # plugin
  .claude-plugin/plugin.json
  skills/                         # design-system-master (router), review-/optimize-/create-design-system
  references/                     # format, rubric, expert-panel, accessibility, patterns, archetypes, codebase-bridge
  references/exemplars/           # 5 curated real DESIGN.md specs spanning the archetype range
designing-for-behaviour/          # plugin
  .claude-plugin/plugin.json
  skills/designing-for-behaviour/ # orchestrator + /designing-for-behaviour entry point
  agents/                         # 4 read-only lens analysts, run in parallel
  references/                     # foundations, scoring rubric, 4 lens refs, ethics, coherence-and-anti-bloat
user-story-review/                # plugin
  .claude-plugin/plugin.json
  skills/user-story-review/       # SKILL.md + rubric, output contract, splitting patterns
```

## Author

Konstantin Valiotti — [PM blog on Substack](https://kvaliotti.substack.com)
