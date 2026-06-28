# SAMPLE-TST-001: Authentication Testing

## Metadata

- Status: `Draft`
- Owner: `QA Engineer`
- Date: `2026-06-03`
- Project Key: `SAMPLE`

## Scope

Verify the authentication requirement (SAMPLE-REQ-001) meets all acceptance criteria, covering backend API, frontend UI, and security constraints.

## Test Strategy

| Layer | Tool | Scope | Environment |
|-------|------|-------|-------------|
| Unit | Vitest | AuthService logic (password hashing, token generation) | CI |
| Integration | Supertest + Vitest | Auth API endpoints against test DB | CI |
| E2E | Playwright | Full browser flow (signup → login → protected page) | CI + Staging |
| Security | Manual | JWT secret handling, error message leakage | Staging |

## Backend Integration Tests

| Test ID | Scenario | Expected Result | Status |
|---------|----------|-----------------|--------|
| API-001 | POST /api/auth/signup with valid data | Returns 201 with success message | Draft |
| API-002 | POST /api/auth/signup with duplicate email | Returns 409 Conflict | Draft |
| API-003 | POST /api/auth/signup with weak password | Returns 400 with validation error | Draft |
| API-004 | POST /api/auth/login with valid credentials | Returns 200 with JWT token | Draft |
| API-005 | POST /api/auth/login with wrong password | Returns 401 Unauthorized | Draft |
| API-006 | POST /api/auth/login with unregistered email | Returns 401 Unauthorized | Draft |
| API-007 | GET /api/protected without token | Returns 401 Unauthorized | Draft |
| API-008 | GET /api/protected with expired token | Returns 401 Unauthorized | Draft |
| API-009 | POST /api/auth/refresh with valid token | Returns 200 with new JWT | Draft |
| API-010 | POST /api/auth/refresh with invalid token | Returns 401 Unauthorized | Draft |

## E2E Tests (Playwright)

| Test ID | Scenario | Expected Result | Status |
|---------|----------|-----------------|--------|
| E2E-001 | User navigates to /signup, fills form, submits | Redirected to /login with success toast | Draft |
| E2E-002 | User logs in with valid credentials | Redirected to /dashboard with user name visible | Draft |
| E2E-003 | User logs in with invalid credentials | Error message displayed, no redirect | Draft |
| E2E-004 | Unauthenticated user visits /dashboard | Redirected to /login | Draft |

## Non-Functional Checks

- Token validation response time <50ms (benchmark with k6 or autocannon)
- Password hashing time <300ms (bcrypt cost 12 benchmark)

## Regression Scope

- N/A — first feature in the project. Future releases must re-run all auth tests.

## Defect Tracking

| Defect ID | Description | Severity | Status |
|-----------|-------------|----------|--------|
| — | No defects found in initial test run | — | — |
