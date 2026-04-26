# Product-Led Acquisition Strategies

Four strategies for acquiring users through the product itself, rather than through sales or marketing alone. Each section covers the mechanism, prerequisites, measurement, and examples.

---

## 1. Viral Acquisition

Viral acquisition means your existing users bring new users as a natural byproduct of using the product.

### Three Types of Virality

#### Exposure Virality
**Mechanism:** Using the product inherently exposes non-users to it.
- The act of using the product IS the marketing
- Non-users see the product in action and want it

**Examples:**
- Calendly: Every meeting invite shows the Calendly brand and link
- Loom: Every video share exposes the viewer to Loom
- Typeform: Every form shows "Made with Typeform"
- Slack: Every external channel invite exposes Slack

**Prerequisites:**
- Product output is shared externally (documents, links, embeds, messages)
- The shared artifact is compelling enough to drive curiosity
- Clear path from exposure to signup (CTA on shared content)

**Optimization levers:**
- Increase frequency of sharing (make sharing the default, not an option)
- Improve CTA on shared artifacts (what does the viewer see?)
- Reduce friction from exposure to signup (one-click from shared content)

#### Incentivised Virality
**Mechanism:** Users are rewarded for bringing others.
- Both referrer and referee get value (double-sided incentive most effective)
- Reward aligns with product value (credits, features, storage)

**Examples:**
- Dropbox: 500MB extra storage per referral (both sides)
- PayPal: Cash bonus for referrer and referee
- Notion: Credits toward paid plan

**Prerequisites:**
- Clear value to offer as incentive (storage, credits, features)
- Existing engaged user base (unhappy users will not refer)
- Tracking infrastructure for referral attribution

**Optimization levers:**
- Incentive value: must be meaningful but sustainable
- Double-sided vs. single-sided: double-sided converts 2-3x better
- Visibility: referral prompt at moments of delight, not frustration
- Simplicity: one-click sharing, pre-written message, unique link

#### Collaboration Virality
**Mechanism:** The product requires or improves with multiple users.
- Core use case is inherently multi-player
- Inviting others is how you USE the product, not a marketing ask

**Examples:**
- Figma: Design collaboration requires sharing with team
- Miro: Whiteboarding is multi-person by nature
- Google Docs: Collaboration IS the product
- Slack: Messaging requires other people

**Prerequisites:**
- Multi-player use case exists in the core workflow
- Product is better with more people (not just "also works with others")
- Invite flow is integrated into the core task (not a separate "invite" page)

**Optimization levers:**
- Make collaboration the default first action (not solo work)
- Reduce invite friction (email, link, SSO domains)
- Show value of collaboration vs. solo (empty state messaging)

### Viral Metrics

**Viral Coefficient (k-factor):**
```
k = i x c
where:
  i = average invites sent per user
  c = conversion rate of invites to new users
```
- k > 1: exponential viral growth (rare and usually temporary)
- k = 0.5-1.0: strong viral supplement to other channels
- k = 0.2-0.5: moderate viral contribution
- k < 0.2: virality is not a meaningful channel

**Viral Cycle Time:**
Time from user signup to their invitees signing up. Shorter = more powerful.
- Hours: messaging apps, collaboration tools (very fast cycles)
- Days: productivity tools, content tools
- Weeks: enterprise tools, complex products

**Impact formula:**
Total viral impact = k-factor / (1 - k-factor) when k < 1
At k = 0.5: each organic user generates 1 additional user (100% amplification)
At k = 0.7: each organic user generates 2.3 additional users (230% amplification)

---

## 2. Product-Driven SEO

Product-driven SEO means your product generates indexable pages that rank in search and bring new users.

### The UGC Indexing Flywheel
```
More users → More user-generated content → More indexed pages → More organic traffic → More users
```

**Examples:**
- Pinterest: User-created boards/pins rank for millions of long-tail queries
- Yelp: Business reviews rank for "[business] reviews" and "[category] near me"
- Canva: Template pages rank for "free [type] template"
- Notion: Public pages and templates index for productivity searches

### Page Types That Drive SEO

**User-Generated Content Pages:**
- Profiles, portfolios, public projects
- Reviews, answers, discussions
- Templates, galleries, collections

**Tool/Calculator Pages:**
- Free tools that solve a specific micro-problem
- Calculators, converters, generators
- Each tool targets a specific search query

**Template/Resource Pages:**
- Pre-built templates for common use cases
- Each template is a landing page for a search intent
- "Free [product type] template" queries

### Prerequisites
- Product generates public, indexable content naturally
- Content is unique and valuable (not thin/duplicate)
- Technical SEO foundation: fast load, mobile-friendly, structured data
- Volume: need hundreds to thousands of pages to see meaningful traffic

