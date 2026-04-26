# Growth Loop Types

A comprehensive taxonomy of growth loops. Every loop follows the same core pattern: User Action → Exposure to Non-Users → Conversion → New User Takes Action → Loop Repeats.

The critical distinction: **Real Loops** compound organically (the product itself drives growth). **Technical Loops** require ongoing investment (money or effort) to sustain.

---

## Real Loops (Organic, Compounding)

### Viral Loops

#### Exposure Viral

**Mechanism:** Normal product usage creates visibility to non-users. No special sharing action required — the product markets itself through regular use.

**How it works:**
1. User performs a normal product action (sends a link, creates a document, shares output)
2. The output is visible to a non-user and carries product branding or a signup CTA
3. Non-user experiences value or sees the product in action
4. Non-user signs up to get the same capability
5. New user performs the same action, exposing more non-users

**Product fit criteria:**
- [ ] Product output is sent to or viewed by non-users as part of normal workflows
- [ ] The output demonstrates product value without explanation
- [ ] There is a natural conversion path from viewing output to signing up
- [ ] The product brand is visible in the output (link, badge, watermark)

**Key metrics:**
- Exposure rate: % of users whose actions are seen by non-users
- View-to-signup rate: % of non-users who see the product and sign up
- Cycle time: time from user action to new user taking the same action

**Examples:**
- **Calendly:** Every meeting link is a product demo. Recipient sees the scheduling experience, brand, and a "Create your own" CTA. k ~0.15, cycle time 2-5 days.
- **Linktree:** Every bio link is a permanent product advertisement. Visitors see the product experience on every social profile. k ~0.05, cycle time very short.
- **Figma:** Shared design prototypes show the Figma interface to stakeholders, who may sign up.
- **Loom:** Video recipient sees the Loom player, branding, and "Record your own" CTA.
- **DocuSign:** Every signing request exposes DocuSign to the signer.

**Strengths:** Completely organic, zero marginal cost, product quality drives loop strength.
**Weaknesses:** Low k-factor per user (most exposure loops have k 0.05-0.2), hard to optimize directly.

---

#### Incentivised Viral

**Mechanism:** Users are explicitly rewarded for inviting non-users. The reward creates a motivation to share beyond natural product behavior.

**How it works:**
1. User is offered a reward for inviting others (credits, storage, features, money)
2. User sends invitations to contacts
3. Invitee receives the invitation with a value proposition
4. Invitee signs up (possibly also receiving a reward)
5. New user is incentivised to invite their own contacts
6. Loop repeats

**Product fit criteria:**
- [ ] Clear value exchange for both referrer and referred (double-sided reward works best)
- [ ] Reward is meaningful but sustainable (marginal cost of delivery is low)
- [ ] Product has a natural reason to share (recommending to someone who would benefit)
- [ ] Users can easily identify who to invite (contacts, colleagues, friends)

**Key metrics:**
- Invitation rate: % of users who send at least one invitation
- Invitations per inviter: average number of invites sent
- Invite acceptance rate: % of invitations that result in signup
- k-factor: invitation rate x invitations per inviter x acceptance rate
- CAC equivalent: cost of reward / new users acquired

**Examples:**
- **Dropbox:** "Get 500MB free for each friend who joins" — both referrer and referred get storage. Famous for driving early growth.
- **Uber:** Referral credits for both rider and referred rider.
- **Notion:** Earn credits toward paid plan for successful referrals.

**Strengths:** Higher k-factor than exposure viral (users are motivated to share), can be tuned (adjust reward to adjust volume).
**Weaknesses:** Attracts low-quality users (motivated by reward, not product value), reward costs add up, can feel spammy.

---

#### Collaboration Viral

**Mechanism:** The product requires or strongly benefits from multiple users. Getting value from the product inherently requires inviting others.

**How it works:**
1. User signs up and starts using the product
2. To get full value, user needs to invite collaborators (teammates, clients, partners)
3. Invited users sign up to participate
4. New users become active and invite their own collaborators
5. Loop compounds as each new user adds their network

**Product fit criteria:**
- [ ] Product value is fundamentally collaborative (team communication, shared workspace, project management)
- [ ] Single-user value is limited (creates urgency to invite)
- [ ] Invitation friction is low (invite by email, link, or SSO domain)
- [ ] New users can contribute value immediately (no lengthy onboarding)

**Key metrics:**
- Invitations per user in first 7 days
- Invitation-to-signup conversion rate
- Time to first collaboration action
- Team size growth rate per account
- k-factor: typically highest among viral types (0.2-0.5+)

**Examples:**
- **Slack:** Messaging tool is useless alone. Every new team member must be invited. Each new member may invite more people or start new channels.
- **Figma:** Collaborative design requires inviting reviewers, developers, and other designers.
- **Notion:** Shared workspaces need team members. Templates and pages are shared across teams.
- **Linear:** Issue tracking requires the whole engineering team.

**Strengths:** Highest k-factor among viral loops, users are genuinely motivated (not just incentivised), expansion is natural.
**Weaknesses:** Slow cycle time (team onboarding takes time), initial "cold start" problem (first user has low value), high activation effort.

