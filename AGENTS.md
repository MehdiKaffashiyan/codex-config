# Global Codex Instructions

## Scope

These instructions define the portable baseline for Codex across repositories, languages, frameworks, operating systems, and toolchains.

Project-level or nested `AGENTS.md` files may add more specific rules. Follow the more specific project rule when it conflicts with this baseline, unless the user explicitly says otherwise.

## Source Of Truth

- Treat the `codex-config` repository as the editable source of truth for global Codex configuration and personal skills.
- The canonical remote is `https://github.com/MehdiKaffashiyan/codex-config.git`.
- Discover the local checkout from the active environment or current repository. Do not hard-code local user names, drive letters, home directories, machine names, ports, secrets, or private network values in reusable instructions.
- Keep long or specialized workflows in on-demand skills under `skills/` instead of expanding this baseline.
- Use these skills when their trigger matches the task:
  - `repo-bootstrap`: new-machine setup and repository bootstrap.
  - `sync-codex-config`: conflict-safe sync between this repository, global Codex configuration, and installed personal skills.
  - `legacy-migration`: legacy replacement, migration, and parity analysis.
  - `verify-changes`: focused build, test, lint, and review verification.
  - `smart-commit`: explicit smart commit workflow.
  - `ef-migration`: Entity Framework migration workflow.
  - `ddd-rich-entity`: rich domain entity modeling rules.

## Language And Documentation

- Respond to the user in Persian by default when the user is conversing in Persian.
- Keep repository Markdown artifacts in English unless the user explicitly requests another language for that artifact.
- After project changes, update affected Markdown or equivalent documentation so it remains synchronized with implementation.

## Portability And Security

- Prefer portable references such as current repository root, workspace root, project configuration, user profile directory, temporary directory, and environment variables.
- Never copy secrets, tokens, credentials, personal data, local database values, private payloads, or machine-specific paths into source code, logs, tests, snapshots, examples, generated artifacts, committed configuration, or reusable setup instructions.
- Treat security, authorization, privacy, input validation, and least privilege as baseline concerns whenever a change touches a boundary.

## Engineering Principles

- Follow existing project architecture, conventions, and neighboring implementations before introducing new patterns.
- Keep changes focused on the requested scope and preserve existing behavior unless the task requires changing it.
- Reuse existing code and abstractions before adding new layers.
- Add abstractions, wrappers, factories, interfaces, extension points, or configuration knobs only when they solve a concrete current problem.
- Name files, types, functions, variables, modules, and services after their actual responsibility and observable behavior in the project domain.
- Prefer simple, readable implementations first. Optimize only with evidence or for an established hot path.
- Keep user-facing text localizable when the project already uses localization infrastructure.

## Code Style

- Treat each repository's selected language version, runtime, framework, package manager, formatter, linter, analyzer, and build system as authoritative.
- Respect `.editorconfig`, `.gitattributes`, formatter configs, linter configs, and language-specific style settings.
- If no repository-specific line-ending rule exists, prefer CRLF for touched text files.
- Preserve non-ASCII text exactly when reading, rewriting, splitting, moving, or generating files.
- Prefer clear names over comments that narrate obvious code.
- Add concise public documentation comments for important public APIs, domain properties, configuration options, and methods whose constraints or side effects are not obvious.
- Prefer the narrowest practical visibility for symbols.
- Treat nullable, optional, and error states as part of the contract.
- Use precise exception or error types. Do not swallow failures silently.
- Prefer modern control-flow syntax, such as switch expressions or the closest language equivalent, when it keeps code clearer and the project toolchain supports it.
- For switch or match logic with guarded cases, prefer inline guarded cases and combine equivalent cases directly when the switch remains readable.
- Do not add `Public Methods` or `Private Methods` regions. Use responsibility-based region names only when they materially improve navigation.

## Git And User Changes

- Preserve unrelated modified and untracked files.
- Do not modify, delete, overwrite, reformat, stage, or commit unrelated user changes.
- Do not use destructive filesystem or Git commands unless the user clearly requested that exact operation and the target has been verified.
- Do not use `git reset --hard`, forced checkouts, or equivalent destructive commands without explicit user approval.
- Do not stage or commit changes unless explicitly requested. A `smart commit` request activates the `smart-commit` skill.
- Never push unless the user explicitly requests it.

## Verification

- Verify repository instructions, README or contributor documentation, project metadata, and tooling conventions before editing unfamiliar code.
- Run the narrowest relevant checks while iterating, then run the relevant build, test, lint, or diff checks before delivery when practical.
- Report build failures, test failures, migration limitations, database connectivity issues, pre-existing warnings, and skipped checks clearly.
