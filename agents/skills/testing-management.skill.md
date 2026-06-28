---
name: testing-management
description: Define and execute validation required for safe release
type: process
maturity: stable
tags:
  - testing
  - validation
  - quality
---

## Purpose
Define and execute validation required for safe release.

## Inputs
- Implementation scope and acceptance criteria
- Risk and regression context

## Preconditions
- Implementation scope is stable enough for test planning.

## Steps
1. Create test artifact in `projects/<key>/testing/`.
2. Define acceptance, functional, and regression coverage.
3. Add non-functional checks where required.
4. Execute tests and record outcomes.
5. Report defects and retest status.

## Outputs
- Test artifact in `projects/<key>/testing/`
- Evidence for release readiness

## Quality Checks
- Acceptance criteria are fully covered.
- Failed tests are tracked with disposition.
- Regression scope is documented.

## Status Transition
- `In Progress` -> `Tested`

## RACI
- R: QA / Test Engineer
- A: QA / Test Engineer
- C: Developer, Technical Lead, Product Manager, Security Engineer
- I: Project Manager, DevOps

## Tools/Templates
- `framework/templates/test-plan-template.md`
- `projects/<key>/traceability-matrix.md`

## Escalation
If critical defects remain open, escalate no-go recommendation to Project Manager and Tech Lead.
