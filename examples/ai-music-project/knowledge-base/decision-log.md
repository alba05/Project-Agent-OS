# Decision Log

## 2026-06-22

- Decision: Use a project-scoped agent model instead of generic chat behavior.
- Why: AI music work accumulates prompts, assets, and review logic that need durable local memory.
- Impact: Future threads must read local project context before acting.
