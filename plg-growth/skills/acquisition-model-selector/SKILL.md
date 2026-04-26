---
name: acquisition-model-selector
description: "Choose the right PLG acquisition model — freemium, free trial, ungated, reverse trial, or self-service demo. Use when someone asks 'freemium or free trial', 'which acquisition model', or 'how should users start using our product'."
---

# Acquisition Model Selector

## Purpose

You help a PM choose the right business acquisition model (or combination of models) for their product. You evaluate five model types against the product's characteristics, audience intent, and operational capacity, then produce a Model Selection Brief with a clear recommendation.

## When to Invoke

Trigger phrases:
- "which acquisition model"
- "freemium or free trial"
- "should we be freemium"
- "acquisition model"
- "ungated vs freemium"
- "reverse trial"
- "self-service demo"
- "how should users start using our product"
- "select PLG model"
- "free tier design"

## Structured Problem-Solving Backbone

1. **Issue Trees (MECE)** — decompose model selection into product characteristics, audience intent, model fit, and operational complexity
2. **Hypothesis Trees** — hypothesize best model before deep analysis
3. **Driver Disaggregation** — separate model effectiveness into conversion rate, revenue quality, and operational cost drivers
4. **80/20 Prioritization** — focus on the 2-3 factors that most strongly determine model fit
5. **So-What Synthesis (Minto Pyramid)** — lead with the model recommendation, then the rationale
6. **Hypothesis-Driven Work Plans** — test the model recommendation with a specific experiment plan

## The Five Acquisition Models

| Model | Core Mechanic | Best For |
|-------|---------------|----------|
| **Freemium** | Unlimited free tier with feature/usage limits; paid for premium | Products with clear free value and natural upgrade triggers |
| **Free Trial** | Full access for limited time; must pay to continue | Products where full value requires full feature set |
| **Ungated** | Use the product without any account creation | Products solving in-moment needs with high-volume traffic |
| **Reverse Trial** | Full premium access initially, downgrade to free after trial period | Products where premium features demonstrate differentiated value |
| **Self-Service Demo** | Pre-generated demo environment with sample data | Complex products where setup is a barrier to experiencing value |

## Step-by-Step Methodology

### Step 1: Assess Product Characteristics

Before evaluating models, understand the product:

**Ask the user:**
1. What is the core value the user gets? (One sentence)
2. How quickly can a new user experience core value? (Minutes / hours / days)
3. How much setup is needed before first value? (None / some / significant)
4. Is the product primarily single-player or multiplayer?
5. What data or content does the user need to bring? (None / some / their own data is essential)
6. What is the competitive landscape? (Blue ocean / crowded / commodity)

**Map to model-selection drivers:**

| Driver | Assessment | Implication |
|--------|-----------|-------------|
| Time to value | Fast (<1 hour) | Favors freemium or ungated |
| Time to value | Slow (days+) | Favors trial, reverse trial, or demo |
| Setup complexity | Low | Favors freemium or ungated |
| Setup complexity | High | Favors demo or reverse trial |
| Data dependency | No data needed | Favors ungated |
| Data dependency | User's own data essential | Favors trial or freemium |
| Multiplayer value | Single-player works | All models viable |
| Multiplayer value | Team needed for value | Favors trial with team invite |
| Competitive intensity | High/commodity | Freemium as defensive moat |
| Competitive intensity | Low/differentiated | Trial to demonstrate unique value |

### Step 2: Evaluate Each Model

Load the model evaluation frameworks:
> Read `references/model-evaluation-frameworks.md`

For each model, score fit (1-5) across 4 dimensions:
1. **Value demonstration fit** — Can this model show the product's core value?
2. **Audience match** — Does this model match how the target user wants to evaluate?
3. **Conversion economics** — Will this model produce healthy conversion rates and unit economics?
4. **Operational feasibility** — Can the team support this model (infrastructure, support, sales)?

Then deep-dive into the top 2-3 scoring models using the detailed references:

> Read `references/freemium-deep-dive.md`
> Read `references/free-trial-deep-dive.md`
> Read `references/ungated-deep-dive.md`
> Read `references/reverse-trial-deep-dive.md`
> Read `references/self-service-demo-deep-dive.md`

### Step 3: Map Intents to Models

Different users arrive with different intents. Different channels bring different intent levels. The right model may vary by entry point.

**Intent spectrum:**

| Intent Level | User Thinking | Best Model |
|---|---|---|
| **Browsing** | "What is this?" | Ungated preview or self-service demo |
| **Evaluating** | "Could this work for me?" | Freemium or free trial |
| **Ready to try** | "Let me test this with my use case" | Free trial or freemium |
| **Ready to buy** | "I need this, show me pricing" | Direct purchase with trial safety net |
| **In-moment need** | "I need to solve this RIGHT NOW" | Ungated (no barrier) |

**Channel-to-intent mapping:**

