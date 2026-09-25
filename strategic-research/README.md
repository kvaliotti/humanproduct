# strategic-research

Research a market and get a recommendation you can read in five minutes. Five steps, each a short markdown file with sourced facts, plain words, and a **What we don't know** list.

```
/strategic-research SplitMetrics
/strategic-research "mobile ad optimization" --from=4
```

| Step | Skill | Writes to `strategic-research/` |
|---|---|---|
| 1 | `industry-process-map`: the steps people go through and how each gets done today | `01-industry-process-map.md` |
| 2 | `audience-segment-research`: segments, how to spot them, who to go after first | `02-audience-segments.md` |
| 3 | `willingness-to-pay-research`: what they pay today and a price range to test, with the arithmetic | `03-willingness-to-pay.md` |
| 4 | `competitor-evaluation`: who else solves it, why people pick or leave them, the gaps | `04-competitor-evaluation.md` |
| 5 | `strategic-synthesis-report`: one page on where to play, how to win, risks, next steps | `05-summary.md` |

Each skill also works on its own and reads whichever earlier files exist. All of them follow [`references/plain-writing.md`](references/plain-writing.md): short sentences, real names and numbers, a source for every fact, no made-up scores, at most two pages per file.
