---
# feature-flow per-repo config.
# Copy to `.claude/feature-flow.local.md` in a project (gitignored) and tune.
# The plugin logic is generic; everything project-specific lives here.

autonomy: auto                 # auto = run to PR after plan approval | step = pause each stage
retry_budget: 3                # failed fix attempts on a task before it becomes a stop-condition

models:                        # per-stage model tiers (cost lever)
  plan: opus                   # strong model authors the plan (the contract)
  implement:                   # per-task complexity → model (Stage 3 tags each task; default standard).
    simple: haiku              #   mechanical: boilerplate, well-patterned, single-file, obvious edits
    standard: sonnet           #   normal feature work
    hard: opus                 #   tricky logic, subtle invariants, many-file coordination
  # implement: sonnet          # …or a single scalar to use one model for every task
  review: sonnet               # review/simplify pass

execution:
  mode: subagent               # subagent (default, preferred) = orchestrator only plans/gates/
                               #   debugs; implementer subagents on models.implement do ALL the
                               #   writing (parallel Task calls for independent disjoint-file tasks,
                               #   one subagent for coupled tasks). Keeps the main session's context
                               #   clean. Even trivial edits prefer a subagent; inline is the rare
                               #   exception. inline = orchestrator writes it itself (legacy; strong
                               #   model does everything and bloats context — use only deliberately).

design_doc_dir: docs/design    # where big-feature design/plan docs are written

verify:
  fast: npm run typecheck      # inner-loop gate, always run
  lint: npm run lint
  test: "npx jest {paths} --forceExit"   # {paths} = changed test paths (targeted, not the whole suite)
  extra:                       # run only when a changed path matches `when`
    - when: "packages/contracts/**"
      run: npm run check:architecture
  full_build:                  # heavy; only when these surfaces change
    when: "server|worker|*.config.*"
    run: npm run build

test_policy:
  test_first:                  # globs/topics that FORCE test-first (invariant-critical)
    - billing
    - payments
    - auth
    - permissions
    - money
  skip:                        # paths that need NO new tests
    - "**/*.css"
    - "view-only tsx"

stop_conditions:               # ADDED to the built-in defaults (never replaces them)
  - touches the LLM prompt / eval config
  - renames a background-job or queue topic
  - edits a large JSON/JSONB column on a hot-path table

pr:
  base: main
  merge: squash                # detection is squash-safe (PR state, not SHA)
  trailers:
    - "Co-Authored-By: Claude <noreply@anthropic.com>"
---

# feature-flow config

This file tunes `/ship` for one repo. Frontmatter above is the settings; this body is notes.

- `autonomy: auto` runs the whole pipeline after you approve the plan, stopping only on a
  stop-condition. Set `step` (or pass `--step`) to pause at each stage.
- `verify.*` is run as the right subset by what changed — see the `verify` skill.
- `stop_conditions` here are **added** to the built-in defaults in
  `references/stop-conditions.md`.
