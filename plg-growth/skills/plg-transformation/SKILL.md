---
name: plg-transformation
description: "Plan the org changes needed to become product-led: strategic alignment, PLG-native goals and incentives, growth team structure, opportunity solution trees, and process design (Freedom Within Frame), with a phased roadmap. Use for: become product-led, PLG transformation, PLG org structure, growth team structure, PLG operating model, PLG goals, PLG culture, how to go PLG as an org, opportunity solution tree for teams, PLG process design."
---

# PLG Transformation

Find the one or two org gaps that stop PLG work from happening, and lay out the order to fix them. This skill does not run change management.

**Quick answers.** If the question is narrow ("how should we structure a growth team of 3 PMs?"), answer it directly.

## 1. Assess four areas and name the gaps

Ask conversationally, a few questions at a time. For each area, output the specific gap and what it blocks. Don't give 1–5 scores.

- **Strategy:** Is PLG in the strategy with a VP+ sponsor and its own budget? Or is it a side project?
- **Goals:** Do teams own product metrics (activation, conversion, expansion) that come from the revenue driver tree (`plg-revenue-analysis`)? Or only revenue and MQL targets?
- **Structure:** Is there a dedicated, cross-functional growth team (PM, design, engineers, data) with authority over the product?
- **Culture:** Does the team ship experiments, talk to users, and survive a failed test without political cost?

Decision rules:
- **No executive sponsor means stop.** The first step is the business case, not a reorg.
- **Growth sits in product, not marketing.** It needs authority over the product and its own engineers.
- **Culture is not a phase.** Work it into every step. Don't schedule it last.

## 2. Align goals and incentives

Replace sales-led measures with product-led ones: MQLs become PQAs and PQLs (`product-led-sales`), and customer count becomes activated customers. Revenue targets get leading indicators beside them: activation, conversion, and ARPA. Align incentives:
- Sales: expansion, not only new logos
- CS: adoption and expansion, not only retention
- Product: metrics moved, not features shipped
- Marketing: activated signups by channel, not signup volume

## 3. Structure the team

- **Small team:** put everyone on the single lever with the highest revenue-tree sensitivity. Explore across levers for a quarter only if no data shows the bottleneck.
- **Larger team:** split by revenue type (new, retained, expansion) when sales is involved. Split by funnel stage when growth is pure self-serve.
- More detail: `${CLAUDE_PLUGIN_ROOT}/references/team-structuring.md`.

Have each team run an opportunity solution tree (Teresa Torres): outcome → opportunities → solutions → experiments. Rules for the outcome: the team must be able to move it by changing the product, and it must be narrow, e.g. "SMB activation" rather than "revenue." Pilot with one team for a quarter before rolling it out.

## 4. Design processes (Freedom Within Frame)

A product process should improve decisions by making information visible. It should not standardize how people work. Define the **frame**, the few non-negotiables (e.g. "every experiment has a hypothesis and guardrails before launch"). Everything else is **freedom**.

When a process isn't followed, find which condition fails before adding more process:
- **Know:** people don't know it exists. Put it inside the tools they already use, not in a wiki.
- **Can:** it's too heavy. Cut steps, pre-fill templates, automate.
- **Want:** people choose to skip it. Make the cost of skipping visible, enforce small violations, and have leaders follow it first. Don't reward compliance.
- **Do:** people forget at the moment of action. Use an escalating set of forcing functions: automatic triggers and follow-up checks first, then soft approvals, and hard blocks only if softer ones keep failing.

Treat the process as a product. Interview its users, pilot it with one team, and delete the steps people consistently skip.

## 5. Roadmap (only if asked)

Phases: **Foundation** (sponsor, business case, revenue tree) → **Instrument** (tracking and dashboards, `plg-data-setup`) → **Activate** (growth team formed, activation metric improving) → **Scale** (experiment cadence, PLS motion) → **Embed** (PLG goals in every team). For each phase, give the exit criteria, the dependencies, and what would make you pause. Don't invent numeric targets. Set them from the user's own baseline.

## Output

Lead with: "Biggest gap: [X]. It blocks [Y]. First move: [Z]." Then give the gaps by area, the goal and incentive changes, the team model, and, if asked, the process design or roadmap. Keep it to about one page.
