# CQM-SOL-001: Core Platform Architecture

## Metadata

- ID: `CQM-SOL-001`
- Status: `Draft`
- Owner: `Engineering Lead`
- Created: `2026-05-17`
- Updated: `2026-05-17`
- Project Key: `CQM`
- Related Requirements: `CQM-REQ-005, CQM-REQ-006, CQM-REQ-007, CQM-REQ-008, CQM-REQ-009, CQM-REQ-010, CQM-REQ-011, CQM-REQ-012, CQM-REQ-013, CQM-REQ-014, CQM-REQ-015, CQM-REQ-016, CQM-REQ-017, CQM-REQ-018, CQM-REQ-019, CQM-REQ-020, CQM-REQ-021, CQM-REQ-022, CQM-REQ-023, CQM-REQ-024, CQM-REQ-025, CQM-REQ-026`

## Summary

Build CQM as a SaaS, multi-tenant, web-first queue platform with static-hosted web applications, authenticated-only APIs, strict tenant data isolation, RBAC, conflict-of-interest controls, worker workplace assignment, and realtime queue/invitation updates using SSE-first for customer TV channel with polling fallback.

## Goals

- Deliver reliable queue lifecycle, ticketing, and processing operations.
- Provide customer-facing queue visibility and workplace invitation web page.
- Enforce security, role scope, and conflict-of-interest controls.
- Support SaaS onboarding and strict tenant isolation.
- Maintain auditability and performance targets under concurrent usage.

## Proposed Design

### 1. System Architecture

- `Frontend apps`
- Staff portal for Worker and Queue Manager operations.
- Customer web page for queue state and invitation view.
- Both apps compiled and deployed as static assets (HTML/CSS/JS) on CDN/static hosting.

- `Backend services`
- `Auth Service`: email/password login and Google signup callback.
- `Access Service`: RBAC + conflict-of-interest policy checks.
- `Tenant Service`: tenant onboarding, tenant config, tenant lifecycle metadata.
- `Queue Service`: queue lifecycle, ownership, tickets, and operations.
- `Workplace Service`: workplace catalog and worker-workplace assignment.
- `Notification/Realtime Service`: SSE-first updates for customer TV view, WebSocket/SSE for staff UIs, polling fallback support.
- `Audit Service`: immutable audit event capture and tenant-scoped query endpoints.

- `Data layer`
- Relational database (core transactional state).
- Append-only audit log table/stream.
- Cache for hot queue state reads (optional phase 2).

### 1.1 Static Web Hosting Model

- Build frontend with static output pipeline.
- Host bundles on CDN/object storage based static hosting.
- Use runtime-injected public config (`api_base_url`, `realtime_url`, `tenant_resolver_mode`) to avoid tenant-specific rebuilds.
- Keep all secrets and privileged logic server-side only.

### 1.2 TV Browser Realtime Strategy

- Customer view transport order:
- primary: `SSE`
- fallback: `polling` (default 5 seconds, configurable)
- TV client behavior:
- auto-reconnect with capped backoff
- stale-data indicator when update freshness threshold is exceeded
- periodic heartbeat monitoring and recovery refresh path
- Support matrix:
- define and validate supported TV browser platforms/versions in testing artifacts.

### 2. Multi-Tenant Model

- `Tenant isolation key`
- Every domain record includes `tenant_id`.
- Every API request resolves exactly one tenant context before business logic executes.

- `Isolation enforcement`
- API layer: tenant-scoped query guards and authorization checks.
- Background jobs: tenant context required for each job execution.
- Realtime channels: subscription namespace per tenant.
- Audit: all events include `tenant_id`.
- Export/report pipelines: tenant-scoped filters mandatory and tested.

- `Phase 1 tenancy strategy`
- Recommended: shared database + tenant-scoped schema model in application layer with strict guards.
- Alternative path: migrate hot/regulated tenants to separate schema or DB when needed.

- `Anti-leak controls`
- fail-closed tenant guard middleware at API edge.
- repository-level query builders require tenant predicate by design.
- security tests for cross-tenant read/write/search/export attempts.

### 3. Core Data Model

- `tenants(id, code, name, status, created_at)`
- `tenant_settings(tenant_id, key, value_json, updated_at)`
- `users(id, tenant_id, email, password_hash, auth_provider, status, created_at)`
- `roles(id, name)`
- `user_roles(user_id, role_id)`
- `queues(id, tenant_id, location_id, name, status, manager_user_id, created_at)`
- `workplaces(id, tenant_id, location_id, workplace_number, status)`
- `worker_assignments(id, tenant_id, user_id, workplace_id, shift_id, active_from, active_to)`
- `tickets(id, tenant_id, queue_id, ticket_number, customer_ref, status, issued_at)`
- `queue_events(id, tenant_id, queue_id, ticket_id, event_type, actor_user_id, workplace_id, created_at)`
- `invitations(id, tenant_id, ticket_id, worker_user_id, workplace_number, issued_at, expires_at, status)`
- `audit_events(id, tenant_id, event_type, actor_user_id, target_type, target_id, payload_json, created_at)`
- `sod_policy_rules(id, tenant_id, rule_name, rule_type, config_json, active)`

### 4. Key Workflows

- `Tenant onboarding`: create tenant, initial Queue Manager user, baseline settings, and default policies.
- `Queue setup`: Queue Manager creates queue, assigns manager, configures active status.
- `Worker setup`: workplaces are created per location; worker assigned to workplace number.
- `Customer enrollment`: customer selects queue, receives unique ticket.
- `Queue processing`: worker calls next ticket; system creates invitation to worker workplace number.
- `Customer view`: web page updates queue state and invitation in near real time.
- `Customer TV channel`: use SSE stream first; auto-fallback to polling on repeated SSE failures.
- `Security flow`: all privileged actions pass RBAC + conflict-of-interest checks.
- `Audit flow`: all critical operations write immutable, tenant-scoped audit events.

