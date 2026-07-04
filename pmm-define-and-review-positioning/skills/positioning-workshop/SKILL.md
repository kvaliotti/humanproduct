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
Use `${CLAUDE_PLUGIN_ROOT}/references/case-studies.md` to cite relevant examples when the user's situation parallels one.
Steps 4-6 have a canonical deep-dive skill, `competitive-alternatives` — invoke it directly whenever the user needs more rigor than the summary below.

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

Steps 4-6 are the analytical core of positioning — where most of it goes wrong. `competitive-alternatives` is the canonical deep-dive skill for these steps, with the full elicitation sequence and attribute taxonomy. The summaries below are enough to keep a workshop moving; hand off to `competitive-alternatives` (or read its reference files directly) whenever the user needs more rigor.

### Step 4: Competitive Alternatives (summary)

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

Full round-by-round elicitation sequence and failure-mode responses: `${CLAUDE_PLUGIN_ROOT}/skills/competitive-alternatives/references/elicitation-guide.md`.

### Step 5: Unique Attributes (summary)

For each competitive alternative cluster, ask: "What do you have that they don't?"

Explore all categories: technical features, delivery model, business model, expertise, partnerships, team skills.

Rules:
- Stay at the attribute level (what you HAVE), not value level (why it MATTERS) — that's Step 6
- Must be provable. "Better UX" is an opinion. "Zero-config setup that takes under 2 minutes" is a fact.
- Include potential negatives — they may be strengths for the right segment
- Cast a wide net (8-15 attributes), then narrow

Full category-by-category probe questions and examples: `${CLAUDE_PLUGIN_ROOT}/skills/competitive-alternatives/references/attribute-categories.md`.

### Step 6: Map Attributes to Value Themes (summary)

For each attribute, run the "So what?" test twice:
- Attribute → Benefit (what it enables)
- Benefit → Value (customer goal it serves)

Then cluster into 1-4 value themes from the customer's perspective.

Each theme needs proof. If there's no proof, the theme gets demoted or cut.

Full clustering method and proof-assignment guidance: see the `competitive-alternatives` skill (Step 6).

### Step 7: Who Cares Most

For each value theme, ask: "Who would care about this intensely — not just a little?"

Push for actionable characteristics:
- NOT "mid-market companies" → YES "B2B SaaS companies with 50-200 employees who sell to enterprise and just hired their first dedicated CS team"
- Validate: "Could you build a prospect list of 50 accounts from this description?"

Apply the narrowing test: Can you hit near-term sales targets with just best-fit customers? If yes, stay narrow. If no, broaden until viable.

## Handoff (When Running as Part of positioning-orchestrator)

If this skill is invoked as Phase 1 of the `positioning-orchestrator` pipeline, **stop here after Step 7**. Do not continue into Phase 3 (Market Framing) or Phase 4 (Capture) below — the orchestrator runs those as its own phases via `market-frame-selector` and its own capture step. Summarize Steps 1-7 and emit:

```yaml
phase_1_output:
  best_fit_customers: [...]
  competitive_alternatives:
    groups: [...]
  unique_attributes: [...]
  value_themes: [...]
  target_market: [...]
```

If running standalone (the common case — the user invoked `positioning-workshop` directly), ignore this section and continue to Phase 3 and Phase 4 below to produce the full canvas, narrative, and pressure test results.

## Phase 3: Market Framing (Steps 8-9)

### Step 8: Market Frame and Positioning Style

Present the three positioning styles (full detail, decision criteria, and case studies in `${CLAUDE_PLUGIN_ROOT}/references/three-styles.md`):
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
- Cite case studies from `${CLAUDE_PLUGIN_ROOT}/references/case-studies.md` when the user's situation parallels one — it makes the framework concrete.
- When the user is stuck, offer 2-3 concrete options rather than open-ended "what do you think?"
