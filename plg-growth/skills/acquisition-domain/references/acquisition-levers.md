# Acquisition Levers

Complete checklist of levers for improving product-led acquisition. Organized by category. Use this as a diagnostic tool: walk through each section, assess current state, identify gaps.

---

## 1. Signup Optimization

The signup flow is the single highest-leverage conversion point. Every percentage point improvement here compounds across all traffic.

### Authentication Methods
- [ ] **Passwordless auth:** Magic link or OTP via email. Eliminates password friction entirely.
- [ ] **OAuth / Social login:** Google, GitHub, Microsoft, Apple. One-click signup for users with existing accounts.
- [ ] **SSO support:** For enterprise/team signups. SAML, OKTA, Azure AD.
- [ ] **Domain-based auto-join:** Users from the same company domain auto-join the existing workspace.

### Form Optimization
- [ ] **Minimal required fields:** Name + email (or just email). Every additional field reduces conversion 5-15%.
- [ ] **Progressive profiling:** Collect additional info AFTER signup, during onboarding, when context makes the ask natural.
- [ ] **Smart defaults:** Pre-fill what you can (company from email domain, timezone from browser, name from OAuth).
- [ ] **Inline validation:** Real-time feedback on form fields. Do not make users submit to find errors.

### Friction Reduction
- [ ] **No credit card required:** For free tier or trial. "No credit card" badge increases signups 10-25%.
- [ ] **Instant access:** Skip email verification for initial access. Verify later or use magic link.
- [ ] **Mobile-optimized:** Responsive signup that works on phone. Especially important if acquisition channels are social/mobile.
- [ ] **Speed:** Signup page loads in under 2 seconds. Every second of load time costs 7% conversion.

### Social Proof on Signup
- [ ] **Customer logos:** Recognizable brands near the signup form.
- [ ] **User count:** "Join 50,000+ teams" (only if number is impressive).
- [ ] **Ratings/reviews:** G2, Capterra, Product Hunt badges.
- [ ] **Testimonials:** Short, specific, from ICP-matching users.

---

## 2. Expectation Setting (Website-to-Product Alignment)

Users who arrive with correct expectations activate faster and retain better. Misalignment = high signup, low activation.

### Website Clarity
- [ ] **Value proposition matches product:** What the homepage promises is what the product delivers in session 1.
- [ ] **Feature previews:** Screenshots, videos, or interactive demos that show the actual product (not abstract illustrations).
- [ ] **Pricing transparency:** Clear pricing page. Users who self-select on price are higher quality.
- [ ] **Use case pages:** Dedicated pages for each ICP segment showing relevant workflows.

### Pre-Signup Experience
- [ ] **Interactive demo:** Let users try core features before signup (product tours, sandbox environments).
- [ ] **Content that educates:** Blog posts, guides, videos that teach the problem space (not just the product).
- [ ] **Community access:** Public community (Slack, Discord, forum) where prospects see real users.

### Handoff Quality
- [ ] **Landing page to signup continuity:** If a user clicks from a "project management" page, the signup flow should reference project management.
- [ ] **Ad-to-page match:** Paid ad copy matches landing page headline and product experience.
- [ ] **Referral context:** If a user comes via referral, the experience acknowledges the referrer and context.

---

## 3. Personalization (Gathering Info to Customize)

Onboarding questions are not friction -- they are investment in a better first experience. But they must be done right.

### Onboarding Questions (ask during or immediately after signup)
- [ ] **Use case / JTBD:** "What are you trying to accomplish?" (2-4 options matching your primary use cases)
- [ ] **Role:** "What is your role?" (to tailor UI, features, and content)
- [ ] **Team size:** "How large is your team?" (to tailor collaboration features and pricing)
- [ ] **Experience level:** "Have you used [category] tools before?" (to tailor onboarding depth)

### Personalization Tactics
- [ ] **Use-case routing:** Based on answers, show different first-run experiences, templates, or tutorials.
- [ ] **Role-based dashboards:** Different default views for different roles.
- [ ] **Template pre-selection:** Auto-suggest templates matching the stated use case.
- [ ] **Email drip customization:** Onboarding emails reference the stated use case and role.

