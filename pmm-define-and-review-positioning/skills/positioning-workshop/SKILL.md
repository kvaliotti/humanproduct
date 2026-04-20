---
name: positioning-workshop
description: >
  Guide a user through the full 10-step product positioning process interactively.
  Use when the user says "position my product", "define positioning", "positioning workshop",
  "help me position", "run the positioning process", "10-step positioning",
  or wants to build product positioning from scratch. Produces a filled 5+1 positioning canvas,
  a positioning narrative, and actionable next steps.
---

# Positioning Workshop

Run the full 10-step positioning process interactively. Work through each phase in order — do NOT skip ahead. Each phase depends on the previous one's output.

## How This Works

This is a facilitated workshop, not a form to fill. At each step:
1. Explain what the step accomplishes and why it matters (1-2 sentences max)
2. Ask targeted questions using AskUserQuestion
3. Challenge weak or generic answers — push for specificity
4. Summarize what was established before moving to the next step

Use `references/10-step-process.md` for the detailed methodology at each step.
Use `references/anti-patterns.md` to catch common mistakes in real time.
Use `references/case-studies.md` to cite relevant examples when the user's situation parallels one.

## Phase 1: Pre-Work (Steps 1-3)

### Step 1: Identify Best-Fit Customers

Ask the user to describe their happiest, most successful customers — not the average ones. Probe for:
- Who understood the product immediately?
- Who bought quickly without heavy discounting?
- Who became advocates and referrers?
- Who represents the type of customer they want more of?

If the user has no customers yet, acknowledge it: keep positioning loose, focus on hypotheses, and flag that this positioning is provisional.

Challenge vague answers. "SMBs" is not a best-fit customer. "3-person marketing teams at B2B SaaS companies who just lost their only designer" is.

### Step 2: Positioning Team Context

Ask who's involved in this positioning work. If it's just the user (common in Cowork), acknowledge the limitation: they're missing sales, CS, and product perspectives. Prompt them to note where those perspectives would add signal.

If they mention a team, ask whether the business leader (CEO/founder/BU head) is involved. Flag if not — positioning done without executive buy-in won't stick.

### Step 3: Surface Baggage

Ask: "How do you currently describe your product? What market did you originally build it for?"

Then challenge: "Is the market you built for still the best frame? Has the product or market changed since launch?"

Get explicit acknowledgment that the user is willing to consider the product being positioned differently than its original intent.

## Phase 2: Core Analysis (Steps 4-7)

### Step 4: Competitive Alternatives

This is the foundational step. See `references/10-step-process.md` (Step 4 section) for the full method.

Core question: "What would your best customers use or do if your product didn't exist?"

Push beyond direct competitors. Probe for:
- General-purpose tools (Excel, Google Docs, Notion)
- Manual processes ("hire an intern", "do it myself")
- Do nothing / status quo
- Combinations ("spreadsheet + Zapier + manual review")

Group into 2-5 clusters. Rank by frequency.

Red flags to catch:
- Only listing startup competitors prospects have never heard of
- Missing "do nothing" as an alternative
- Listing what the user thinks competitors are vs. what customers actually use

### Step 5: Unique Attributes

For each competitive alternative cluster, ask: "What do you have that they don't?"

Explore all categories: technical features, delivery model, business model, expertise, partnerships, team skills.

Rules:
- Stay at the attribute level (what you HAVE), not value level (why it MATTERS) — that's Step 6
- Must be provable. "Better UX" is an opinion. "Zero-config setup that takes under 2 minutes" is a fact.
- Include potential negatives — they may be strengths for the right segment
- Cast a wide net (8-15 attributes), then narrow

### Step 6: Map Attributes to Value Themes

For each attribute, run the "So what?" test twice:
- Attribute → Benefit (what it enables)
- Benefit → Value (customer goal it serves)

Then cluster into 1-4 value themes from the customer's perspective.

Each theme needs proof. If there's no proof, the theme gets demoted or cut.

### Step 7: Who Cares Most

For each value theme, ask: "Who would care about this intensely — not just a little?"

Push for actionable characteristics:
- NOT "mid-market companies" → YES "B2B SaaS companies with 50-200 employees who sell to enterprise and just hired their first dedicated CS team"
- Validate: "Could you build a prospect list of 50 accounts from this description?"

Apply the narrowing test: Can you hit near-term sales targets with just best-fit customers? If yes, stay narrow. If no, broaden until viable.

## Phase 3: Market Framing (Steps 8-9)

### Step 8: Market Frame and Positioning Style

Present the three positioning styles from `references/10-step-process.md` (Step 8 section):
1. **Head to Head** — compete directly in existing market
2. **Big Fish, Small Pond** — win a subsegment with different rules
3. **Create a New Game** — define a new category

Walk through the decision tree with the user. Default recommendation for most startups/scaleups: Big Fish, Small Pond.

The user must choose a market category AND state two rejected options with reasoning.

### Step 9: Trend (Optional)

Ask if there's a trend that reinforces the positioning. Apply the three-circle test:
- Does it connect to product strengths?
- Does it connect to the market context?
- Do customers actually care about this trend?

If all three: use it. If forcing any connection: skip it. "Better boring than baffling."

## Phase 4: Capture (Step 10)

### Step 10: Document the Positioning

Produce the final deliverables:

**1. Filled 5+1 Positioning Canvas** — use the template from `references/positioning-canvas-template.md`

**2. Positioning Narrative** — tight paragraph in this shape:
> For **[best-fit customer]** who **[struggles with X when doing Y]**, most teams today rely on **[top alternatives]**. **[Product]** is a **[market category]** that **[unique mechanism]**, so customers can **[measurable/observable value]**. Unlike **[top alternative]**, we **[key differentiator]**.

**3. One-line elevator version**

**4. Stop/Start list:**
- 3 things the team should STOP saying (commoditized, generic, or actively harmful)
- 3 things the team should START saying (unique, provable, resonant)

**5. Pressure test results** — run the 9-question checklist from `references/pressure-tests.md` against the positioning. Flag any failures and suggest patches.

## Style Rules

- Be a tough facilitator, not a yes-machine. Challenge weak answers.
- Never accept "everyone" as a target market.
- If the market category choice is weak, say so directly and explain why.
- Strip adjectives. "Seamless", "powerful", "intuitive" are banned.
- Cite case studies from `references/case-studies.md` when the user's situation parallels one — it makes the framework concrete.
- When the user is stuck, offer 2-3 concrete options rather than open-ended "what do you think?"
