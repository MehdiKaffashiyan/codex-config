---
name: ddd-rich-entity
description: Apply rich domain entity modeling rules for repositories that use aggregate roots, child entities, value objects, and integrity checks.
---

# DDD Rich Entity

Use this skill when creating or changing domain entities in a repository that follows rich DDD entity patterns.

## Modeling Rules

- Treat each domain entity class as exactly one of:
  - aggregate root
  - child entity
  - value object
- Do not place anemic persistence models in the domain entity folder.
- Keep child-entity construction controlled by the owning aggregate root. Repositories and controllers should not construct child entities directly.
- Do not redeclare inherited identity properties on derived child entities.
- Keep value objects identity-free unless repository rules define a different pattern.
- Do not put persistence attributes in rich domain entities when the repository uses Fluent API mapping.

## Integrity And Persistence

- Follow the repository's base classes, cloning pattern, integrity checksum pattern, and identity methods exactly.
- Configure required fields, maximum lengths, keys, table names, indexes, concurrency tokens, relationships, and other persistence concerns through the repository's mapping configuration.
- After entity changes, use the repository's migration workflow and inspect generated migration artifacts before delivery.
