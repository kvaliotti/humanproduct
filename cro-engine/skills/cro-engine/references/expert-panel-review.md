# Expert Panel Review

A quality gate for CRO recommendations. Before any set of conversion optimization recommendations is returned to the user, run it through a simulated panel of six real-world CRO authorities, each scoring the work through their own lens. Iterate until the panel's average score reaches 90+.

## How It Works

1. **Draft recommendations first.** Complete the normal CRO workflow (identify stage, load patterns, assess current state, apply framework) before invoking the panel.
2. **Score through each lens.** For every expert below, evaluate the draft recommendations against their specific lens and assign a 0-100 score with 1-3 sentences of concrete, specific feedback (not generic praise).
3. **Average the six scores.**
4. **Gate on the average:**
   - **90+**: Recommendations are ready to return.
   - **Below 90**: Revise the recommendations to address the lowest-scoring lenses first, then re-score. Repeat until the threshold is met or it becomes clear a lens's objection is out of scope (e.g., no pricing exists to critique) — state that explicitly rather than forcing a fit.
5. **Show the work.** When presenting final recommendations, briefly summarize the panel scores and the key feedback that shaped the final version — this makes the quality bar visible rather than asserted.

## The Panel

### Laja — Conversion Optimization
Evaluates whether recommendations are grounded in evidence (user research, analytics, session recordings) rather than best-practice cargo-culting. Penalizes generic "just add urgency" advice; rewards hypothesis-driven changes tied to a specific, observed friction point. Asks: "What evidence suggests this is actually the problem, and how will we know if the fix worked?"

### Wiebe — CTA and Form Copy
Evaluates the actual words used in headlines, CTAs, labels, and error messages. Penalizes generic verbs ("Submit," "Learn More," "Sign Up") and vague value props. Rewards specific, benefit-first, first-person microcopy that reflects how a real customer would say it. Asks: "Would a customer actually say this sentence about their own goal?"

### Wroblewski — Mobile and Form UX
Evaluates field-level and interaction-level UX: input types, touch target sizing, label placement, multi-step sequencing, and mobile-specific friction. Penalizes designs that only work on desktop or that ignore field-by-field cost. Asks: "Does this hold up on a thumb, on a small screen, under bad connectivity?"

### Cialdini — Persuasion Psychology
Evaluates the use (and misuse) of influence principles — social proof, authority, scarcity, commitment/consistency, reciprocity, liking, unity. Penalizes manipulative or fabricated pressure (fake countdowns, false scarcity) and rewards genuine, ethical application matched to where the user actually is in their decision journey. Asks: "Is this persuasive because it's true and relevant, or because it tricks?"

### Poyar — Monetization and Pricing
Evaluates packaging, pricing presentation, and upgrade/paywall logic for revenue soundness — not just click-through. Penalizes recommendations that could lift a shallow metric (clicks) while hurting a deeper one (plan mix, expansion revenue, trial-to-paid quality). Asks: "Does this improve the metric that matters, not just the metric that's easy to move?"

### Dunford — Positioning and Wording
Evaluates whether the language used across the page/flow reflects a clear, differentiated market position and speaks in the target customer's own category language. Penalizes vague, undifferentiated, or internally-focused wording. Asks: "Would the target customer recognize themselves and their alternative in this language?"

## Applying the Gate in Practice

- Run this gate on the final recommendation set, not on every individual idea — score the package as a whole.
- If a lens genuinely doesn't apply (e.g., no persuasion elements are being changed), note it as N/A and average across the remaining lenses rather than forcing a score.
- Keep feedback specific enough to action: "Cialdini: 72 — the discount countdown resets on refresh, which is fabricated urgency; use a real cohort-based deadline instead" is useful, "Cialdini: 72 — needs more persuasion" is not.
- The threshold (90+) is intentionally high: it should force at least one revision pass on most first drafts.
