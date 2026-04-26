# Pricing Triangle: Packaging x Metric x Price

The three dimensions of any pricing strategy. Get one wrong and the others cannot compensate. Always evaluate all three together.

## 1. Packaging (What You Charge For)

### Good / Better / Best Tier Design

The most common PLG packaging pattern. Each tier targets a distinct user segment with distinct needs.

**Good (Free or Starter):**
- Target: Individual user, evaluator, small team
- Includes: Core use case, enough to reach aha moment
- Goal: Drive adoption, prove value, create upgrade desire
- Limitation principle: Limit on the dimension that correlates with value received (not on features that punish)

**Better (Pro / Team):**
- Target: Growing team, power user, small business
- Includes: Everything in Good + collaboration, integrations, higher limits
- Goal: Capture willingness to pay from engaged users
- This is usually the highest-volume paid tier

**Best (Business / Enterprise):**
- Target: Department, company, enterprise buyer
- Includes: Everything in Better + admin, security, compliance, SSO, API, SLA
- Goal: Capture maximum value from large accounts
- Often requires sales-assist (connects to product-led-sales skill)

### Feature Gating Principles

**Gate on value, not on punishment:**
- GOOD: Gate collaboration features (more users = more value = should pay more)
- GOOD: Gate advanced analytics (deeper insights = more value = should pay more)
- BAD: Gate basic export (user feels punished for wanting their own data)
- BAD: Gate removing branding/watermarks without value-add (feels like extortion)

**Limit on the dimension that correlates with value received:**
- If value scales with team size → limit seats
- If value scales with usage volume → limit usage
- If value scales with project complexity → limit projects or features
- If value scales with data → limit storage or history

**Feature allocation decision framework:**

| Question | If Yes | If No |
|----------|--------|-------|
| Is it needed for the aha moment? | Free tier | Consider gating |
| Does it primarily serve teams/orgs? | Paid tier | Could be free |
| Is it a security/compliance feature? | Enterprise tier | Lower tier |
| Does it create viral exposure? | Free tier (it markets for you) | Consider gating |
| Is it a power-user feature? | Pro/Team tier | Depends on above |

### Add-on Strategy

Add-ons work when:
- The feature serves a subset of users on any tier (not everyone needs it)
- It has standalone value (can be evaluated independently)
- It does not fragment the core experience
- Examples: advanced security pack, premium support, additional integrations, AI features

## 2. Pricing Metric (How You Charge)

### Metric Types

**Per-Seat (User-Based):**
- How it works: Price per user per month/year
- Best when: Each additional user gets independent value, value scales linearly with users
- Examples: Slack, Figma, Notion, Asana
- Pros: Predictable revenue, easy to understand, natural expansion
- Cons: Discourages broad adoption, users share accounts, penalizes collaboration
- PLG consideration: Can create tension with viral adoption (more users = more cost)

**Per-Usage (Consumption-Based):**
- How it works: Price per unit consumed (API calls, messages, storage, compute)
- Best when: Usage directly correlates with value, usage varies widely across customers
- Examples: Twilio, AWS, Snowflake, OpenAI
- Pros: Low barrier to start, revenue scales with value, fair pricing
- Cons: Unpredictable revenue (for vendor), bill shock risk (for customer), hard to budget
- PLG consideration: Natural freemium model (generous free tier with usage cap)

**Per-Feature (Module-Based):**
- How it works: Price for access to specific features or modules
- Best when: Product has distinct modules serving different needs
- Examples: HubSpot (Marketing Hub, Sales Hub, Service Hub)
- Pros: Customers pay only for what they need, clear upgrade path
- Cons: Complex pricing page, decision paralysis, may feel nickel-and-dime

**Per-Outcome (Value-Based):**
- How it works: Price per successful outcome (per lead generated, per transaction, per hire)
- Best when: Outcomes are measurable and directly attributable to the product
- Examples: Stripe (per transaction), job boards (per application)
- Pros: Perfect alignment between price and value, easy ROI calculation
- Cons: Revenue depends on customer success, requires robust measurement

**Hybrid:**
- How it works: Base price (platform fee or per-seat) + usage component
- Best when: There is a baseline value plus variable value
- Examples: Intercom (base + per-contact), Datadog (per-host + usage)
- Pros: Predictable base + growth upside, captures both types of value
- Cons: More complex pricing, harder to communicate

### Pricing Metric Selection Criteria

Score each candidate metric against these criteria:

| Criterion | Question | Why It Matters |
|-----------|----------|----------------|
| Value alignment | Does more usage of this metric = more value for the customer? | The metric should feel fair |
| Predictability | Can the customer predict their bill? | Bill shock kills trust |
| Growth alignment | Does the metric grow as the customer succeeds? | Natural expansion revenue |
| Measurability | Can you accurately meter this metric? | Billing accuracy is essential |
| Simplicity | Can you explain it in one sentence? | Complex metrics reduce conversion |
| Competitive fit | How do competitors charge? | Switching cost consideration |

### Value Metric Identification Process

1. List all dimensions that scale with customer value (users, usage, projects, data, outcomes)
2. For each, ask: "If a customer doubled this dimension, would they say they are getting 2x value?"
3. Score each on the 6 criteria above
4. Pick the metric where the answer is most clearly "yes" across criteria
5. Validate with MaxDiff research or customer interviews (see `research-methods.md`)

## 3. Price (What You Charge)

### Competitive Positioning

**Premium positioning:**
- Price 20-50% above market midpoint
- Requires: demonstrably superior product, strong brand, unique capabilities
- Risk: smaller addressable market, higher expectation bar
- Works for: products with strong differentiation and proof points

**Mid-market positioning:**
- Price within 10-20% of market midpoint
- Default safe choice for most PLG products
- Risk: undifferentiated, race to middle
- Works for: products competing on UX, integration, or ease of use

**Value positioning:**
- Price 30-50% below market midpoint
- Requires: cost advantage (lower COGS, more efficient delivery)
- Risk: perceived as low quality, attracts price-sensitive customers
- Works for: disruptors targeting underserved segment or simplifying complex tools

### Value-Based Pricing Principles

1. **Price to customer value, not to cost:** Your cost to serve is irrelevant to the customer. Their willingness to pay is based on the value they receive.
2. **Anchor to the alternative:** If replacing a $50K/year solution, pricing at $10K/year is compelling even if your cost is $100/year.
3. **Price fences, not discounts:** Create different tiers for different willingness-to-pay segments rather than discounting the same product.
4. **Annual billing as value exchange:** Offer 15-25% discount for annual commitment. This is not a discount — it is a fair exchange for revenue predictability and reduced churn.

### Price Anchoring Techniques

- **Decoy pricing:** Make the middle tier look like the best deal by pricing the top tier high
- **Penny-a-day:** Frame price as per-day or per-user-per-day to reduce sticker shock
- **ROI calculator:** Show the value delivered vs the price paid
- **Competitive comparison:** Show what the alternative costs (time, money, effort)
- **Feature-per-dollar:** Highlight features you include that competitors charge extra for
