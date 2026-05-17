# CQM-REQ-019: Customer Web Page for Queue State and Workplace Invitation

## Metadata

- ID: `CQM-REQ-019`
- Status: `Draft`
- Priority: `High`
- Owner: `Product Manager`
- Stakeholders: `Customer, Worker, Queue Manager`
- Created: `2026-05-17`
- Project Key: `CQM`
- Origin Backlog Item: `CQM-IDEA-001`
- Target Release: `TBD`

## Problem Statement

Customers need a clear digital channel to monitor queue progress and know exactly when and where to go for service.

## Business Value

A customer web page with live queue state and workplace invitations reduces confusion, improves waiting experience, and speeds handoff to service points.

## Business Value Metric

- Metric Name: `Business Value Score`
- Formula: `Reach x Impact x Confidence`
- Reach: `300 customers/week`
- Impact: `9`
- Confidence: `0.85`
- Calculated Score: `2295`
- Measurement Window: `First 30 days after rollout`
- Evidence / Assumptions: `Based on expected customer self-service usage during wait period`

## Users / Actors

- Customer
- Worker
- Queue Manager

## Requirement

Customers must have a web page that shows the current queue state and invites customers to the workplace number of the worker who is ready to serve them.

## Acceptance Criteria

- [ ] Customer web page displays current queue state (position, current serving number, estimated wait time).
- [ ] When customer is called, page displays invitation message with target workplace number.
- [ ] Invitation updates in near real time and reflects latest queue operation state.
- [ ] System records invitation event with ticket ID, worker ID, workplace number, and timestamp.

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

- Draft status retained until UX text, refresh strategy, and invitation event contract are finalized.

## Non-Functional Requirements

- Performance: `Queue state and invitation updates should be visible to customers within 5 seconds under normal load.`
- Reliability: `Displayed invitation must match the latest committed queue call action.`
- Security: `Customer page must expose only ticket-scoped or public-safe queue information.`
- Compliance: `Invitation events must be audit logged according to retention policy.`

## Out of Scope

- Native mobile app implementation.
- Personalized marketing content on waiting page.

## Dependencies

- Queue processing operations (`CQM-REQ-008`).
- Customer queue visibility (`CQM-REQ-011`).
- Worker workplace model (`CQM-REQ-018`).

## Open Questions

- Should invitation expire automatically if customer does not appear within configured timeout?

## Links

- Related backlog item: `CQM-IDEA-001`
- Related solution: `TBD`
- Related decision: `TBD`
