# RACI and Skill Matrix Template

Use this template to define which roles are needed, which skills are required, and who is Responsible/Accountable/Consulted/Informed for each activity in the NextStep flow.

## Project Context

- Project Key: `TBD`
- Project Name: `TBD`
- Version: `v1`
- Owner: `TBD`
- Last Updated: `YYYY-MM-DD`

## Role Catalog

| Role | Primary Responsibility | Required Skill Areas | Backup Role | Notes |
|---|---|---|---|---|
| Project Manager | Delivery coordination and governance | Planning, prioritization, dependency management, risk management, status tracking | TBD | |
| Product Manager / Business Owner | Outcome definition and value ownership | Product strategy, business value modeling, scope control, stakeholder alignment | TBD | |
| System Analyst | Requirement analysis and traceability | Elicitation, process modeling, acceptance criteria, decomposition, traceability | TBD | |
| Solution Architect | Solution design and architecture fitness | Architecture patterns, integration design, NFR analysis, trade-off analysis | TBD | |
| Technical Lead | Execution planning and technical oversight | Work slicing, estimation, code quality practices, implementation governance | TBD | |
| Developer | Implementation delivery | Coding standards, testing basics, code review, debugging | TBD | |
| QA / Test Engineer | Test strategy and validation | Test design, regression strategy, defect triage, quality reporting | TBD | |
| DevOps / Release Engineer | Deployment and release safety | CI/CD, release orchestration, rollback planning, observability | TBD | |
| Security Engineer (as needed) | Security assurance | Threat modeling, security controls, secure review, compliance checks | TBD | Optional for low-risk items |

## Skill Proficiency Scale

Use this scale for each role and project:

- `1 - Awareness`: understands concepts
- `2 - Working`: can execute with guidance
- `3 - Independent`: can execute without guidance
- `4 - Advanced`: can optimize and mentor others

## Role Skill Assessment

| Role | Planning | Requirements | Architecture | Implementation | Testing | Release | Governance/Audit | Security | Current Level (avg) | Target Level (avg) | Gap Actions |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Project Manager |  |  |  |  |  |  |  |  |  |  | |
| Product Manager / Business Owner |  |  |  |  |  |  |  |  |  |  | |
| System Analyst |  |  |  |  |  |  |  |  |  |  | |
| Solution Architect |  |  |  |  |  |  |  |  |  |  | |
| Technical Lead |  |  |  |  |  |  |  |  |  |  | |
| Developer |  |  |  |  |  |  |  |  |  |  | |
| QA / Test Engineer |  |  |  |  |  |  |  |  |  |  | |
| DevOps / Release Engineer |  |  |  |  |  |  |  |  |  |  | |
| Security Engineer (as needed) |  |  |  |  |  |  |  |  |  |  | |

## Activity RACI Matrix (Framework Level)

RACI legend:

- `R`: Responsible (does the work)
- `A`: Accountable (final owner)
- `C`: Consulted (provides input)
- `I`: Informed (kept updated)

| Activity | Artifact/Location | PM | Product | Analyst | Architect | Tech Lead | Dev | QA | DevOps | Security | Status Gate |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Intake and triage new work | `projects/<key>/backlog.md` | A | R | C | I | C | I | I | I | I | `Draft` -> `Ready` |
| Define requirement and business value | `projects/<key>/requirements/` | C | A | R | C | I | I | C | I | C | `Draft` -> `Ready` |
| Validate requirement checklist | `templates/requirement-checklist.md` | A | C | R | I | I | I | C | I | C | `Ready` |
| Design solution and assess risks | `projects/<key>/solutions/` | C | C | R | A | C | I | C | I | C | `In Review` |
| Record architecture/product decision | `projects/<key>/decisions/` | I | C | C | A | R | I | I | I | C | `Draft` -> `Accepted` |
| Maintain decision register | `projects/<key>/decision-register.md` | A | I | C | R | C | I | I | I | I | `In Progress` |
| Create implementation plan | `projects/<key>/implementation/` | C | I | C | C | A | R | C | C | I | `Ready` |
| Execute implementation tasks | Implementation tasks and codebase | I | I | I | C | A | R | C | C | I | `In Progress` |
| Define and execute test plan | `projects/<key>/testing/` | I | C | C | I | C | C | A/R | I | C | `Tested` |
| Prepare and run release | `projects/<key>/releases/` | C | I | I | I | C | C | C | A/R | C | `Deployed` |
| Update traceability links | `projects/<key>/traceability-matrix.md` | A | C | R | C | C | I | C | I | I | `Closed` |
| Run project audit | `projects/<key>/audit-log.md` | A | I | C | C | C | I | C | C | C | Audit cadence |

## Staffing and Training Gaps

| Gap ID | Missing Role or Skill | Impacted Activity | Risk Level (Low/Med/High) | Mitigation | Owner | Due Date | Status |
|---|---|---|---|---|---|---|---|
| GAP-001 |  |  |  |  |  |  | |

## Assignment for Current Quarter

| Workstream | Required Roles | Named Assignees | Coverage Status | Notes |
|---|---|---|---|---|
| Requirements and Analysis | Product, Analyst |  | Complete/Partial/Missing | |
| Solution and Decisions | Architect, Tech Lead |  | Complete/Partial/Missing | |
| Build and Test | Dev, QA |  | Complete/Partial/Missing | |
| Release and Operations | DevOps, QA, Tech Lead |  | Complete/Partial/Missing | |
| Governance and Audit | PM, Analyst, Architect |  | Complete/Partial/Missing | |

## Usage Notes

1. Copy this template into each project folder as `raci-skill-matrix.md`.
2. Fill the Role Catalog with actual names.
3. Score current vs target proficiency levels.
4. Confirm no activity has missing `A` or missing `R`.
5. Review and update at least once per quarter, or when major scope changes occur.
