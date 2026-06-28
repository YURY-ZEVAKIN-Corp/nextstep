---
name: new-feature-delivery
description: End-to-end delivery of a new feature from backlog intake to release
phases:
  - intake
  - requirements
  - solution
  - implementation
  - testing
  - release
---

# New Feature Delivery Playbook

## Overview

End-to-end workflow for delivering a new feature through the full governance lifecycle, from initial backlog intake through release.

## Entry Point

`agents/prompts/full-delivery-flow.prompt.md`

## Phases

### 1. Intake

| Step | Skill | Agent | Artifact |
|------|-------|-------|----------|
| Capture work item | `backlog-intake.skill.md` | `backlog-agent.agent.md` | `runtime/projects/<key>/backlog.md` |
| Classify and prioritize | — | `backlog-agent` | Backlog entry with ID, type, priority |

**Handoff:** `backlog-agent` → `requirement-agent` when status moves to `Ready`

### 2. Requirements

| Step | Skill | Agent | Artifact |
|------|-------|-------|----------|
| Create requirement | `requirement-management.skill.md` | `requirement-agent.agent.md` | `runtime/projects/<key>/requirements/` |
| Run quality checklist | — | `requirement-agent` | Checklist in `framework/templates/requirement-checklist.md` |
| Link in traceability matrix | — | `requirement-agent` | `runtime/projects/<key>/traceability-matrix.md` |

**Gate:** Requirement must pass checklist before advancing to `Ready` status.

### 3. Solution Design

| Step | Skill | Agent | Artifact |
|------|-------|-------|----------|
| Design solution | `solution-design.skill.md` | `solution-agent.agent.md` | `runtime/projects/<key>/solutions/` |
| Capture decisions | `decision-management.skill.md` | `decision-agent.agent.md` | `runtime/projects/<key>/decisions/` |
| Update traceability | — | `solution-agent` | Updated matrix links |

### 4. Implementation

| Step | Skill | Agent | Artifact |
|------|-------|-------|----------|
| Plan implementation | `implementation-planning.skill.md` | `implementation-agent.agent.md` | `runtime/projects/<key>/implementation/` |
| Assign tasks and dependencies | — | `implementation-agent` | Task breakdown with owners |

### 5. Testing

| Step | Skill | Agent | Artifact |
|------|-------|-------|----------|
| Define test plan | `testing-management.skill.md` | `testing-agent.agent.md` | `runtime/projects/<key>/testing/` |
| Execute and record | — | `testing-agent` | Test evidence |

**Gate:** All acceptance criteria must pass; critical defects resolved.

### 6. Release

| Step | Skill | Agent | Artifact |
|------|-------|-------|----------|
| Create release record | `release-management.skill.md` | `release-agent.agent.md` | `runtime/projects/<key>/releases/` |
| Deploy and verify | — | `release-agent` | Deployment outcome |

## Orchestration

The `delivery-orchestrator.agent.md` coordinates the full flow, managing handoffs between agents and enforcing phase gates.

## Quality Gates

1. **Intake → Requirements:** Backlog item is `Ready` with priority and value statement
2. **Requirements → Solution:** Requirement checklist passes
3. **Solution → Implementation:** Decision records are accepted
4. **Implementation → Testing:** Tasks are complete with done criteria met
5. **Testing → Release:** All tests pass, no critical defects
6. **Release → Closed:** Post-deploy checks pass

## Instructions Applied

- `artifact-naming.instructions.md` — ensures all artifact IDs follow `<KEY>-<PREFIX>-<###>` format
- `artifact-cross-reference.instructions.md` — maintains traceability links across artifacts
- `markdown-style.instructions.md` — consistent document formatting
