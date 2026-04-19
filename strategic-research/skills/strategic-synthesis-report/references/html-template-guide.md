# HTML Template Guide

The scaffold lives at `assets/html-template.html`. This guide explains how to fill it in without breaking the layout or the charts.

## Rendering model

The template uses `{{PLACEHOLDER}}` tokens that the skill replaces with real content. There are **three placeholder flavors**:

1. **Plain-text placeholders** — drop a string in. E.g., `{{ANCHOR_NAME}}`, `{{N_SEGMENTS}}`.
2. **HTML-fragment placeholders** — drop a block of HTML. E.g., `{{IPM_PROCESS_TREE_HTML}}`, `{{AUDIENCE_SEGMENT_CARDS_HTML}}`, `{{WHITESPACE_CARDS_HTML}}`.
3. **JSON-data placeholders** — drop a valid JSON literal. Used by the Chart.js initializers. E.g., `{{WTP_CHART_DATA_JSON}}`, `{{KANO_CHART_DATA_JSON}}`, `{{PROOF_CHART_DATA_JSON}}`, `{{STRATEGY_CANVAS_DATA_JSON}}`.

**Rule:** if a placeholder is not replaced, the file still parses — but the section will be empty or the chart will silently skip. Always replace every placeholder, even if the value is `"—"` or an empty array `[]`.

## Workflow

1. Read `assets/html-template.html` in full once before generating.
2. Build the data structures in memory from the four upstream handoffs.
3. Render each HTML fragment as a string.
4. Serialize JSON chart data with no trailing commas, no `undefined`, no comments.
5. Do a single whole-file `replace_all` pass per placeholder (or write a fresh file from scratch using the template as reference).
6. Before writing the final HTML: mentally walk the page from top to bottom and confirm every placeholder is filled.

## Data shapes for JSON placeholders

### `{{WTP_CHART_DATA_JSON}}`

```json
{
  "labels": ["S1 · Solo PMs", "S2 · Mid-market UA", "S3 · Agency leads"],
  "low":    [50, 180, 900],
  "high":   [120, 450, 3000],
  "unit":   "$/user/month"
}
```

- `labels`, `low`, `high` must be the same length.
- `unit` is a short human-readable string.
- Numbers are monthly dollars unless unit says otherwise.

### `{{KANO_CHART_DATA_JSON}}`

Stacked bar per segment, counts of each Kano class:

```json
{
  "labels":       ["S1", "S2", "S3"],
  "must":         [2, 3, 4],
  "performance":  [4, 2, 2],
  "delighter":    [1, 2, 1],
  "indifferent":  [1, 1, 0],
  "reverse":      [0, 0, 1]
}
```

### `{{PROOF_CHART_DATA_JSON}}`

Radar: one line per Leader outcome, 4 axes (vividness, speed, travelability, defensibility, each 0–5):

```json
{
  "labels": ["Vividness", "Speed", "Travelability", "Defensibility"],
  "series": [
    { "name": "Ship brief in under 30 min", "data": [4, 5, 3, 3] },
    { "name": "Never miss a follow-up",     "data": [3, 2, 4, 5] }
  ]
}
```

Cap at 5–7 series; any more and the radar becomes unreadable. If you have more Leaders, show top 5 by `opportunity_score` from WTP handoff.

### `{{STRATEGY_CANVAS_DATA_JSON}}`

Array. Each item = one canvas (one strategic group). The template's `{{STRATEGY_CANVAS_BLOCKS}}` placeholder injects the `<canvas>` elements; this JSON drives the radar.

```json
[
  {
    "canvasId": "canvas-g1-ai-schedulers",
    "title":    "Strategic group · AI schedulers",
    "factors":  ["Setup time", "Re-planning", "Admin view", "Privacy", "Mobile UX", "Price"],
    "series": [
      { "name": "Motion",     "data": [4, 5, 1, 2, 4, 3] },
      { "name": "Reclaim.ai", "data": [3, 4, 2, 3, 3, 3] },
      { "name": "Anchor",     "data": [2, 3, 4, 5, 2, 4], "isAnchor": true }
    ]
  }
]
```

