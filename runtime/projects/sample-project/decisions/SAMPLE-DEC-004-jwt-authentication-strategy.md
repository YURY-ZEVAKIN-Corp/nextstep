# SAMPLE-DEC-004: JWT Authentication Strategy

## Metadata

- ID: `SAMPLE-DEC-004`
- Decision Type: `Architecture Decision Record (ADR)`
- Status: `Accepted`
- Owner: `Solution Architect`
- Date: `2026-06-01`
- Project Key: `SAMPLE`

## Context

TaskFlow requires stateless authentication for its RESTful API. Session-based auth would require a shared session store (Redis) and sticky sessions, adding infrastructure complexity. The auth mechanism must be simple to implement, secure, and easy to test.

## Decision

Use **JWT (JSON Web Tokens)** with **HS256** signing for stateless authentication, with **bcrypt** (cost factor 12) for password hashing.

Rationale:
- JWT is stateless — no server-side session storage needed, simplifying horizontal scaling
- HS256 (HMAC-SHA256) is sufficient for a single-service MVP; can migrate to RS256 if microservices emerge
- Bcrypt with cost 12 provides strong password hashing with reasonable performance (~200ms per hash)
- Token expiry set to 24 hours with a simple renewal endpoint
- Implementation using `jsonwebtoken` and `bcrypt` npm packages — both mature and widely audited

## Consequences

- Positive: No Redis or session store needed for MVP
- Positive: Token-based auth is easy to test with HTTP headers
- Positive: Same auth mechanism works for both browser and mobile (future PWA)
- Negative: JWT cannot be revoked server-side without a blocklist (add blocklist table if needed)
- Negative: HS256 requires careful secret management — secret must not be committed to version control
- Negative: Token size (~1KB) adds slight overhead to every request

## Alternatives

- Alternative 1: Session-based auth with Redis — allows server-side revocation, but adds infrastructure dependency and operational complexity
- Alternative 2: OAuth 2.0 / OIDC — too complex for MVP; revisit when third-party SSO is needed
- Alternative 3: PASETO — more secure token format, but smaller community and fewer libraries compared to JWT

## Decision Checklist Review

Checklist file: `framework/templates/decision-checklist.md`

- Review Date: `2026-06-01`
- Reviewer: `Tech Lead`
- Result: `Pass`
- Triage: `Critical`

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
- Related technology stack entries: Authentication → JWT (jsonwebtoken + bcrypt)
