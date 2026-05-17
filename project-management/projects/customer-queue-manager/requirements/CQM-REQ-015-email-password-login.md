# CQM-REQ-015: User Login with Email and Password

## Metadata

- ID: `CQM-REQ-015`
- Status: `Draft`
- Priority: `High`
- Owner: `Product Manager`
- Stakeholders: `Worker, Queue Manager, System Administrator`
- Created: `2026-05-17`
- Project Key: `CQM`
- Origin Backlog Item: `CQM-IDEA-002`
- Target Release: `TBD`

## Problem Statement

Staff users need a secure and consistent authentication method before accessing queue management capabilities.

## Business Value

Email/password login establishes controlled access, enables user accountability, and supports role-based authorization across the system.

## Business Value Metric

- Metric Name: `Business Value Score`
- Formula: `Reach x Impact x Confidence`
- Reach: `300 customers/week`
- Impact: `9`
- Confidence: `0.85`
- Calculated Score: `2295`
- Measurement Window: `First 30 days after rollout`
- Evidence / Assumptions: `Based on expected staff usage and security baseline requirements`

## Users / Actors

- Worker
- Queue Manager
- System Administrator

## Requirement

User must log in to the system using email and password.

## Acceptance Criteria

- [ ] User can sign in with registered email and valid password.
- [ ] System rejects invalid email/password combinations with safe error messages.
- [ ] Successful login creates authenticated session for authorized system access.
- [ ] Failed login attempts are rate-limited and security logged.

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

- Draft status retained until password policy and session security rules are finalized.

## Non-Functional Requirements

- Performance: `Authentication response should complete within 2 seconds under normal load.`
- Reliability: `Authentication service should preserve session consistency and prevent duplicate sessions from race conditions.`
- Security: `Passwords must be stored using approved one-way hashing and secure password policy.`
- Compliance: `Authentication and failed login events must be retained per security audit policy.`

## Out of Scope

- Social login providers.
- Passwordless login methods.
- Role and permission policy definition (covered by `CQM-REQ-009`).
- Broad security/data protection controls outside login flow (covered by `CQM-REQ-014`).

## Dependencies

- User account management with email identity.
- Session management service.
- Audit/security logging pipeline.

## Open Questions

- Is multi-factor authentication required at initial release or later phase?

## Links

- Related backlog item: `CQM-IDEA-002`
- Related solution: `TBD`
- Related decision: `TBD`
