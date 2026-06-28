---
name: artifact-naming
description: Naming conventions for NextStep delivery artifacts
applyTo:
  - "runtime/projects/**/*.md"
  - "framework/templates/**/*.md"
---

## Artifact ID Format

`<PROJECT-KEY>-<PREFIX>-<###>-<short-kebab-name>.md`

| Prefix | Artifact |
|--------|----------|
| REQ | Requirement |
| SOL | Solution |
| IMP | Implementation Plan |
| TST | Test Plan |
| REL | Release Record |
| DEC | Decision Record |

Example: `SAMPLE-REQ-001-user-authentication.md`

## Backlog ID Format

`<PROJECT-KEY>-BL-<###>` — sequential, independent of REQ IDs.

## Status Model

`Draft` -> `Ready` -> `In Progress` -> `Blocked` -> `In Review` -> `Tested` -> `Deployed` -> `Closed`
