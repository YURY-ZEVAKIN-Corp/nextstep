# CQM-DEC-008: SSE-First Strategy for Customer TV Channel

## Metadata

- ID: `CQM-DEC-008`
- Status: `Draft`
- Owner: `Engineering Lead`
- Date: `2026-05-17`
- Project Key: `CQM`

## Context

CQM customer view will run on TV browsers that may not reliably support WebSocket behavior across all target devices. Customer display is primarily a server-to-client update stream (queue state and invitation), which suits one-way push transport.

## Decision

Use SSE-first transport for customer/TV channel. If SSE is unavailable or repeatedly fails, fallback to polling with configurable interval (default 5 seconds). Keep WebSocket/SignalR availability for staff-facing channels where richer bidirectional interaction is needed.

## Consequences

- Positive consequence 1: Better compatibility for constrained TV browser environments.
- Positive consequence 2: Simpler client/runtime behavior for one-way updates.
- Positive consequence 3: Reduced operational risk of broken customer display during queue operations.
- Negative consequence 1: SSE is one-way; some interaction patterns still require separate APIs.
- Negative consequence 2: Polling fallback can increase API load if not tuned.

## Alternatives

- Alternative 1: WebSocket-first for all clients.
- Alternative 2: Polling-only approach.
- Alternative 3: Device-specific transport selection without common default.

## Decision Checklist Review

Checklist file: `project-management/templates/decision-checklist.md`

- Review Date: `TBD`
- Reviewer: `TBD`
- Result: `Fail`
- Triage: `High`

### Checklist Summary

- [x] Decision conflict check completed
- [x] Decision triage assigned
- [x] Context is clear
- [x] Alternatives were considered
- [x] Consequences are understood
- [x] Links to impacted artifacts are recorded

### Review Notes

- Draft until TV compatibility matrix and fallback thresholds are validated in test plan.

## Links

- Related requirements: `CQM-REQ-019, CQM-REQ-022, CQM-REQ-026`
- Related solutions: `CQM-SOL-001`
- Related implementation: `CQM-IMP-001`
- Related technology stack entries: `CQM-STACK-OPTIONS-TEAM-DISCUSSION`
- Related portfolio or project decision register: `project-management/projects/customer-queue-manager/decision-register.md`
