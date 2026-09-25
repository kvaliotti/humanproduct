---
name: analyze-sales-call
description: Analyze sales, discovery, or demo call transcripts. Runs one Opus sub-agent per client, merging each client's transcripts, and extracts pain points, desired outcomes, objections, and decision criteria, each with verbatim quotes, then lists what it would take to convert the prospect and what messaging would hook them. Use when the user pastes or links call transcripts and asks for call analysis, voice of customer, pains and objections, or deal insights.
argument-hint: "[folder or files with transcripts; defaults to transcripts/]"
---

# Analyze Sales Call

## Orchestration

1. Group transcripts by client, using the filename prefix and the transcript's participants. Default input is `transcripts/`.
2. Before running, show a table (client → transcripts → output file, with existing files flagged) and tell the user:
   1. Each client gets its own sub-agent (Opus).
   2. Transcripts for one client are merged into one analysis.

   Ask them to confirm or change either default with AskUserQuestion. Wait for their answer.
3. Spawn all sub-agents in one message: `subagent_type: "sales-call-analysis:call-analyst"`, `model: "opus"`. Pass each one the client, transcript paths, merge or not, "our side" speakers if known, the output path, and the path to this file (`${CLAUDE_PLUGIN_ROOT}/skills/analyze-sales-call/SKILL.md`).
4. Output: `analyses/<client>.md`, or `analyses/<client>-<call>.md` when not merged.
5. Finish with a table: client, calls, file, summary. Mention `/sales-call-analysis:aggregate-call-analyses`.

## Analysis

Infer which speakers are "our side".

Produce these sections in this order:

1. Pain points of the prospect
2. Exact quotes of wording used to describe pain points
3. Desired outcomes of the prospect
4. Exact quotes of wording used to describe outcomes
5. Objections of the prospect, including implied risks
6. Exact quotes of wording used to describe objections
7. Decision criteria: what they will judge us and the alternatives by
8. Exact quotes of wording used to describe decision criteria
9. What it would take to convert them: concrete things they need to see or get
10. What would hook them: the phrasing that would get them to review or research the platform

Rules:
- Start with a header: the call, the prospect's name and role, our side, and a one-line **Context** covering team, volume, channels, current tools, and next step.
- Quotes must be verbatim from the transcript, transcription errors included, in *"italics"*. Never paraphrase inside quotes.
- Numbered lists for analysis and bullets for quotes. Bold a short lead phrase on each analysis item, then write one or two plain sentences.
- Group quotes under bold labels matching the lead phrases of the analysis items.
- Only the prospect's words count as evidence. Our side's claims are not.
- If there are no hard objections, say so and list implied risks instead: an incumbent tool, churn, timing, fit gaps, and unanswered questions.
- Items in section 9 must be specific to this prospect and testable during a trial. Name their assets, tools, metrics, and numbers.
- Build section 10 from their own vocabulary. Write ready-to-use one-liners, each with a bold theme label, then add **Words to use** and **Words to avoid**.
- End with **Follow-ups to confirm**: questions left unanswered or promises made on the call.
- Merged calls: analyze as one chronology, list all source files in the header, tag quotes with the call date, and mark items as new, persistent, or resolved.
