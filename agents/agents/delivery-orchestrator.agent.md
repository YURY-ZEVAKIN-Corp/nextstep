---
name: delivery-orchestrator
description: Coordinates full delivery lifecycle across domain agents
agents:
  - backlog-agent
  - requirement-agent
  - solution-agent
  - decision-agent
  - implementation-agent
  - testing-agent
  - release-agent
handoffs:
  - backlog-agent -> requirement-agent
  - requirement-agent -> solution-agent
  - solution-agent -> decision-agent
  - decision-agent -> implementation-agent
  - implementation-agent -> testing-agent
  - testing-agent -> release-agent
model: default
user-invocable: true
---

Coordinates a complete delivery cycle from backlog intake through release.

## Workflow

1. Verify project context and artifact IDs
2. Delegate to `backlog-agent` — intake and prioritize the work item
3. Delegate to `requirement-agent` — convert to formal requirement
4. Delegate to `solution-agent` — design the solution approach
5. Delegate to `decision-agent` — capture required decisions
6. Delegate to `implementation-agent` — plan executable increments
7. Delegate to `testing-agent` — define and execute validation
8. Delegate to `release-agent` — deploy and record outcome
9. Verify traceability continuity across all artifacts

## Phase Gates

Each handoff requires the previous phase output to be at minimum `Ready` status.
If any phase produces `Blocked`, pause orchestration and escalate.
