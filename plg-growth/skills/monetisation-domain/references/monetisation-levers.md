# Monetisation Levers Checklist

A comprehensive checklist of levers across four categories: Conversion, Expansion, Contraction Prevention, and ARPA Improvement. Use this to audit your current monetisation mechanics and identify gaps.

---

## 1. Conversion Levers (Free → Paid)

### Checkout UX
- [ ] Upgrade flow is 3 clicks or fewer from trigger to payment
- [ ] No page reloads during checkout (single-page experience)
- [ ] Progress indicator shows steps remaining
- [ ] Form fields are minimal (auto-fill company info if possible)
- [ ] Mobile-optimized checkout
- [ ] Error handling is clear and non-destructive (no lost form data)

### Pricing Page Clarity
- [ ] Plans are easy to compare (side-by-side table)
- [ ] Recommended plan is visually highlighted
- [ ] Feature descriptions use user language, not jargon
- [ ] "Most popular" or social proof badge on target plan
- [ ] Per-user-per-month pricing displayed (even if billed annually)
- [ ] Clear indication of what is in free vs paid
- [ ] FAQ section addresses common objections
- [ ] Calculator or estimator for usage-based pricing

### Social Proof
- [ ] Customer logos on pricing page
- [ ] Testimonials specific to each plan/tier
- [ ] Case studies with ROI metrics
- [ ] "X companies upgraded this month" counter
- [ ] G2/Capterra rating badges
- [ ] Security/compliance badges (SOC2, GDPR)

### Urgency and Scarcity (use ethically)
- [ ] Limited-time offer for annual billing
- [ ] Trial expiry countdown (if applicable)
- [ ] Usage limit approaching notification
- [ ] "Your team is growing — unlock collaboration" prompt
- [ ] Seasonal or event-based promotions

### Payment Methods
- [ ] Credit/debit card (Visa, Mastercard, Amex)
- [ ] PayPal or digital wallet
- [ ] ACH/wire for enterprise
- [ ] Local payment methods for key markets
- [ ] Invoice/PO option for enterprise (purchase order flow)
- [ ] Crypto (if relevant to audience)

### Annual Discount
- [ ] Annual option presented alongside monthly
- [ ] Savings clearly displayed ("Save 20%" or "2 months free")
- [ ] Default to annual (with easy switch to monthly)
- [ ] Annual is the anchor price, monthly is the "premium"

### Free Trial Extension Offers
- [ ] Offer trial extension when user has not activated
- [ ] Extend trial in exchange for completing onboarding steps
- [ ] "Not ready? Get 7 more days" at trial end
- [ ] Use extension as data collection opportunity (why not ready?)

---

## 2. Expansion Levers (Grow Revenue from Existing Customers)

### Seat-Based Expansion
- [ ] Track active users per account vs paid seats
- [ ] Identify accounts with unpaid collaborators (sharing logins)
- [ ] Prompt team admin when new members are added
- [ ] "Invite your team" CTA in collaboration contexts
- [ ] Volume discount tiers to encourage bulk seat purchases
- [ ] Self-serve seat addition (no sales call needed)
- [ ] Usage data: track when team size outgrows current plan

**Triggers to monitor:**
- New user invited to workspace
- Shared project/doc created with external email
- Account reaches seat limit
- Multiple users accessing from same company domain

### Feature-Based Expansion (Upsell)
- [ ] In-product discovery of premium features (visible but gated)
- [ ] "Upgrade to unlock" prompts at point of need
- [ ] Feature usage tracking to identify power users approaching limits
- [ ] Contextual upgrade prompts (not interrupting workflow)
- [ ] Free trial of premium feature for limited time
- [ ] Feature comparison in settings/account page

**Triggers to monitor:**
- User attempts to use a gated feature
- User hits usage limit (projects, storage, API calls)
- User searches for or views documentation of premium feature
- User's usage pattern matches power-user profile

