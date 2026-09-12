---
name: sync-codex-config
description: Synchronize the codex-config repository with global Codex configuration and installed personal skills using a conflict-safe workflow.
---

# Sync Codex Configuration

Use this skill when the user asks to sync Codex configuration, install personal skills from `codex-config`, update the global `AGENTS.md`, or prepare the same configuration on another machine.

## Source

- Treat the local `codex-config` checkout as the editable source of truth.
- The canonical remote is `https://github.com/MehdiKaffashiyan/codex-config.git`.
- Discover the active global Codex configuration directory from the environment or Codex runtime. If it cannot be discovered, ask for the location before writing outside the repository.

## Conflict-Safe Sync

1. Inspect local repository state:
   - `git status --short --branch`
   - `git remote -v`
2. Fetch remote state when network access is available.
3. Compare local branch, upstream branch, and working tree state before merging, rebasing, or copying files.
4. Stop before writing if both source and destination changed in non-equivalent ways. Report both locations and the conflicting sections.
5. Copy only clearly selected files:
   - repository `AGENTS.md` to global `AGENTS.md`
   - repository `skills/<name>/` to the installed personal skills directory
6. Preserve destination-only files unless the user explicitly asks to remove them.
7. After copying, normalize text files according to the active line-ending policy and verify the installed files exist.

## Rules

- Never blind-overwrite local or remote content.
- Never delete destination content to make sync easier.
- Never push unless the user explicitly asks.
- Keep sync lossless: preserve both versions when there is uncertainty.
- Report authentication, network, permission, or conflict limitations clearly.
