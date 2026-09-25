# sales-call-analysis

Turn call transcripts into pains, outcomes, objections and decision criteria, each with verbatim quotes, plus what it would take to convert each prospect and which hooks would land with them. Then roll all clients up into cross-client tables.

- `/sales-call-analysis:analyze-sales-call`: one Opus sub-agent per client, with each client's transcripts merged. It confirms both defaults before running. Writes to `analyses/<client>.md`.
- `/sales-call-analysis:aggregate-call-analyses`: two-level tables (category → item) for pains, outcomes, objections and decision criteria, with companies, quotes and counts. Writes to `synthesis/`.
