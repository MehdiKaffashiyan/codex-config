---
name: legacy-migration
description: Plan and verify legacy replacement, migration, or parity work against an existing implementation.
---

# Legacy Migration

Use this skill when replacing a legacy engine, migrating behavior, or claiming parity with an existing workflow.

## Required Evidence

- Trace the relevant legacy code, tests, data model, persistence semantics, edge cases, and observable outputs before declaring behavior.
- Build a parity matrix that lists each required behavior, the legacy evidence, the new implementation location, and the verification method.
- Prefer characterization, regression, or parity tests for behavior that already exists.
- Record unsupported, skipped, or intentionally changed behavior explicitly.

## Migration Tooling

- Make migration commands idempotent where practical.
- Provide explicit skip options when skipping is meaningful.
- Report visible counts for migrated, skipped, failed, and unsupported items.
- Do not apply data migrations to an unconfirmed database.

## Delivery

- Do not declare replacement readiness until required behavior is implemented and verified.
- Report remaining parity gaps and the evidence still needed.
