# Skill Instruction: Project Audit

## Purpose
Verify project compliance with framework controls, traceability, and governance standards.

## Inputs
- Project artifacts and registers
- Audit cadence date
- Applicable standards/checklists

## Preconditions
- Project artifacts are accessible.
- Audit scope and period are defined.

## Steps
1. Execute audit checklist.
2. Verify traceability continuity across REQ/SOL/DEC/IMP/TST/REL.
3. Check checklist compliance for requirements and decisions.
4. Record findings, risks, and corrective actions.
5. Update project audit log.

## Outputs
- Audit findings in `projects/<key>/audit-log.md`
- Corrective action list with owners and due dates

## Quality Checks
- Evidence references are included for each finding.
- Findings are severity-ranked.
- Follow-up actions have owner and due date.

## Status Transition
- N/A (audit activity); findings tracked to closure

## RACI
- R: System Analyst
- A: Project Manager
- C: Architect, Tech Lead, QA, DevOps, Security
- I: Product Manager, Delivery team

## Tools/Templates
- `templates/audit-checklist.md`
- `projects/<key>/audit-log.md`
- `projects/<key>/traceability-matrix.md`

## Escalation
If severe non-compliance is found, escalate to portfolio governance immediately.