### Measurement
- Pages indexed / pages created ratio
- Organic traffic from product pages vs. marketing pages
- Signup rate from organic product page visitors
- Time from content creation to indexing to ranking

---

## 3. Piggybacking

Piggybacking means distributing your product through platforms, marketplaces, or ecosystems where your users already are.

### Distribution Mechanisms

**Marketplace Integrations:**
- List in app stores / marketplaces of adjacent platforms
- Salesforce AppExchange, Shopify App Store, Chrome Web Store, VS Code Marketplace
- Users discover your product while looking for solutions within their existing tool

**Embed / Widget Codes:**
- Embeddable product components that live on other websites
- Intercom chat widget, Typeform embedded forms, Calendly scheduling widget
- Every embed is a distribution point

**API Partnerships:**
- Power features within another product via API
- Users experience your technology through the partner product
- Conversion path: user sees "Powered by [you]" → explores your standalone product

**Platform Distribution:**
- Build on top of a growing platform (early Zynga on Facebook, early apps on iPhone)
- Ride the platform's growth curve
- Risk: platform dependency

### Prerequisites
- Clear integration value proposition (why install this?)
- Technical capability to build and maintain integrations
- Partner platform has meaningful user overlap with your ICP
- Conversion path from integration user to standalone user

### Evaluation Criteria
- Platform user volume and growth trajectory
- Overlap with your ICP (not just volume, but fit)
- Integration effort vs. expected user acquisition
- Platform risk: dependency, policy changes, competition from platform

---

## 4. Sidecar Products

Sidecar products are free, standalone tools designed to attract your ICP and funnel them to your core product.

### The Concept
Build a small, free tool that:
1. Solves a specific, narrow problem your ICP has
2. Requires no signup or very low friction to use
3. Naturally leads to awareness of your core product
4. Is SEO-friendly and shareable

### Classic Examples

**HubSpot Website Grader:**
- Free tool: enter your URL, get a website grade
- ICP: marketers who care about website performance
- Funnel: use grader → see areas for improvement → discover HubSpot marketing tools

**Snyk Open Source:**
- Free tool: scan your code for security vulnerabilities
- ICP: developers who care about code security
- Funnel: use free scanner → discover vulnerabilities → want Snyk for continuous protection

**CoSchedule Headline Analyzer:**
- Free tool: paste a headline, get a quality score
- ICP: content marketers
- Funnel: optimize headlines → discover CoSchedule content planning tools

### Design Principles
- **Instant value:** No signup required for first use. Value in seconds.
- **ICP magnet:** Solve a problem ONLY your ICP has (not a generic tool)
- **Natural bridge:** The sidecar output should surface a problem your core product solves
- **SEO-native:** Target high-volume search queries your ICP searches
- **Shareable:** Results should be shareable (creates exposure virality)

### Prerequisites
- Clear ICP definition (who are you attracting?)
- Identified ICP pain point that can be solved with a small tool
- Engineering capacity to build and maintain a standalone tool
- SEO/content team to drive traffic to the sidecar

### Measurement
- Sidecar tool usage volume
- Sidecar → core product signup conversion rate
- SEO traffic to sidecar pages
- Quality of sidecar-sourced users (activation rate, retention, monetization)

---

## Strategy Evaluation Matrix

Use this matrix to assess which strategies fit your product. Score each cell Green/Yellow/Red.

| Criterion | Viral | Product-Driven SEO | Piggybacking | Sidecar |
|-----------|-------|--------------------|--------------|---------|
| **Structural fit** | Product output is shared externally? Multi-player? | Product generates indexable content? | Adjacent platforms with ICP overlap? | Identifiable ICP micro-problem? |
| **Expected yield** | k-factor estimate? | Addressable search volume? | Platform user volume? | Search volume for tool? |
| **Investment** | Invite flow + CTA engineering | SEO infrastructure + content at scale | Integration development + maintenance | Standalone tool development |
| **Time to impact** | Weeks-months (if structural fit exists) | 3-6 months (SEO timeline) | 1-3 months (marketplace listing) | 2-4 months (build + SEO ramp) |
| **Defensibility** | High if collaboration-driven | Moderate (content moat) | Low (platform-dependent) | Low-moderate (easy to copy) |

### Decision Guide

- **Pursue if Green on structural fit AND yield.** Investment and time are secondary -- if the strategy fits and the yield is there, find the resources.
- **Investigate if Yellow on structural fit.** Run a small experiment to validate before committing.
- **Skip if Red on structural fit.** No amount of investment overcomes structural misfit.
- **Pursue multiple strategies.** These are not mutually exclusive. Most successful PLG companies use 2-3 simultaneously.
