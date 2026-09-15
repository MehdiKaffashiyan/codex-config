---
name: reference-project-implementation
description: Implement organizational project tasks by using a provided company reference project as the concrete architecture and code-convention source of truth.
---

# Reference Project Implementation

Use this skill when the user asks to implement, refactor, align, compare, or migrate work according to a company reference/sample project.

The reference project is evidence, not a source for blind copying. Inspect it first, identify the relevant patterns, then implement the current task in the active repository with the same architectural direction, naming conventions, dependency boundaries, and verification style while preserving current business behavior.

## Reference Discovery

- Use the reference project path, branch, project name, or repository name provided by the user for the current task.
- If the reference is ambiguous and materially affects architecture, ask one concise question before editing.
- Compare equivalent layers and files before deciding the implementation shape, especially domain entities, DTOs, application services, interfaces, repositories, infrastructure services, controllers, dependency injection, migrations, tests, and README guidance.
- Prefer multiple nearby reference examples over a single file when the pattern affects architecture or public API shape.
- Treat project-specific instructions in both repositories as authoritative. If the current repository and reference project conflict, preserve the current repository's public behavior unless the user explicitly requests the reference behavior.

## Implementation Rules

- Build from the requested task, not from a broad clone of the reference project.
- Keep changes scoped to the smallest coherent batch that moves the current repository toward the reference structure.
- Do not copy secrets, local paths, connection strings, environment-specific settings, generated artifacts, or unrelated business logic from the reference project.
- Preserve public API behavior, persistence behavior, domain invariants, comments, localization text, and Unicode text unless the task explicitly changes them.
- Follow the reference project's naming and placement conventions for the touched concepts.
- When moving code between layers, update namespaces, DI registrations, imports/usings, tests, and documentation in the same batch.
- If a reference pattern requires a shared abstraction, use the abstraction already present in the current repository or its shared libraries before creating a new one.

## Comparison Checklist

Before editing, inspect the relevant reference examples and record the practical mapping in your working notes:

- current concept name to reference concept name
- source and target layer or folder
- interface and implementation naming
- request/response DTO naming
- controller route shape and authorization conventions
- repository/unit-of-work conventions
- domain model and aggregate/entity/value-object boundaries
- persistence configuration and migration implications
- verification commands used by the current repository

Keep this checklist lightweight. Use it to prevent drift, not as a separate deliverable unless the user asks for one.

## Verification

- Run focused scans to ensure old names, old namespaces, or old layer references were not left behind.
- Run the narrowest relevant build/test command, then broader checks when the change affects shared architecture or public APIs.
- For persistence or domain model changes, check pending migrations with the repository's EF workflow and inspect generated migrations before keeping them.
- Report any reference mismatch, skipped check, pre-existing warning, tool failure, or required follow-up clearly.

## Source Control

- Do not commit or push application repository changes unless the user explicitly requests it.
- When the requested work is a Codex configuration or skill change inside the configuration repository, commit only the related configuration files and push after verification if the user asked to keep that repository synchronized.
