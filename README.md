# NextStep

NextStep is a lightweight framework for governing software delivery across multiple projects from idea to production.

## Why This Framework Matters for AI-Driven Development

Traditional delivery systems (for example, Jira-based processes) were designed for human interaction, not autonomous AI execution. They rely on manual updates, UI-driven workflows, and unstructured project context.

AI-driven development requires direct, reliable, and permissioned access to project data so agents can operate as contributors, not just assistants. To support that, teams need a machine-first framework that enables AI agents to read, update, and correlate delivery data across requirements, tasks, code, tests, and incidents.

This framework provides that foundation through structured artifacts, governed changes, end-to-end traceability, and report generation from live project state.

Without this layer, AI remains advisory. With it, AI can participate in planning, delivery, and reporting as an operational execution layer.

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

## The 5 Levels of STLC AI Maturity

Organizations scale from ad-hoc usage to fully autonomous quality assurance systems.

**Traditionalist (Level 1)**
State: Zero to minimal AI usage. Testing is heavily manual or relies entirely on static, human-written scripts.

**AI-Supported (Level 2)**
State: Ad-hoc AI use. Teams use LLMs for basic prompt-based test case generation or minor automation assistance.

**AI-Assisted (Level 3)**
State: Structured AI workflows within teams. AI scans requirements for gaps, generates automated test suites, and flags inconsistencies.

**AI-Native (Level 4)**
State: Integrated, pipeline-wide AI. AI-driven self-healing automatically fixes scripts when UI elements change, while predictive analytics triage bugs and determine release readiness.

**AI-Autonomous (Level 5)**
State: Continuous, self-optimizing quality ecosystem. AI agents independently reason, identify edge cases, execute tests, and analyze defects with minimal human intervention.

### Estimated Level for This Framework

Based on the current repository structure and governance assets, this framework is best positioned at **AI-Assisted (Level 3)**.

It already supports structured, machine-readable delivery workflows (requirements, traceability, testing plans, releases, decisions), which is the foundation for consistent AI-assisted QA and testing orchestration. To reach Level 4, it would need deeper pipeline-native automation such as self-healing test execution and predictive release gates integrated directly into CI/CD.

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

Example projects are available in [YuryZevakin/nextstep-KeyStone](https://github.com/YuryZevakin/nextstep-KeyStone).


