# Squash-safe finish — don't confuse "merged" with "same SHA"

## The trap

Squash merge collapses a branch into **one new commit on the base**, with a **brand-new SHA** that matches no commit on the feature branch. So SHA/ancestry checks lie:

- `git branch --merged` → the branch looks **un**merged.
- "Is my commit in main?" by SHA → **not found**.

This makes agents wrongly conclude the work never landed and re-do or re-open it. The merge strategy is fine; the **detection** is what's wrong.

## Detect merge by PR state, not by SHA

```bash
gh pr view <branch-or-number> --json state,mergedAt,mergeCommit
# state == "MERGED" and a non-null mergedAt  → it merged. Trust this over git ancestry.
```

Fallback when there's no PR (content check, not SHA check):

```bash
git fetch origin
git cherry -v origin/<base> <branch>   # lines starting with '-' are already present upstream
# or compare the diff: git diff origin/<base>...<branch> --stat  (empty-ish → changes are in base)
```

## After a confirmed merge

```bash
git fetch --prune                      # drop refs deleted on the remote
git branch -d <branch>                 # safe delete (local)
```

`commit-commands:clean_gone` automates pruning `[gone]` local branches (and their worktrees) once the remote branch is deleted.

## Why keep squash

One clean, linear commit per feature on `main` — easy to read, easy to revert. For a small team that's the best trade-off. Rebase-merge has the same new-SHA problem; merge-commits keep ancestry but clutter history. Keep squash; just detect by PR state.
