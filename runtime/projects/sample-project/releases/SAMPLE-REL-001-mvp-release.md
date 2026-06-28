# SAMPLE-REL-001: MVP Release

## Metadata

- Status: `Draft`
- Owner: `DevOps Engineer`
- Date: `2026-06-12`
- Project Key: `SAMPLE`
- Change Set: `SAMPLE-REQ-001` (User Authentication)

## Deployment Plan

1. Merge `feature/auth` branch into `main` via PR with required approvals (Tech Lead + QA)
2. CI pipeline runs lint → unit tests → integration tests → build → push Docker image
3. CD pipeline deploys to staging environment
4. Run E2E tests (Playwright) against staging
5. Manual smoke test: create user, log in, verify protected route access
6. Tag release: `v0.1.0`
7. Deploy to production

## Rollback Steps

1. `git revert` the merge commit
2. Docker rollback to previous image tag
3. Knex rollback the `users` table migration: `knex migrate:down`
4. Verify staging first, then production

## Pre-Deployment Checks

- [x] All integration tests pass (CI)
- [ ] All E2E tests pass (staging)
- [ ] Security review completed (Tech Lead)
- [ ] JWT secret configured in production environment
- [ ] PostgreSQL migration verified (up and down)
- [ ] CORS configured for production frontend URL
- [ ] Rate limiting enabled on auth endpoints

## Post-Deployment Checks

- [ ] Smoke test: signup, login, protected route
- [ ] Monitor auth error rate (target: <1% 5xx /auth/*)
- [ ] Monitor signup-to-login conversion
- [ ] Confirm rollback procedure works by testing down-migration

## Verification Evidence

- CI pipeline report: `pending`
- Playwright E2E report: `pending`
- Security review sign-off: `pending`
- Tech Lead sign-off: `pending`
- QA sign-off: `pending`

## Outcome

- Deployment result: `Pending`
- Follow-up actions: Monitor auth metrics for first 48 hours post-release
