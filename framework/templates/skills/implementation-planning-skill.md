# Skill Instruction: Implementation Planning

## Purpose
Break approved solution scope into executable increments with ownership and dependencies.

## Inputs
- Approved solution and decisions
- Team capacity and constraints

## Preconditions
- Solution is in review/approved for execution.
- Blocking decisions are accepted.

## Steps
1. Create implementation plan in `projects/<key>/implementation/`.
2. Split work into milestones and tasks.
3. Define owners, dependencies, and done criteria.
4. Add delivery risks and mitigations.
5. Link to requirement/solution/decision IDs.

## Outputs
- Implementation artifact in `projects/<key>/implementation/`

## Quality Checks
- Each task has owner and done criteria.
- Dependency chain is explicit.
- Scope is traceable to upstream artifacts.

## Status Transition
- `Draft` -> `Ready`

## RACI
- R: Developer
- A: Technical Lead
- C: Architect, QA, DevOps, Analyst
- I: Project Manager, Product Manager

## Tools/Templates
- `templates/implementation-plan-template.md`
- `projects/<key>/traceability-matrix.md`

## Escalation
If capacity or dependencies block scheduling, escalate to Project Manager.
