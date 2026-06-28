# Migration to Split Layout

This repository now supports a split layout to separate framework assets, runtime project data, and AI-agent assets.

## Canonical Paths

- `framework/` for reusable governance assets and templates
- `runtime/` for live portfolio and project data
- `agents/` for AI automation assets (4-tier artifact system)

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

## Agent Artifact System (`agents/`)

The `agents/` directory uses a 4-tier artifact hierarchy (plus playbooks):

| Tier | Directory | Extension | Purpose |
|------|-----------|-----------|---------|
| Prompts | `agents/prompts/` | `.prompt.md` | Workflow entry points — capture user intent, delegate to agents |
| Agents | `agents/agents/` | `.agent.md` | Task-specific behaviors with subagent delegation and tool access |
| Instructions | `agents/instructions/` | `.instructions.md` | Passive guidance auto-applied via glob patterns |
| Skills | `agents/skills/` | `.skill.md` | On-demand process knowledge with progressive disclosure |
| Playbooks | `agents/playbooks/` | `.playbook.md` | End-to-end multi-phase workflow orchestration |

Delegation flow: `User Request -> Prompt -> Agent -> Instructions (auto-applied) / Skills (on-demand)`

For multi-phase delivery, see `agents/playbooks/` which combine skills, agents, and gates into complete workflows.

## Adoption Guidance

1. Use `runtime/*` for all new project artifacts.
2. Use `framework/templates/*` for all new template updates.
3. Use `agents/{prompts,agents,instructions,skills}/*` for all new agent assets.
4. Keep legacy references until downstream forks have migrated.
