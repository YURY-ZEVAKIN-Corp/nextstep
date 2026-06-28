---
name: requirement-management
description: Convert prioritized backlog items into clear, testable requirements with business value
type: process
maturity: stable
tags:
  - requirement
  - business-value
  - analysis
---

## Purpose
Convert prioritized backlog items into clear, testable requirements with business value.

## Inputs
- Approved backlog item
- Business context and stakeholders
- Initial success criteria

## Preconditions
- Backlog item exists and is prioritized.
- Requirement file naming pattern is defined.

## Steps
1. Create requirement in `runtime/projects/<key>/requirements/`.
2. Define problem, affected users, expected outcome, scope boundaries.
3. Calculate and record business value.
4. Define measurable success criteria.
5. Run requirement checklist.
6. Link requirement in traceability matrix.

## Outputs
- Requirement artifact in `runtime/projects/<key>/requirements/`
- Updated `runtime/projects/<key>/traceability-matrix.md`

## Quality Checks
- Checklist passed: `framework/templates/requirement-checklist.md`
- Requirement is specific, measurable, and testable.
- Business value is calculated and explicit.

## Status Transition
- `Draft` -> `Ready`

## RACI
- R: System Analyst
- A: Product Manager / Business Owner
- C: Project Manager, Architect, QA
- I: Dev, DevOps

## Tools/Templates
- `framework/templates/requirement-template.md`
- `framework/templates/requirement-checklist.md`
- `runtime/projects/<key>/traceability-matrix.md`

## Escalation
If success criteria or value cannot be agreed, escalate to Product Manager for decision.
