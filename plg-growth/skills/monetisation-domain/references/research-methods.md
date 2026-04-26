# Pricing Research Methods

## Van Westendorp Price Sensitivity Meter

### Overview

A survey-based method to identify an acceptable price range for a product. Uses four questions to map price perception across your user base.

### The 4 Questions

Ask each respondent these four questions about your product (or a specific tier/plan):

1. **Too Cheap:** "At what price would you consider this product to be so cheap that you would question its quality?"
2. **Cheap / Good Value:** "At what price would you consider this product to be a bargain — a great buy for the money?"
3. **Getting Expensive:** "At what price would you start to think this product is getting expensive — you would still consider it, but you would have to think about it?"
4. **Too Expensive:** "At what price would you consider this product to be so expensive that you would not consider buying it?"

### Setup Guidelines

**Sample size:** Minimum 100 respondents for meaningful results. 200+ preferred.

**Respondent selection:**
- Must be current users or qualified prospects (not random people)
- Segment by: plan/tier, company size, role, usage level
- Include both free users and paid users for comparison

**Question format:**
- Present as open-ended price fields (not multiple choice)
- Currency should match respondent's market
- Show the product/tier description before asking questions
- Ensure respondents understand what they are pricing

### Plotting Methodology

1. For each of the 4 questions, create a cumulative distribution:
   - Too Cheap: cumulative from HIGH to LOW (% who said this price or higher is too cheap)
   - Cheap/Good Value: cumulative from HIGH to LOW
   - Getting Expensive: cumulative from LOW to HIGH (% who said this price or lower is getting expensive)
   - Too Expensive: cumulative from LOW to HIGH

2. Plot all 4 curves on the same chart (X axis = price, Y axis = cumulative %)

3. Identify the intersection points:

### Intersection Points

| Point | Intersection Of | Meaning |
|-------|----------------|---------|
| **Point of Marginal Cheapness (PMC)** | Too Cheap and Getting Expensive | Below this price, more people think it is suspiciously cheap than think it is expensive. Floor of acceptable range. |
| **Indifference Price Point (IDP)** | Cheap/Good Value and Getting Expensive | Equal number think it is a bargain vs getting expensive. Often close to current market price. |
| **Optimal Price Point (OPP)** | Too Cheap and Too Expensive | Minimum price resistance. Fewest people reject the price on either extreme. |
| **Point of Marginal Expensiveness (PME)** | Cheap/Good Value and Too Expensive | Above this price, more people reject than see value. Ceiling of acceptable range. |

### Acceptable Price Range

**Range: PMC to PME**
- Below PMC: price signals low quality
- Above PME: price exceeds perceived value
- IDP: safe middle ground
- OPP: theoretical optimum (least resistance)

### Interpreting Results

- **Narrow range (PMC close to PME):** Strong price consensus, limited room to maneuver. Market has clear expectations.
- **Wide range:** Segments have different willingness to pay. Consider tier differentiation.
- **OPP below IDP:** Market may accept a price increase. Current pricing may be leaving money on the table.
- **OPP above IDP:** Market is price-sensitive. Tread carefully with increases.

### Limitations

- Stated preference, not revealed preference (people say one thing, do another)
- Best used directionally, not as exact price points
- Does not account for competitive context well
- Supplement with actual conversion data and A/B tests

### Sample Survey Template

```
We are evaluating pricing for [Product/Plan Name].

[Description of what is included in this plan:
- Feature A
- Feature B
- Limit: X users / Y projects / Z GB]

Thinking about the product described above, please answer these questions
with a specific dollar amount per month:

1. At what monthly price would you consider this product so cheap
   that you would question its quality? $____/mo

2. At what monthly price would you consider this product a bargain
   — a great buy for the money? $____/mo

3. At what monthly price would you start to think this product is
   getting expensive — you would still consider it, but you would
   have to think about it? $____/mo

4. At what monthly price would you consider this product so expensive
   that you would not consider buying it, regardless of quality? $____/mo
```

---

## MaxDiff (Best-Worst Scaling)

### Overview

A survey method that forces respondents to make trade-offs between features, packages, or pricing metrics. Reveals relative importance when everything seems "important."

### When to Use

- **Pricing metric selection:** Which metric (per-seat, per-usage, per-project) do customers prefer?
- **Feature prioritization:** Which features drive willingness to pay? What should be in each tier?
- **Package design:** Which bundle of features is most appealing?
- **Value driver identification:** What product attributes matter most for purchase decisions?

### How It Works

1. **Define attributes:** List 8-15 items to evaluate (features, metrics, benefits)
2. **Design choice sets:** Each set shows 4-5 attributes. Respondent picks BEST and WORST.
3. **Repeat:** Each respondent sees 8-12 choice sets (each attribute appears 3-4 times)
4. **Analyze:** Calculate importance scores (how often chosen as best vs worst)

