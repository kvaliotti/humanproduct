---
name: willingness-to-pay-research
description: Estimate what each customer segment pays today, what outcome they'd pay more for, and a price range worth testing, grounded in real prices and the cost of their current alternative. Use when the user asks about willingness to pay, pricing research, "what would they pay", "how should we price", or value to the customer. Step 3 of /strategic-research.
argument-hint: "[product, category, or industry]"
---

# Willingness-to-Pay Research

Output: `strategic-research/03-willingness-to-pay.md`. Follow `${CLAUDE_PLUGIN_ROOT}/references/plain-writing.md`.

## Steps

1. Read `strategic-research/02-audience-segments.md` if it exists and use its segments. Otherwise pick 2 or 3 segments and state them.
2. Research real prices: competitor pricing pages, review sites, agency rates, salaries for the people doing the work by hand.
3. Write the file.

## Sections

1. **Price table:** one row per segment. Columns: what they pay today (tool, agency, or people's time, in money per month), the outcome they care about most, what that outcome is worth to them, suggested price range to test.
2. **How we got each range:** for each segment, 2 to 4 sentences of plain arithmetic, e.g. "They pay an agency $3k/month. A tool that replaces half of that work can charge $500 to $1,500."
3. **What they need to see before paying:** for each segment, the proof that would make them buy (a free trial result, a case study from a peer, a number in their own dashboard).
4. **How to charge:** what the price should scale with (seats, usage, accounts, outcomes) and why, in 2 sentences.
5. **Questions to test pricing:** 5 interview questions about what they've paid for and switched from, not "would you pay X?".
6. **What we don't know**
7. **Sources**

Rules:
- Every price in the table comes from a source or a calculation shown in section 2. No invented numbers.
- Compare to what they do today, including doing it by hand, not to an imaginary zero.
