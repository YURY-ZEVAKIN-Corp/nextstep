# NextStep Operating Model

> Legacy-compatible path notice: `project-management/` remains supported for existing forks.
> Canonical structure for new work is split into `framework/`, `runtime/`, and `agents/`.

This framework supports multiple projects under one portfolio.

## Anchor Model Alignment

This framework is a hybrid operating model. It is intentionally aligned to a small set of anchor models so teams can understand which practices come from where.

### Anchor Models

- `Scrum / Kanban`: backlog management, prioritization, iterative delivery flow
- `PMBOK-style governance`: traceability, review gates, audit discipline
- `ADR-based architecture governance`: decision records and decision registers
- `SAFe-lite`: multi-project and portfolio coordination
- `DevOps / Continuous Delivery`: implementation, testing, deployment, and release feedback
- `TOGAF-lite / Open Agile Architecture`: governed technology stack and architecture oversight

### How To Interpret The Framework

- Delivery anchor: `Scrum` or `Kanban`
- Architecture anchor: `ADR` plus `TOGAF-lite / Open Agile Architecture`
- Portfolio anchor: `SAFe-lite`
- Control anchor: `PMBOK-style traceability and audits`
- Release anchor: `DevOps / Continuous Delivery`

### Mapping Rules

- Backlog and prioritization rules should stay consistent with Agile backlog practices.
- Traceability, checklists, and audits should stay consistent with lightweight governance, not heavyweight stage-gate bureaucracy.
- Technical and stack choices should be captured through decision records, not hidden inside implementation plans.
- Portfolio controls should coordinate projects, not replace project-level delivery ownership.
- Release and deployment controls should support continuous delivery and fast feedback.

### Tailoring Rule

Not every project needs every practice at the same depth.

- Small projects may use lighter solution, testing, and release artifacts.
- High-risk or multi-team projects should use the full governance model.
- Portfolio governance should scale with the number of active projects and cross-project dependencies.

## Structure

### Portfolio Level

Use the `portfolio/` folder for cross-project visibility:

- `project-register.md`: list of active projects
- `roadmap.md`: portfolio priorities and sequencing
- `dependency-log.md`: dependencies between projects
- `standards.md`: shared governance and delivery rules
- `decision-register.md`: index of shared decisions
- `decisions/`: shared portfolio decisions using `SHARED-DEC-###-short-name.md`
- `audit-schedule.md`: portfolio audit calendar
- `audit-log.md`: portfolio audit history

### Project Level

Each project lives under `projects/<project-key>/`.

Each project contains its own:

- project charter
- technology stack
- decision register
- audit log
- backlog
- sprint plan
- roadmap
- traceability matrix
- requirements
- solutions
- implementation plans
- test artifacts
- release records
- decision records

This framework uses six artifact types inside each project:

- `REQ`: business or user requirement
- `SOL`: proposed solution for one or more requirements
- `IMP`: implementation plan or execution slice
- `TST`: test plan or test report
- `REL`: deployment or release record
- `DEC`: decision record with explicit type (for example `Architecture Decision Record (ADR)`, product, or process)

In addition, each project maintains a technology stack document that summarizes selected technologies and links each choice to one or more decision records.
Each project also maintains a backlog as the intake source for future requirements.

## Status Model

Use these statuses consistently:

- `Draft`
- `Ready`
- `In Progress`
- `Blocked`
- `In Review`
- `Tested`
- `Deployed`
- `Closed`

## Delivery Flow

### 0. Backlog

Each project must maintain a backlog in `projects/<project-key>/backlog.md`.

The backlog is the intake layer for:

- ideas;
- feature requests;
- defects;
- technical improvements;
- research items;
- operational work.

Every new piece of work should enter the framework through the backlog before it becomes a formal requirement, unless it is an emergency production issue.

Backlog items should include:

- a unique backlog ID;
- title;
- work type;
- priority;
- status;
- source or requester;
- assigned team member;
- short value statement;
- next action.
- target sprint or `Unscheduled`.

Definition of Ready gate for backlog items:

- clear description and business value;
- defined acceptance criteria;
- size estimate;
- identified dependencies;
- understood test approach;
- no blocking open questions.

If any Definition of Ready criterion is missing, the backlog item stays `Draft` and must not be promoted to requirement creation.

Recommended flow:

`Backlog -> Requirement -> Solution -> Decision -> Implementation -> Sprint -> Test -> Release`

### Sprint Planning

Each project must maintain a sprint plan in `projects/<project-key>/sprints.md`.

Sprints are timeboxed delivery iterations used to:

- commit a prioritized subset of ready backlog and implementation work;
- align ownership and capacity for a short window;
- track sprint goal, scope changes, and outcome.

Each sprint entry should include:

- sprint ID and date window;
- sprint goal;
- committed items;
- in-sprint changes;
- sprint outcome and carryover.

### 1. Requirements

Each requirement should answer:

- what problem exists;
- who is affected;
- what outcome is needed;
- what quantified business value it creates;
- how success will be measured;
- what is out of scope.

Store requirements in `projects/<project-key>/requirements/` using `<PROJECT>-REQ-###-short-name.md`.

Before a requirement can move from `Draft` to `Ready`, it must pass the requirement checklist in `templates/requirement-checklist.md`.
Each requirement must also include a calculated business value metric.

### 2. Solutions

Each solution should link back to one or more requirements and describe:

- approach;
- system impact;
- risks;
- alternatives;
- rollout approach.

Store solutions in `projects/<project-key>/solutions/` using `<PROJECT>-SOL-###-short-name.md`.

Solutions must align with the approved project technology stack or explicitly propose a change through a new decision record.
Solutions that introduce, change, or depend on major technologies must also be checked against the Technology Radar before approval.

