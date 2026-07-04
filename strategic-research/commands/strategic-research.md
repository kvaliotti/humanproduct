---
description: Run the full strategic-research pipeline (5 skills) end-to-end on a given anchor, or resume from a specific step. Produces four markdown artifacts plus one self-contained HTML synthesis report.
argument-hint: "[anchor name or product/industry] [optional: --from=step-N to resume]"
---

# /strategic-research

Orchestrate the full five-skill strategic-research pipeline. Each step consumes the upstream YAML handoff and writes one markdown artifact. The final step also writes a self-contained HTML report.

## Pipeline

```
1. industry-process-map        → strategic-research/01-industry-process-map.md      (+ YAML handoff)
2. audience-segment-research   → strategic-research/02-audience-segments.md         (+ YAML handoff)
3. willingness-to-pay-research → strategic-research/03-willingness-to-pay.md        (+ YAML handoff)
4. competitor-evaluation       → strategic-research/04-competitor-evaluation.md     (+ YAML handoff)
5. strategic-synthesis-report  → strategic-research/05-synthesis-report.html + .md  (final deliverable)
```

All artifacts land in a `strategic-research/` subfolder of the current working directory, under fixed step-numbered names (see `${CLAUDE_PLUGIN_ROOT}/references/common-conventions.md`).

## Arguments

- `$1` — the anchor. Can be a product name ("SplitMetrics"), a category ("mobile ad optimization"), or an industry ("B2B revenue intelligence"). Required.
- `--from=step-N` — optional. Resume from step N (2, 3, 4, or 5). Assumes prior steps' artifacts already exist in the `strategic-research/` subfolder of the current working directory under their fixed step-numbered names (`01-industry-process-map.md`, etc.).

## Behavior

1. **Parse the anchor** from `$ARGUMENTS`. Artifact filenames are fixed and step-numbered (no slug needed for them); when a skill derives a kebab-case ID from a name (segment / competitor / matrix-cell IDs), apply the slug algorithm in `${CLAUDE_PLUGIN_ROOT}/references/common-conventions.md` (lowercase; non-alphanumeric → single hyphen; trim) so IDs stay reproducible on resume.
2. **Confirm scope** with the user via `AskUserQuestion` if ambiguous (max 2 questions — anchor clarification, B2B vs. B2C if not obvious). Otherwise state assumptions explicitly and proceed.
3. **Sequentially invoke each skill in order**. Between steps:
   - Verify the upstream artifact was written and its YAML handoff is valid.
   - Stop and surface the error if a step fails.
4. **On step 5 completion**, tell the user the local path to the HTML report (`strategic-research/05-synthesis-report.html`) and a one-sentence top-line. Do not restate content in chat.

## Resume behavior (`--from=step-N`)

If `--from=step-N` is given:

1. Load all prior steps' YAML handoffs from their fixed-name markdown artifacts in `strategic-research/` (`01-industry-process-map.md`, `02-audience-segments.md`, `03-willingness-to-pay.md`, `04-competitor-evaluation.md`).
2. Validate that segment IDs, matrix cell IDs, and WTP band IDs are consistent across handoffs.
3. Begin execution at step N.

If any prior artifact is missing at its fixed path or its handoff is malformed, halt and tell the user which upstream artifact (by filename) needs to be regenerated.

## Writing style for chat between steps

One line per step completion:

```
✓ Step 1 · industry-process-map → strategic-research/01-industry-process-map.md (conf N%)
✓ Step 2 · audience-segment-research → strategic-research/02-audience-segments.md (conf N%)
...
```

No prose between steps. The deliverables are the files.

## Failure modes & recovery

| Failure | Action |
|---|---|
| Step 1 produces a matrix that is all zeroes / all cells marked "absent" | Halt; re-run step 1 with tighter scope |
| Step 2 produces segments with wtp_variance_ratio later < 2 | Flag in step 3; continue but mark segmentation as tentative |
| Step 3 produces no Leader outcomes with opportunity_score ≥ 10 | Continue but flag in step 5 — no strong white space likely |
| Step 4 produces a competitive set of all-direct competitors | Halt; force an indirect + non-consumption sweep |
| Step 5 can't find one of the handoffs | Render the fallback stub HTML with the red warning banner |

## Examples

```
/strategic-research SplitMetrics
```
Runs all 5 steps on anchor "SplitMetrics".

```
/strategic-research "AI Chief of Staff app" --from=step-4
```
Resumes from step 4, assuming steps 1–3 already wrote their artifacts to `strategic-research/` (`01`–`03`).
