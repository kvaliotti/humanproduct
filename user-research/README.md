# user-research

Plan interviews, analyze each participant's transcript, then roll everyone up into answers, tables, and next steps. Every finding carries verbatim quotes and a count of who said it.

- `/user-research:plan-research`: the decision the research informs, the riskiest assumptions, who to talk to, and an interview guide that asks about past behaviour. Writes `research/plan-<topic>.md`.
- `/user-research:analyze-interviews`: one Opus sub-agent per participant. It confirms the setup before running. Writes `research/analyses/<participant>.md`.
- `/user-research:synthesize-research`: answers to the research questions, assumptions marked confirmed / killed / open, and two-level tables (theme → finding) for pains, goals, barriers and workarounds. Writes `research/YYYY-MM-DD-synthesis.md`.

Put transcripts in `research/transcripts/`, or point the analysis at any folder.
