---
name: verify-changes
description: Choose and run focused checks for changed code, documentation, configuration, or generated artifacts before delivery.
---

# Verify Changes

Use this skill when validating a completed change, selecting tests, reviewing a diff, or preparing delivery notes.

## Workflow

- Inspect the relevant diff before final verification.
- Run the narrowest meaningful checks while iterating.
- Before delivery, run the relevant build, test, lint, type-check, formatter, migration inspection, or documentation checks that match the changed surface.
- Prefer repository scripts and documented workflows over generic commands.
- Keep command output concise and report the important failure lines or summaries.

## Test Expectations

- Add or update tests for changed public behavior, regressions, invariants, parsing, persistence behavior, and failure paths.
- Keep tests deterministic, isolated, order-independent, and safe for parallel execution unless a shared resource is explicitly documented.
- Test through public behavior and avoid widening production visibility solely for tests unless the repository already does so.

## Reporting

- Clearly report checks that passed, failed, or were skipped.
- Include known limitations such as unavailable services, database connectivity, missing credentials, pre-existing warnings, or generated files that were inspected but not applied.
