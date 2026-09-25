---
description: Run the strategic-research pipeline on a product, category, or industry - process map, segments, willingness to pay, competitors, then a one-page recommendation. Resume with --from=N.
argument-hint: "[product, category, or industry] [optional: --from=N to resume at step N]"
---

# /strategic-research

Anchor: `$ARGUMENTS`.

Run these skills in order. Each writes one file to `strategic-research/` and reads the files before it.

| Step | Skill | File |
|---|---|---|
| 1 | industry-process-map | `01-industry-process-map.md` |
| 2 | audience-segment-research | `02-audience-segments.md` |
| 3 | willingness-to-pay-research | `03-willingness-to-pay.md` |
| 4 | competitor-evaluation | `04-competitor-evaluation.md` |
| 5 | strategic-synthesis-report | `05-summary.md` |

- If the anchor is ambiguous (what product, B2B or B2C), ask at most 2 questions with AskUserQuestion. Otherwise state assumptions and start.
- `--from=N`: start at step N. If an earlier file is missing, name it and ask whether to run that step first.
- After each step, print one line: `✓ Step N · <skill> → strategic-research/<file>`. No other prose between steps.
- At the end, show the summary's **The answer** section and the file path.
