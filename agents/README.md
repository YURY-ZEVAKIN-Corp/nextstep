# Agent Assets

AI automation assets organized in a 4-tier artifact hierarchy (plus playbooks):

| Tier | Directory | Extension | Purpose |
|------|-----------|-----------|---------|
| Prompts | `prompts/` | `.prompt.md` | Workflow entry points — capture user intent, delegate to agents |
| Agents | `agents/` | `.agent.md` | Task-specific behaviors with subagent delegation and tool access |
| Instructions | `instructions/` | `.instructions.md` | Passive guidance auto-applied via glob patterns |
| Skills | `skills/` | `.skill.md` | On-demand process knowledge with progressive disclosure |
| Playbooks | `playbooks/` | `.playbook.md` | End-to-end multi-phase workflow orchestration |

**Delegation flow:** `User Request → Prompt → Agent → Instructions (auto-applied) / Skills (on-demand)`

For multi-phase delivery, see `playbooks/` which combine skills, agents, and gates into complete workflows.
