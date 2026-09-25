---
name: synthesize-research
description: Roll up per-participant interview analyses into cross-participant findings. Answers each research question with how many participants support it, marks each assumption as confirmed, killed, or open, and builds two-level tables (theme → finding) for pains, goals, barriers, and workarounds with participants, verbatim quotes, and counts. Use after analyze-interviews, or when the user asks to synthesize research, find patterns across interviews, or turn interviews into recommendations.
argument-hint: "[analysis files; defaults to research/analyses/]"
---

# Synthesize Research

Input: every analysis in `research/analyses/`, unless the user names files, plus the newest `research/plan-*.md` if there is one.

Spawn one sub-agent per dimension, all in one message (`general-purpose`, `model: "opus"`), and pass each one the rules below:

| Dimension | Analysis section | Quote section |
|---|---|---|
| Pains | 3 | 4 |
| Goals | 5 | 6 |
| Barriers | 7 | 8 |
| Workarounds | 1 | 2 |

Skip Barriers if no analysis has section 7.

Rules:
- **Finding:** one specific thing, merged across participants, named plainly, e.g. "Exports break when the file has more than 10k rows".
- **Theme:** a group of related findings, 3 to 8 per dimension.
- Assign each quote to exactly one finding. Copy quotes verbatim, with the participant tag.
- **Count** = number of participants who said it, not number of quotes. A theme's count is the number of distinct participants across its findings.
- Mark a finding **(said, not done)** if all of its evidence is marked that way in the analyses.
- Sort themes and findings by count, highest first.
- Write to `research/.parts/<dimension>.md` in this format:

```
## Pains

| # | Theme / Finding | Participants | Count | Quotes |
|---|---|---|---|---|
| **1** | **Reporting takes too long** | P1, P3, P4 | **3** | |
| 1.1 | Rebuilding the weekly report by hand | P1, P4 | 2 | • *"quote"* (P1)<br>• *"quote"* (P4) |
```

Then write `research/YYYY-MM-DD-synthesis.md` yourself:
- Header: participants, segments, and source files.
- **Answers:** for each research question in the plan, a two-sentence answer and the number of participants behind it. Say "not enough evidence" when fewer than 3 participants speak to it.
- **Assumptions:** each riskiest assumption from the plan, marked **confirmed**, **killed**, or **open**, with one line of evidence.
- **What to do next:** 3 to 5 actions, each tied to a finding by number.
- **Open questions:** what the next round of interviews should ask.
- The dimension tables.

Check that each row's Count equals its number of participants, then delete `research/.parts/`. In chat, show Answers, Assumptions, and the file path.
