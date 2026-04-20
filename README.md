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
```

## Author

Konstantin Valiotti
