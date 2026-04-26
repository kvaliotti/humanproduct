# PLG Suitability Criteria — Scoring Rubric

## Overview

Four criteria determine baseline PLG viability. Score each 1-5. These are necessary but not sufficient conditions — a product must also pass pillar, PMF, and decision-driver assessments.

---

## Criterion 1: Self-Serve Capability

**Question:** Can a user sign up, set up, and derive value from the product without human assistance?

| Score | Description | Examples |
|-------|-------------|----------|
| 5 | Fully self-serve. User signs up and gets value in one session, zero human touch. | Canva, Notion, Slack, Figma |
| 4 | Mostly self-serve. Occasional help docs or tooltips needed, but no human required. | Amplitude, Airtable |
| 3 | Partially self-serve. User can start alone but hits walls that require support/onboarding calls. | HubSpot CRM, Mixpanel |
| 2 | Minimally self-serve. User can browse/explore but cannot get real value without guided setup. | Salesforce, Workday |
| 1 | Not self-serve. Product requires implementation, data migration, custom configuration by specialists. | SAP, Epic (healthcare) |

**Probing questions:**
- Can a user complete the core use case without talking to anyone?
- What % of signups reach first value without support intervention?
- How long is the setup before first use? (Minutes vs. hours vs. days)
- Does the product require connecting data sources, importing content, or configuring workflows before any value?

**Improvement levers (if score < 4):**
- Pre-populated templates / sample data
- Progressive onboarding (don't require full setup upfront)
- Sandbox or playground mode
- Guided setup wizard with smart defaults

---

## Criterion 2: Low Barrier to Start

**Question:** How easy is it for someone to begin using the product? Consider cost, time, approval, and technical barriers.

| Score | Description | Examples |
|-------|-------------|----------|
| 5 | Instant, free, no approval needed. Sign up with email/Google, start immediately. | Notion, Linear, Loom |
| 4 | Free tier or trial, minimal friction. Might need work email or brief form. | Slack, Datadog free tier |
| 3 | Free trial but requires credit card, or significant form-fill, or manager approval at some companies. | Salesforce trial, Adobe CC trial |
| 2 | Demo/consultation required to access. Free tier exists but is extremely limited. | Enterprise analytics tools |
| 1 | Must go through procurement, legal, security review before any access. RFP process. | Enterprise infrastructure, regulated industries |

**Probing questions:**
- Can someone start today if they decided right now?
- Is there a credit card requirement?
- Do they need manager/IT approval?
- Is there a security review or compliance gate?
- How many fields in the signup form?

**Improvement levers (if score < 4):**
- Remove credit card requirement for trial
- Reduce signup form fields (name + email minimum)
- Offer browser-based experience (no download/install)
- Create ungated preview or demo
- SSO/Google sign-in to reduce friction

---

## Criterion 3: Value Demonstrable Pre-Purchase

**Question:** Can the user experience the core value proposition before paying? How quickly?

| Score | Description | Examples |
|-------|-------------|----------|
| 5 | Aha moment in < 5 minutes. Core value is immediately obvious and experienced. | Canva (design created), Loom (video recorded), Grammarly (errors caught) |
| 4 | Aha moment in < 1 hour. Requires some setup but value is clear within first session. | Notion (workspace organized), Figma (design collaboration experienced) |
| 3 | Aha moment in < 1 day. Needs data import, team onboarding, or multi-step configuration. | Amplitude (first insight from data), Slack (team communication flowing) |
| 2 | Aha moment in days-weeks. Value emerges over time with accumulated data or adoption. | CRM tools (pipeline visibility), project management (team adoption) |
| 1 | Aha moment in weeks-months. Value requires organizational change, full data migration, or long observation period. | ERP systems, data warehouses, security platforms |

**Probing questions:**
- What is the aha moment? (Define it precisely)
- How long from signup to aha moment? (TTV — time to value)
- Can the aha moment happen with sample/demo data, or does it require the user's own data?
- Is the aha moment for an individual or does it require team participation?

**Improvement levers (if score < 4):**
- Pre-load sample data that demonstrates value
- Create a "quick win" workflow that proves value before full setup
- Show value preview before signup (ungated demo)
- Reduce steps between signup and aha moment
- Focus free experience on fastest-to-value use case

---

## Criterion 4: Natural Expansion Dynamics

**Question:** Does product usage naturally lead to more users, more usage, or higher revenue without sales intervention?

| Score | Description | Examples |
|-------|-------------|----------|
| 5 | Strong viral loop + seat expansion. Product is shared/embedded in daily work, pulling in new users organically. | Slack (invite team), Figma (share design), Loom (send video), Notion (share workspace) |
| 4 | Good expansion mechanics. Seat growth, usage-based pricing, or natural sharing. | Datadog (more hosts), Twilio (more API calls), Airtable (invite collaborators) |
| 3 | Some expansion potential. Users might invite others but it is not core to the value prop. Upsell requires prompting. | Analytics tools, project management, documentation |
| 2 | Limited natural expansion. Growth requires sales/CS outreach. Some word-of-mouth but no product mechanics. | Dev tools used solo, single-player productivity apps |
| 1 | No natural expansion. Single-user product with fixed pricing. Growth is purely acquisition-driven. | Standalone utilities, consumer apps with fixed subscription |

**Probing questions:**
- Do users naturally invite others as part of using the product?
- Is the product visible to non-users? (Shared links, embeds, emails with branding)
- Does the pricing model reward expansion? (Per-seat, usage-based, feature tiers)
- What is the typical expansion path? (Individual → team → department → org?)
- What is current net revenue retention? (>110% = strong expansion, <100% = contraction)

**Improvement levers (if score < 4):**
- Add collaboration features that require inviting others
- Make outputs shareable/embeddable with product branding
- Create team/workspace features that incentivize multi-user adoption
- Design usage-based pricing that grows with value
- Build integration ecosystem that increases stickiness and visibility

---

## Aggregate Scoring

| Average Score | Interpretation | Recommended Action |
|---------------|---------------|-------------------|
| 4.0 - 5.0 | **Strong PLG candidate.** Product has natural PLG characteristics. Focus on execution. | Proceed to acquisition model selection and revenue analysis. |
| 3.0 - 3.9 | **Viable with investment.** PLG is possible but requires deliberate product changes. | Identify weakest criteria, build improvement plan. May need hybrid model. |
| 2.0 - 2.9 | **PLG as secondary motion.** Product's primary GTM should be sales/marketing-led, with PLG as a complement. | Consider self-serve demo, PLG for specific segment, or bottom-up awareness play. |
| 1.0 - 1.9 | **PLG not recommended.** Fundamental product characteristics don't support self-serve. | Focus on SLG/MLG optimization. Revisit PLG only if product can be fundamentally redesigned. |

## Common Patterns

**High suitability but low expansion (5-5-5-2):** Individual tool problem. Add collaboration, sharing, or team features.

**High expansion but low self-serve (2-2-3-5):** Enterprise product with viral potential. Consider PLG for initial adoption with sales-assist for conversion.

**High barrier but high value speed (2-2-5-3):** Procurement friction problem. Lobby for self-serve purchasing or create freemium bottom-up entry.

**All 3s:** Most common pattern. Product CAN do PLG but needs deliberate investment in each dimension. Start with the cheapest-to-fix criterion.
