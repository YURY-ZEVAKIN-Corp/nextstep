# CQM-REQ-020: SaaS Delivery Model

## Metadata

- ID: `CQM-REQ-020`
- Status: `Draft`
- Priority: `High`
- Owner: `Product Manager`
- Stakeholders: `Queue Manager, System Administrator, Compliance Reviewer`
- Created: `2026-05-17`
- Project Key: `CQM`
- Origin Backlog Item: `CQM-IDEA-002`
- Target Release: `TBD`

## Problem Statement

If CQM is delivered to multiple organizations without a SaaS model, onboarding, operations, upgrades, and support become difficult to scale.

## Business Value

SaaS delivery enables faster customer onboarding, centralized maintenance, consistent feature rollout, and repeatable operations across tenants.

## Business Value Metric

- Metric Name: `Business Value Score`
- Formula: `Reach x Impact x Confidence`
- Reach: `10 tenant organizations/year`
- Impact: `9`
- Confidence: `0.8`
- Calculated Score: `72`
- Measurement Window: `First 12 months after launch`
- Evidence / Assumptions: `Assumes managed multi-tenant product strategy with centralized operations`

## Users / Actors

- Queue Manager
- System Administrator
- Compliance Reviewer

## Requirement

The system must be delivered as a SaaS platform.

## Acceptance Criteria

- [ ] System supports multi-tenant architecture with strict tenant data isolation.
- [ ] Tenant onboarding and configuration can be completed without code changes.
- [ ] Platform supports centralized deployment, upgrades, and rollback procedures.
- [ ] Tenant-scoped usage, security, and audit data are available for operational support.

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

- Draft status retained until tenancy strategy (shared DB vs isolated DB model) is approved.

## Non-Functional Requirements

- Performance: `Tenant isolation controls must not break core SLA targets for queue operations.`
- Reliability: `SaaS operations must support safe rollback for failed releases with tenant impact visibility.`
- Security: `Tenant boundaries must be enforced in data access, API authorization, and background jobs.`
- Compliance: `Tenant-level audit and retention controls must satisfy policy obligations.`

## Out of Scope

- On-premise deployment model.
- Single-tenant custom code forks per customer.

## Dependencies

- RBAC and conflict-of-interest controls (`CQM-REQ-009`, `CQM-REQ-017`).
- Security and audit controls (`CQM-REQ-012`, `CQM-REQ-014`).
- Reliability and operations baseline (`CQM-REQ-013`).

## Open Questions

- Which tenancy model is selected for phase 1: shared schema, separate schema, or separate database per tenant?

## Links

- Related backlog item: `CQM-IDEA-002`
- Related solution: `TBD`
- Related decision: `TBD`
