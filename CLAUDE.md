# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A Claude Code plugin marketplace (not an application). No build, lint, or test step — it ships content (skills and slash commands) consumed by Claude Code when a user installs a plugin from it. Published at `kvaliotti/humanproduct` and installed via `/plugin marketplace add kvaliotti/humanproduct`.

## Structure

```
.claude-plugin/marketplace.json   # marketplace manifest — lists every plugin in the repo
prd-workflow/                     # plugin (directory referenced by marketplace.json)
  .claude-plugin/plugin.json      # plugin manifest (name, version, description, keywords)
  skills/<skill-name>/SKILL.md    # each skill: YAML frontmatter + markdown body
  skills/<skill-name>/references/ # optional supporting docs the skill reads at runtime
strategic-research/               # plugin — also ships a slash command
  .claude-plugin/plugin.json
  commands/<command>.md           # optional: slash commands with frontmatter (description, argument-hint)
  skills/<skill-name>/SKILL.md
  skills/<skill-name>/assets/     # optional: templates the skill writes out (HTML, md scaffolds)
  skills/<skill-name>/references/
```

Adding a plugin: create `<plugin>/.claude-plugin/plugin.json` and `<plugin>/skills/...` (plus `<plugin>/commands/...` if it exposes slash commands), then register it in the root `marketplace.json` `plugins` array with `name`, `source` (relative path), `description`, `version`.

## Skill contract

Every `SKILL.md` starts with YAML frontmatter:

- `name` — must match the directory name
- `description` — trigger phrases; this is what Claude Code matches against user intent to decide when to activate the skill. Be generous with phrasings.
- `user-invocable: true` — exposes the skill as `/skill-name` (optional — skills can also activate purely from description matching)
- `argument-hint` — shown in the slash-command picker

Skill bodies are prose instructions the model follows at activation time. They can reference sibling files via relative paths (e.g., `references/prd-template.md`, `assets/html-template.html`).

## Command contract

Slash commands live in `<plugin>/commands/<name>.md` with frontmatter:

- `description` — shown in the command picker and used for matching
- `argument-hint` — placeholder text for the argument field

The body is the prompt the command runs. `strategic-research/commands/strategic-research.md` is the working example.

## prd-workflow architecture

The three skills form a sequential pipeline that enriches a single `PRD-[feature-name].md` file in the user's working directory:

1. `prd-draft` — writes the initial PRD from messy input, using `references/prd-template.md`
2. `prd-evaluate` — runs gap analysis against `references/evaluation-checklist.md`; the user accepts/rejects findings, PRD is updated
3. `sit-beh` — runs Situation/Behaviour analysis on the PRD's situations section, adds new user stories and acceptance criteria; also writes to `.sitbeh/` in the user's working directory

Each skill's SKILL.md describes the handoff to the next. When editing one, keep the chaining instructions at the end of the file consistent with the others.

## strategic-research architecture

Five skills chained by YAML handoffs, orchestrated by the `/strategic-research` command. Each skill emits a markdown artifact plus a YAML handoff block the next skill parses:

1. `industry-process-map` — process tree + matrix of what end users do in the space
2. `audience-segment-research` — segments, stakeholders, tensions
3. `willingness-to-pay-research` — per-segment value, drivers, proof signals
4. `competitor-evaluation` — 7 Powers grid, strategy canvases
5. `strategic-synthesis-report` — consumes all four handoffs, renders a self-contained HTML report (plus a one-page markdown companion) using `assets/html-template.html`

The YAML handoff schemas are the contract between skills — they live under each skill's `references/handoff-schema.md`. Breaking a schema breaks the pipeline, so treat those files as load-bearing and bump `version` in `plugin.json` + `marketplace.json` when changing one.

Skills are also callable individually. The orchestrator command supports `--from=step-N` to resume mid-pipeline when upstream artifacts already exist.

## Distribution

`main` is the published branch — pushing updates it live for anyone who has added the marketplace. Bump `version` in both the plugin's `plugin.json` and the matching entry in `marketplace.json` when shipping breaking changes to a skill or handoff schema.

## Ignored paths

`.remember/` is Claude session state (logs, tmp). Never commit it. `.DS_Store` is also gitignored. `strategic-research/working/` holds local draft artifacts and should stay out of commits.
