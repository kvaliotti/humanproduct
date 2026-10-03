# Model playbooks

Key decisions and failure modes per model. Use the one you're designing.

## Freemium

- **Two shapes.** Unlimited core with paid power features (risk: free is good enough forever). Or a limited core (seats, projects, records, storage, history, integrations, API) where the paid tier lifts the cap.
- **Put limits at natural growth moments**, such as the team growing past the seat limit, not at arbitrary walls. Hitting a limit should feel like "you've outgrown free", not "you can't work".
- **Paid features should line up with growth moments**: team expansion, power use, admin and security.
- **Upgrade triggers.** Prefer natural ones (limit reached, paid feature tried, team grows) over nagging (pop-ups every visit, blocked core workflow, fake countdowns).
- **Check the economics.** Compare revenue per 100 signups (conversion × ARPA) with the cost of serving 100 free users plus acquisition. If free users are expensive, use a trial instead.
- Downgrading must keep the user's data.

## Free trial

- **Length.** Long enough to reach first value and repeat the core use at least once. Longer for team adoption, data import or committee buyers. Longer trials lose urgency.
- **Card up front or not.** A card requirement means far fewer signups, but more serious ones and automatic conversion. No card means more users who can convert later, refer others or become PQLs. For most PLG products, start without a card. Require one when ARPA is high and buyers are serious. Compare total paying customers, not conversion rate.
- **Trial end.** Downgrade to free if a free tier exists. Otherwise use read-only access or a short grace period. A hard lockout loses people for good.
- **Onboarding matters more than in freemium** because time is short. Deliver the aha moment on day one. Mid-trial messages point to unused features. Pre-expiry messages show the value the user got.
- **Extensions should be earned.** Offer them to engaged users who haven't finished setup, not to everyone.

## Reverse trial

Full premium at signup, then a downgrade to a usable free tier instead of a lockout. It converts in two waves: during the trial (urgency), and after the downgrade, when the user misses features they actually used.

- Needs a clear free/paid split the user will feel, a free tier that stands on its own, and a low cost to serve free users.
- Use one onboarding flow that includes premium features, each marked with a consistent subtle badge.
- Track premium-feature use per user. Before and after the downgrade, name the features *they* used: "You used Advanced Analytics 14 times."
- At downgrade, lock features but don't hide them, and never hide or delete data. Free features must work exactly as before.
- After the downgrade, nudge monthly, not weekly. Report trial-period and post-downgrade conversion separately.

## Ungated

- **Fit.** The audience has an immediate need and dislikes signing up. Value arrives in one session without knowing who the user is. There's a strong reason to sign up afterwards: saving work, using it across devices, sharing, or collaborating. Newsletters are a weak reason.
- **Define the value unit**: the single most useful thing a user can do without an account. Strip everything else: no email, name, password or verification.
- **Ask for signup at peak value** ("save your design"), never before value.
- **Keep the work through signup.** Losing work at signup is the top way ungated models fail.
- **In-moment need versus new concept.** If users arrive with a task, let them do it immediately. If they're exploring, guide them through sample content, then prompt "try it with your own data".
- Track the ungated funnel: visit → core action → value reached → prompt shown → signup → activation. Test where and how the prompt appears.

## Self-service demo

- **Fit.** Heavy setup, value that depends on accumulated data, or several stakeholders who need to see it without accounts. A poor fit when the value is in creating (design, writing) or depends entirely on the user's own data.
- **Show the day-30 product.** Use realistic, industry-relevant data (not "Test User 1"), and offer 2–3 variants by persona or industry. Make it interactive, not screenshots. Label it clearly as a demo.
- **Show outcomes, not a feature tour.** Make every demo insight one the user wants for their own data. That wish is the signup trigger: "set this up with your data".
- **Build.** Start with a shared sandbox that resets. Move to per-user sandboxes when conversion justifies the cost. Keep demo data in line with the current product.
- The usual drop-off is between seeing the insight and clicking signup, which means the demo didn't create enough desire.
