# Human-Led Product Claude Plugins

A Claude Code plugin marketplace for product work — turning messy input into engineering-ready specs, and scoping new markets into boardroom-ready strategy, all grounded in real user behaviour.

## Install the marketplace

In Claude Code:

```
/plugin marketplace add kvaliotti/humanproduct
```

Then browse and install plugins:

```
/plugin install prd-workflow@human-led-product-claude-plugins
/plugin install strategic-research@human-led-product-claude-plugins
/plugin install pmm-define-and-review-positioning@human-led-product-claude-plugins
/plugin install user-research@human-led-product-claude-plugins
/plugin install plg-growth@human-led-product-claude-plugins
/plugin install event-tracking@human-led-product-claude-plugins
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
```

## Author

Konstantin Valiotti — [PM blog on Substack](https://kvaliotti.substack.com)
