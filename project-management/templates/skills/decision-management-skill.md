# Skill Instruction: Decision Management

## Purpose
Capture and govern significant product or technical decisions with rationale.

## Inputs
- Decision trigger from solution/implementation
- Options and trade-offs
- Impact assessment

## Preconditions
- Decision scope and owner are identified.

## Steps
1. Create decision record in `projects/<key>/decisions/`.
2. Document context, options, selected option, rationale, consequences.
3. Run decision checklist.
4. Set decision status and update decision register.
5. Link decision in traceability matrix and related artifacts.

## Outputs
- Decision artifact in `projects/<key>/decisions/`
- Updated `projects/<key>/decision-register.md`

## Quality Checks
- Checklist passed: `templates/decision-checklist.md`
- Trade-offs and consequences are explicit.
- Links to impacted artifacts are complete.

## Status Transition
- `Draft` -> `Accepted`

## RACI
- R: Technical Lead
- A: Solution Architect
- C: Product Manager, Security Engineer
- I: Project Manager, Dev, QA, DevOps

## Tools/Templates
- `templates/decision-template.md`
- `templates/decision-checklist.md`
- `templates/decision-register-template.md`

## Escalation
If stakeholders cannot agree on option selection, escalate to architecture/governance review.
