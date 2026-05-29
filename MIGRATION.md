# Migration to Split Layout

This repository now supports a split layout to separate framework assets, runtime project data, and AI-agent assets.

## Canonical Paths

- `framework/` for reusable governance assets and templates
- `runtime/` for live portfolio and project data
- `agents/` for skills, prompts, and playbooks

## Compatibility for Existing Forks

To avoid breaking existing forks and scripts:

- `project-management/` is still present and remains usable.
- No destructive move or deletion was applied.
- Migration is additive and can be adopted incrementally.

## Current Mapping

- `project-management/templates` -> `framework/templates`
- `project-management/portfolio` -> `runtime/portfolio`
- `project-management/projects` -> `runtime/projects`
- `project-management/templates/skills` -> `agents/skills`

## Adoption Guidance

1. Use `runtime/*` for all new project artifacts.
2. Use `framework/templates/*` for all new template updates.
3. Use `agents/*` for prompt and skill evolution.
4. Keep legacy references until downstream forks have migrated.
