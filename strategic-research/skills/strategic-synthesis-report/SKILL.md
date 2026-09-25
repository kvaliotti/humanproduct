---
name: strategic-synthesis-report
description: Turn the strategic-research files (process map, segments, willingness to pay, competitors) into a one-page recommendation - where to play, how to win, what it's worth, the risks, and next steps. Use when the user asks for a strategy summary, "so what should we do", an executive summary of the research, or to wrap up /strategic-research. Step 5 of /strategic-research.
argument-hint: "[optional: folder with the research files; defaults to strategic-research/]"
---

# Strategic Synthesis Report

Input: `strategic-research/01-*.md` to `04-*.md`. If any are missing, say which ones and write the summary from the rest, marking the gaps.

Output: `strategic-research/05-summary.md`. Follow `${CLAUDE_PLUGIN_ROOT}/references/plain-writing.md`, but the limit here is one page.

## Sections

1. **The answer:** 3 sentences. What to build, for whom, and why now.
2. **Where to play:** the segment to go after first and why, citing the file it comes from, e.g. (02, Segments at a glance).
3. **How to win:** the gap we'd fill and why competitors won't close it quickly (04).
4. **What it's worth:** the price range and what it's based on (03).
5. **Top 3 risks:** for each, what would have to be true for it to kill the plan, and the cheapest test to check it.
6. **Next 3 steps:** concrete actions for the next two weeks.
7. **Files:** links to 01 to 04.

Rules:
- Add no new facts. Everything comes from 01 to 04, cited by file number.
- If the files disagree with each other, say so in one line instead of smoothing it over.
- In chat, show section 1 and the file path.
