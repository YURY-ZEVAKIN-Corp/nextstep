# NextStep

NextStep is a lightweight framework for governing software delivery across multiple projects from idea to production.

It is designed to help you:

- capture and refine requirements;
- review each new requirement with a checklist;
- calculate business value for each requirement;
- govern each project's technology stack through decisions;
- turn requirements into solution designs;
- implement work in small, traceable increments;
- plan and track iterative delivery through sprints;
- test changes before release;
- deploy safely and record what was shipped.

## Methodology Positioning

This is a hybrid framework rather than a copy of one existing methodology.

It combines:

- Agile and Scrum-style backlog management for work intake and prioritization
- PMI or PMBOK-style governance for traceability, control points, and audits
- ADR-based architecture governance for technical and stack decisions
- SAFe-like portfolio coordination for multi-project oversight
- DevOps and continuous delivery thinking for implementation, testing, and deployment

Recommended interpretation:

- Delivery anchor: Scrum or Kanban
- Architecture anchor: ADR plus TOGAF-lite or Open Agile Architecture
- Portfolio anchor: SAFe-lite
- Control anchor: PMBOK-style traceability and audit discipline
- Release anchor: DevOps and continuous delivery

NextStep is best suited for teams that need both delivery flow and governance, especially when working across multiple software projects.

## Structure

```text
project-management/
  README.md
  portfolio/
    roadmap.md
    project-register.md
    dependency-log.md
    standards.md
  projects/
    sample-project/
      backlog.md
      sprints.md
      roadmap.md
      traceability-matrix.md
      requirements/
      solutions/
      implementation/
      testing/
      releases/
      decisions/
  templates/
    requirement-template.md
    solution-template.md
    implementation-plan-template.md
    sprint-template.md
    test-plan-template.md
    release-template.md
    decision-template.md
    project-charter-template.md
```

## Recommended Workflow

1. Create a requirement in `project-management/projects/<project-key>/requirements/`.
2. Link that requirement in `project-management/projects/<project-key>/traceability-matrix.md`.
3. Create a solution document in `project-management/projects/<project-key>/solutions/`.
4. Break the work into implementation tasks in `project-management/projects/<project-key>/implementation/`.
5. Assign and plan implementation work in `project-management/projects/<project-key>/sprints.md`.
6. Define test coverage in `project-management/projects/<project-key>/testing/`.
7. Record the deployment and outcome in `project-management/projects/<project-key>/releases/`.

## How to Start

Fork this framework and start your own project using Codex, Gemini CLI, Copilot CLI, or Claude Code.


