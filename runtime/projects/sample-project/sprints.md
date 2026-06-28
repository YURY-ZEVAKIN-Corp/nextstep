# Sprint Plan

Use this file to plan and track sprint execution for this project.

## Sprint Cadence

- Length: `2 weeks`
- Planning Day: `Monday`
- Review and Retro Day: `Friday`

## Sprint Index

| Sprint ID | Window | Goal | Status | Notes |
|---|---|---|---|---|
| SPRINT-2026-06-A | 2026-06-01 to 2026-06-12 | Deliver user authentication (SAMPLE-REQ-001) | Active | Foundation sprint — auth unblocks all other work |
| SPRINT-2026-06-B | 2026-06-15 to 2026-06-26 | Task CRUD API and database schema | Draft | Depends on auth being complete |
| SPRINT-2026-07-A | 2026-06-29 to 2026-07-10 | Real-time task board (WebSocket) | Draft | Depends on task CRUD |
| SPRINT-2026-07-B | 2026-07-13 to 2026-07-24 | Profile management and UI polish | Draft | Lower priority feature work |

## Sprint Details

### SPRINT-2026-06-A

- Status: `Active`
- Window: `2026-06-01 to 2026-06-12`
- Sprint Goal: Deliver user authentication with signup, login, and JWT session management.
- Capacity Notes: 2 backend devs, 1 frontend dev, 1 QA (part-time). Backend-heavy sprint.

#### Committed Items

| Work Item | Type | Owner | Planned Outcome | Status |
|---|---|---|---|---|
| SAMPLE-REQ-001 | Requirement | Product Manager | Approved and ready for implementation | Ready |
| TASK-001 | Implementation | Backend Dev | Users table migration | In Progress |
| TASK-002 | Implementation | Backend Dev | Auth service (signup, login, refresh) | Pending |
| TASK-003 | Implementation | Backend Dev | Auth routes with zod validation | Pending |
| TASK-004 | Implementation | Backend Dev | Authenticate middleware | Pending |
| TASK-005 | Implementation | Frontend Dev | AuthContext (React) | Pending |
| TASK-006 | Implementation | Frontend Dev | LoginPage and SignupPage | Pending |
| TASK-007 | Testing | QA Engineer | Integration tests (Supertest) | Pending |
| TASK-008 | Testing | QA Engineer | E2E tests (Playwright) | Pending |
| TASK-009 | Review | Tech Lead | Security review | Pending |

#### In-Sprint Scope Changes

| Date | Change | Reason | Approved By |
|---|---|---|---|
| 2026-06-03 | Added TASK-009 (security review) | Auth risk identified during refinement | Tech Lead |

#### Outcome

- Goal achieved: `Pending`
- Completed items:
- Carryover items:
- Key learnings:
