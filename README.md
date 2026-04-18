# Human-Led Product Claude Plugins

A Claude Code plugin marketplace for product work — turning messy input into engineering-ready specs, grounded in real user behaviour.

## Install the marketplace

In Claude Code:

```
/plugin marketplace add kvaliotti/humanproduct
```

Then browse and install plugins:

```
/plugin install prd-workflow@human-led-product-claude-plugins
```

## Plugins

### prd-workflow

End-to-end PRD pipeline: draft from messy input, evaluate for gaps, then run Situation/Behaviour analysis to ground the spec in real user moments.

Includes three skills:
- **prd-draft** — structured PRD from unstructured input
- **prd-evaluate** — gap analysis across 12 categories
- **sit-beh** — situation/behaviour framework with product-led mechanisms

See [prd-workflow/README.md](./prd-workflow/README.md) for details.

## Repository layout

```
.claude-plugin/marketplace.json   # marketplace manifest
prd-workflow/                     # plugin
  .claude-plugin/plugin.json
  skills/
```

## Author

Konstantin Valiotti
