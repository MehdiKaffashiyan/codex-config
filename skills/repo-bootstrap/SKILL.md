---
name: repo-bootstrap
description: Bootstrap Codex configuration on a new machine or initialize a repository from the codex-config source of truth.
---

# Repository Bootstrap

Use this skill when setting up Codex configuration on a new machine, repairing a missing global configuration, or preparing a repository before project work.

## Workflow

- Locate or clone the `codex-config` repository from `https://github.com/MehdiKaffashiyan/codex-config.git`.
- Prefer a `codex-config` checkout inside the active Codex configuration directory.
- If the configured checkout is missing on a machine, clone the canonical remote into the active Codex configuration directory before starting repository work.
- Discover local paths from the active environment. Do not embed machine-specific paths in reusable files.
- Verify the checkout before installing configuration:
  - `git status --short --branch`
  - `git remote -v`
  - `git fetch origin` when network access is available
- Use the `sync-codex-config` skill to synchronize repository-root instructions and install personal skills from this repository.
- Create or update a standalone global `AGENTS.md` only when the user explicitly asks for one.
- When entering another repository, ensure its root `AGENTS.md` exists. Initialize it from the `codex-config` baseline only when missing, and preserve repository-specific rules.
- Before editing project code, inspect repository instructions, README or contributor docs, project files, formatter and linter configuration, and documented build or test commands.
- Confirm Git identity before committing. Do not invent or change identity values unless the user asks.

## Constraints

- Keep the flow idempotent: rerunning setup should update missing or stale instructions without duplicating sections.
- Never copy secrets, local database values, private payloads, or local machine paths into reusable setup files.
- If remote state cannot be checked, continue from the best local source and report the limitation.
