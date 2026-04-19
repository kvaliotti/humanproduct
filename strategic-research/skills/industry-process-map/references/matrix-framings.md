# Matrix Framings Catalog

A catalog of common matrix framings, when each works, and when each fails. Use this in Phase 3 to generate candidate framings, not as a menu to pick from blindly.

The horizontal axis is almost always **user verbs / workflow steps**. The catalog below mostly varies the vertical axis. Occasionally a different horizontal axis is better — note those cases too.

---

## Framing 1 — Process step × Method (how it gets done)

**Rows (horizontal):** workflow steps the user performs
**Columns (vertical):** methods — how each step can happen (manual, spreadsheet, specialized tool, agency, AI agent, in-house build)

**When it works best:**
- The industry has multiple maturity levels (manual → specialized → automated)
- Substitutes and hacks are a real part of the landscape
- The downstream question is "where will specialized tools displace manual work?"

**When it fails:**
- When the work is dominated by one method (e.g., always manual, always one SaaS)
- When the meaningful variance is by channel, not by method

**Example:**
| Process step | Manual | Spreadsheet | Specialized tool | Agency | AI agent |

---

## Framing 2 — Process step × Channel / Platform

**Rows (horizontal):** workflow steps
**Columns (vertical):** channels or platforms the work happens on

**When it works best:**
- The work is fundamentally channel-specific (ads, social, distribution)
- Users operate across multiple channels and need parity
- The anchor product covers one channel and we want to show the broader multi-channel picture

**When it fails:**
- When the channels are mostly equivalent (redundant columns)
- When the meaningful variance is by method, not by platform

**Example:**
| Process step | Apple Ads | Google UAC | Meta | TikTok | ASO |

---

## Framing 3 — Process step × Persona

**Rows (horizontal):** workflow steps
**Columns (vertical):** roles in the user's org that touch each step

**When it works best:**
- The workflow involves handoffs between specialists (designer → PM → marketer → analyst)
- Organizational friction is a real pain
- Downstream question is "who is the buyer / user / champion / blocker?"

**When it fails:**
- When one persona owns the entire workflow (no handoff story)
- When org structure varies too much to generalize

**Example:**
| Process step | Designer | PM | UA Manager | Analyst | CFO |

---

## Framing 4 — Job-to-be-done × Context

**Rows (horizontal):** jobs (in JTBD phrasing: "when... I want to... so that...")
**Columns (vertical):** contexts (company size, maturity, stage, budget)

**When it works best:**
- The same job looks very different in different contexts (e.g., early-stage startup vs. enterprise)
- Downstream question is "which segment to serve?"

**When it fails:**
- When the job is basically the same across contexts
- When contexts don't cleanly partition the market

**Example:**
| JTBD | Solo indie | Small startup | Growth-stage | Enterprise |

---

## Framing 5 — Pain × Solution class

**Rows (horizontal):** recurring pains users have
**Columns (vertical):** classes of response (avoid, tolerate, workaround, tool, agency, rebuild)

**When it works best:**
- The market is defined more by pain than by workflow (e.g., compliance, reliability, trust)
- Downstream question is "what painkillers to build?"

**When it fails:**
- When pains map cleanly to workflow steps (then Framing 1 is better)
- When pain identification is speculative — skill #2 would do this better

**Example:**
| Pain | Avoid it | Tolerate | DIY workaround | Buy a tool | Hire agency |

---

## Framing 6 — Stage × Maturity

**Rows (horizontal):** user journey stages (discover → decide → do → measure → improve)
**Columns (vertical):** maturity of the user's practice (ad-hoc, repeatable, measured, optimized)

**When it works best:**
- The space has a clear maturity curve
- Downstream question is "who to sell to first?"

**When it fails:**
- When maturity isn't a meaningful variable
- When the stages collapse into one

---

## Scoring rubric for candidates

Score each candidate 1-5 on these four criteria. Pick the highest total — break ties on actionability.

| Criterion | Bad (1) | Good (5) |
|---|---|---|
| **MECE** | Rows/columns overlap; gaps exist | Clean partition, no gaps, no overlap |
| **Coverage** | Covers only the anchor's slice | Covers the full end-user workflow and its substitutes |
| **Actionability** | Output is decorative | Output feeds user research, positioning, gap analysis |
| **End-user grounding** | Axes read like vendor categories | Axes read like user verbs |

## Meta-note

The catalog is not exhaustive. If the space suggests a different framing — e.g., **Process step × Data source**, **Workflow step × Decision type** — use that. The catalog is a starting point, not a constraint.

When tempted to pick the safest framing (usually "Process × Channel"), pause and ask whether it's actually right. Safe framings produce safe (i.e., boring, already-known) insights.
