# Ethics & Dark-Patterns Gate

Behavioural mechanisms are dual-use. The same lever — loss aversion, scarcity, social proof, variable reward, streaks — can help a user get something they genuinely want, or exploit them into acting against their own interest. This gate is applied by the orchestrator to the **recommendations** (and flagged by lenses during analysis) so the fixes this plugin proposes never cross into manipulation. A behavioural-design tool that hands users a manipulation playbook is a liability, not a product.

The three source books that each carried an ethics section (*Hooked*, PCT, *Thinking Fast and Slow*) are consolidated here so it's checked **once**, well, rather than six times, weakly.

## Two tests every recommendation must pass

**1. The Manipulation Matrix** (Eyal). Two questions:
- *Does it materially improve the user's life?*
- *Would the maker use it themselves / be glad someone they care about used it heavily?*

|  | Maker would use it | Maker would not |
|---|---|---|
| **Improves user's life** | **Facilitator** ✅ ship | **Peddler** ⚠️ reconsider |
| **Doesn't improve life** | **Entertainer** ⚠️ only if honest & wanted | **Dealer** ❌ never |

Aim for **Facilitator**. A recommendation in the Peddler or Dealer quadrant is reframed to an honest version or cut.

**2. The endorse-on-reflection test** (Kahneman + PCT). *Would the user still endorse this mechanism if they fully understood how it works?* If knowing how it operates would make the user feel tricked, resentful, or trapped, it fails — reduce friction and clarify, don't bypass agency.

## Dark patterns to reject outright

If a recommendation relies on any of these, cut it or replace it with the honest alternative:

- **Fake urgency / manufactured scarcity** — countdowns, "only 2 left," fabricated deadlines that aren't real.
- **Manufactured error / engineered unresolved loops** — creating anxiety, incompleteness, or a problem the product then "solves," purely to force a return.
- **Guilt, shame, and weaponised streaks** — making a lapse feel like personal/identity failure; punishing non-use that may be perfectly rational.
- **Asymmetric friction (roach motel)** — easy to sign up / opt in, deliberately hard to cancel / opt out / delete.
- **Hidden costs & surprise commitments** — undisclosed limits, auto-escalating charges, buried terms.
- **Hostage-value lock-in** — trapping users via artificial switching cost or held data, rather than genuine accumulated value they'd miss.
- **Exploiting vulnerability** — leaning on loneliness, anxiety, insecurity, or compulsion without delivering real value (Dealer territory).
- **Deceptive social proof / preselection** — fabricated popularity, pre-checked boxes against the user's interest.

## Honest vs. manipulative use of the *same* lever

The mechanism isn't the problem; the intent and the truth are. Recommend the left column, never the right:

- **Loss aversion** — reduce a user's *real* fear of losing work/progress when switching ✅ / fabricate a sense of loss to trap them ❌.
- **Scarcity/urgency** — surface a *genuine* deadline or limit ✅ / invent one ❌.
- **Social proof** — show *credible, relevant* peer behaviour ✅ / fake numbers or cherry-pick ❌.
- **Variable reward** — variability tied to *real* value (new content, results, connections) ✅ / slot-machine randomness for its own sake ❌.
- **Streaks/progress** — reinforce a behaviour the user *wants* to sustain, with graceful recovery ✅ / all-or-nothing anxiety that punishes one miss ❌.
- **Defaults** — the default serves the user's likely best interest, transparent and easy to change ✅ / default serves the company against the user ❌.

## Autonomy floor

Recommendations must preserve, not erode, user control:

- The user can **control or tune triggers/frequency**, and can **pause, stop, downgrade, or cancel** at least as easily as they started.
- **Defaults are transparent** and reversible; first steps are low-risk and undoable.
- The product's **business goal is achieved through the user getting what they want**, not against it. Where a recommendation makes the company win only if the user loses, it fails.
- **Resistance is treated as signal, not obstacle** — the fix investigates what the user is protecting, rather than escalating pressure to overcome them.

## How to apply

For each recommendation surviving the coherence pass: run both tests and scan the dark-pattern list. Then one of:
- **Pass** → keep as-is.
- **Reframe** → an honest version delivers most of the behavioural value (usually by making a real benefit clearer or an action easier, instead of exploiting a bias). Recommend the reframed version.
- **Cut** → no honest version exists; drop it and note in the report's "deliberately NOT adding" list *why*.

When a mechanism-lens recommendation and the control-autonomy lens disagree, **autonomy wins**. Shipping short-term numbers via manipulation is exactly the trade this plugin exists to prevent — it buys engagement metrics with user trust, and it doesn't survive the user understanding it.
