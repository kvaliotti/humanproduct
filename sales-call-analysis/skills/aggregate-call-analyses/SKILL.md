---
name: aggregate-call-analyses
description: Roll up per-client sales call analyses into cross-client tables. For pain points, desired outcomes, objections, and decision criteria, builds a two-level table (category → specific item) with the companies, verbatim quotes, and number of times each item was found. Use after analyze-sales-call, when the user asks for cross-client themes, patterns across calls, or a VoC roll-up.
argument-hint: "[analysis files; defaults to analyses/]"
---

# Aggregate Call Analyses

Input: every analysis in `analyses/`, unless the user names files. Use only one file per client.

Spawn one sub-agent per dimension, all in one message (`general-purpose`, `model: "opus"`), and pass each one the rules below:

| Dimension | Analysis section | Quote section |
|---|---|---|
| Pain points | 1 | 2 |
| Desired outcomes | 3 | 4 |
| Objections | 5 | 6 |
| Decision criteria | 7 | 8 |

Rules:
- **Item:** one specific thing, merged across clients, named plainly, e.g. "Vendor production takes a month".
- **Category:** a group of related items, 3 to 8 per dimension.
- Assign each quote to exactly one item. Copy quotes verbatim, with the client and date tag.
- **Count** = number of quotes. A category's count is the sum of its items' counts.
- Sort categories and items by count, highest first.
- Write to `synthesis/.parts/<dimension>.md` in this format:

```
## Pain points

| # | Category / Item | Companies | # Co. | Count | Quotes |
|---|---|---|---|---|---|
| **1** | **Production speed and cost** | Pocket Gems, Evercommerce | **2** | **9** | |
| 1.1 | Vendor production takes a month | Pocket Gems | 1 | 2 | • *"quote"* (Pocket Gems) [Aug 19]<br>• *"quote"* (Pocket Gems) [Sep 4] |
```

Assemble `synthesis/YYYY-MM-DD-cross-client-analysis.md`:
- Header: clients and source files.
- **Top themes:** the 3 items per dimension found at the most companies.
- The four tables.
- Note: Count follows the number of calls, so check # Co. for how widespread an item is.

Check that the number of bullets equals Count in every row, then delete `synthesis/.parts/`. In chat, show Top themes and the file path.
