# SAMPLE-DEC-002: Express.js for Backend API

## Metadata

- ID: `SAMPLE-DEC-002`
- Decision Type: `Architecture Decision Record (ADR)`
- Status: `Accepted`
- Owner: `Solution Architect`
- Date: `2026-06-01`
- Project Key: `SAMPLE`

## Context

TaskFlow requires a RESTful API server to handle authentication, task CRUD, and WebSocket connections. The team is primarily JavaScript developers, so a Node.js runtime is the natural choice. The framework must be lightweight, well-documented, and easy to extend.

## Decision

Use **Express.js 5** as the backend web framework.

Rationale:
- Express is the most widely adopted Node.js framework with extensive middleware ecosystem
- Express 5 includes async error handling natively, reducing boilerplate
- Lightweight — no opinionated structure, the team controls the architecture
- Easy to integrate with WebSocket libraries (ws or socket.io) later
- Vast middleware available: Helmet, CORS, morgan, rate-limiting, etc.

## Consequences

- Positive: Rapid development, huge community, extensive middleware
- Positive: Same language as frontend — reduces context switching
- Negative: Express has no built-in request validation — must add a library (zod or joi)
- Negative: No built-in ORM — must choose one (Knex or Prisma)
- Negative: Requires manual project structuring (routes, controllers, middleware layers)

## Alternatives

- Alternative 1: Fastify — faster benchmarks, built-in schema validation, but smaller ecosystem and fewer team members know it
- Alternative 2: NestJS — opinionated (Angular-style DI), steep learning curve, over-engineered for MVP
- Alternative 3: Hono — ultra-light, but too new and unproven for a production app

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
- Related technology stack entries: Backend → Node.js + Express.js
