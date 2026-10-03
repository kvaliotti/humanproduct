---
name: cro-engine
description: |
  Conversion rate optimization review. Finds the few changes most likely to lift
  conversion on a landing page, pricing page, signup flow, onboarding, paywall or
  upgrade screen, popup, or form, each tied to a concrete element and a test.
  Use when the user says "page not converting", "improve my landing page",
  "signup drop-off", "reduce friction", "increase activation", "free to paid",
  "upgrade modal", "paywall", "exit intent", "email popup", "form completion",
  "lead capture", "checkout", or mentions CRO, conversion, or funnel.
user-invocable: true
argument-hint: "[URL, screenshot, HTML/component file, or description of the page or flow]"
effort: high
---

# CRO Engine

Review one page or flow and return the few fixes most likely to lift conversion. Do not hand back a checklist.

## Before reviewing

1. Get the real thing: open the URL, read the file, or look at the screenshot. If you only have a description, say so in the first line and treat every fix as a hypothesis.
2. Find out or infer the **one conversion goal**, the **traffic source** (ad, search, email, in-product), and any **numbers** the user has (conversion rate, step drop-off, field drop-off). Ask once if the goal is unclear. Never invent a baseline.
3. Name the biggest leak first. A broken step, mismatched message, or premature ask beats ten polish items.

## What to look for

Look for the problems below first. You already know generic best practice, so only raise it when it is the actual leak on this page.

- **Every page:** The headline must match the ad, email, or link that brought the visitor here. Use the customer's own words for the problem and the category, not internal jargon. Make one primary action. Put proof (named customers, specific results) next to the CTA, not in a band at the bottom.
- **Landing page:** Remove navigation and secondary CTAs. Make the whole argument on one page.
- **Pricing page:** Answer "which plan is for me?" by naming who each plan is for. Mark one plan as recommended. Show what is excluded, not only what is included.
- **Signup:** A field must earn its place before first use. Move role, company, and team size into onboarding, or infer them from the email domain. Drop "confirm email". Allow pasting passwords, and show password rules before the first failure. B2B should offer Google and Microsoft sign-in. Let people into the product before they verify their email, unless verification is essential.
- **Onboarding:** Activation is the action that retained users take and churned users don't. If nobody knows that action, finding it is fix #1. Get users doing the task, not touring it. An empty state should be the first step of the task, not a dead end. Checklists must be dismissible and must never gate features.
- **Paywall / upgrade:** Show it right after a value moment, never during onboarding or mid-task. The headline says what they unlock, not the price. For a usage limit, offer a way out other than upgrading, such as freeing up space or buying a top-up. When a trial ends, show what they made and what they will lose. Give a clean "Continue free". After a dismissal, wait days, not hours.
- **Popup:** Prefer click-triggered popups over interruptions. Exit intent does not work on mobile. Never show a popup in checkout or to users who already converted, and remember dismissals. Google penalizes intrusive full-screen interstitials on mobile.
- **Form:** Ask which fields sales or the team actually use after submission, and delete the rest. Keep labels visible and use placeholders only for examples. Validate when the user leaves a field, not while they type. Never clear the form on an error. The button names what the user gets ("Get my quote"), not "Submit".

## Guardrails

- **Evidence over cargo cult.** Tie each fix to something you saw on the page or in their data. If it is just "best practice" with no visible problem behind it, cut it.
- **Protect the deeper metric.** Don't lift clicks or signups at the expense of trial-to-paid, plan mix, refunds, or churn. Say which metric each fix should move.
- **No manipulation.** No fake countdowns, false scarcity, hidden close buttons, guilt-trip decline copy ("No, I don't like saving money"), or pre-checked opt-ins (unlawful under GDPR). If the page uses any of these, flag it as a fix.
- **Suggest a test, don't promise a lift.** Never quote a percentage improvement or an industry benchmark. Tell them to measure their own baseline. For a low-traffic page, recommend shipping obvious fixes directly instead of A/B testing them.
- **Mobile counts.** Check the fix on a small screen and a thumb: touch targets, keyboard types, and whether the CTA is visible without scrolling.

## Output

Keep it to about one page. Use this order:

1. **Verdict.** One or two sentences: the biggest leak and why.
2. **Top fixes.** Give three, or up to five only if each is clearly independent. Rank them by expected impact over effort. For each:
   - **Where:** the exact element. Quote the copy (*"Start your journey"*), name the field or step ("step 2 of 3, 'Company size'"), or give `file:line`.
   - **Why it hurts:** one sentence about this user at this moment.
   - **Change:** the smallest edit, with the new copy written out when copy is the fix.
   - **Check:** the metric to watch, or the A/B test to run, and what result would confirm it.
3. **Leave alone.** One line naming anything that already works, so nobody "optimizes" it away.
4. **Need from you.** Only the data that would change the ranking, such as field-level drop-off or traffic source. Skip this section if nothing is needed.

End with one line offering depth on request: copy alternatives, a full field-by-field audit, a redesigned flow, or a test plan. Do not include them unless asked.

Never include a score, a scorecard, or a framework walkthrough.
