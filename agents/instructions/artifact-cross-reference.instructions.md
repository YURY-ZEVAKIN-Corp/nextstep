---
name: artifact-cross-reference
description: Cross-referencing rules for traceability continuity
applyTo:
  - "runtime/projects/**/*.md"
---

## Cross-Reference Rules

Every artifact MUST include a `Links` or references section that traces to related artifacts:

- **REQ** — links to backlog item, traceability matrix
- **SOL** — links to REQ ID(s), technology stack, decisions
- **IMP** — links to SOL ID, REQ ID, DEC ID(s)
- **TST** — links to REQ ID, SOL ID, IMP ID
- **REL** — links to IMP ID, TST ID
- **DEC** — links to impacted artifacts

Every project MUST maintain a `traceability-matrix.md` that indexes all artifacts.

## Business Value Metric

`Business Value Score = Reach × Impact × Confidence`

Record in requirement artifacts and traceability matrix.
