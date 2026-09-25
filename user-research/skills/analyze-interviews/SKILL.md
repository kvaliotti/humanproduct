---
name: analyze-interviews
description: Analyze user interview transcripts or notes. Runs one Opus sub-agent per participant and extracts what they actually did, pains, goals, workarounds, and barriers, each with verbatim quotes, plus answers to the study's research questions. Use when the user shares interview transcripts or notes and asks to analyze interviews, code transcripts, pull insights, or "what did we learn".
argument-hint: "[folder or files with transcripts; defaults to research/transcripts/]"
---

# Analyze Interviews

## Orchestration

1. Group transcripts by participant, using the filename and the speakers. Default input is `research/transcripts/`. Find the newest `research/plan-*.md`; if there is none, the analysis still runs but section 10 is skipped.
2. Before running, show a table (participant → transcripts → output file, with existing files flagged) and tell the user:
   1. Each participant gets their own sub-agent (Opus).
   2. The analysis answers the research questions from `<plan file>`, or from none if no plan was found.

   Ask them to confirm or change either with AskUserQuestion. Wait for their answer.
3. Spawn all sub-agents in one message: `subagent_type: "user-research:interview-analyst"`, `model: "opus"`. Pass each one the participant, transcript paths, the plan path if any, the interviewer's name if known, the output path, and the path to this file (`${CLAUDE_PLUGIN_ROOT}/skills/analyze-interviews/SKILL.md`).
4. Output: `research/analyses/<participant>.md`.
5. Finish with a table: participant, file, one-line summary. Mention `/user-research:synthesize-research`.

## Analysis

Infer which speaker is the interviewer.

Produce these sections in this order:

1. What they actually did: the specific episodes they described, in order, with the tools, people, and workarounds involved
2. Exact quotes describing what they did
3. Pains: problems that cost them time, money, or stress
4. Exact quotes describing pains
5. Goals: what they were trying to achieve, in their terms
6. Exact quotes describing goals
7. Barriers: why they didn't do the target behaviour, tagged **don't know**, **can't**, or **don't want**
8. Exact quotes describing barriers
9. Surprises: anything that contradicts the plan's assumptions or the team's beliefs
10. Answers to the research questions: for each question in the plan, what this participant tells us, or "not covered"

Rules:
- Start with a header: participant, role, segment, interview date, and a one-line **Context** covering their situation, tools, and how often they face the problem.
- Quotes must be verbatim from the transcript, transcription errors included, in *"italics"*. Never paraphrase inside quotes.
- Numbered lists for analysis and bullets for quotes. Bold a short lead phrase on each analysis item, then write one or two plain sentences.
- Group quotes under bold labels matching the lead phrases of the analysis items.
- Only the participant's words count as evidence. The interviewer's words don't.
- Mark anything they said they *would* do, or said in general terms ("I always…", "people like me…"), as **(said, not done)**. Compliments and feature requests are not evidence of need; if you keep one, say what problem sits behind it.
- Skip sections 7 and 8 if the study has no target behaviour.
- End with **Follow-ups to confirm**: things left unclear or worth asking them again.
