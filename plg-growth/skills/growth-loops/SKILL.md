---
name: growth-loops
description: "Design, evaluate, and optimize growth loops (viral, content, paid, sales), including k-factor and viral-coefficient math and network-effects analysis. Use for: growth loops, viral loop, referral loop, content or UGC loop, flywheel, compounding growth, loops vs funnels, k-factor, viral coefficient, network effects. Owns loop design and virality math. For acquisition channels or signup conversion, use acquisition-domain."
---

# Growth Loops

Help a PM find the one or two loops that fit the product, map how they work, and find the step to fix first. A loop is a funnel whose output feeds its own input.

**Quick answers.** If the question is narrow ("how do I calculate k?", "which loop fits us?"), answer it directly. Offer the full blueprint only if they want it.

## 1. Check structural fit

A loop that the product's normal use does not create cannot be bolted on. Disqualify any type that fails its prerequisite:

| Loop | Prerequisite |
|---|---|
| Exposure viral (Calendly link, Loom video) | Normal use shows the product's output to non-users, with the brand visible |
| Incentivised viral (Dropbox storage referral) | A reward that is cheap to give and worth something to both sides |
| Collaboration viral (Slack, Figma) | The product is much weaker used alone, so users must invite others |
| Content via search or social (Quora, Pinterest) | Users create public, indexable or shareable content as they use it |
| Content via creators (Substack, YouTube) | Creators bring their own audience, and some of the audience becomes creators |
| Paid | LTV clearly above CAC, and channels with room to spend more |
| Sales | Accounts worth enough to pay for sales, identifiable from product signals (see `product-led-sales`) |

Paid and sales loops stop the day the spending stops. Only the others compound by themselves.

## 2. Map the loop as a chain of steps

Write each step from user action to the new user repeating it: action → exposure → visit → signup → activation → new user takes the action. Put a conversion rate on each step. Mark each rate **measured** or **(assumption)**. Never borrow another company's k-factor or step rates; this plugin has no sourced benchmarks for them. Tell the user to measure their own baseline.

## 3. Do the math

- **k** = loop actions per user per cycle × product of the step rates. For invite loops: invites sent per user × share of invites that become active users.
- **Cycle time** = time from one user's action to the new user's same action. Compare loops on growth per month, not k alone. A high k with a six-month cycle compounds slowly.
- **Amplification** (k < 1): each organic user brings k/(1−k) extra users in total. Example: 1,000 organic users a month at k = 0.3 adds about 430 more.
- k above 1 is rare and does not last. Most loops amplify other acquisition; they do not replace it.

## 4. Pick the step to fix

In a chain of multiplied rates, doubling any step doubles k. So pick the step that is **cheapest to double**. This is usually the lowest rate, because a 5% step has room to double and a 60% step does not. Name its likely cause (CTA not seen, invitee lands on a bad first screen, few users create content) and one fix to test.

## 5. Check for network effects

Network effects are separate from virality. Virality brings users in. Network effects make the product better as it grows, which keeps users. A product can have one without the other: Hotmail was viral with no network effect, while Uber has network effects but grew mostly through paid channels.

Check for three kinds: direct (each user adds value for others), cross-side (marketplaces), and data (more usage improves the product). Then check whether each is local (a city or a team) or global. To test it, compare retention for users with many connections against users with few.

## Output

Lead with the answer: which loop, the bottleneck step, and the first action. Then give:
1. The loop diagram with the rate on each step, each marked measured or (assumption)
2. k, cycle time, and the extra users per month the loop adds
3. Whether network effects are present, and what kind
4. Three hypotheses to raise k, each with the step it targets and how to test it (route to `plg-experimentation`)
5. What we don't know: the rates to go and measure first

Keep it to about one page.

## Don't

- Force a loop where normal use creates no exposure.
- Optimize k before retention is fixed. A viral loop on a product people leave just burns through the market faster.
- Ignore cycle time.
- Treat a loop as the source of growth. It needs a base of organic or paid users to feed it.

Route to `acquisition-domain` for channels, `monetisation-domain` for paid-loop unit economics, `product-led-sales` for sales loops, and `plg-orchestrator` for a broader diagnosis.
