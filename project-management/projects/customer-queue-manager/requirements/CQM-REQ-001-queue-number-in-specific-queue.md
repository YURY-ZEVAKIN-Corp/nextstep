# CQM-REQ-001: Customer Can Get Queue Number in Specific Queue

## Metadata

- ID: `CQM-REQ-001`
- Status: `Superseded`
- Priority: `High`
- Owner: `Product Manager`
- Stakeholders: `Customers, Worker, Queue Manager`
- Created: `2026-05-17`
- Project Key: `CQM`
- Origin Backlog Item: `CQM-IDEA-001`
- Target Release: `TBD`

## Problem Statement

Customers need a clear and reliable way to join a selected service queue. Without a queue number tied to a specific queue, waiting order becomes unclear and service flow is inconsistent.

## Business Value

Assigning a queue number in a specific queue ensures fair ordering, reduces front-desk confusion, and improves customer trust in the waiting process.

## Business Value Metric

- Metric Name: `Business Value Score`
- Formula: `Reach x Impact x Confidence`
- Reach: `200 customers/week`
- Impact: `8`
- Confidence: `0.8`
- Calculated Score: `1280`
- Measurement Window: `First 30 days after rollout`
- Evidence / Assumptions: `Estimated from expected queue volume in pilot location`

## Users / Actors

- Customer
- Queue Management System
- Worker

## Requirement

The system must allow a customer to get a queue number in a specific system queue.

## Acceptance Criteria

- [ ] Customer can select a specific queue from available queue types.
- [ ] System generates a unique queue number for the selected queue.
- [ ] Queue number is visible to the customer with queue identifier and timestamp.
- [ ] Queue entry is stored and visible to staff in queue management view.

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
- [ ] Dependencies are identified
- [x] Out-of-scope items are listed

### Review Notes

- Dependency details to be finalized during solution design.
- Superseded by `CQM-REQ-007` to avoid duplicate scope.

## Non-Functional Requirements

- Performance: `Queue number issuance should complete within 2 seconds under normal load.`
- Reliability: `No duplicate queue numbers within the same queue on the same day.`
- Security: `Queue creation endpoint must enforce input validation and rate limiting.`
- Compliance: `No sensitive personal data required for anonymous queue ticket issuance.`

## Out of Scope

- Reservation of future queue slots.
- Priority bypass rules.

## Dependencies

- Configured queue catalog with active queue types.
- Backend queue-number generation service.

## Open Questions

- Should queue numbers reset daily per queue or continue sequentially?

## Links

- Related backlog item: `CQM-IDEA-001`
- Related solution: `TBD`
- Related decision: `TBD`
- Superseded by: `CQM-REQ-007`
