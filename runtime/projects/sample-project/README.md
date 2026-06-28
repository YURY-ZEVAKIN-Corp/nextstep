# TaskFlow — Sample Project

- Project Key: `SAMPLE`
- Status: `Active`
- Owner: `Product Manager`
- Stack: React + Vite / Node.js + Express / PostgreSQL

A collaborative task management application used as an end-to-end demonstration of the NextStep governance framework.

## Stack Decisions

| Area | Choice | ADR |
|------|--------|-----|
| Frontend | React + Vite | SAMPLE-DEC-001 |
| Backend | Node.js + Express | SAMPLE-DEC-002 |
| Database | PostgreSQL 16 | SAMPLE-DEC-003 |
| Auth | JWT + bcrypt | SAMPLE-DEC-004 |

## Artifact Map

| Artifact | Location | Status |
|----------|----------|--------|
| Project Charter | `project-charter.md` | Active |
| Technology Stack | `technology-stack.md` | Active |
| Backlog | `backlog.md` | Active |
| Roadmap | `roadmap.md` | Active |
| Sprint Plan | `sprints.md` | Active |
| Decision Register | `decision-register.md` | Active |
| Traceability Matrix | `traceability-matrix.md` | Active |
| Requirement (Auth) | `requirements/SAMPLE-REQ-001-user-authentication.md` | Ready |
| Solution (Auth) | `solutions/SAMPLE-SOL-001-auth-solution.md` | Ready |
| Implementation (Auth) | `implementation/SAMPLE-IMP-001-auth-implementation.md` | In Progress |
| Test Plan (Auth) | `testing/SAMPLE-TST-001-auth-testing.md` | Draft |
| Release (Auth/MVP) | `releases/SAMPLE-REL-001-mvp-release.md` | Draft |
| ADR: React + Vite | `decisions/SAMPLE-DEC-001-react-vite-frontend.md` | Accepted |
| ADR: Express | `decisions/SAMPLE-DEC-002-express-backend.md` | Accepted |
| ADR: PostgreSQL | `decisions/SAMPLE-DEC-003-postgresql-database.md` | Accepted |
| ADR: JWT Auth | `decisions/SAMPLE-DEC-004-jwt-authentication-strategy.md` | Accepted |

## Delivery Flow

`backlog.md → requirements/ → solutions/ → decisions/ → implementation/ → sprints.md → testing/ → releases/`
