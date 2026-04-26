# Growth Model Comparison: SLG vs MLG vs PLG

## Overview

Three primary growth models exist. Most successful companies use a blend, but one model is always primary. This framework helps determine which should be primary and which should complement.

---

## Comparison Matrix

| Dimension | SLG (Sales-Led) | MLG (Marketing-Led) | PLG (Product-Led) |
|-----------|-----------------|--------------------|--------------------|
| **Primary engine** | Sales team (SDR → AE → CSM) | Marketing campaigns, content, nurture | Product experience, self-serve |
| **Buyer journey** | Rep-guided discovery → demo → proposal → close | Content discovery → nurture → MQL → sales | Self-serve signup → use → upgrade |
| **Typical deal size** | $25K-$500K+ ACV | $5K-$50K ACV | $0-$25K self-serve, $25K+ with sales assist |
| **Sales cycle** | 3-12+ months | 1-6 months | Minutes to weeks (self-serve); 1-3 months (sales-assist) |
| **CAC** | $5K-$50K+ | $1K-$10K | $100-$2K (self-serve) |
| **CAC payback** | 12-24+ months | 6-18 months | 1-6 months |
| **Buyer persona** | Executive / committee | Manager / director | Individual contributor / end user |
| **Value proof** | ROI calculation, references, POC | Case studies, content, social proof | Direct product experience |
| **Expansion model** | CSM-driven upsell, QBRs | Nurture campaigns, event triggers | Usage-driven upgrades, seat expansion, viral |
| **Key metric** | Pipeline, win rate, ACV | MQLs, conversion rate, pipeline contribution | Activation rate, PQL rate, free-to-paid conversion |
| **Scalability** | Linear (add more reps) | Sub-linear (content compounds) | Non-linear (product scales infinitely) |
| **Defensibility** | Relationships, brand, switching costs | Brand, content moat | Product experience, network effects, data moat |
| **Team investment** | Heavy: sales, SE, CS | Medium: content, demand gen, ops | Heavy engineering: growth, product, data |

---

## Decision Framework: Which Model is Primary?

### Use SLG-Primary When:
- Average deal size > $50K ACV
- Buyer is C-suite or committee (not end user)
- Product requires significant implementation/customization
- Competitive differentiation is in service/relationships, not product
- Market is small (<1000 potential customers)
- Regulatory/compliance requirements mandate procurement process
- Long time-to-value that cannot be shortened

### Use MLG-Primary When:
- Deal size $5K-$50K ACV
- Buyer is manager/director influenced by content and peers
- Product value is understood but requires education on approach
- Category is established with known evaluation criteria
- Inbound demand can be generated through content
- Sales cycle is 1-6 months

### Use PLG-Primary When:
- Individual end user can adopt and get value independently
- Time-to-value is short (minutes to hours)
- Product can be experienced before purchase
- Natural expansion from individual to team to org
- Market is large (thousands to millions of potential users)
- Competitive advantage is in product experience
- Viral or network effects present
- Usage-based or seat-based pricing model

---

## Hybrid Models

Most companies at scale operate hybrid models. Common patterns:

### PLG + Sales Assist (Bottom-Up SLG)
- **How it works:** Users adopt self-serve. Sales engages when usage signals emerge (PQLs). Sales accelerates enterprise expansion.
- **Examples:** Slack, Figma, Datadog, Notion
- **Best when:** Product has strong self-serve adoption but enterprise deals need human touch for procurement, security, legal.
- **Key metric:** PQL-to-opportunity conversion rate

### PLG + MLG (Content-Amplified PLG)
- **How it works:** Content/SEO drives awareness and education. Product is the conversion engine (not sales).
- **Examples:** HubSpot, Canva, Airtable
- **Best when:** Product category needs education, but once understood, product sells itself.
- **Key metric:** Content-sourced signups that activate

### SLG + PLG Motion (Top-Down with Product Experience)
- **How it works:** Enterprise sales leads. Free tier or trial used as proof point during sales cycle. Land-and-expand within accounts.
- **Examples:** Atlassian (evolved), MongoDB, Snowflake
- **Best when:** Enterprise product that can offer meaningful self-serve experience to accelerate sales cycles.
- **Key metric:** Trial/free usage to closed-won correlation

---

## Model Mismatch Diagnosis

### Signs You Are Running SLG When PLG Would Be Better:
- High CAC relative to ACV (payback >18 months)
- Users adopt the product without sales involvement but sales takes credit
- Significant inbound demand with long sales cycle creating friction
- Competitors with similar product winning on easier access
- Customer feedback: "I wish I could just sign up and try it"

### Signs You Are Running PLG When SLG Would Be Better:
- Low free-to-paid conversion (<2%) despite good activation
- Average deal size when customers DO pay is high (>$50K)
- Product requires significant configuration for value
- Buyers are not the users (IT, procurement, executive decision)
- Free users consuming resources without converting

### Signs You Need Hybrid:
- You have both SMB self-serve AND enterprise segments
- PLG drives adoption but enterprise expansion stalls without sales
- Great bottom-up traction but monetization requires sales conversation
- Net revenue retention is low without CSM involvement

---

## Model Transition Playbook

### From SLG to PLG-Inclusive:
1. Create free tier or trial (does not need to be full PLG, just an entry point)
2. Build self-serve signup and onboarding
3. Define PQL criteria based on usage signals
4. Route PQLs to sales instead of cold outbound
5. Measure: PQL conversion rate vs. traditional pipeline conversion
6. Gradually shift sales focus from hunting to farming PQLs

### From PLG to Adding Sales:
1. Identify expansion ceiling where self-serve stalls
2. Define PQL criteria (usage thresholds, team size, feature requests)
3. Hire solutions-oriented AEs (not traditional hunters)
4. Build PQL routing and scoring into CRM
5. Measure: incremental revenue from sales-assisted accounts vs. pure self-serve
6. Maintain self-serve as primary — sales accelerates, not replaces

---

## Output Template

After assessment, produce:

```
### Growth Model Assessment

**Current model:** [SLG / MLG / PLG / Hybrid — describe]
**Recommended primary model:** [SLG / MLG / PLG]
**Recommended secondary model:** [if applicable]

**Rationale:**
- [Key reason 1 based on comparison dimensions]
- [Key reason 2]
- [Key reason 3]

**Model mismatch identified:** [Yes/No — describe if yes]

**Transition priority:** [High/Medium/Low]
**First transition action:** [specific next step]
```
