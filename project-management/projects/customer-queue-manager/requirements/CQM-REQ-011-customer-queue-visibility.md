# CQM-REQ-011: Customer Queue Visibility

## Metadata

- ID: `CQM-REQ-011`
- Status: `Draft`
- Priority: `High`
- Owner: `Product Manager`
- Stakeholders: `Customers, Worker`
- Created: `2026-05-17`
- Project Key: `CQM`
- Origin Backlog Item: `CQM-IDEA-001`
- Target Release: `TBD`

## Problem Statement

Customers need visibility into queue position and expected waiting time.

## Business Value

Visibility reduces anxiety and improves waiting experience.

## Business Value Metric

- Metric Name: `Business Value Score`
- Formula: `Reach x Impact x Confidence`
- Reach: `300 customers/week`
- Impact: `7`
- Confidence: `0.85`
- Calculated Score: `1785`
- Measurement Window: `First 30 days after rollout`
- Evidence / Assumptions: `Customer experience assumptions`

## Users / Actors

- Customer

## Requirement

The system must show customers their queue position and estimated wait time with near real-time updates.

## Acceptance Criteria

- [ ] Customer can view current queue position.
- [ ] Customer can view estimated wait time.
- [ ] Display refresh interval is configurable and near real-time.
- [ ] Shown data matches backend queue state.

## Non-Functional Requirements

- Performance: `Status updates propagate within 5 seconds under normal load.`
- Reliability: `Position and ETA are recalculated correctly after queue events.`
- Security: `Customer view cannot access privileged staff controls.`
- Compliance: `No sensitive data shown in public display mode.`

## Out of Scope

- Personalized marketing in waiting view.

## Dependencies

- Queue event stream and ETA calculation service.

## Links

- Related backlog item: `CQM-IDEA-001`
- Related solution: `TBD`
- Related decision: `TBD`
