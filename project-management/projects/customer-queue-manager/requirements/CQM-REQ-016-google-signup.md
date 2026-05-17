# CQM-REQ-016: User Signup with Google

## Metadata

- ID: `CQM-REQ-016`
- Status: `Draft`
- Priority: `Medium`
- Owner: `Product Manager`
- Stakeholders: `Worker, Queue Manager, System Administrator`
- Created: `2026-05-17`
- Project Key: `CQM`
- Origin Backlog Item: `CQM-IDEA-002`
- Target Release: `TBD`

## Problem Statement

Some users need a faster onboarding path than manual credential creation.

## Business Value

Google sign-up can reduce onboarding friction and speed user access setup while preserving account security controls.

## Business Value Metric

- Metric Name: `Business Value Score`
- Formula: `Reach x Impact x Confidence`
- Reach: `200 users/year`
- Impact: `6`
- Confidence: `0.75`
- Calculated Score: `900`
- Measurement Window: `First 90 days after rollout`
- Evidence / Assumptions: `Assumes a subset of staff prefers federated onboarding`

## Users / Actors

- Worker
- Queue Manager
- System Administrator

## Requirement

User can sign up in the system with Google.

## Acceptance Criteria

- [ ] User can start sign-up flow using Google account.
- [ ] System creates user account after successful Google identity verification.
- [ ] If email already exists, system links or blocks account creation according to configured policy.
- [ ] New Google sign-up users are assigned default role with restricted permissions until admin review (if required).

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

- Draft status retained until account linking and role assignment policy is approved.

## Non-Functional Requirements

- Performance: `OAuth sign-up callback processing should complete within 3 seconds under normal load.`
- Reliability: `Account creation or linking must be idempotent for repeated callback events.`
- Security: `OAuth tokens must be validated and stored/handled according to security policy.`
- Compliance: `Authentication and account-creation events must be audit logged.`

## Out of Scope

- Non-Google social providers.
- Automatic elevation to privileged roles on first sign-up.
- Role and permission policy definition (covered by `CQM-REQ-009`).
- Broad security/data protection controls outside signup flow (covered by `CQM-REQ-014`).

## Dependencies

- Google OAuth configuration and client credentials.
- User identity/linking policy.
- Audit/security logging pipeline.

## Open Questions

- Is sign-up open for all users or restricted to allowed email domains?

## Links

- Related backlog item: `CQM-IDEA-002`
- Related solution: `TBD`
- Related decision: `TBD`
