# Free Trial Model — Deep Dive

## Core Concept

A free trial provides full (or nearly full) product access for a limited time. The time constraint acts as a forcing function — users must evaluate the product within the trial window and make a purchase decision.

---

## Trial Duration Selection

### Factors in Duration Choice

| Factor | Shorter Trial (7-14 days) | Longer Trial (30+ days) |
|---|---|---|
| Time to value | Fast (< 1 day) | Slow (days to weeks) |
| Setup complexity | Low | High (data import, team onboarding) |
| Decision maker | End user (can decide quickly) | Committee (needs time for approval) |
| Product complexity | Simple, focused product | Complex, multi-feature product |
| Usage frequency | Daily use product | Weekly/monthly use product |
| Competitive pressure | Users might try competitors during long trial | Users need time to compare |

### Common Durations and When to Use

| Duration | Best For | Risk |
|---|---|---|
| **7 days** | Simple products with fast TTV, daily-use tools | Not enough time for complex products |
| **14 days** | Most B2B SaaS, moderate complexity | Sweet spot for many products |
| **30 days** | Complex products, enterprise, requires team adoption | High drop-off, trial fatigue |
| **60+ days** | Enterprise with procurement cycles | Very low urgency, most users forget |

**Rule of thumb:** Trial should be 2-3x the typical time-to-value. If TTV is 2 days, a 7-day trial works. If TTV is 1 week, 14-21 days.

---

## The Forcing Function

The trial's time limit creates urgency. This is its primary advantage over freemium — users MUST evaluate and decide.

### Forcing Function Design

**Countdown communication:**
- Day 1: Welcome, here's how to get the most from your trial
- Day 3-5: Check in, highlight features not yet tried
- Day 7 (of 14): Midpoint, show progress and value received
- Day 10: "4 days left" — summarize value delivered, show upgrade path
- Day 12: "2 days left" — urgency + special offer (optional)
- Day 14: Trial ends — clear CTA to upgrade or downgrade path

**What happens when trial ends:**

| Approach | Pros | Cons |
|---|---|---|
| **Hard wall** (locked out) | Maximum urgency | Frustrating, users may churn permanently |
| **Downgrade to free** (if freemium exists) | Retains users, second chance to convert | Reduces urgency during trial |
| **Grace period** (3-7 days reduced access) | Gentle transition, allows decision time | Complex to implement |
| **Read-only mode** | Users see their data but can't create | Good compromise, data hostage concern |

**Recommendation:** If you have a free tier, downgrade to it. If not, grace period with reduced access is the most user-friendly approach.

---

## Credit Card Upfront: The Great Debate

### No Credit Card Required

**Pros:**
- 2-4x more trial signups
- Lower barrier for evaluation
- More users experience the product (larger PQL pool)
- Better for brand perception

**Cons:**
- Lower trial-to-paid conversion (8-20% typical)
- More unqualified signups
- Higher infrastructure costs for free usage

**Best when:** Product value is clear within the trial, self-serve upgrade is easy, cost-to-serve is low.

### Credit Card Required Upfront

**Pros:**
- Much higher conversion rate (40-60% typical)
- More qualified signups (serious evaluators)
- Auto-conversion at trial end
- Lower cost to serve (fewer tire-kickers)

**Cons:**
- 60-80% fewer signups
- Higher perceived risk for user
- More refund requests
- "Forgot to cancel" bad experience

**Best when:** Product is expensive (high ARPA), target audience is serious buyers, market is enterprise-leaning.

### The Math

```
No CC: 10,000 signups x 15% conversion x $50 ARPA = $75,000 MRR
With CC: 3,000 signups x 50% conversion x $50 ARPA = $75,000 MRR

Same revenue, different user bases. No-CC gives you 7,000 extra users
who might convert later, refer others, or become PQLs.
```

For most PLG products, no-CC is recommended. The extra volume feeds viral loops, PQL pipeline, and brand awareness.

---

## Trial Onboarding: The Forcing Function Amplifier

Trial onboarding is MORE critical than freemium onboarding because time is limited. Every wasted day is a lost conversion opportunity.

### Trial Onboarding Principles

1. **First session = first value.** User must experience aha moment on day 1, ideally in the first hour.
2. **Progressive depth.** Day 1: core value. Day 3: advanced features. Day 7: power features.
3. **Milestone communication.** "You've completed 3 of 5 key steps" — progress creates investment.
4. **Feature discovery prompts.** Mid-trial emails highlighting unused premium features.
5. **Value quantification.** "In 7 days, you've saved X hours / created Y items / collaborated with Z people."

### Trial Onboarding Checklist
- [ ] Day 1 aha moment is designed and measured
- [ ] Onboarding flow has < 5 required steps
- [ ] Daily/regular touchpoints guide feature discovery
- [ ] Mid-trial email shows value delivered so far
- [ ] Pre-expiration email quantifies value and shows upgrade path
- [ ] Post-expiration email with last chance + alternative (downgrade to free)

---

## When Trial Beats Freemium

| Signal | Why Trial is Better |
|---|---|
| Product requires full feature set for evaluation | Freemium would hide the best parts |
| Value accumulates over days/weeks | Users need time pressure to evaluate seriously |
| Setup investment is significant | Users won't invest setup time without full access |
| Premium features ARE the differentiation | Can't demonstrate value with a stripped-down version |
| Target audience is enterprise/mid-market | Buyers expect trial periods, have evaluation processes |
| High ARPA (>$100/month) | Trial qualifies serious buyers, worth the conversion trade-off |

## When Freemium Beats Trial

| Signal | Why Freemium is Better |
|---|---|
| Core value is available without premium features | Free tier works standalone |
| Viral/network growth is important | Free users drive adoption |
| Large TAM, land-and-expand strategy | Volume of free users feeds enterprise pipeline |
| Competitive market with strong free alternatives | Must match free competitors |
| Low cost-to-serve per user | Sustainable to support free users |
| Consumer or prosumer market | Users resist time pressure |

---

## Trial Conversion Optimization

### Highest-Impact Levers

| Lever | Expected Impact | Effort |
|---|---|---|
| Shorten time-to-first-value (faster aha moment) | +20-40% conversion | Medium |
| Add trial extension option (for engaged users) | +5-15% conversion | Small |
| Improve trial-end communication sequence | +10-20% conversion | Small |
| Add team invitation during trial | +15-25% conversion (team stickiness) | Medium |
| Implement "save your work" messaging at trial end | +5-10% conversion | Small |
| Offer annual discount at trial end | +10-20% conversion (anchor effect) | Small |

### Trial Extension Strategy
Instead of letting users churn at trial end, offer targeted extensions:
- **Engaged but not converted:** "Need more time? Here's 7 more days."
- **Partially onboarded:** "You haven't tried [key feature] yet. Extend to try it."
- **Team not fully onboarded:** "Your team is just getting started. Extend to let them catch up."

Extensions should be conditional (requires engagement) not universal (everyone gets more time).