- `canvasId` must match a `<canvas id="...">` injected via `{{STRATEGY_CANVAS_BLOCKS}}`.
- `isAnchor: true` renders a dashed white line so the anchor stands out.
- Keep factor count to 5–8 for readability.

### `{{STRATEGY_CANVAS_BLOCKS}}` (HTML fragment)

For each canvas, emit:

```html
<div class="chart-wrap">
  <h4>Strategic group · AI schedulers</h4>
  <div class="chart-canvas"><canvas id="canvas-g1-ai-schedulers"></canvas></div>
  <p class="faint">Factors plotted 0–5. Dashed white line = anchor's current position; lower = underserved.</p>
</div>
```

The skill emits one `<div class="chart-wrap">…</div>` per strategic group, concatenated as one string.

## HTML fragment shapes

### Process tree `{{IPM_PROCESS_TREE_HTML}}`

Nested `<li>` structure. Top-level steps carry `step-label top`, leaves carry `step-label leaf`:

```html
<li><span class="step-label top">Decide where to spend</span>
  <ul>
    <li><span class="step-label leaf">Review last week's cohort LTV</span></li>
    <li><span class="step-label leaf">Allocate by channel ROI</span></li>
  </ul>
</li>
<li><span class="step-label top">Brief &amp; produce creative</span>
  <ul>...</ul>
</li>
```

### Matrix rows `{{IPM_MATRIX_HEADERS}}` + `{{IPM_MATRIX_ROWS}}`

Headers are `<th>` cells. Rows are `<tr>` with the row label in the first cell, then one cell per column with a `.heat-N` class (0 = absent, 1 = manual, 2 = emerging, 3 = established, 4 = commodity, 5 = mature). Anchor cells get `.anchor` added (border highlight in CSS already present — or wrap content in a `<b>`).

Example:

```html
<!-- headers -->
<th>Apple Ads</th><th>Google UAC</th><th>Meta</th><th>TikTok</th><th>ASO</th>

<!-- rows -->
<tr>
  <td><b>Decide where to spend</b></td>
  <td class="heat-4">Commodity</td>
  <td class="heat-3">Established</td>
  <td class="heat-3">Established</td>
  <td class="heat-2">Emerging</td>
  <td class="heat-1">Manual</td>
</tr>
```

Add a small ★ or border for cells where the anchor plays: `<td class="heat-3"><b>Anchor ★</b></td>` — keep it lightweight.

### Segment cards `{{AUDIENCE_SEGMENT_CARDS_HTML}}`

One card per segment:

```html
<div class="seg-card">
  <div class="id">s1-high-volume-agencies</div>
  <div class="name">High-volume performance agencies</div>
  <div class="one-line">10+ client retainers, weekly creative refresh, full-funnel attribution.</div>
  <dl>
    <dt>Prevalence</dt><dd>~18% (conf 60%)</dd>
    <dt>Key jobs</dt><dd>Keep CPA stable across 12+ accounts</dd>
    <dt>Current alternatives</dt><dd>AppsFlyer + manual spreadsheet; Singular for enterprise</dd>
    <dt>Blocker</dt><dd>Agency head of ops — approval latency</dd>
    <dt>Confidence</dt><dd><span class="conf high"><span class="dot"></span>78%</span></dd>
  </dl>
</div>
```

### Whitespace cards `{{WHITESPACE_CARDS_HTML}}`

One card per ranked hypothesis. These are the headline of the cross-skill section — invest in them:

