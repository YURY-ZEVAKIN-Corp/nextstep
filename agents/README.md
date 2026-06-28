# Agent Assets

AI automation assets organized in a 4-tier artifact hierarchy:

| Tier | Directory | Extension | Purpose |
|------|-----------|-----------|---------|
| Prompts | `prompts/` | `.prompt.md` | Workflow entry points — capture user intent, delegate to agents |
| Agents | `agents/` | `.agent.md` | Task-specific behaviors with subagent delegation and tool access |
| Instructions | `instructions/` | `.instructions.md` | Passive guidance auto-applied via glob patterns |
| Skills | `skills/` | `.skill.md` | On-demand process knowledge with progressive disclosure |

**Delegation flow:** `User Request → Prompt → Agent → Instructions (auto-applied) / Skills (on-demand)`