### 3. Implementation

Implementation plans break a solution into executable work:

- milestones;
- dependencies;
- owners;
- task checklist;
- done criteria.

Store implementation plans in `projects/<project-key>/implementation/` using `<PROJECT>-IMP-###-short-name.md`.

### 4. Testing

Testing should be defined before release:

- acceptance checks;
- functional tests;
- regression scope;
- non-functional checks where needed.

Store test artifacts in `projects/<project-key>/testing/` using `<PROJECT>-TST-###-short-name.md`.

### 5. Release and Deployment

Every deployment should record:

- what changed;
- what was tested;
- rollback plan;
- deployment result;
- follow-up actions.

Store release notes in `projects/<project-key>/releases/` using `<PROJECT>-REL-###-short-name.md`.

### 6. Decisions

Capture important product and technical decisions so context is not lost.

Store decisions in `projects/<project-key>/decisions/` using `<PROJECT>-DEC-###-short-name.md`.
Store shared cross-project decisions in `portfolio/decisions/` using `SHARED-DEC-###-short-name.md`.

Before a decision can move to `Accepted`, it must pass the decision checklist in `templates/decision-checklist.md`.

### 7. Technology Stack

Each project must maintain a technology stack document in `projects/<project-key>/technology-stack.md`.

The technology stack should define the selected technologies for areas such as:

- frontend;
- backend;
- database;
- infrastructure;
- CI/CD;
- testing;
- observability;
- security;
- integrations.

Each stack choice must reference at least one decision record that explains why it was selected.
Each major stack choice must also record its Technology Radar assessment.

## Core Rules

- Every project must maintain a backlog.
- Every project must maintain a sprint plan.
- Every new candidate work item should be recorded in the backlog before requirement creation.
- Every backlog item must have a named team-member assignee.
- Every backlog item must include a target sprint or be marked `Unscheduled`.
- Every backlog item must satisfy the Definition of Ready before it can move to `Ready`.
- Team members may be assigned across multiple projects.
- Every new `REQ` must be checked against the requirement checklist before approval.
- Every new `REQ` must include a calculated business value metric.
- Every project must maintain a technology stack document.
- Every major technology choice must be linked to a `DEC` record.
- Every major technology choice must be checked against the Technology Radar.
- Every new `DEC` must be checked against the decision checklist before acceptance.
- Every project must maintain a decision register.
- Every project must be reviewed on a scheduled audit cadence.
- Every scheduled audit must use the audit checklist.
- Every `SOL` must reference at least one `REQ`.
- Every `IMP` must reference at least one `SOL`.
- Every `TST` must reference the `REQ`, `SOL`, and `IMP` it validates.
- Every `REL` must reference the implementation and test artifacts used for the release.
- Update the project `traceability-matrix.md` whenever a new artifact is created.

## Business Value Metric

Use a simple weighted score for each requirement:

`Business Value Score = Reach x Impact x Confidence`

Where:

- `Reach`: number of users, transactions, or teams affected in a defined time period
- `Impact`: expected benefit on a 1-5 scale
- `Confidence`: certainty of the estimate on a 0.2-1.0 scale

Example:

- Reach: `500 users per month`
- Impact: `4`
- Confidence: `0.8`
- Business Value Score: `500 x 4 x 0.8 = 1600`

You can adapt the inputs later, but every requirement should use one consistent formula.

## Technology Governance

Use the following flow:

1. Record the problem or constraint.
2. Create a decision record for the technology choice.
3. Check the proposed technology against the Technology Radar.
4. Run the decision checklist, including conflict check and triage.
5. Update the project technology stack document with the selected tool, decision link, and radar assessment.
6. Update the relevant decision register.
7. Ensure solutions and implementation plans follow the approved stack.

## Scheduled Audit

Use scheduled audits to verify that each project still follows the framework.

Recommended cadence:

- project audit: every 2 weeks
- portfolio audit: monthly
- all-projects high-level audit: monthly or quarterly
- framework audit: monthly or after major framework changes

Audit outputs should be recorded in:

- `projects/<project-key>/audit-log.md`
- `portfolio/audit-log.md`
- `portfolio/all-projects-audit-log.md`
- `portfolio/framework-audit-log.md`

Every audit must use `templates/audit-checklist.md`.
The all-projects high-level audit must use `templates/all-projects-audit-checklist.md`.
The framework audit must use `templates/framework-audit-checklist.md`.

The audit taxonomy is defined in `templates/audit-model.md`.

## Framework Audit

Use a framework audit to review the governance system itself.

The framework audit should check:

- internal consistency of templates, standards, and process rules;
- conflicts between framework rules;
- missing traceability between framework artifacts;
- outdated or duplicated governance guidance;
- whether audit rules themselves remain coherent and usable.

The goal is to ensure the framework does not become self-contradictory as it evolves.

### Audit Type Separation

- `Project audit`: one project, detailed compliance review
- `Portfolio audit`: portfolio-level governance controls and shared artifacts
- `All-projects high-level audit`: summary health review across all active projects
- `Framework audit`: the framework itself

## Lightweight Weekly Cadence

- Review backlog intake and promote ready items into requirements.
- Review new requirements.
- Approve or reject solutions.
- Check implementation progress and blockers.
- Review test results.
- Review deployment readiness.
- Review cross-project dependencies and portfolio priorities.

## Suggested Artifact Sequence

1. `AUTH-IDEA-001` in `backlog.md`
2. `AUTH-REQ-001-user-authentication.md`
3. `AUTH-SOL-001-user-authentication.md`
4. `AUTH-DEC-001-backend-framework.md`
5. `AUTH-IMP-001-user-authentication.md`
6. `AUTH-TST-001-user-authentication.md`
7. `AUTH-REL-001-user-authentication.md`
