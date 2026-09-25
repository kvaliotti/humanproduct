---
name: competitor-evaluation
description: Evaluate the competitors in a market, including indirect ones and doing it by hand: who they serve, what they charge, why customers pick or leave them, what is genuinely hard to copy, and where the gaps are. Use when the user asks for competitor analysis, competitive landscape, "who else does this", "how do we compare", or "where's the gap". Step 4 of /strategic-research.
argument-hint: "[product, category, or industry; optionally named competitors]"
---

# Competitor Evaluation

Output: `strategic-research/04-competitor-evaluation.md`. Follow `${CLAUDE_PLUGIN_ROOT}/references/plain-writing.md`.

## Steps

1. Read `strategic-research/01-*.md` to `03-*.md` if they exist and use their segments and workflow steps.
2. Research each competitor: its site, pricing page, reviews (G2, Capterra, app stores, Reddit), and recent news.
3. Write the file.

## Sections

1. **Competitor table:** 5 to 8 rows. Include at least one indirect alternative and one "do it by hand / do nothing". Columns: name, type (direct / indirect / by hand), who it's for, price, best at, weakest at.
2. **Competitor profiles:** for each, up to 5 bullets:
   - **Says it's for:** its own headline, quoted from its site.
   - **Why people pick it:** from reviews, with a source.
   - **Why people leave it:** from reviews, with a source.
   - **Hard to copy:** what would take a newcomer years to match (customer data, network, integrations, brand, price from scale). "Nothing" is a valid answer.
3. **How buyers choose:** a table with 5 to 7 factors buyers mention when choosing, one column per competitor, cells Strong / OK / Weak. One line under the table on where each factor comes from.
4. **Gaps:** 2 or 3 things no one does well, each naming the segment that cares.
5. **What we don't know**
6. **Sources**

Rules:
- Judge competitors by what customers say, not by their feature lists.
- Factors in section 3 come from reviews and buyer quotes, not from our own opinion of what matters.
