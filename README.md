# codex-config

Portable Codex configuration and personal skills, versioned in Git and reusable across machines.

## Purpose

This repository is the editable source of truth for:

- global Codex baseline instructions in `AGENTS.md`
- personal on-demand skills under `skills/`
- documentation for bootstrapping, synchronizing, and maintaining the configuration

Use a `codex-config` checkout inside the active Codex configuration directory for durable Codex behavior. If it is missing on a machine, clone this repository there before starting repository work. Avoid treating a standalone global `AGENTS.md` file as the source of truth when this checkout is available.

The canonical remote is:

```text
https://github.com/MehdiKaffashiyan/codex-config.git
```

## Structure

```text
codex-config/
|-- AGENTS.md
|-- README.md
`-- skills/
    |-- repo-bootstrap/
    |   `-- SKILL.md
    |-- sync-codex-config/
    |   `-- SKILL.md
    |-- legacy-migration/
    |   `-- SKILL.md
    |-- verify-changes/
    |   `-- SKILL.md
    |-- smart-commit/
    |   `-- SKILL.md
    |-- ef-migration/
    |   `-- SKILL.md
    |-- ddd-rich-entity/
    |   `-- SKILL.md
    `-- codex-skill-workflow/
        `-- SKILL.md
```

Keep `AGENTS.md` short. Move specialized, lengthy, evolving, or occasional workflows into focused skills so Codex only loads them when they are relevant.

## Setup On A New Machine

1. Clone the repository into a local path of your choice:

   ```bash
   git clone https://github.com/MehdiKaffashiyan/codex-config.git
   ```

2. Inspect the checkout before installing anything:

   ```bash
   cd codex-config
   git status --short --branch
   git remote -v
   ```

3. Use the `repo-bootstrap` skill for new-machine setup. It explains how to initialize global Codex configuration from this repository without hard-coding local paths.

## Update And Pull Workflow

Before updating the local checkout, inspect local changes and fetch remote state:

```bash
git status --short --branch
git fetch origin
```

Only merge or rebase after confirming the local branch, upstream branch, and working tree state. Do not overwrite local edits blindly. If local and remote changes conflict, preserve both sides and resolve deliberately.

## Sync With Global Codex Configuration

Use the `sync-codex-config` skill when synchronizing this repository with the active Codex configuration directory.

The sync workflow should:

- treat this repository as the editable source
- copy `AGENTS.md` into the global Codex configuration only after comparing both files
- install or update personal skills from `skills/`
- preserve local-only files unless the user asks to remove them
- stop and report real conflicts instead of deleting or overwriting content

## Adding A Skill

Add each skill as a folder under `skills/` with a required `SKILL.md`.

Good skills are:

- short and reusable
- clear about when they should activate
- self-contained for one workflow
- portable across machines
- free of secrets and local-only paths

After adding or changing a skill, verify that its frontmatter has a `name` and `description`, and that the body contains only the instructions needed for that workflow.

## Maintenance And Version Control

- Keep general rules in `AGENTS.md`; move workflow detail to skills.
- Remove duplicated rules between `AGENTS.md` and skills.
- Review diffs before committing.
- Stage only related files.
- Use meaningful conventional commit messages.
- Do not push unless explicitly requested.
- For this repository only, push related configuration commits after verification when keeping the remote synchronized is the intended outcome.

## Markdown Files

- [Global Codex instructions](AGENTS.md)
- [Repository bootstrap skill](skills/repo-bootstrap/SKILL.md)
- [Codex configuration sync skill](skills/sync-codex-config/SKILL.md)
- [Legacy migration skill](skills/legacy-migration/SKILL.md)
- [Verification skill](skills/verify-changes/SKILL.md)
- [Smart commit skill](skills/smart-commit/SKILL.md)
- [Entity Framework migration skill](skills/ef-migration/SKILL.md)
- [DDD rich entity skill](skills/ddd-rich-entity/SKILL.md)
- [Codex skill workflow](skills/codex-skill-workflow/SKILL.md)
