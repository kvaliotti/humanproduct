# Stakeholder Map

For B2B, profiling only the end-user is insufficient. The buying unit has 5–9 roles that each shape the deal. Miss one — especially the blocker — and the segment profile is incomplete.

For B2C, the user/influencer/purchaser triad collapses to one person in many categories but diverges for gift-buying, household budget holders, parents buying for children, accessibility-driven purchases, and regulated purchases (alcohol, firearms, pharma).

## B2B roles

Every B2B segment profile maps these roles, even if a single person fills multiple. Name the person's role, not the individual.

| Role | What they do | Typical title (varies by industry) | Failure mode if ignored |
|---|---|---|---|
| **User** | Touches the product daily; experiences the value directly | IC — marketer, dev, analyst, ops | Adoption drops, renewal dies |
| **Champion** | Advocates internally; writes the business case; runs POC | User's manager, team lead, director | Deal stalls in committee |
| **Economic buyer** | Signs the cheque; owns the budget line | VP, head of, director, CFO for large ACV | Deal gets trimmed or postponed |
| **Approver / decision committee** | Veto rights on specific domains | Legal, Security, IT, Procurement, Compliance | Deal dies in SOC2 / DPA review |
| **Blocker / gatekeeper** | The role most likely to kill the deal | Often Security for data tools; IT for deploy; Finance for cost; a competing internal team | Deal dies silently after a seemingly-successful demo |
| **Renewer** | Decides renewal; may differ from initial buyer | Ops lead, manager of user, procurement | Revenue churns on year 2 |
| **Implementer** | Actually deploys / integrates | SRE, RevOps, Sales Ops, IT admin | Time-to-value stretches; value story breaks |
| **Executive sponsor** | Umbrella cover; rarely in meetings | VP or C-level | Deal loses priority vs. competing initiatives |
| **Influencer** | Affects the decision without a formal role | Peer who used it before; industry analyst; advisor | Surprise objections at committee |

## For each segment, fill this table

| Role | Who | Their KPI | What they fear | What earns their trust | Signals of engagement |
|---|---|---|---|---|---|
| User | | | | | |
| Champion | | | | | |
| Economic buyer | | | | | |
| Approver(s) | | | | | |
| Blocker | | | | | |
| Renewer | | | | | |
| Implementer | | | | | |

**Mandatory:** every B2B segment must name at least one plausible **blocker**. If you can't name one, you don't understand the segment's buying process yet.

## Common blocker archetypes

| Blocker | Triggers on | How they kill deals |
|---|---|---|
| Security / InfoSec | Data sensitivity, external transmission, SSO | Requires SOC2, pentest, DPA; fails on 1 checklist item |
| IT / DevOps | Deployment, identity, SSO, data residency | Refuses shadow IT; demands centralized provisioning |
| Procurement | Deal size, renewal terms | Forces RFP, multi-vendor bid, concessions |
| Legal | Contracts, IP, liability | Rewrites MSA; blocks on indemnity clauses |
| Finance | Any recurring cost above a threshold | Caps ACV, forces quarterly billing, blocks multi-year |
| Incumbent team | Internal team owns adjacent tool | Frames new tool as duplication; demands consolidation |
| Data Privacy Officer | PII, cross-border data | Blocks EU→US transfers, GDPR DPIA required |

If a segment is above a certain ACV ($25K+ typical threshold), the default assumption is all seven are potential blockers until proven otherwise.

## B2C mapping

Simpler, but don't collapse too fast. Three roles:

| Role | What they do | When they diverge from user |
|---|---|---|
| **User** | Uses the product | Always present |
| **Purchaser** | Pays | Gift purchases, household budget, employer-provided, insurance-reimbursed |
| **Influencer** | Shapes the choice | Reviewer ecosystems (app store, Yelp), partner, friend group, professional advisor (doctor, lawyer, trainer) |

For B2C, profile:

- **Moment of purchase** — impulse, considered, triggered by event
- **Comparison set** — what they benchmark against
- **Dissuaders** — who in their life might talk them out of it
- **Social proof mechanism** — reviews, peer recommendation, creator endorsement, influencer, brand loyalty

## Stakeholder map per segment vs. global

The full stakeholder map is done **per segment** — different segments often have different blockers. A scale-stage B2B SaaS has IT/Security as blockers; an SMB often doesn't have an IT function and the blocker is the Owner/CFO treating it as a budget line.

A global stakeholder map averaged across all segments hides this and produces GTM motions that work for no one.

## Handoff to downstream skills

The stakeholder map feeds:
- **Willingness-to-pay** (skill #3): different stakeholders have different price sensitivities and budget authorities
- **Positioning**: champion-language vs. economic-buyer-language vs. user-language are different
- **GTM / sales motion**: who to target first (bottom-up PLG vs. top-down ABM)
