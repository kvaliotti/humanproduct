# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A Claude Code plugin marketplace (not an application). No build, lint, or test step — it ships content (skills) consumed by Claude Code when a user installs a plugin from it. Published at `kvaliotti/humanproduct` and installed via `/plugin marketplace add kvaliotti/humanproduct`.

## Structure

```
.claude-plugin/marketplace.json   # marketplace manifest — lists every plugin in the repo
prd-workflow/                     # one plugin (a directory referenced by marketplace.json)
  .claude-plugin/plugin.json      # plugin manifest (name, version, description, keywords)
  skills/<skill-name>/SKILL.md    # each skill: YAML frontmatter + markdown body
  skills/<skill-name>/references/ # optional supporting docs the skill reads at runtime
```

Adding a plugin: create `<plugin>/.claude-plugin/plugin.json` and `<plugin>/skills/...`, then register it in the root `marketplace.json` `plugins` array with `name`, `source` (relative path), `description`, `version`.

## Skill contract

Every `SKILL.md` starts with YAML frontmatter:

- `name` — must match the directory name
- `description` — trigger phrases; this is what Claude Code matches against user intent to decide when to activate the skill. Be generous with phrasings.
- `user-invocable: true` — exposes the skill as `/skill-name`
- `argument-hint` — shown in the slash-command picker

Skill bodies are prose instructions the model follows at activation time. They can reference sibling files via relative paths (e.g., `references/prd-template.md`).

## prd-workflow architecture

The three skills form a sequential pipeline that enriches a single `PRD-[feature-name].md` file in the user's working directory:

1. `prd-draft` — writes the initial PRD from messy input, using `references/prd-template.md`
2. `prd-evaluate` — runs gap analysis against `references/evaluation-checklist.md`, the user accepts/rejects findings, PRD is updated
3. `sit-beh` — runs Situation/Behaviour analysis on the PRD's situations section, adds new user stories and acceptance criteria; also writes to `.sitbeh/` in the user's working directory

Each skill's SKILL.md describes the handoff to the next. When editing one, keep the chaining instructions at the end of the file consistent with the others.

## Distribution

`main` is the published branch — pushing updates it live for anyone who has added the marketplace. Bump `version` in both the plugin's `plugin.json` and the matching entry in `marketplace.json` when shipping breaking changes to a skill.

## Ignored paths

`.remember/` is Claude session state (logs, tmp). Never commit it. `.DS_Store` is also gitignored.
