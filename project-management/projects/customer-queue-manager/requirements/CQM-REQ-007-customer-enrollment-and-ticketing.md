# CQM-REQ-007: Customer Enrollment and Ticketing

## Metadata

- ID: `CQM-REQ-007`
- Status: `Draft`
- Priority: `High`
- Owner: `Product Manager`
- Stakeholders: `Customers, Worker`
- Created: `2026-05-17`
- Project Key: `CQM`
- Origin Backlog Item: `CQM-IDEA-001`
- Target Release: `TBD`

## Problem Statement

Customers need an unambiguous process to join a selected queue and obtain a service ticket.

## Business Value

Reliable enrollment improves fairness, trust, and flow efficiency.

## Business Value Metric

- Metric Name: `Business Value Score`
- Formula: `Reach x Impact x Confidence`
- Reach: `300 customers/week`
- Impact: `8`
- Confidence: `0.85`
- Calculated Score: `2040`
- Measurement Window: `First 30 days after rollout`
- Evidence / Assumptions: `Pilot volume assumptions`

## Users / Actors

- Customer
- Worker

## Requirement

The system must let customers enroll in a specific queue and receive a unique queue ticket.

## Acceptance Criteria

- [ ] Customer can select queue and submit enrollment.
- [ ] System issues unique ticket number in queue scope.
- [ ] Ticket includes queue identifier and issue timestamp.
- [ ] Enrollment record is visible to staff.

## Non-Functional Requirements

- Performance: `Ticket issuance completes within 2 seconds.`
- Reliability: `No duplicate ticket number in queue/day scope.`
- Security: `Input validation and abuse protection are applied.`
- Compliance: `Minimal personal data collection.`

## Out of Scope

- Future appointment scheduling.

## Dependencies

- Queue catalog and ticket generator service.

## Links

- Related backlog item: `CQM-IDEA-001`
- Related solution: `TBD`
- Related decision: `TBD`
