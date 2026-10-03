---
name: acquisition-model-selector
description: "Choose how new users start using the product: freemium, free trial, reverse trial, ungated, or self-service demo, or a deliberate mix, and design the chosen model. Use when someone asks 'freemium or free trial', 'should we be freemium', 'which acquisition model', 'reverse trial', 'ungated vs freemium', 'self-service demo', 'free tier design', 'credit card for trial', or 'how should users start using our product'."
---

# Acquisition Model Selector

Recommend one entry model, or two with a clear reason, and its key design choices. Follow `${CLAUDE_PLUGIN_ROOT}/references/problem-solving-backbone.md`.

## Default: quick recommendation

Ask only what you need: core value in one sentence, time to first value, setup effort, whether the user must bring their own data, single-player or team, competitive intensity, and cost to serve a free user. Then answer with the model, the deciding reason, and the 2–3 design choices that matter most. Write the full brief only on request.

## Choosing

Walk this order and stop at the first fit:

1. **Value in minutes with no setup and no account?** → **Ungated.** Ask for signup at the moment of value (save, share, continue).
2. **Is the core use case valuable on its own, with a clearly better paid tier?** → **Freemium.** If there's no meaningful paid tier, fix packaging first.
3. **Does value take days or the full feature set to show?** → **Free trial.** If premium features are the differentiator, and there's a viable free tier to land on, make it a **reverse trial**.
4. **Is setup heavy but the value obvious once seen?** → **Self-service demo** with pre-built data.
5. Still unclear → start with a free trial. It's the easiest to change later.

Adjust for context:

- **Data dependency.** If value needs the user's own data, ungated and demo only work as a preview. Pair them with a trial or freemium.
- **Team value.** If value needs several people, the trial must include inviting the team.
- **Competition.** In a commodity market with strong free alternatives, freemium is table stakes. A differentiated product can gate more.
- **Cost to serve.** If free users are expensive to serve, prefer a trial over freemium or reverse trial.
- **Audience.** Developers and consumers expect ungated or free tiers. Enterprise buyers expect a guided trial or demo.
- **Intent by entry point.** Problem searches and social traffic suit ungated or demo. Brand searches and colleague referrals suit a trial or freemium. Sales-sourced prospects suit a demo or reverse trial. Different pages can offer different entry points.

**Start with one model.** Add a second only when evidence shows it serves a different, valuable segment. Each extra model adds messaging, packaging and onboarding work. Never launch three at once without a dedicated growth team.

## Designing the chosen model

Read `references/model-playbooks.md` for the chosen model's key decisions and failure modes.

## Output

```
## Acquisition model
**Recommendation:** [model] — [deciding reason]
**Design:** [3–5 key choices: limits, trial length, card or not, end-of-trial behaviour, signup trigger]
**Second model (if any):** [model] for [segment/entry point] because [evidence]
**Rejected:** [model] — [one-line reason each]
**Hypothesis:** We believe [model] will convert because [reason]. We'll know by [metric, guardrail, timeframe].
**Risks:** [risk → mitigation]
```

Never state an expected conversion rate unless the user has a sourced comparable. Measure your own baseline.

## Rules

- Don't copy a competitor's model. Their product characteristics differ.
- Don't default to a trial because it's easiest. Check whether freemium or ungated fits better.
- The moment a user hits a limit or loses a feature is the most important conversion moment. Design it.
- Calibrate the free tier with decision drivers (from `plg-readiness`): free must prove the top driver; paid serves the next need.

## Next skills

Design of the free/paid line → `monetisation-domain`. First-run experience → `activation-domain`. Fit not established → `plg-readiness`.
