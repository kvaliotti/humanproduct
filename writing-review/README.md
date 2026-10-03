# writing-review

Review a draft the way a linter reviews code: find defects, don't rewrite. Five narrow reviewers run in parallel without seeing each other's work, then their findings are merged into one ranked review.

- `/writing-review:review-writing`: confirms the purpose, reader, and desired change, then runs the **reader**, **structure**, **argument**, **evidence**, and **prose** reviewers as Opus sub-agents. Every finding is an exact quote, the problem it causes, and the smallest fix. Pass `--only argument,prose` (or just ask for one kind of review) to run fewer.

The prose reviewer checks a short list of Zinsser-style clutter rules and AI-writing tells (`skills/review-writing/references/writing-rules.md`). The review's own text follows the same rules.

If the draft is a file, the review is also written to `<draft-name>-review.md` beside it.