```html
<div class="ws-card">
  <div class="rank">#1 · Confidence 72%</div>
  <div class="hypothesis">Solo PMs will pay $80–120/mo for briefing automation that no current tool owns as a Leader.</div>
  <p class="dim">Non-consumption is growing in s1 (41% of forum threads describe "I just wing it"). Leader outcome "ship a brief in under 30 min" has opportunity_score 14. No 7 Powers competitor covers the matrix cell `brief-assembly | meeting-prep`.</p>
  <div class="ws-inputs">
    <div class="ws-input"><div class="key">Segment</div><div class="val">s1-solo-pms</div></div>
    <div class="ws-input"><div class="key">Leader</div><div class="val">ship-brief-30min</div></div>
    <div class="ws-input"><div class="key">Power gap</div><div class="val">Network, Switching</div></div>
    <div class="ws-input"><div class="key">Matrix cell</div><div class="val">brief-assembly|meeting-prep</div></div>
    <div class="ws-input"><div class="key">Non-consumption</div><div class="val">growing</div></div>
  </div>
</div>
```

### Segment affinity rows `{{COMP_AFFINITY_ROWS}}`

One row per segment. Each competitor column uses the `.aff-*` classes:

```html
<tr>
  <td><b>s1-solo-pms</b></td>
  <td><div class="aff-strong">STRONG</div></td>
  <td><div class="aff-weak">WEAK</div></td>
  <td><div class="aff-absent">—</div></td>
  <td><div class="aff-fit">FIT</div></td>
</tr>
```

### 7 Powers rows `{{COMP_POWERS_ROWS}}`

One row per competitor, 7 verdict cells:

```html
<tr>
  <td><b>Motion</b></td>
  <td><div class="verdict-na">N/A</div></td>
  <td><div class="verdict-na">N/A</div></td>
  <td><div class="verdict-asserted">ASSERTED</div></td>
  <td><div class="verdict-operational">OP. LEAD</div></td>
  <td><div class="verdict-asserted">ASSERTED</div></td>
  <td><div class="verdict-na">N/A</div></td>
  <td><div class="verdict-na">N/A</div></td>
</tr>
```

### Confidence pills `{{EVIDENCE_HONESTY_PARAGRAPH}}` and elsewhere

Use the `.conf` helper:

```html
<span class="conf high"><span class="dot"></span>80%</span>
<span class="conf med"><span class="dot"></span>55%</span>
<span class="conf low"><span class="dot"></span>25%</span>
```

Threshold guide: ≥ 70 = high, 40–69 = med, < 40 = low.

## Fallback stub (inputs missing)

If an upstream handoff is missing, the skill still emits a valid HTML file. Rules:

1. Uncomment the warning banner block in the template (remove the outer `<!-- -->`).
2. In every section that depends on the missing skill, render a single `<p class="dim">Unavailable — requires <code>{{skill-name}}</code> to be run first.</p>`.
3. The exec summary still runs and flags the incomplete state in the lead sentence.
4. The companion markdown summary file explicitly names the missing skill in its header.

## Color palette (design-tokens)

Defined in `:root` at the top of the template. Don't override inline — edit the token if a global change is needed.

| Token | Use |
|---|---|
| `--accent` | Primary highlight (bet cards, pills, chart lines) |
| `--accent-2` | Secondary highlight (chart fills, id badges) |
| `--good / --warn / --bad` | Traffic lights, confidence pills, risk cards |
| `--heat-0 … --heat-5` | Sequential heatmap (0 = absent, 5 = mature) |
| `--aff-strong / fit / weak / anti` | Segment affinity diverging scale |

## Accessibility

- Affinity and verdict classes each include a text label inside the colored pill. **Do not remove the label** — it is the color-blind fallback.
- Radar charts have a text table nearby (Leaders + proof signals table) so a screen-reader user can read the data even if the canvas is inaccessible.
- Do not rely on color alone anywhere. The `.heat-*` cells include text; the `.verdict-*` cells include the verdict word; the `.aff-*` cells include the grade.

## Print

The `@media print` block at the bottom of the template inverts the theme for printing (white background). All `.heat-*`, `.aff-*`, `.verdict-*` classes include `-webkit-print-color-adjust: exact` so colored cells survive printing. Test by opening the file in Chrome → Print → "Save as PDF" mentally before shipping.

## File size budget

A healthy synthesis report is 120–250 KB of HTML (everything inline). If the file balloons past 500 KB, the skill is dumping raw handoff text into the HTML instead of compressing it — go back to Phase 4 and tighten.
