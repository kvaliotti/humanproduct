---
name: plg-readiness
description: "Judge whether product-led growth fits a product: self-serve suitability, PMF signals, which growth motion should lead, and whether the free or trial experience can prove what buyers actually decide on. Use when someone asks 'is PLG right for us', 'should we go product-led', 'PLG readiness', 'PLG fit', 'PLG suitability', 'PLG maturity', or 'can the product prove its value before purchase'."
---

# PLG Readiness

Answer one question: should this product lead with PLG, and if not yet, what has to change first? Follow `${CLAUDE_PLUGIN_ROOT}/references/problem-solving-backbone.md`.

The idea that makes this skill worth running: suitability alone isn't enough. PLG converts only if the free or trial experience proves the thing buyers actually decide on. A product can look self-serve and still fail because the trial shows ease of use while buyers choose on reliability.

Out of scope: positioning and messaging. Use the `pmm-define-and-review-positioning` plugin for that.

## Default: quick verdict

Use what the user gives you and ask only for what's missing. Assess:

1. **Suitability.** Can a user get value without help? Start without a sales step, card or approval? Reach the aha moment before paying, and how fast? Does use spread on its own (invites, shared outputs, seats, usage)? Common patterns:
   - Strong on the first three, weak on spread: an individual tool. Add sharing or team features.
   - Weak self-serve, strong spread: enterprise with viral potential. PLG for adoption, sales for conversion.
   - Fast value, high entry barrier: procurement friction. Create a bottom-up entry point.
   - Middling everywhere: PLG is possible but needs work. Fix the cheapest gap first.
2. **PMF.** Don't recommend PLG investment before PMF. Signals: the Sean Ellis test (40%+ of users "very disappointed" without the product, per Sean Ellis); a retention curve that flattens rather than decays to zero; actual usage frequency close to the use case's natural frequency (daily tool used daily); usage that deepens over time. Recommend the Ellis survey if they haven't run it.
3. **Decision drivers.** What do buyers choose on, and can the free or trial experience prove it? Drivers that need time (reliability, long-term ROI), a whole team (collaboration), or human reassurance (vendor stability, enterprise support) can't be proven in a short solo trial. Mitigate with trial design, social proof, or sales assist. If activation proves the #1 driver, PLG has natural conversion power. If it doesn't, redesign activation or don't lead with PLG.
4. **Which motion should lead.**
   - Running sales-led when PLG would fit better: users adopt without sales but sales takes credit, inbound demand stalls in a long cycle, competitors win on easier access, customers ask to "just try it".
   - Running PLG when sales should lead: good activation but very low conversion, large deals when they do close, buyers aren't users, free users cost money and never convert.
   - Needs a hybrid: both SMB self-serve and enterprise segments, or bottom-up traction that stalls at enterprise expansion.
5. **Defensibility.** PLG is easy to try and easy to leave. If a competitor can copy the free experience, name the moat to build: network effects, accumulated data or content, workflow integrations, or system-of-record status.

Output, under one page:

```
## PLG readiness: [Lead with PLG / PLG with sales assist / Hybrid / Sales-led with a PLG entry point / Not yet]
[2–3 sentences: why, naming the deciding factor]

Top gaps (max 3): [gap] — why it blocks PLG — what would fix it
Decision drivers: [top drivers, or "unknown — research needed"] — free experience proves them: yes / partly / no
Next steps: [action] → [plg-growth skill]
```

No numeric scores. A verdict plus the gaps that drive it is more useful than an average.

## Full assessment (on request)

When the user wants evidence rather than judgment, or the drivers are unknown, run decision-driver research with `references/decision-driver-research.md`: interviews to discover drivers, a survey to rank them, and a map of each top driver to whether the free experience can prove it.

## Next skills

Fit confirmed → `acquisition-model-selector` (how users start) or `plg-revenue-analysis` (which lever to pull). Org blocks it → `plg-transformation`.
