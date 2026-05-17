# CQM Tech Stack Options for Team Discussion

## Context

This document compares feasible CQM stack options against current requirements, especially:

- SaaS delivery (`CQM-REQ-020`)
- Multi-tenant architecture (`CQM-REQ-021`)
- No cross-tenant data disclosure (`CQM-REQ-024`)
- API for authenticated users only (`CQM-REQ-023`)
- Static hosting for web application (`CQM-REQ-022`)
- Realtime queue state and workplace invitation (`CQM-REQ-019`)

## Evaluation Criteria

- Requirement fit
- Long-term scalability
- Tenant isolation confidence
- Delivery speed
- Operating cost predictability
- Vendor lock-in risk
- Team skill alignment
- Testing consistency and automation coverage

## Option A: React/Vite + Node/Fastify + PostgreSQL + WebSockets

### Stack

- Frontend: `React + Vite + TypeScript`, static CDN hosting
- Backend: `Node.js + Fastify` modular monolith
- Realtime: `WebSocket` or `SSE`
- DB: `PostgreSQL` (shared DB with strict `tenant_id` model)
- Auth: email/password + Google OAuth (Auth.js or custom)
- Cache/rate limit: `Redis` (optional phase 1, likely phase 2)

### Pros

- Strong fit with static hosting requirement.
- Good cost-efficiency for startup and growth.
- Full control over multitenancy and anti-leak safeguards.
- Large talent pool and ecosystem.

### Cons

- More custom backend/auth/security implementation than Firebase-first.
- Requires disciplined architecture for tenant guards and SoD rules.

### Requirement Fit

- `REQ-022`: strong
- `REQ-023`: strong
- `REQ-024`: strong
- `REQ-020/021`: strong

### Cost Profile

- Low to medium, predictable with proper observability and autoscaling strategy.

### Testing Stack (Consistent)

- Unit: `Vitest` or `Jest`
- API integration: `Supertest` + test Postgres container
- E2E UI: `Playwright`
- Load/perf: `k6`
- Contract/API schema: `OpenAPI` validation in CI
- Tenant isolation tests: automated read/write/search/export cross-tenant negative tests in CI

## Option B: Blazor WebAssembly + ASP.NET Core API + SignalR + PostgreSQL

### Stack

- Frontend: `Blazor WebAssembly` static-hosted
- Backend: `ASP.NET Core API`
- Realtime: `SignalR`
- DB: `PostgreSQL`
- Auth: ASP.NET Identity/OIDC + Google

### Pros

