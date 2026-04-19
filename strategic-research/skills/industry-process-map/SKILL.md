---
name: industry-process-map
description: Build an end-user-centered process map and matrix for an industry, product category, or solution space — wider than any single vendor. Use this skill whenever the user asks to "map the industry", "understand the market", "map processes in [domain]", "what's happening in [category]", "understand the solution landscape", "build a process matrix", "understand what users actually do in [industry]", or provides a product name / company / industry and wants the broader workflow mapped beyond that one product. Trigger even when the user doesn't say "map" — e.g., they say "help me understand the Apple Ads space" or "how does ad creation actually work end-to-end", or they want a strategic view of a market to feed downstream research on users, competitors, or positioning. Output is one markdown doc with a process tree, one chosen matrix (with rejected candidates in an appendix), a glossary, and a YAML handoff block for downstream skills.
---

# Industry Process Map

## Promise

Given a product, a category, or an industry name, produce **one markdown artifact** that captures what end users actually do in that space, structured as:

1. A **process tree** — the user's end-to-end workflow, decomposed into steps and sub-steps.
2. **One matrix** — the single most useful framing (rows × columns) of that workflow, with a short rationale for why this framing beat the alternatives.
3. A **glossary** — end-user terminology (not vendor-speak).
4. A **YAML handoff block** — structured data for downstream skills (customer analysis, positioning, competitive research) to consume.

The output is deliberately *wider than the anchor product*. If a user anchors on "SplitMetrics", the map covers the full job ("get profitable installs") including Meta Ads, Google UAC, ASO, influencer, and manual approaches — not just Apple Search Ads.

## Operating principles

These four principles are the spine of the skill. When in doubt, return to them.

### 1. Start from the verb, not the noun

Axis labels describe what the user is **doing**, not what vendors **sell**.

- "Competitive intelligence tools" → vendor category. Reject.
- "Figuring out which keywords competitors are winning" → user verb. Accept.

Vendors carve categories to defend pricing. End users don't care about categories — they care about getting a job done. The map should read like an anthropologist's field notes on user behavior, not a Gartner quadrant.

### 2. Zoom to the right altitude

Every anchor has three altitudes. Pick the middle one.

