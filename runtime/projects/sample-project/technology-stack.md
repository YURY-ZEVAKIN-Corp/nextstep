# Technology Stack

Project Key: `SAMPLE`

Every selected technology in this file must be justified by a decision record.

| Area | Selected Technology | Purpose | Decision Record | Status | Notes |
|---|---|---|---|---|---|
| Frontend | React + Vite | UI framework with fast HMR and optimized builds | SAMPLE-DEC-001 | Accepted | Chosen for ecosystem maturity and team familiarity |
| Backend | Node.js + Express.js | RESTful API server | SAMPLE-DEC-002 | Accepted | Lightweight, widely adopted, same language as frontend |
| Database | PostgreSQL 16 | Primary data store | SAMPLE-DEC-003 | Accepted | Reliable, ACID-compliant, strong JSON support |
| Authentication | JWT (jsonwebtoken + bcrypt) | Stateless auth for API | SAMPLE-DEC-004 | Accepted | Simple, no session store needed, sufficient for MVP |
| Infrastructure | Docker + Docker Compose | Local dev and reproducible environments | SAMPLE-DEC-001 | Accepted | Consistent across team machines |
| CI/CD | GitHub Actions | Automated build, test, and deploy | SAMPLE-DEC-001 | Accepted | Native to GitHub, no extra tooling |
| Testing | Vitest + Supertest | Unit/integration for frontend and API | Accepted | Fast, compatible with Vite ecosystem |
| Observability | Morgan + console logger | Request logging (MVP) | Draft | Minimal — revisit post-MVP |
| Security | Helmet + CORS + bcrypt | HTTP headers, cross-origin, password hashing | SAMPLE-DEC-004 | Accepted | Standard Express security middleware |
| Integrations | None (MVP) | — | — | Draft | Post-MVP: Slack, GitHub webhooks |

## Technology Radar Check

For each major technology choice, record:

- Radar source: ThoughtWorks Technology Radar — Vol 30
- Radar category: Platforms & Tools / Languages & Frameworks
- Radar status: `Adopt | Trial | Assess | Hold | Not Listed`
- Assessment date: `2026-06-01`
- Assessment notes: React, Express, Postgres, Docker, and GitHub Actions are all in the `Adopt` ring. JWT is `Trial` — sufficient for MVP but consider OAuth for production.

## Change Rules

- Add a new decision record before changing a major technology.
- Update this file after the decision is accepted.
- Update the project decision register after the decision is accepted.
- Ensure solutions and implementation plans use only approved technologies.