### Add-On Cross-Sell
- [ ] Add-ons visible in product (not just pricing page)
- [ ] Contextual recommendation: "Based on your usage, you might benefit from..."
- [ ] Bundle discounts for multiple add-ons
- [ ] Free trial of add-on triggered by relevant behavior
- [ ] Add-on marketplace or catalog

**Triggers to monitor:**
- User workflow touches add-on territory (e.g., security review → security add-on)
- User integrates with tool that has a premium integration available
- Support ticket about a topic solved by an add-on

---

## 3. Contraction Prevention Levers (Prevent Downgrades and Churn)

### Seat Utilization Monitoring
- [ ] Track seats paid vs seats active (monthly)
- [ ] Alert CSM/system when utilization drops below 60%
- [ ] Proactive outreach for under-utilized accounts
- [ ] Identify "zombie seats" (paid but inactive >30 days)
- [ ] Offer seat right-sizing proactively (builds trust, prevents churn)

### Downgrade Friction (ethical, not punitive)
- [ ] Downgrade flow shows what they will lose (specific features, data)
- [ ] Offer pause option instead of downgrade
- [ ] Offer reduced plan (bridge tier) instead of full downgrade
- [ ] "Talk to us" option to understand and solve the real issue
- [ ] Survey: reason for downgrade (mandatory, brief)

### Value Demonstration at Renewal
- [ ] Monthly/quarterly usage report emailed to admins
- [ ] "Your team accomplished X this month with [Product]" summary
- [ ] ROI calculator populated with their actual data
- [ ] Renewal email 30 days before annual renewal with value summary
- [ ] In-app dashboard showing usage trends and value metrics

### Churn Risk Signals
- [ ] Login frequency decline
- [ ] Key feature usage drop
- [ ] Admin login absence
- [ ] Support ticket spike (frustration)
- [ ] Competitor evaluation signals (if detectable)
- [ ] Failed payment + no update after 3 attempts

---

## 4. ARPA Improvement Levers

### Upsell Triggers
- [ ] Usage-based threshold approaching: "You have used 80% of your plan limit"
- [ ] Team growth signal: "Your team added 5 new members this month"
- [ ] Feature adoption signal: "You are using 3 premium features — upgrade for full access"
- [ ] Time-based trigger: "You have been on Free for 90 days — here is what Pro unlocks"
- [ ] Milestone trigger: "Congratulations on your 100th project — Pro users average 3x more"

### Cross-Sell Opportunities
- [ ] Identify complementary products or add-ons based on usage
- [ ] "Customers like you also use..." recommendation
- [ ] Bundle pricing that is cheaper than buying individually
- [ ] Integration partnerships that drive add-on adoption

### Annual Billing Incentives
- [ ] Monthly-to-annual conversion campaign
- [ ] "Lock in current price" before price increase
- [ ] Annual billing as default for new signups
- [ ] Multi-year discounts for enterprise
- [ ] Cash flow benefit messaging for finance buyers

### Price Increase Strategy
- [ ] Grandfathering: existing customers keep current price for X months
- [ ] Value increase before price increase (add features first)
- [ ] 60-90 day advance notice
- [ ] Price increase applies to new customers first, then renewal
- [ ] Segment by sensitivity: increase prices for segments with highest value-to-price ratio first

---

## Prioritization Framework

When deciding which levers to pull first:

| Factor | Weight | How to Assess |
|--------|--------|---------------|
| Revenue impact | High | Model the $ impact of improving this lever by 10-20% |
| Effort to implement | Medium | Engineering/design time required |
| Risk | Medium | Could this backfire? (Churn risk, brand damage) |
| Speed to impact | Medium | Days, weeks, or months to see results? |
| Data readiness | Low | Do you have the data to measure this lever today? |

**Typical priority order for most PLG products:**
1. Pricing page clarity (low effort, immediate impact)
2. Upgrade prompts at usage limits (moderate effort, high signal)
3. Annual billing incentive (low effort, revenue predictability)
4. Seat utilization monitoring (moderate effort, contraction prevention)
5. Checkout flow optimization (moderate effort, conversion lift)
6. Value demonstration at renewal (moderate effort, retention)
