---
name: market-frame-selector
description: >
  Decision tool for choosing between the three positioning styles: Head to Head, Big Fish Small
  Pond, or Create a New Game. Use when the user says "what market should we be in", "head to
  head vs niche", "positioning style", "should we create a category", "market frame", "which
  market to compete in", "Big Fish Small Pond", "category creation", "how to position in the
  market", or has completed competitive alternatives and value mapping and needs to choose their
  market frame of reference. Can run standalone or as a sub-step of the positioning workshop.
---

# Market Frame Selector

This skill covers Step 8 of the positioning framework — choosing the market frame that makes your strengths most obvious to the people who care most. The market you choose triggers assumptions about competitors, features, and pricing. Choose wrong, and you fight uphill forever.

## Prerequisites

This skill works best with:
- Competitive alternatives (from Step 4 or competitive-alternatives skill)
- Unique attributes and value themes (from Steps 5-6)
- Best-fit customer characteristics (from Step 7)

If these don't exist, ask the user for a quick version of each before proceeding.

## Step 1: Find Market Options

Use three methods to generate candidates:

### Method 1: Abductive Reasoning
"If a product had these attributes and delivered this value, what type of product would people assume it is?"

Look at the attributes and value themes. What category of product typically has these characteristics?

### Method 2: Adjacent Markets
"What neighboring or overlapping markets are growing? Could any of them be a better frame?"

Examine markets that share some characteristics but have different buying criteria or competitive sets.

### Method 3: Customer Input (Use Cautiously)
"What market do your customers place you in when they describe you to others?"

Warning: Customers default to the obvious category, not necessarily the best one. Use as input, not as the answer.

### Output: 3-5 Market Options
List each candidate market with:
- What assumptions it triggers (competitors, features, pricing)
- Whether those assumptions help or hurt

## Step 2: Evaluate the Three Positioning Styles

Present each style with its decision criteria. Use `references/three-styles-deep.md` for detail.

### Style 1: Head to Head

**What:** Compete directly in an existing market. Accept current buying criteria. Claim superiority.

**Choose when:**
- You ARE the market leader and want to defend
- No clear leader exists in an emerging category
- You have overwhelming evidence of superiority + resources to compete

**Reject when:**
- You're a small company vs. an entrenched incumbent
- No clear competitive advantage on current buying criteria
- You can't outspend the leader on marketing

**Decision question:** "If you enter this market head-on, can you win on the existing buying criteria? Or are you hoping the criteria change?"

### Style 2: Big Fish, Small Pond (DEFAULT for most startups)

**What:** Carve off a subsegment of an existing market where different rules apply. Your product has an edge in this subsegment that the category leader can't match.

**Choose when:**
- Clear leader exists that you can't beat head-on
- Definable subsegment with unique unmet needs
- You can serve those needs much better than the leader
- Subsegment is large enough for business goals

**Reject when:**
- No definable subsegment exists
- The subsegment is too small for near-term targets
- The leader serves the subsegment well enough

**Decision question:** "Is there a group of customers for whom the general-purpose leader is notably inadequate?"

### Style 3: Create a New Game

**What:** Define an entirely new market category. Set the boundaries, define purchase criteria, establish leadership.

**Choose when:**
- You've evaluated EVERY existing category and none makes strengths obvious
- A massive enabling change (technology, regulation, economics) supports a new category
- Product is demonstrably, inarguably new
- You have resources AND patience for long-term category education

**Reject when:**
- An existing category works reasonably well (don't create when you can carve)
- You lack resources for category education (content, events, analyst relations)
- The product is really a feature of an existing category, not a category itself

**Decision question:** "Is your product genuinely a new category, or just a better version of something that already exists?"

## Step 3: Run the Decision Tree

Walk through this with the user:

```
Can you position in an existing market where your strengths are obvious?
├── YES: Is there a clear leader?
│   ├── YES: Can you beat them head-on?
│   │   ├── YES → Head to Head
│   │   └── NO → Big Fish, Small Pond (find a subsegment)
│   └── NO → Head to Head (claim leadership of emerging category)
└── NO: Is there a massive enabling change?
    ├── YES → Create a New Game (if you have resources)
    └── NO → Reexamine — you may be missing an adjacent market
```

**Default recommendation:** Big Fish, Small Pond unless there's an overwhelming reason not to. It's the lowest risk, fastest path to traction for most startups and scaleups.

## Step 4: Specify the Chosen Market

Once the style is selected, define:

1. **Market category name** — specific enough to trigger correct assumptions
2. **Why this frame wins** — which assumptions it triggers that help
3. **Two rejected options** — with reasoning for why they lose
4. **Work required** — what this positioning style demands (see `references/three-styles-deep.md`)

## Step 5: Validate

Run these checks:
- **Category test:** Would an outsider correctly predict your core features from the category name?
- **Assumption test:** Does the category trigger helpful assumptions about competitors, features, and pricing?
- **Subsegment test (Big Fish):** Is the subsegment definable, reachable, and large enough?
- **Education test (New Game):** Can you afford the investment to create the category?

Output the selected market frame with full rationale, ready for the positioning canvas.

## Style Rules

- Push hard toward Big Fish, Small Pond unless clear evidence supports another style.
- Challenge category creation attempts: "Is this genuinely a new category, or are you avoiding the discipline of competing within an existing one?"
- Always require rejected options with reasoning — it proves the choice was deliberate.
- Cite case studies from `references/case-studies.md` when relevant.
