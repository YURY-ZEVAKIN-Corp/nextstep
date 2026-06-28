---
name: solution-design
description: Define a feasible solution approach aligned to requirements and stack constraints
type: process
maturity: stable
tags:
  - solution
  - architecture
  - design
---

## Purpose
Define a feasible solution approach aligned to requirements and stack constraints.

## Inputs
- Approved requirement(s)
- Existing architecture and stack constraints
- Non-functional needs

## Preconditions
- Linked requirement(s) are `Ready`.
- Relevant system context is available.

## Steps
1. Create solution artifact in `runtime/projects/<key>/solutions/`.
2. Describe approach and impacted components.
3. Document risks and alternatives.
4. Define rollout approach.
5. Identify whether new decisions are needed.
6. Update traceability links.

## Outputs
- Solution artifact in `runtime/projects/<key>/solutions/`
- Updated traceability links

## Quality Checks
- Solution maps to requirement scope.
- Risks and alternatives are explicit.
- Stack alignment is confirmed or flagged.

## Status Transition
- `Draft` -> `In Review`

## RACI
- R: System Analyst
- A: Solution Architect
- C: Technical Lead, QA, Product Manager
- I: Project Manager, DevOps

## Tools/Templates
- `framework/templates/solution-template.md`
- `runtime/projects/<key>/technology-stack.md`

## Escalation
If solution conflicts with approved stack, escalate for decision record creation.
