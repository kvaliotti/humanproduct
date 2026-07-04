---
name: verify
description: "Run the project's verification gate and report real output — trigger on \"run verification\", \"run the gates/checks\", \"does it pass typecheck/lint/tests\", \"check it's green\", or when /ship reaches its verify stage. Runs the right subset (typecheck / lint / tests / arch-checks / build) by what changed, per the repo config, and requires green + pasted evidence before anything is called done."
argument-hint: "[changed paths]"
allowed-tools: Read, Bash, Grep, Glob
---

# verify — evidence-based gate

Prove the change is sound. **Evidence, not assertions**: never claim a gate passed without showing its command and output.

## Steps

1. **Load config** — read the `verify` block from `.claude/feature-flow.local.md`. If absent, fall back to common defaults (`npm run typecheck`, `npm run lint`, `npx jest {paths} --forceExit`) **only if this is a Node repo** (a `package.json` exists). Otherwise don't guess a toolchain — detect it from the repo (e.g. `pyproject.toml`/`tox.ini` → the project's Python test/lint commands; `go.mod` → `go build`/`go vet`/`go test`; `Cargo.toml` → `cargo check`/`clippy`/`test`) or ask the user for the verify commands. Report which gate commands you're using and why.
2. **Determine changed paths** — from `$ARGUMENTS` if given, else `git diff --name-only <base>...HEAD` plus unstaged (`git diff --name-only`).
3. **Always run** the fast gate (`verify.fast`, typically typecheck) and `verify.lint`.
4. **Tests — targeted, never the whole suite by reflex.** Substitute the changed test paths into `verify.test` (`{paths}`). For Jest: keep `--forceExit`; remember path filters are regex, so escape bracketed route segments (`\[id\]`) and route groups (`\(frontend\)`) or the run silently matches nothing.
5. **Conditional extras** — for each entry in `verify.extra`, if a changed path matches its `when` glob, run its command (e.g. an architecture/contract check for a specific area).
6. **Full build** — run `verify.full_build.run` ONLY if a changed path matches `verify.full_build.when` (e.g. server/worker/build-config surfaces). Otherwise skip it; the fast gate is the inner loop.

## Reporting

- For each gate: show the command, then the first ~150–200 relevant output lines.
- **Any failure → stop and report it with the failing output** so the caller can invoke the `debug` skill (root cause before fixes). This skill is read-only; it diagnoses nothing itself. Do not proceed to review/PR on red, and do not paper over it.
- **Definition of Done** = every selected gate green, with its output shown. Only then report the gate as passed.
