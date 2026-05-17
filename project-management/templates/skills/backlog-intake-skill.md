# Skill Instruction: Backlog Intake

## Purpose
Capture and triage new work items before formal requirement creation.

## Inputs
- New idea/request/defect/technical task
- Source/requester information
- Project key

## Preconditions
- Project backlog file exists: `projects/<key>/backlog.md`

## Steps
1. Add backlog item with unique ID.
2. Classify work type and priority.
3. Assign the item to a named team member.
4. Add short value statement.
5. Define next action.
6. Set status to `Draft` unless ready for immediate analysis.

## Outputs
- Updated backlog entry in `projects/<key>/backlog.md`

## Quality Checks
- Item has ID, title, type, priority, source, assignee, value statement, next action.
- Duplicates are checked.

## Status Transition
- `Draft` -> `Ready` for requirement analysis

## RACI
- R: Product Manager / Business Owner
- A: Project Manager
- C: System Analyst, Technical Lead
- I: Dev, QA, DevOps

## Tools/Templates
- `projects/<key>/backlog.md`
- `templates/backlog-template.md`

## Escalation
If scope or urgency is unclear, escalate to Project Manager for triage decision.
