# SAMPLE-DEC-003: PostgreSQL for Primary Data Store

## Metadata

- ID: `SAMPLE-DEC-003`
- Decision Type: `Architecture Decision Record (ADR)`
- Status: `Accepted`
- Owner: `Solution Architect`
- Date: `2026-06-01`
- Project Key: `SAMPLE`

## Context

TaskFlow needs a relational database to store users, tasks, and board state. The data model has clear relationships (users own tasks, tasks belong to boards) that map naturally to SQL. The database must support JSON fields for extensibility and be producible in Docker for local development.

## Decision

Use **PostgreSQL 16** as the primary data store with **Knex.js** as the query builder and migration tool.

Rationale:
- PostgreSQL is the most advanced open-source relational database with excellent JSONB support
- Knex provides migration-based schema management, essential for team collaboration
- Knex allows raw SQL when needed but provides a query builder for common operations
- PostgreSQL's JSONB columns allow flexible schema extensions without migrations
- Excellent Docker image support for local development and CI

## Consequences

- Positive: ACID compliance guarantees data integrity for task management
- Positive: JSONB allows storing flexible metadata per task without schema changes
- Positive: Knex migrations provide version-controlled schema history
- Negative: Requires team to know SQL and relational design principles
- Negative: Knex adds an abstraction layer — raw SQL may be faster for complex queries
- Trade-off: Chose Knex over Prisma to keep control over SQL; Prisma's abstraction hides performance details

## Alternatives

- Alternative 1: MongoDB — schema-less, simpler initial model, but eventual consistency and no joins make reporting harder
- Alternative 2: SQLite — zero-config, but not suitable for multi-user production workloads
- Alternative 3: Prisma — modern ORM with auto-generated types, but adds abstraction overhead and debugging complexity

## Decision Checklist Review

Checklist file: `framework/templates/decision-checklist.md`

- Review Date: `2026-06-01`
- Reviewer: `Tech Lead`
- Result: `Pass`
- Triage: `Medium`

### Checklist Summary

- [x] Decision conflict check completed
- [x] Decision triage assigned
- [x] Context is clear
- [x] Alternatives were considered
- [x] Consequences are understood
- [x] Links to impacted artifacts are recorded

## Links

- Related requirements: `SAMPLE-REQ-001`
- Related solutions: `SAMPLE-SOL-001`
- Related technology stack entries: Database → PostgreSQL 16
