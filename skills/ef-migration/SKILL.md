---
name: ef-migration
description: Create, inspect, and report Entity Framework migrations without applying them to an unconfirmed database.
---

# Entity Framework Migration

Use this skill when a change requires an Entity Framework migration or the user asks to add, inspect, or adjust EF migration artifacts.

## Workflow

- Inspect existing DbContext, entity mappings, migrations, naming conventions, relationships, indexes, query filters, and persistence patterns before changing persistence code.
- Keep persistence configuration separate from domain logic when the repository follows that pattern.
- Generate migrations with the repository's documented tooling. When this repository family uses `Src/`, run migration scaffolding from `Src/` unless local instructions say otherwise.
- Inspect the scaffolded migration and model snapshot before delivery.
- Verify the migration represents only the intended schema change.

## Rules

- Never apply a migration to an unconfirmed database.
- Do not edit generated migration artifacts casually; prefer regenerating when the tooling supports it and the repository expects generated output.
- Report migration limitations, design-time factory issues, database connectivity issues, and skipped database update steps clearly.
