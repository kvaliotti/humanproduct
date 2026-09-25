---
name: industry-process-map
description: Map what people in a market actually do, step by step, and how each step gets done today (tools, manual work, agencies, or not at all). Wider than any one product. Use when the user says "map the industry", "understand the market", "how does [domain] work end to end", "what do users do in [category]", or names a product or industry and wants the landscape around it. Step 1 of /strategic-research.
argument-hint: "[product, category, or industry]"
---

# Industry Process Map

Output: `strategic-research/01-industry-process-map.md`. Follow `${CLAUDE_PLUGIN_ROOT}/references/plain-writing.md`.

## Steps

1. Decide whose work we're mapping (a job title) and where the map stops. If the anchor is ambiguous, ask one question with AskUserQuestion; otherwise state your assumption and go.
2. Run 5 to 10 web searches: practitioner forums, job posts, how-to guides, review sites, and the anchor's own site. Look for the steps people describe, the words they use, and what they use instead of software.
3. Write the file.

## Sections

1. **Scope:** whose work, the anchor product (if any), and what's out of scope. Three lines.
2. **The workflow:** 5 to 9 numbered steps, in the order the person does them. Name each step with a verb in their words ("Decide which ads to pause"). Add up to 3 sub-steps as bullets.
3. **How each step gets done today:** a table with one row per step and columns for the ways it's done (e.g. dedicated tool, spreadsheet, agency, in-house build, skipped). Put real product names in the cells.
4. **Where it hurts:** the 3 to 5 most painful steps. For each, one sentence on the pain and one on what people do about it, with a source.
5. **Glossary:** the practitioner terms a newcomer needs, one line each.
6. **What we don't know**
7. **Sources**

Rules:
- The map covers the whole job, not just what the anchor product does. Include manual work, agencies, and doing nothing.
- Steps must not overlap, and together they must cover the job from start to finish.
