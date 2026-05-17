# CQM-REQ-003: Every Queue Must Have a Manager User

## Metadata

- ID: `CQM-REQ-003`
- Status: `Superseded`
- Priority: `High`
- Owner: `Product Manager`
- Stakeholders: `Queue Manager, System Administrator`
- Created: `2026-05-17`
- Project Key: `CQM`
- Origin Backlog Item: `CQM-IDEA-002`
- Target Release: `TBD`

## Problem Statement

Without clear ownership for each queue, operational accountability is weak and issues such as misconfiguration, slow response, or unmanaged customer flow can occur.

## Business Value

Assigning a manager user to every queue creates accountability, improves queue governance, and enables faster operational decision making.

## Business Value Metric

- Metric Name: `Business Value Score`
- Formula: `Reach x Impact x Confidence`
- Reach: `300 customers/week`
- Impact: `7`
- Confidence: `0.8`
- Calculated Score: `1680`
- Measurement Window: `First 30 days after rollout`
- Evidence / Assumptions: `Based on expected multi-queue operation and supervisor coverage`

## Users / Actors

- Queue Manager
- System Administrator

## Requirement

Every system queue must have an assigned manager, and the manager must be a valid user in the system.

## Acceptance Criteria

- [ ] System requires assignment of a manager user when creating a queue.
- [ ] System prevents activating a queue without an assigned manager user.
- [ ] Assigned manager must reference an existing active user account.
- [ ] Authorized staff can reassign queue manager and the change is auditable.

## Requirement Checklist Review

Checklist file: `project-management/templates/requirement-checklist.md`

- Review Date: `TBD`
- Reviewer: `TBD`
- Result: `Fail`

### Checklist Summary

- [x] Problem is clearly stated
- [x] Business value is clear
- [x] Business value metric is calculated
- [x] Scope is clear
- [x] Acceptance criteria are testable
- [x] Dependencies are identified
- [x] Out-of-scope items are listed

### Review Notes

- Draft status retained until review confirms role model and permissions.
- Superseded by `CQM-REQ-006` to avoid duplicate scope.

## Non-Functional Requirements

- Performance: `Manager assignment and validation should complete within 2 seconds under normal load.`
- Reliability: `Queue-manager relation must be transactionally consistent.`
- Security: `Only authorized roles can assign or change queue managers.`
- Compliance: `Manager assignment changes must be retained in audit history.`

## Out of Scope

- Manager performance scoring.
- Automated manager assignment recommendations.

## Dependencies

- User management module with active/inactive status.
- Role-based access control for queue administration.
- Audit logging for administrative actions.

## Open Questions

- Can one manager user own multiple queues, and is there an upper limit?

## Links

- Related backlog item: `CQM-IDEA-002`
- Related solution: `TBD`
- Related decision: `TBD`
- Superseded by: `CQM-REQ-006`
