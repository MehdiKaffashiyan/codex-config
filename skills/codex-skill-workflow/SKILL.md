---
name: codex-skill-workflow
description: Evaluate and apply Codex skill or plugin recommendations from articles, roundups, or external sources to a repository or Codex configuration with attribution and safe dependency boundaries.
---

# Codex Skill Workflow

Use this skill when the user asks whether Codex can use skills, plugins, MCP servers, or recommendations from an external article or roundup, or when they ask to turn those recommendations into durable `codex-config` behavior.

Reference examples include Composio's Codex skills roundup at `https://composio.dev/content/top-codex-skills` and the Unicodeveloper Medium roundup at `https://medium.com/@unicodeveloper/9-must-have-skills-for-codex-in-2026-b5124b375eec`. Verify current page contents before relying on specific claims.

## Workflow

- Identify the intended scope before editing: active repository, `codex-config`, global Codex configuration, or a specific skill.
- Treat public articles and roundups as reference material, not source text to copy. Cite source URLs when their ideas influence instructions, and summarize in original wording.
- If a referenced page is current, niche, or not already available in context, verify it from the web before relying on details. If only snippets or partial content are available, state that limitation instead of presenting the details as fully verified.
- Separate recommendations into practical categories:
  - already installed local skills that should be used when their scope matches the task
  - useful but optional external tools that require installation, MCP setup, accounts, API keys, or browser access
  - irrelevant or low-value items for the current repository or workflow
- Prefer local and repository-owned skills before adding new external tools. Do not install, connect, or configure external services unless the current task clearly needs them and the user authorizes the dependency or account access.
- When the user wants recurring behavior, prefer a focused skill under `skills/` and keep `AGENTS.md` short. Update the available-skills list and repository documentation when adding or renaming a skill.
- For project work, map skill recommendations to the repository's real architecture, toolchain, tests, risks, and documentation conventions before making changes.
- For legacy replacement, data migration, EF Core, verification, or committing workflows, use the existing focused skills instead of duplicating their instructions here.
- When committing and pushing related configuration changes is requested, use `smart-commit` and preserve unrelated local files.

## Reporting

- Name the recommendations that are immediately usable, the ones that need authorization or setup, and the ones intentionally skipped.
- Mention the exact files changed in `codex-config` or the active repository.
- Report verification performed and any skipped checks.