### 5. API Surface (Initial)

- `POST /auth/login`
- `POST /auth/google/signup`
- `POST /tenants`
- `PATCH /tenants/{id}`
- `POST /queues`
- `PATCH /queues/{id}`
- `POST /queues/{id}/tickets`
- `POST /queues/{id}/call-next`
- `POST /queues/{id}/tickets/{ticketId}/complete`
- `POST /workplaces`
- `POST /workers/{userId}/assign-workplace`
- `GET /customer/tickets/{ticketId}/state`
- `GET /realtime/stream` (SSE primary for customer TV view)

### 5.1 API Security Model

- Default policy: all API endpoints require authentication.
- Public exceptions (if any) must be explicitly allowlisted.
- Request pipeline order:
- authenticate token/session
- resolve tenant context
- enforce RBAC and conflict-of-interest rules
- execute tenant-scoped business operation
- log audit/security event

### 6. Conflict-of-Interest Enforcement

- Implement policy rules in `Access Service`.
- Example rules:
- user cannot approve own critical queue configuration change.
- dual-control required for selected high-risk actions.
- policy violations blocked and tenant-audit logged.

### 7. SaaS Operations Design

- `Tenant onboarding automation`: API-driven creation, default queue/workplace config templates.
- `Centralized release management`: staged rollout by environment and tenant cohort.
- `Rollback model`: versioned deployments with tenant impact checks.
- `Support model`: tenant-scoped diagnostics, metrics, and audit access.
- `Static frontend delivery`: CDN cache versioning with atomic release/rollback by asset manifest.
- `TV rollout policy`: validate SSE/polling behavior against target TV browser matrix before production promotion.

### 8. Non-Functional Design Alignment

- Response-time targets for ticket/operation/auth endpoints at P95 within requirement thresholds.
- Tenant scoping checks integrated into request pipeline with bounded latency overhead.
- Optimistic locking/version fields on queue and ticket state to prevent race conditions.
- Idempotency keys for critical write endpoints.
- Centralized metrics and alerts for queue lag, invitation latency, auth failures, and tenant-boundary violations.
- API unauthorized and forbidden rates monitored by endpoint and tenant.
- Explicit leakage canary tests in CI for tenant isolation guarantees.
- TV realtime fallback success rate and stale-display duration are monitored as SLO metrics.

## Components Affected

- `staff-portal` (new)
- `customer-web-page` (new)
- `auth-service` (new)
- `access-service` (new)
- `tenant-service` (new)
- `queue-service` (new)
- `workplace-service` (new)
- `audit-service` (new)
- `database-schema` (new)
- `static-hosting-config` (new)
- `tv-compatibility-test-suite` (new)

## Alternatives Considered

- `Single-tenant deployment`: simplest isolation but poor SaaS scalability.
- `Separate database per tenant from day 1`: strongest isolation, highest operational overhead.
- `Shared DB with strong tenant guards` (selected for phase 1): balanced speed and scalability, with migration path to stronger isolation tiers.

## Risks

- Invitation latency may exceed target under peak load.
- Incorrect queue/event ordering can show wrong invitation state.
- Policy-rule complexity can block valid operations if misconfigured.
- Tenant context propagation bugs can create isolation risk.
- Misconfigured public endpoint allowlist can expose API surface.
- Runtime config drift between static frontend and backend endpoints can break tenant routing.
- TV browser engine limitations can degrade realtime behavior without fallback and soak testing.

## Rollout Strategy

1. Phase 1: tenant service, auth, RBAC, queue lifecycle, ticketing, basic worker operations.
2. Phase 2: workplace assignment, customer invitation page, static hosting rollout, and SSE-first TV channel implementation.
3. Phase 3: authenticated-only API hardening, explicit public endpoint review, and TV browser compatibility testing.
4. Phase 4: conflict-of-interest controls, tenant anti-leak verification, and SLA tuning.
5. Phase 5: SaaS onboarding automation and tenant operations hardening.
6. Pilot with selected tenant cohort using feature flags and TV soak tests.
7. Expand tenant-by-tenant after KPI, security, audit, and TV compatibility pass.

## Monitoring and Observability

- Metrics:
- ticket issuance latency
- call-next latency
- invitation delivery latency
- queue depth per queue
- auth success/failure rate
- conflict-of-interest block count
- tenant onboarding lead time
- tenant-boundary violation block count
- unauthorized API request rate
- cross-tenant leakage test pass rate
- static asset cache hit ratio
- TV channel reconnect rate
- TV stale-display duration percentile

- Logs:
- structured request/response logs for critical endpoints
- security/auth events
- tenant resolution events
- audit event write confirmations

- Alerts:
- P95 latency breach
- realtime delivery lag
- duplicate ticket detection anomaly
- failed audit writes
- tenant-boundary violation detection
- unexpected public endpoint access pattern
- prolonged TV display staleness or fallback lock condition

## Technology Radar Check

Complete this section when the solution introduces, changes, or depends on major technologies.

- Radar source: `TBD`
- Technologies checked: `Web framework, static hosting/CDN, realtime transport (SSE-first + polling fallback), relational DB, auth stack, multitenancy strategy`
- Radar status summary: `TBD`
- Decision impact: `Requires follow-up ADRs for backend framework, static hosting strategy, DB, realtime protocol, TV compatibility strategy, and tenancy model`
- Follow-up needed: `Create CQM-DEC-001..008`

## Links

- Requirement: `CQM-REQ-005..026`
- Implementation plan: `CQM-IMP-001`
- Test plan: `TBD`
- Decision records: `TBD`
