# Model Evaluation Frameworks

## 4-Dimension Evaluation Matrix

Score each model 1-5 on each dimension for the specific product being assessed.

### Dimension 1: Value Demonstration Fit

Does this model allow the user to experience the product's core value?

| Score | Description |
|-------|-------------|
| 5 | Model perfectly showcases core value. User experiences the full "aha moment" within the model's constraints. |
| 4 | Model shows most of the value. Minor compromises but core value is clear. |
| 3 | Model shows partial value. Some important aspects are behind paywall or require more time/setup. |
| 2 | Model poorly demonstrates value. Key features locked or experience too limited. |
| 1 | Model fails to show value. Core value requires paid features, team adoption, or extended time. |

### Dimension 2: Audience Match

Does this model match how the target audience wants to evaluate products?

| Score | Description |
|-------|-------------|
| 5 | Target audience strongly prefers this evaluation style. Cultural/behavioral fit. |
| 4 | Good fit. Audience is comfortable with this model. |
| 3 | Neutral. Audience can work with this model but has no strong preference. |
| 2 | Mild friction. Audience prefers different evaluation approach. |
| 1 | Strong mismatch. Audience expects a fundamentally different experience. |

**Audience considerations:**
- Developers prefer: ungated, free tier, no sales touch
- Designers prefer: visual demo, free tier to experiment, community templates
- Enterprise buyers prefer: guided trial, demo, proof of concept
- SMB owners prefer: free trial with clear pricing, quick setup
- Consumers prefer: ungated or freemium with instant gratification

### Dimension 3: Conversion Economics

Will this model produce healthy conversion rates and sustainable unit economics?

| Score | Description |
|-------|-------------|
| 5 | High conversion expected. Clear upgrade trigger, strong value delta between free and paid. |
| 4 | Good conversion potential. Reasonable upgrade path with some optimization needed. |
| 3 | Moderate conversion expected. May require significant CRO work or sales assist. |
| 2 | Low conversion likely. Weak upgrade triggers or value delta. |
| 1 | Very low conversion expected. Free experience too generous or paid value unclear. |

**Economic factors:**
- Cost to serve free users (infrastructure, support)
- Expected conversion rate (varies by model — see benchmarks)
- Revenue quality (self-serve ARPA vs. sales-assisted ARPA)
- Time to conversion (faster = lower CAC)
- Expansion potential (does model seed multi-user adoption?)

### Dimension 4: Operational Feasibility

Can the team build, maintain, and optimize this model?

| Score | Description |
|-------|-------------|
| 5 | Straightforward to implement. Team has skills and infrastructure. |
| 4 | Feasible with some new tooling or skills. Reasonable investment. |
| 3 | Requires significant new infrastructure or capabilities. 1-2 quarter investment. |
| 2 | Major undertaking. New billing system, complex access control, or significant re-architecture. |
| 1 | Not feasible with current team/resources. Would require major investment. |

---

## Intent-Model Fit Matrix

Map user intent to optimal model:

```
                    URGENCY
            Low              High
         ┌──────────────┬──────────────┐
  High   │  Free Trial   │  Ungated     │
INTENT   │  Reverse Trial│  (solve now) │
  TO     │  (evaluate    │              │
  BUY    │   deeply)     │              │
         ├──────────────┼──────────────┤
  Low    │  Freemium    │  Self-Service │
INTENT   │  (explore    │  Demo        │
  TO     │   slowly)    │  Ungated     │
  BUY    │              │  (quick look)│
         └──────────────┴──────────────┘
```

---

## Multi-Model Complexity Assessment

When considering running multiple models simultaneously:

### Marketing Complexity
| # Models | Challenge | Mitigation |
|---|---|---|
| 1 | None | Single CTA, single message |
| 2 | Two CTAs compete for attention | Segment by page/channel; A/B test CTAs |
| 3+ | User confusion, choice paralysis | Use intent detection to auto-route; reduce visible options |

### Business Complexity
| # Models | Challenge | Mitigation |
|---|---|---|
| 1 | None | Clean pricing page |
| 2 | Pricing page complexity, feature comparison | Clear comparison table, recommend default |
| 3+ | Cannibalization risk, upgrade path confusion | Strict segment rules, no model switching |

### Operational Complexity
| # Models | Challenge | Mitigation |
|---|---|---|
| 1 | Single onboarding flow | Standard |
| 2 | Two onboarding paths, feature flagging | Shared components with branching points |
| 3+ | Multiple codepaths, A/B testing across models | Dedicated growth engineering, feature flag system |

---

## Model Selection Decision Tree

```
START
│
├── Can user get value in < 5 minutes with NO setup?
│   ├── YES → Consider UNGATED
│   │   └── Is signup valuable for the user (save work, personalize)?
│   │       ├── YES → Ungated → Signup prompt at value moment
│   │       └── NO → Ungated with account optional
│   └── NO → Continue
│
├── Is core value available without premium features?
│   ├── YES → Consider FREEMIUM
│   │   └── Is there a clear paid tier that's meaningfully better?
│   │       ├── YES → Freemium with clear upgrade triggers
│   │       └── NO → Rethink packaging or consider trial
│   └── NO → Continue
│
├── Does the product need time to demonstrate value (days/weeks)?
│   ├── YES → Consider FREE TRIAL
│   │   └── Would users benefit from seeing premium features first?
│   │       ├── YES → REVERSE TRIAL
│   │       └── NO → Standard FREE TRIAL
│   └── NO → Continue
│
├── Is setup complex but value is clear once seen?
│   ├── YES → Consider SELF-SERVICE DEMO
│   └── NO → Re-evaluate product for PLG fit
│
└── Still unsure? → Default to FREE TRIAL (safest starting point)
```

---

## Conversion Benchmarks by Model

| Model | Typical Conversion | Best-in-Class | Time to Convert |
|---|---|---|---|
| Freemium | 2-5% | 7-15% | Weeks to months |
| Free Trial (no CC) | 8-15% | 25-40% | During trial period |
| Free Trial (CC required) | 25-50% | 50-70% | During trial period |
| Ungated → Signup | 5-15% | 20-40% | Within session |
| Reverse Trial | 10-20% | 25-40% | During/after trial |
| Self-Service Demo → Signup | 3-10% | 15-25% | Within session |

**Note:** CC-required trials have higher conversion but far fewer signups. Net revenue is often higher with no-CC trials due to volume.
