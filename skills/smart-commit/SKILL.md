---
name: smart-commit
description: Safely inspect, stage, and commit only relevant changes when the user explicitly requests a smart commit or otherwise authorizes a commit.
---

# Smart Commit

Use this skill only when the user explicitly asks for a smart commit or clearly authorizes staging and committing changes.

## Workflow

1. Inspect repository state with `git status --short --branch`.
2. Review diffs for files that appear related to the task.
3. Exclude unrelated user changes, secrets, generated outputs that should not be committed, local IDE state, user-specific settings, and temporary artifacts.
4. Run relevant verification before committing when practical.
5. Stage only the selected files.
6. Re-check staged diff.
7. Commit with a meaningful conventional commit message.
8. Report the commit hash and files included.

## Rules

- Do not push unless the user explicitly requests it.
- Do not use destructive Git commands.
- Do not modify Git identity unless the user asks.
- If related and unrelated edits are mixed in one file, stage only the relevant hunks when practical; otherwise explain the limitation and ask before committing that file.