### Design Principles for Onboarding Questions
- **2-4 questions maximum.** Every question must change the experience. If the answer does not change what you show, do not ask.
- **Visual, not text-heavy.** Icons/illustrations for each option. Feels like choosing, not filling out a form.
- **Skippable.** Always allow "Skip" but track skip rate. High skip rate = questions feel irrelevant.
- **Show progress.** "Step 1 of 3" reduces anxiety.

---

## 4. Channel-Specific Acquisition Levers

### Organic Channels

#### SEO
- [ ] **Keyword strategy:** Target ICP search queries, not vanity terms.
- [ ] **Product-driven pages:** UGC, templates, tools that index (see product-led-strategies.md).
- [ ] **Content hub:** Educational content organized by topic cluster, not random blog posts.
- [ ] **Technical SEO:** Fast, mobile-friendly, structured data, internal linking.

#### Content Marketing
- [ ] **ICP-relevant topics:** Content that your ICP searches for when they have the problem you solve.
- [ ] **Content-to-signup path:** Every piece of content has a relevant CTA (not just "sign up" but "try this feature").
- [ ] **Gated vs. ungated:** Gate sparingly. Ungated content builds trust and SEO. Gate only high-value assets.

#### Community
- [ ] **Own community:** Slack/Discord/forum where ICP gathers.
- [ ] **Community content:** AMAs, showcases, challenges that generate shareable content.
- [ ] **Ambassador/champion program:** Power users who evangelize in their networks.

#### Word of Mouth
- [ ] **NPS > 40:** Prerequisite for organic WOM. If NPS is low, fix product before investing in WOM.
- [ ] **Shareable moments:** Features that generate content worth sharing (reports, achievements, creations).
- [ ] **Review cultivation:** Systematically ask happy users to review on G2, Capterra, Product Hunt.

### Paid Channels

#### Benchmarks (PLG SaaS)
- Paid search CAC: $50-$200 for SMB, $200-$1000 for mid-market
- Paid social CAC: $30-$150 for SMB
- Content syndication: $100-$500 per MQL

#### Channel-Market Fit Assessment
For each channel, evaluate:
- [ ] **Reach:** Does ICP use this channel? At what volume?
- [ ] **Intent:** Are users in discovery/research mode on this channel?
- [ ] **Cost:** CAC vs. LTV ratio (target 3:1+ for healthy unit economics)
- [ ] **Scalability:** Can you increase spend while maintaining CAC?

### Product-Led Channels

#### Viral
- [ ] **Invite flow:** Integrated into core workflow, not a separate page.
- [ ] **Share mechanics:** Easy sharing of output (links, embeds, exports with branding).
- [ ] **Referral program:** Double-sided incentives for existing users to invite.

#### Referral
- [ ] **Referral link:** Unique, trackable link per user.
- [ ] **Incentive:** Meaningful reward for both referrer and referee.
- [ ] **Prompt timing:** Ask for referral at moments of delight (after activation, after a win).
- [ ] **Visibility:** Referral option visible in product (not buried in settings).

#### Embed / Integration
- [ ] **Embeddable widgets:** Core product functionality in an embeddable format.
- [ ] **Marketplace listings:** Present in relevant app stores and directories.
- [ ] **Powered-by branding:** Attribution on embedded/integrated product surfaces.

---

## 5. Acquisition Quality Diagnostics

### Signals of Quality Problems
- High signup volume but low activation rate = wrong users or misaligned expectations
- High CAC channel outperforming on activation = may be worth the premium
- Referral users activating at 2x rate = expand referral program
- One channel drives 80% of signups but 20% of revenue = channel-market misfit

### Quality Metrics to Track
- Signup-to-activation rate by channel
- 30-day retention by acquisition source
- LTV by acquisition channel
- ICP match rate by channel (if ICP scoring exists)
- Time-to-activation by channel

### The Channel Scorecard

For each active acquisition channel, maintain:

| Metric | Channel A | Channel B | Channel C |
|--------|-----------|-----------|-----------|
| Monthly signups | | | |
| CAC | | | |
| Signup → Activation % | | | |
| 30-day retention | | | |
| Estimated LTV | | | |
| LTV:CAC ratio | | | |
| Payback period | | | |
| Scalability (1-5) | | | |

Channels with LTV:CAC > 3:1 and payback < 12 months deserve more investment. Channels below 1:1 should be cut or radically redesigned.
