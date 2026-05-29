# Skill Instruction: Release Management

## Purpose
Deploy validated changes safely and record release outcomes.

## Inputs
- Tested implementation scope
- Deployment plan and rollback steps
- Release window constraints

## Preconditions
- Test evidence is available and acceptable.
- Rollback plan is defined.

## Steps
1. Create release record in `projects/<key>/releases/`.
2. Document change set and verification evidence.
3. Execute deployment.
4. Run post-deploy checks.
5. Record result and follow-up actions.

## Outputs
- Release artifact in `projects/<key>/releases/`
- Deployment outcome and follow-up list

## Quality Checks
- Rollback steps are validated.
- Post-release checks are completed.
- Incident/failure notes are explicit.

## Status Transition
- `Tested` -> `Deployed` -> `Closed`

## RACI
- R: DevOps / Release Engineer
- A: DevOps / Release Engineer
- C: QA, Tech Lead, Developer, Security Engineer
- I: Project Manager, Product Manager

## Tools/Templates
- `templates/release-template.md`
- `projects/<key>/traceability-matrix.md`

## Escalation
If deployment risk is high or checks fail, trigger rollback and escalate incident handling.