---

### Content Loops

#### Content Loop by Distribution Channel

**Mechanism:** Users create content on the platform. The content is distributed through a channel (search, social) that brings new users to the platform who create more content.

**How it works:**
1. User creates content on the platform (answers, reviews, templates, tutorials)
2. Content is indexed by search engines or shared on social platforms
3. Non-users discover the content through search or social feeds
4. Non-users consume the content and some sign up to contribute
5. New users create their own content
6. Loop repeats with a growing content library

**Product fit criteria:**
- [ ] Users naturally create content as part of product usage
- [ ] Content is publicly accessible (not behind auth wall)
- [ ] Content is indexable by search engines (proper technical SEO)
- [ ] Content addresses long-tail search queries or social interest
- [ ] There is a clear path from content consumption to signup

**Subtypes:**

**UGC → SEO → Traffic → More UGC:**
- Content is indexed, drives organic search traffic
- Examples: Quora (answers), Stack Overflow (Q&A), G2 (reviews), Yelp (reviews)
- Key metric: pages indexed, ranking distribution, organic traffic to signup rate
- Cycle time: weeks to months (SEO is slow)

**UGC → Social → Traffic → More UGC:**
- Content is shared on social platforms, drives social traffic
- Examples: Pinterest (pins), TikTok (videos), Medium (articles)
- Key metric: shares per content piece, social traffic to signup rate
- Cycle time: hours to days (social is fast but less durable)

---

#### Content Loop by Creator

**Mechanism:** Professional creators use the platform to reach an audience. The audience grows the platform, which attracts more creators.

**How it works:**
1. Creator publishes content on the platform
2. Creator promotes their content to their existing audience
3. Audience visits the platform to consume content
4. Some audience members become creators themselves
5. More creators attract more audience
6. Loop compounds

**Product fit criteria:**
- [ ] Platform supports content creation and distribution
- [ ] Creators have an incentive to publish on the platform (audience, monetisation, tools)
- [ ] Audience can discover content easily (feed, recommendations, search)
- [ ] Low barrier for audience members to become creators

**Examples:**
- **Substack:** Writers bring their audience. Audience discovers other writers. Some readers become writers.
- **YouTube:** Creators upload videos, audience subscribes, some viewers become creators.
- **Teachable/Gumroad:** Course creators bring students, students discover other courses.

---

## Technical Loops (Investment-Dependent)

### Paid Loop

**Mechanism:** Revenue is reinvested into paid acquisition, which generates more revenue.

**How it works:**
1. Spend money on paid channels (SEM, social ads, display, sponsorships)
2. Traffic converts to signups
3. Signups convert to paid customers
4. Revenue exceeds cost of acquisition (LTV > CAC)
5. Reinvest surplus into more paid acquisition
6. Loop continues as long as LTV > CAC and channels are not saturated

**Product fit criteria:**
- [ ] Positive unit economics (LTV > CAC with healthy margin)
- [ ] Scalable paid channels exist (search volume, audience size)
- [ ] Conversion funnel is optimized (spend is not wasted on leaky funnels)
- [ ] Payback period is manageable (cash flow can sustain acquisition investment)

**Key metrics:**
- CAC by channel
- LTV:CAC ratio (target: 3:1+)
- Payback period (months to recoup CAC)
- Channel capacity (how much can you spend before diminishing returns?)

**Strengths:** Predictable, scalable (up to channel capacity), controllable.
**Weaknesses:** Not compounding (stops when you stop spending), competitive (CPAs increase), requires capital.

---

### Outbound Sales Loop

**Mechanism:** Revenue from sales funds more sales capacity, which generates more revenue.

**How it works:**
1. SDR/AE team generates and works leads
2. Leads convert to customers
3. Revenue funds more sales hiring
4. More salespeople generate more leads and close more deals
5. Loop continues as revenue supports team growth

**Product fit criteria:**
- [ ] High enough ACV to justify sales cost (typically $10K+ ACV)
- [ ] Identifiable target accounts
- [ ] Repeatable sales process
- [ ] Positive sales unit economics (revenue per rep > fully loaded cost per rep)

**Note:** In PLG, the sales loop is typically powered by product signals (PQA/PQL), making it a hybrid. See `product-led-sales` skill for the PLS-specific version.

---

## Loop Selection Framework

When evaluating which loops to pursue, score each on:

| Factor | Weight | How to Assess |
|--------|--------|---------------|
| Structural fit | Critical | Does the product have the prerequisites? (No = disqualify) |
| Expected k-factor | High | Estimate based on comparable products |
| Cycle time | High | Faster cycles = faster compounding |
| Implementation effort | Medium | Engineering, design, content investment required |
| Sustainability | Medium | Will the loop continue without ongoing investment? |
| Quality of users acquired | Medium | Do loop-acquired users retain and pay? |

**Decision heuristic:**
1. Eliminate loops that fail structural fit criteria
2. Among remaining, prioritize by: highest k-factor x shortest cycle time
3. If multiple loops are viable, start with the one requiring least implementation effort
4. Always validate that loop-acquired users retain (otherwise you are filling a leaky bucket faster)
