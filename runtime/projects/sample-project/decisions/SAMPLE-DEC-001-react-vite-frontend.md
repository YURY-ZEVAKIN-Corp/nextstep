# SAMPLE-DEC-001: React + Vite for Frontend

## Metadata

- ID: `SAMPLE-DEC-001`
- Decision Type: `Architecture Decision Record (ADR)`
- Status: `Accepted`
- Owner: `Solution Architect`
- Date: `2026-06-01`
- Project Key: `SAMPLE`

## Context

TaskFlow needs a modern frontend framework for its single-page application. The team has experience with React, and the ecosystem is mature. The choice of build tool (Vite vs Create React App vs Next.js) also needs resolution.

## Decision

Use **React 19 with Vite** as the frontend framework and build tool.

Rationale:
- React has the largest ecosystem and talent pool of any frontend framework
- Vite provides sub-second HMR (Hot Module Replacement), significantly improving developer experience over CRA
- Vite produces optimised production builds via Rollup
- Next.js is overkill for this SPA — no SSR/SSG needed for MVP
- Vite has first-class TypeScript and JSX support out of the box

## Consequences

- Positive: Fast development iteration, broad ecosystem, easy CI/CD integration
- Positive: Vite's native ESM support means faster cold starts
- Negative: Team must learn Vite-specific configuration (plugins, env vars)
- Negative: No SSR — page load SEO relies on client-side rendering (acceptable for MVP)
- Trade-off: Chose Vite over Next.js to avoid SSR complexity; can migrate later if SEO becomes critical

## Alternatives

- Alternative 1: Next.js — full SSR/SSG, but adds routing and data-fetching complexity not needed for MVP
- Alternative 2: Create React App — officially deprecated, slower HMR, no longer recommended
- Alternative 3: SvelteKit — smaller bundle, but smaller ecosystem and team lacks Svelte experience

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
- Related technology stack entries: Frontend → React + Vite
