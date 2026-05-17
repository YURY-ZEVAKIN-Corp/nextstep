# CQM-REQ-004: Queue Manager Dashboard for Owned Queues

## Metadata

- ID: `CQM-REQ-004`
- Status: `Superseded`
- Priority: `High`
- Owner: `Product Manager`
- Stakeholders: `Queue Manager, System Administrator`
- Created: `2026-05-17`
- Project Key: `CQM`
- Origin Backlog Item: `CQM-IDEA-002`
- Target Release: `TBD`

## Problem Statement

Queue managers need a dedicated workspace to monitor and operate queues they are responsible for. Without a focused dashboard and access boundaries, queue operations are slower and prone to mistakes.

## Business Value

A dedicated dashboard improves operational speed, reduces queue handling errors, and enforces accountability by limiting actions to managed queues.

## Business Value Metric

- Metric Name: `Business Value Score`
- Formula: `Reach x Impact x Confidence`
- Reach: `300 customers/week`
- Impact: `8`
- Confidence: `0.8`
- Calculated Score: `1920`
- Measurement Window: `First 30 days after rollout`
- Evidence / Assumptions: `Based on expected queue manager usage in pilot operations`

## Users / Actors

- Queue Manager
- Queue Management System

## Requirement

Queue manager must have their own dashboard for managing queues that are under their control.

## Acceptance Criteria

- [ ] Queue manager can access a dedicated dashboard after authentication.
- [ ] Dashboard shows only queues assigned to that queue manager.
- [ ] Queue manager can perform allowed queue operations (for example, open, pause, resume, close) only on assigned queues.
- [ ] System blocks queue manager actions on queues outside their ownership scope.

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

- Draft status retained until UI and permission model are reviewed.
- Superseded by `CQM-REQ-010` to avoid duplicate scope.

## Non-Functional Requirements

- Performance: `Dashboard should load assigned queue list within 3 seconds under normal load.`
- Reliability: `Dashboard operations must be idempotent where relevant and error-safe.`
- Security: `Authorization must enforce per-queue access boundaries for queue managers.`
- Compliance: `Manager actions from dashboard must be fully auditable.`

## Out of Scope

- Cross-manager analytics across all queues.
- Executive-level reporting dashboards.

## Dependencies

- Authentication and role-based access control.
- Queue-to-manager assignment model.
- Queue operations API and audit logging.

## Open Questions

- Which exact operations are allowed for queue managers versus operations managers?

## Links

- Related backlog item: `CQM-IDEA-002`
- Related solution: `TBD`
- Related decision: `TBD`
- Superseded by: `CQM-REQ-010`