- **Too zoomed in** (the anchor product's own feature list): "Optimize Apple Search Ads bids." Excludes substitutes.
- **Too zoomed out** (the ultimate outcome): "Acquire users profitably." Loses structural detail.
- **Right altitude** (the end-user's recurring workflow): "Decide where to spend paid acquisition budget, brief creative, launch campaigns, optimize them, and report on them."

When uncertain, write all three explicitly, then choose. Bias toward zooming out — a process map that only covers the anchor is useless downstream.

### 3. MECE is the cross-check

Before publishing, verify:
- **Rows don't overlap.** "Ad creation" and "Creative generation" collapse into one.
- **Columns don't overlap.** "Apple Ads" and "Mobile paid acquisition" live on different axes.
- **Together they cover the space.** If a user's real workflow step has no row, the map is incomplete.

MECE is the single most common failure mode. Run the check explicitly and fix before moving on.

### 4. Include substitutes, hacks, and non-consumption

Users don't use products — they solve problems. A complete map includes:
- Spreadsheets and manual work
- Agencies and consultants
- In-house builds
- Doing nothing / tolerating the pain
- Adjacent AI tools being repurposed

If the map only lists SaaS tools in a category, it's a competitive landscape, not a process map. Downstream skills depend on knowing what users do *instead*.

## Workflow

Execute in this order. Don't skip phases — each feeds the next.

### Phase 1 — Intake & calibration

Ask clarifying questions with `AskUserQuestion` only when needed. If the user provided enough context up front, skip questions and proceed.

Resolve these four variables before research:

| Variable | What it is | Example |
|---|---|---|
| **Anchor** | Optional reference product/company | "SplitMetrics" |
| **Industry / domain** | The space in the user's words | "Mobile ad optimization" |
| **End-user persona** | Whose view the map takes | "Mobile UA manager at a consumer app" |
| **Scope boundary** | How wide to go | "All paid acquisition channels for mobile apps, excluding organic ASO" |

When to ask vs. assume:
- **Ask** if the anchor is ambiguous (e.g., "Figma" — design tool? whiteboarding? prototyping?) or if no persona is obvious.
- **Assume** if the user gave a clear anchor + a one-line framing. State the assumptions you're making explicitly before proceeding, so the user can correct.

Cap questions at 2-3. Overasking annoys the user.

### Phase 2 — Web research

Goal: ground the map in how practitioners actually describe the work, not how Claude's training data describes it.

Run 5-10 targeted searches. Skip if the domain is one Claude knows cold *and* the user signals speed. Otherwise research — it catches terminology, substitutes, and workflow steps that pure reasoning misses.

Research playbook is in `references/research-playbook.md`. Read it at the start of this phase.

Capture from research:
- **Verbs** practitioners use for each workflow step
- **Channels / methods / platforms** the work happens through
- **Substitute approaches** (manual, agencies, adjacent tools)
- **Named steps** in industry workflows (e.g., "creative refresh cadence", "cohort LTV modeling")
- **The anchor's actual scope** (what cells it claims to cover) — fetch its homepage if useful

### Phase 3 — Generate candidate matrix framings

Produce **3-4 candidate framings** internally. Don't show the user yet. Each candidate has rows, columns, and a one-line reason.

The catalog of common framings — with when each works best — is in `references/matrix-framings.md`. Read it before generating candidates.

Examples of framings (not an exhaustive list):
- **Process step × Method** (how the step gets done: manually, via tool, via agency, via AI)
- **Process step × Channel** (Apple Ads, Google, Meta, TikTok, ASO)
- **User stage × Persona** (where different people in the org touch the workflow)
- **Job-to-be-done × Context** (same job in different situations)
- **Pain × Solution category** (pains the user has × classes of response)

### Phase 4 — Score & select the winner

Score each candidate on four criteria (1-5):

1. **MECE** — rows mutually exclusive, columns mutually exclusive, together exhaustive
2. **Coverage** — captures the full end-user workflow, not just the anchor's slice
3. **Actionability** — downstream skills (user research, positioning, gap analysis) can use it
4. **End-user grounding** — axis labels read like user verbs, not vendor categories

Pick the winner. Note a one-paragraph rationale: why this framing beat the others. Save the losers for the appendix — they're evidence the choice was considered, not default.

### Phase 5 — Build the full matrix

Fill every cell. A cell contains:
- The dominant **approach(es)** users take for that row × that column
- **Notable tools / methods** — actual names where possible
- **Maturity note** — commodity, emerging, manual, underserved
- **Anchor coverage flag** — `[anchor]` if the anchor product plays in this cell

Empty cells are a signal — either the framing is wrong, or the cell represents an underserved space. Call it out explicitly rather than hiding it.

### Phase 6 — Assemble the output

Use the template in `assets/output-template.md`. Structure:

1. **Framing** — anchor, industry, end-user persona, scope boundary
2. **Process tree** — indented hierarchy of user workflow steps
3. **Chosen matrix framing** — one paragraph on why this framing won
4. **The matrix** — markdown table
5. **Glossary** — end-user terminology
6. **Substitutes & adjacent approaches** — what users do instead of tools in the category
7. **Anchor coverage map** (if anchor given) — which cells the anchor plays in
8. **Open questions & calibration notes** — what's uncertain, what a follow-up skill (user/customer analysis) should probe
9. **Appendix — rejected matrix framings** — the 2-3 losers with their scores and why they lost
10. **YAML handoff block** — structured data at the end for downstream skills

The YAML handoff block is non-negotiable — it's the contract with downstream skills. Its schema is in `references/handoff-schema.md`.

Write the artifact to `/sessions/bold-dreamy-mccarthy/mnt/tempSkills/industry-process-map-[short-slug].md` where `[short-slug]` is a kebab-case tag of the anchor or industry (e.g., `splitmetrics-apple-ads`).

### Phase 7 — Share

Link the file with a `computer://` link. Keep the message short — title, one-sentence summary of the chosen framing, link. Don't rehash the content in chat; the file is the deliverable.

## MECE audit — mandatory before Phase 6

Before writing the final artifact, run this audit explicitly and fix any failures:

- [ ] Can I name two rows that partially mean the same thing? (If yes, merge.)
- [ ] Can I name two columns that partially mean the same thing? (If yes, merge.)
- [ ] Is there a real workflow step I'd mention in a user interview that has no row? (If yes, add it.)
- [ ] Does every axis label use a user verb, not a vendor noun? (If no, rewrite.)
- [ ] Have I included at least one non-SaaS substitute per column? (If no, add it.)

If you can't pass all five, the framing is wrong. Go back to Phase 3.

## Writing style for the output

The output is a strategic artifact read by a CPO-level user. Write accordingly:

- **No filler.** No "this document aims to..." openers. Start with the framing table.
- **Tables and trees over prose.** Prose only when a concept needs explanation.
- **Verbs in axis labels.** "Deciding target audience", not "Target audience analysis".
- **Specific names, not categories.** "Appfigures, AppTweak, SensorTower" beats "ASO tools".
- **Honest uncertainty.** If a cell is speculative or data is thin, mark it with `?` and explain in the open questions section.

## When this skill is the wrong tool

- User wants a competitive teardown of specific named competitors → use `product-management:competitive-brief`.
- User wants to evaluate a specific product idea → use `pm-sage:evaluate-idea`.
- User wants positioning work → use `pm-sage:position-product`.
- User wants user research synthesis → wait for skill #2 in this plugin.

This skill maps the **space**, not the products in it and not the users in it. Stay in lane.
