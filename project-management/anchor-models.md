# Anchor Models Mapping

This document maps the framework artifacts to their primary anchor models.

| Framework Element | Primary Anchor Model | Secondary Anchor Model | Notes |
|---|---|---|---|
| Backlog | Scrum / Kanban | SAFe-lite | Intake and prioritization of work |
| Requirement | PMBOK-style governance | Agile product management | Formalized, testable requirement after backlog refinement |
| Traceability Matrix | PMBOK-style governance | SAFe-lite | End-to-end visibility across delivery artifacts |
| Solution Document | SAFe-lite | TOGAF-lite | Solution intent and design rationale |
| Decision Record | ADR | TOGAF-lite | One significant decision per record |
| Decision Register | ADR governance | PMBOK-style governance | Index for conflict checks and oversight |
| Technology Stack | TOGAF-lite / Open Agile Architecture | ADR governance | Stack choices must link to decisions and Technology Radar checks |
| Implementation Plan | Agile delivery | PMBOK-style governance | Execution slicing and coordination |
| Test Plan | DevOps / quality governance | PMBOK-style governance | Validation before release |
| Release Record | DevOps / Continuous Delivery | PMBOK-style governance | Deployment evidence and follow-up |
| Project Audit | PMBOK-style governance | SAFe-lite | Detailed project control review |
| Portfolio Audit | SAFe-lite | PMBOK-style governance | Shared governance and portfolio controls |
| All Projects High-Level Audit | SAFe-lite | Agile portfolio management | Summary health review across active projects |
| Framework Audit | Process governance | PMBOK-style governance | Review of the framework itself |

## Usage Rule

Use this mapping when extending the framework:

- If the change affects intake or prioritization, validate it against Agile backlog practice.
- If the change adds control, validate it against lightweight governance principles.
- If the change affects stack or technical direction, validate it against ADR and architecture governance.
- If the change affects multi-project coordination, validate it against portfolio governance.
- If the change affects deployment flow, validate it against DevOps and continuous delivery.