| Channel | Typical Intent | Suggested Model |
|---|---|---|
| Organic search (problem query) | Evaluating / In-moment | Ungated or freemium |
| Organic search (product/brand query) | Ready to try | Free trial or freemium |
| Paid search (category term) | Evaluating | Free trial or demo |
| Social media ad | Browsing | Ungated or demo |
| Referral from colleague | Ready to try | Free trial or freemium |
| Product Hunt / review site | Evaluating | Free trial |
| Sales outreach response | Evaluating | Demo or reverse trial |

**Key insight:** You do NOT have to pick one model. Different pages can offer different entry points. But complexity increases with each additional model.

### Step 4: Assess Multi-Model Complexity

If the analysis suggests multiple models, evaluate the complexity:

**Marketing complexity:** Can messaging clearly explain different entry points without confusing users?
**Business complexity:** Can pricing/packaging support multiple models cleanly?
**Operational complexity:** Can the team build and maintain multiple onboarding flows?

**Complexity scoring:**

| Factor | 1 Model | 2 Models | 3+ Models |
|---|---|---|---|
| Marketing | Simple | Manageable | Requires careful segmentation |
| Business | Clean | Adds edge cases | Significant packaging work |
| Operations | Straightforward | 1.5-2x effort | 2-3x effort, dedicated team needed |

**Rule of thumb:** Start with 1 model. Add a second only when you have clear evidence it serves a different, valuable segment. Never launch with 3+ models unless you have a dedicated growth team.

### Step 5: Design the Selected Model

Once a model (or model combination) is selected, design the key parameters:

**For Freemium:**
- What features are free vs. paid?
- What are the usage limits?
- What triggers the upgrade prompt?
- How generous is the free tier?

**For Free Trial:**
- What is the trial duration?
- Is a credit card required upfront?
- What happens when the trial ends?
- Is there a trial extension option?

**For Ungated:**
- What can users do without signing up?
- What triggers the signup prompt?
- How is value preserved from ungated to signed-up state?
- What data is captured pre-signup?

**For Reverse Trial:**
- How long is the premium period?
- What is the downgrade experience?
- How is the "you're losing these features" communicated?
- What free tier do they land on after trial?

**For Self-Service Demo:**
- What pre-generated data/content is shown?
- How realistic is the demo environment?
- What is the demo-to-signup conversion flow?
- How is the demo personalized?

### Step 6: Produce Model Selection Brief

```
## Model Selection Brief

### Product Context
[2-3 sentences: product, target user, current state]

### Recommended Primary Model: [Model Name]

**Why this model:**
- [Reason 1 — tied to product characteristic]
- [Reason 2 — tied to audience intent]
- [Reason 3 — tied to conversion economics or feasibility]

**Model Design:**
- [Key parameter 1]
- [Key parameter 2]
- [Key parameter 3]

### Secondary Model (if applicable): [Model Name]
**For segment/channel:** [which users/channels]
**Why:** [rationale]

### Models Considered and Rejected
| Model | Score | Rejection Reason |
|---|---|---|
| [Model A] | X/5 | [why not] |
| [Model B] | X/5 | [why not] |

### Conversion Hypothesis
"We believe [model] will achieve [X%] conversion because [evidence/reasoning]. We will validate this by [experiment/measurement]."

### Implementation Plan
Phase 1 (Weeks 1-4): [what to build]
Phase 2 (Weeks 5-8): [what to optimize]
Phase 3 (Weeks 9-12): [what to add/refine]

### Metrics to Track
- Primary: [conversion rate metric]
- Secondary: [activation metric, revenue metric]
- Guardrail: [metric that should NOT degrade]

### Risks and Mitigations
| Risk | Mitigation |
|---|---|
| [Risk 1] | [Mitigation] |
| [Risk 2] | [Mitigation] |
```

## Connection to Other Skills

| Skill | Handoff |
|-------|---------|
| `plg-orchestrator` | Receives diagnostic context, returns model recommendation |
| `plg-readiness` | Model selection assumes PLG viability confirmed; decision-driver research informs which value to demonstrate in free experience |
| `plg-revenue-analysis` | Selected model affects top-of-funnel drivers in the revenue tree |
| Future activation skill | Model design directly determines onboarding and activation strategy |

## Inputs Required

- Product description and core value proposition
- Target user and buying dynamic
- Current acquisition model (if any)
- Time to value and setup complexity
- Team size and engineering capacity
- Traffic volume and channel mix (if known)
- Decision-driver research results (if available from plg-readiness)

## Anti-Patterns

- **Copying competitors:** Just because a competitor uses freemium does not mean you should. Their product characteristics may be different.
- **Defaulting to free trial because it's easiest:** Free trial is often the lazy choice. Evaluate whether freemium or ungated would convert better for your specific product.
- **Over-engineering multi-model from day 1:** Start with one model. Get it working. Add complexity only with evidence.
- **Ignoring the downgrade experience:** For reverse trial and freemium, the moment a user hits a limit or loses a feature is the most important conversion moment. Design it carefully.
- **Free tier too generous or too restrictive:** Both kill conversion. Use decision-driver research to calibrate what must be free (to prove value) vs. what should be paid (to drive upgrades).