- Single language stack (C#) for UI and backend.
- Enterprise-grade framework and tooling.
- Strong realtime with SignalR.
- Good long-term maintainability for .NET teams.

### Cons

- Usually higher infra footprint than lightweight Node stack.
- Frontend flexibility/velocity can be lower than React in some teams.

### Requirement Fit

- `REQ-022`: strong (WASM only)
- `REQ-023`: strong
- `REQ-024`: strong
- `REQ-020/021`: strong

### Cost Profile

- Medium, predictable.

### Testing Stack (Consistent)

- Unit: `xUnit` or `NUnit`
- API integration: `ASP.NET WebApplicationFactory` + test Postgres container
- E2E UI: `Playwright` (or Selenium if needed)
- Load/perf: `k6`
- Contract/API schema: OpenAPI compatibility checks in CI
- Tenant isolation tests: automated cross-tenant negative tests in CI

## Option C: Blazor Server + ASP.NET Core (Unified UI + BE)

### Stack

- UI + BE in one ASP.NET Core/Blazor Server runtime
- Realtime is intrinsic to Blazor Server connection model
- DB: `PostgreSQL`

### Pros

- Fastest path for .NET teams needing one deployment unit.
- Minimal API/UI integration complexity.

### Cons

- Conflicts with `REQ-022` static-hosting requirement.
- Requires always-on server connections per session.
- Horizontal scale can get expensive as concurrent sessions grow.

### Requirement Fit

- `REQ-022`: weak (mismatch)
- `REQ-023`: strong
- `REQ-024`: strong
- `REQ-020/021`: medium-strong

### Cost Profile

- Medium to high as concurrency increases.

### Testing Stack (Consistent)

- Unit: `xUnit` or `NUnit`
- Component/UI integration: `bUnit` for Blazor components
- End-to-end and session behavior: `Playwright`
- Load/perf for concurrent sessions: `k6`
- Tenant isolation/security regression tests in CI

## Option D: Firebase-First (Auth + Firestore + Hosting + Realtime)

### Stack

- Frontend static hosting on Firebase Hosting
- Firebase Auth (email/password + Google)
- Firestore for primary operational data
- Realtime via Firestore listeners

### Pros

- Very fast initial implementation.
- Minimal backend ops in phase 1.

### Cons

- Harder to model strict SoD and complex RBAC safely at scale.
- Higher vendor lock-in.
- Read-driven pricing can become less predictable with queue polling/listeners.
- Tenant isolation depends heavily on security rules discipline.

### Requirement Fit

- `REQ-022`: strong
- `REQ-023`: medium-strong
- `REQ-024`: medium (high implementation discipline required)
- `REQ-020/021`: medium-strong

### Cost Profile

- Low early, variable at scale.

### Testing Stack (Consistent)

- Unit: `Vitest/Jest` for frontend logic, `firebase-functions-test` where applicable
- Security rules tests: Firestore rules unit/integration suite (mandatory)
- E2E UI: `Playwright`
- Load/perf: `k6` with focus on listener/polling cost behavior
- Tenant isolation tests: rule-level and API-level leakage tests

## Option E: Hybrid (Firebase UI/Auth + Custom Backend + PostgreSQL)

### Stack

- Static frontend (Firebase Hosting or Cloudflare Pages)
- Firebase Auth only
- Custom backend for domain logic, RBAC, SoD, tenancy guards
- PostgreSQL as source of truth
- Realtime via backend WS/SSE

### Pros

- Faster auth onboarding, while preserving backend control for governance-critical logic.
- Better long-term control than Firebase-first.

### Cons

- Two platform models to manage.
- Added integration complexity.

### Requirement Fit

- `REQ-022`: strong
- `REQ-023`: strong
- `REQ-024`: strong
- `REQ-020/021`: strong

### Cost Profile

- Medium; still fairly predictable.

### Testing Stack (Consistent)

- Unit: split by frontend/backend tech choice
- API integration: backend framework-native integration tests + Postgres container
- E2E UI: `Playwright`
- Load/perf: `k6`
- Tenant isolation tests: backend mandatory; Firebase config/rules checks if Firebase Auth/hosting is used

## Cloud Provider Options

### Provider A: AWS

- Best for long-term custom SaaS with PostgreSQL and managed scaling.
- Typical mapping:
- Static frontend: `S3 + CloudFront`
- Backend: `ECS/Fargate` or `EKS` or `App Runner`
- DB: `RDS PostgreSQL`
- Cache: `ElastiCache Redis`
- Observability: `CloudWatch`, `X-Ray`, `OpenSearch` (optional)
- Pros: ecosystem depth, enterprise maturity, flexible tenancy patterns.
- Cons: operational complexity can be higher than startup PaaS.

### Provider B: Azure

- Strong fit for .NET/Blazor-centric teams.
- Typical mapping:
- Static frontend: `Azure Static Web Apps` or Blob + CDN
- Backend: `App Service` or `Container Apps`
- DB: `Azure Database for PostgreSQL`
- Cache: `Azure Cache for Redis`
- Observability: `Application Insights`, `Log Analytics`
- Pros: strong .NET integration, enterprise governance tooling.
- Cons: sometimes higher cost for equivalent small workloads.

### Provider C: Google Cloud (GCP)

- Strong fit for Firebase-heavy or hybrid Firebase architecture.
- Typical mapping:
- Static frontend: `Firebase Hosting` or Cloud Storage + CDN
- Backend: `Cloud Run`
- DB: `Cloud SQL PostgreSQL`
- Cache: `Memorystore Redis`
- Observability: `Cloud Monitoring/Logging/Trace`
- Pros: best integration if Firebase services are used.
- Cons: mixed model complexity if moving off Firebase data plane later.

### Provider D: Cloudflare + Secondary Compute Provider

- Cost-efficient edge/static delivery.
- Typical mapping:
- Static frontend: `Cloudflare Pages`
- Backend: `Railway/Render/Fly` (or Cloudflare Workers where suitable)
- DB: `Supabase Postgres` or managed Postgres elsewhere
- Pros: low-cost global delivery, simple static hosting.
- Cons: multi-provider operations and IAM boundaries to manage.

### Provider E: Startup PaaS (Render/Railway/Fly)

- Fast MVP delivery with low ops overhead.
- Typical mapping:
- Static frontend: platform static hosting
- Backend: single container/service deployment
- DB: managed Postgres add-on
- Pros: fastest setup, low initial cost.
- Cons: less enterprise depth, migration likely at larger scale.

## Cloud Recommendation by Option

- Option A (Node/Postgres): `AWS` or `Cloudflare + Railway/Render` for MVP, migrate to AWS later.
- Option B (Blazor WASM/.NET): `Azure` first, `AWS` as secondary.
- Option C (Blazor Server): `Azure` preferred.
- Option D (Firebase-first): `GCP` mandatory/primary.
- Option E (Hybrid): `GCP` (if Firebase Hosting/Auth retained) or `Cloudflare + AWS` split.

## Testing Strategy Baseline (Required for Any Option)

1. `Test Pyramid`
- Unit tests for domain logic and policy checks.
- API integration tests for auth, tenancy, and queue workflows.
- E2E tests for customer invitation and worker operations.

2. `Mandatory Security/Tenancy Suites`
- Authenticated-only API enforcement checks.
- Cross-tenant leakage negative tests.
- Conflict-of-interest/Segregation-of-duties rule tests.

3. `Performance and Reliability`
- Load tests for queue throughput (`60 customers/hour/tenant` baseline).
- Realtime latency tests for invitation updates.
- Soak tests for multi-tenant concurrency.

4. `Release Gates`
- No release if tenant-isolation suite fails.
- No release if P95 latency regression breaches threshold.
- No release if critical E2E flow fails.

5. `Test Environments`
- Ephemeral PR environments where possible.
- Dedicated staging with representative tenant fixtures.
- Production smoke checks after deployment.

## Tech Radar Position (Recommended)

- `PostgreSQL`: `Adopt`
- `Static frontend hosting`: `Adopt`
- `Backend modular monolith (Node or .NET)`: `Adopt`
- `WebSockets/SignalR for realtime`: `Adopt`
- `Redis`: `Trial`
- `Firebase-first data plane`: `Hold` for CQM core domain
- `Project-per-tenant Firebase`: `Assess` for high-compliance tenants only

## Recommendation Paths

### Path 1 (Cost + Control Priority)

Choose `Option A`.

### Path 2 (.NET Team Priority)

Choose `Option B`.

### Path 3 (Fast MVP with Future Hardening)

Choose `Option E`.

## Decision Questions for Team Meeting

1. Is `REQ-022` (static hosting) fixed, or negotiable?
2. Is team stronger in TypeScript or C#?
3. How strict must tenant isolation evidence be for audits in phase 1?
4. Is lowest immediate implementation speed more important than long-term cost predictability?
5. Do we accept vendor lock-in risk for faster MVP?
6. Which cloud provider aligns best with team skill and compliance expectations?
7. What test gate policy is mandatory before production rollout?

## Suggested Final Decision Format

- Selected option:
- Why selected:
- Why alternatives rejected:
- First 90-day implementation scope:
- Exit criteria to scale to next phase:

## Next Artifacts to Create After Decision

- `CQM-DEC-001`: Stack decision
- `CQM-DEC-002`: Tenant isolation model
- `CQM-DEC-003`: Realtime transport decision
- `CQM-DEC-004`: Auth and token/session model
- `CQM-DEC-005`: Static hosting + runtime config strategy
- `CQM-DEC-006`: Cloud provider selection
- `CQM-DEC-007`: Testing and release gate policy
