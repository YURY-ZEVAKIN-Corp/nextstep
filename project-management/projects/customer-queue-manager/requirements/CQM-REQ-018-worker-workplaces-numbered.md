# CQM-REQ-018: Worker Workplaces with Unique Numbers

## Metadata

- ID: `CQM-REQ-018`
- Status: `Draft`
- Priority: `High`
- Owner: `Product Manager`
- Stakeholders: `Worker, Queue Manager, System Administrator`
- Created: `2026-05-17`
- Project Key: `CQM`
- Origin Backlog Item: `CQM-IDEA-002`
- Target Release: `TBD`

## Problem Statement

Queue operations need clear physical service points to direct customers correctly. Without numbered workplaces, customer routing is ambiguous and slows service flow.

## Business Value

Numbered workplaces improve clarity of customer direction, reduce routing errors, and increase service throughput.

## Business Value Metric

- Metric Name: `Business Value Score`
- Formula: `Reach x Impact x Confidence`
- Reach: `300 customers/week`
- Impact: `8`
- Confidence: `0.85`
- Calculated Score: `2040`
- Measurement Window: `First 30 days after rollout`
- Evidence / Assumptions: `Based on expected multi-worker service model`

## Users / Actors

- Worker
- Queue Manager
- System Administrator

## Requirement

All workers must have assigned workplaces, and each workplace must have a unique number within its service location.

## Acceptance Criteria

- [ ] System stores workplace entities with unique workplace number per location.
- [ ] Each worker can be assigned to one active workplace for current shift/session.
- [ ] System blocks duplicate workplace numbers within the same location.
- [ ] Workplace assignment changes are logged with actor and timestamp.

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

- Draft status retained until workplace model and location boundaries are confirmed.

## Non-Functional Requirements

- Performance: `Workplace lookup and assignment should complete within 2 seconds under normal load.`
- Reliability: `No duplicate active workplace assignment for the same worker in the same session.`
- Security: `Only authorized roles can create or modify workplaces and assignments.`
- Compliance: `Assignment history must be retained for audit review.`

## Out of Scope

- Floor-map visualization of workplaces.
- Automatic worker-to-workplace optimization.

## Dependencies

- Queue configuration model with location context.
- RBAC and audit logging (`CQM-REQ-009`, `CQM-REQ-012`).

## Open Questions

- Can a worker operate from multiple workplaces in one shift, and under what rules?

## Links

- Related backlog item: `CQM-IDEA-002`
- Related solution: `TBD`
- Related decision: `TBD`
