# CQM-IMP-001: Requirement Delivery Plan and Gantt

## Metadata

- ID: `CQM-IMP-001`
- Status: `Draft`
- Priority: `High`
- Owner: `Engineering Lead`
- Project Key: `CQM`
- Created: `2026-05-17`
- Updated: `2026-05-17`

## Requirement Status Snapshot

Status date: `2026-05-17`

| Requirement ID | Title | Status |
|---|---|---|
| CQM-REQ-001 | Customer can get queue number in specific queue | Superseded by CQM-REQ-007 |
| CQM-REQ-002 | System can create many queues | Superseded by CQM-REQ-005 |
| CQM-REQ-003 | Every queue must have a manager user | Superseded by CQM-REQ-006 |
| CQM-REQ-004 | Queue manager dashboard for owned queues | Superseded by CQM-REQ-010 |
| CQM-REQ-005 | Queue setup and lifecycle | Draft |
| CQM-REQ-006 | Queue ownership and accountability | Draft |
| CQM-REQ-007 | Customer enrollment and ticketing | Draft |
| CQM-REQ-008 | Queue processing operations | Draft |
| CQM-REQ-009 | Role-based access control | Draft |
| CQM-REQ-010 | Queue manager dashboard | Draft |
| CQM-REQ-011 | Customer queue visibility | Draft |
| CQM-REQ-012 | Audit and history | Draft |
| CQM-REQ-013 | Reliability and performance SLA | Draft |
| CQM-REQ-014 | Security and data protection | Draft |
| CQM-REQ-015 | User login with email and password | Draft |
| CQM-REQ-016 | User signup with Google | Draft |
| CQM-REQ-017 | Role conflict-of-interest control | Draft |
| CQM-REQ-018 | Worker workplaces with unique numbers | Draft |
| CQM-REQ-019 | Customer web queue state and workplace invitation | Draft |
| CQM-REQ-020 | SaaS delivery model | Draft |
| CQM-REQ-021 | Multi-tenant architecture | Draft |
| CQM-REQ-022 | Static hosting for web application | Draft |
| CQM-REQ-023 | API secured for authenticated users only | Draft |
| CQM-REQ-024 | No cross-tenant data disclosure | Draft |
| CQM-REQ-025 | Dev, test, and production environments | Draft |

## Gantt Diagram

```mermaid
gantt
    title CQM Requirement Delivery with Status
    dateFormat  YYYY-MM-DD
    excludes    weekends

    section Superseded (No Implementation)
    REQ-001 Superseded by REQ-007              :done, s1, 2026-05-17, 1d
    REQ-002 Superseded by REQ-005              :done, s2, 2026-05-17, 1d
    REQ-003 Superseded by REQ-006              :done, s3, 2026-05-17, 1d
    REQ-004 Superseded by REQ-010              :done, s4, 2026-05-17, 1d

    section Foundation and Access
    REQ-009 RBAC (Draft)                       :a1, 2026-05-18, 6d
    REQ-014 Security baseline (Draft)          :a2, after a1, 5d
    REQ-015 Email/password login (Draft)       :a3, after a1, 5d
    REQ-016 Google signup (Draft)              :a4, after a3, 4d
    REQ-023 Authenticated API only (Draft)     :a6, after a3, 4d
    REQ-012 Audit/history backbone (Draft)     :a5, 2026-05-20, 12d

    section Queue Domain Core
    REQ-005 Queue setup lifecycle (Draft)      :b1, after a1, 7d
    REQ-006 Queue ownership (Draft)            :b2, after b1, 5d
    REQ-007 Enrollment and ticketing (Draft)   :b3, after b1, 8d
    REQ-008 Queue operations (Draft)           :b4, after b3, 8d
    REQ-018 Worker workplaces (Draft)          :b5, after b2, 6d

    section Dashboards and Visibility
    REQ-010 Queue manager dashboard (Draft)    :c1, after b2, 9d
    REQ-011 Customer queue visibility (Draft)  :c2, after b4, 7d
    REQ-019 Customer invitation page (Draft)   :c3, after b5, 7d

    section SaaS and Tenant Isolation
    REQ-020 SaaS delivery model (Draft)        :e1, 2026-05-19, 7d
    REQ-021 Multi-tenant architecture (Draft)  :e2, after e1, 8d
    REQ-024 No cross-tenant disclosure (Draft) :e3, after e2, 6d

    section Delivery Platform
    REQ-022 Static web hosting (Draft)         :f1, 2026-05-19, 5d
    REQ-025 Dev/test/prod environments (Draft) :f2, after f1, 6d

    section Hardening and Closure
    REQ-017 Conflict-of-interest controls (Draft):d0, after a1, 6d
    REQ-013 Reliability and SLA (Draft)        :d1, after c3, 7d
    Integration and UAT                         :d2, after d1, 5d
```

## Notes

- `CQM-REQ-001..004` are retained for history and traceability only.
- Active implementation scope is `CQM-REQ-005..025`.