### Setup Process

**Step 1: Define the attributes (8-15 items)**

Example for pricing metric selection:
- Per-seat pricing (price per user per month)
- Per-project pricing (price per active project)
- Usage-based pricing (pay per API call / action)
- Flat monthly fee (unlimited use, single price)
- Per-team pricing (price per team, unlimited seats within)
- Outcome-based pricing (pay per successful outcome)
- Freemium + premium features (free base, pay for advanced)
- Annual subscription (pay once per year)

Example for feature prioritization:
- Advanced analytics dashboard
- SSO / SAML authentication
- API access
- Custom integrations
- Priority support
- Unlimited projects
- Collaboration features (comments, sharing)
- Export capabilities
- Mobile app
- Automation workflows

**Step 2: Design choice sets**

Each set contains 4-5 randomly selected attributes. Respondent sees:

```
Of these features, which is MOST important and LEAST important
to you when choosing a [product category] tool?

□ Advanced analytics dashboard
□ API access
□ Priority support
□ Unlimited projects

MOST important: [select one]
LEAST important: [select one]
```

**Step 3: Sample size and sets**
- Minimum 150 respondents per segment
- 8-12 choice sets per respondent
- Each attribute should appear 3-4 times across all sets
- Use balanced incomplete block design (tools like Sawtooth, Conjointly, or SurveyMonkey can auto-generate)

### Analyzing Results

**Importance scores:** For each attribute, calculate:
- Best count: how many times chosen as best
- Worst count: how many times chosen as worst
- Raw score: Best count - Worst count
- Scaled score: Normalize to 0-100 scale

**Output:** A ranked list of attributes by relative importance. The gaps between scores matter — a large gap indicates a clearly more/less important attribute.

### Interpreting for Pricing Decisions

**For metric selection:**
- Highest-scored metric = customers prefer to pay this way
- Compare top 2-3 metrics. If scores are close, either works. If one dominates, strong signal.

**For feature prioritization:**
- Top 3-4 features: must be in paid tier (these drive willingness to pay)
- Bottom 3-4 features: can be in free tier or removed (do not drive payment)
- Middle features: tier differentiators (put in higher tiers)

**For tier design:**
- Free: bottom-scored features + core functionality
- Pro: add mid-scored features
- Enterprise: add top-scored features that appeal to organizations

### Sample MaxDiff Survey Template

```
Thank you for helping us improve [Product Name].

We are going to show you sets of [features/pricing options].
For each set, please select which is MOST important and which
is LEAST important to you.

There are no right or wrong answers — we want your honest preferences.

[Set 1 of 10]
Of the following, which is MOST important and LEAST important
when deciding to pay for a [product category] tool?

                        Most    Least
API access               ○       ○
Unlimited projects       ○       ○
Priority support         ○       ○
Team collaboration       ○       ○

[Continue for 9 more sets...]
```

---

## Decision-Driver Research for Pricing

### Overview

Qualitative interviews focused specifically on understanding what drives upgrade/purchase decisions.

### Interview Guide: Upgrade Decision Drivers

**Target respondents:**
- Recently upgraded users (within last 30 days)
- Users who started upgrade flow but abandoned
- Power free users who have not upgraded
- Churned paid users who downgraded

**Core questions (30 min interview):**

```
CONTEXT
1. What do you use [product] for? Walk me through your typical workflow.
2. How long have you been using [product]?

TRIGGER (for upgraders)
3. What specifically triggered you to upgrade?
4. Was there a specific moment or event? What happened right before?
5. What were you trying to do that required the paid plan?

EVALUATION
6. What alternatives did you consider? (Other tools, workarounds, doing nothing)
7. How did you compare [product] pricing to alternatives?
8. What would have made the decision easier/harder?

VALUE PERCEPTION
9. Now that you are on the paid plan, is it worth the price? Why or why not?
10. If the price doubled, would you still pay? At what price would you cancel?
11. What feature would you miss most if we removed it?

BARRIERS (for non-upgraders)
12. Have you considered upgrading? What held you back?
13. What would need to change for you to upgrade?
14. Is it a price issue, a value issue, or something else?
```

### Analysis Framework

Cluster responses into:
1. **Trigger events:** What specific events cause upgrade consideration?
2. **Must-have features:** What paid features are non-negotiable?
3. **Price anchors:** What do respondents compare the price to?
4. **Barriers:** What prevents or delays upgrade?
5. **Value proof points:** What ROI evidence do they cite?

Use these clusters to inform packaging (which features gate), pricing (what range is acceptable), and conversion (what triggers to leverage).
