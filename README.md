# Project-Agent-OS

Project-Agent-OS is a repo-native workflow for running long-lived project agents with stable memory, reusable SOPs, and thread handoff discipline.

Project-Agent-OS 是一套仓库级工作方法，用来把长期 AI 项目协作从“零散聊天记录”升级为“可续接、可写回、可复用的项目操作系统”。

It is designed for teams or solo operators who want to turn AI chats into a persistent project operating system instead of a pile of disconnected conversations.

它适合团队或个人操作者，用 `Agent + Workspace + Memory + SOP + Thread Handoff` 这套结构来运行长期项目。

## Core Formula

`Agent + Workspace + Memory + SOP + Thread Handoff`

Each project gets:

1. A dedicated workspace folder.
2. A project-scoped agent prompt.
3. A local memory structure.
4. Stable SOPs for repeatable work.
5. A handoff protocol across multiple threads.

## What This Solves

Typical AI chat workflows break when:

1. Each new thread starts from zero.
2. Good decisions stay trapped in chat history.
3. SOPs are implicit and drift over time.
4. Multiple threads cannot coordinate around one project state.
5. Agents answer well but do not operate like durable collaborators.

Project-Agent-OS fixes that by making the repository itself the project memory surface.

## System Layers

1. `Agent`
   The active execution role for the current thread.
2. `Workspace`
   The project folder and its owned files, assets, scripts, and docs.
3. `Memory`
   Stable summaries, current state, open loops, and key decisions.
4. `SOP`
   Repeatable operating procedures for recurring tasks.
5. `Thread Handoff`
   Structured summaries that let a new thread continue without re-learning everything.

## Repository Structure

```text
docs/
  memory/
  handoff/
  sop/
  system/
templates/
examples/
  ai-music-project/
```

See:

- [System Overview](C:/Users/Administrator/Documents/Project-Agent-OS/docs/system/system-overview.md)
- [Methodology Glossary](C:/Users/Administrator/Documents/Project-Agent-OS/docs/system/methodology-glossary.md)
- [GitHub Strategy](C:/Users/Administrator/Documents/Project-Agent-OS/docs/system/github-strategy.md)
- [Repository Roadmap](C:/Users/Administrator/Documents/Project-Agent-OS/docs/system/repository-roadmap.md)
- [Issue And Milestone Guide](C:/Users/Administrator/Documents/Project-Agent-OS/docs/system/issue-milestone-guide.md)
- [Project-Scoped Agent Prompt Spec](C:/Users/Administrator/Documents/Project-Agent-OS/docs/system/project-scoped-agent-prompt.md)
- [Memory Architecture](C:/Users/Administrator/Documents/Project-Agent-OS/docs/memory/memory-architecture.md)
- [Thread Handoff Protocol](C:/Users/Administrator/Documents/Project-Agent-OS/docs/handoff/thread-handoff-protocol.md)
- [Startup SOP](C:/Users/Administrator/Documents/Project-Agent-OS/docs/sop/startup-sop.md)

## Documentation Layers

1. `README.md`
   GitHub-facing overview of what the system is and how to start.
2. `docs/system/`
   Core methodology, definitions, and base operating logic.
3. `docs/memory/`, `docs/sop/`, `docs/handoff/`
   Detailed rules for each durable system layer.
4. `templates/`
   Reusable starter files for new project workspaces.
5. `examples/`
   Optional example projects that show one application of the method without redefining it.

For public repository positioning and GitHub evolution rules, see [GitHub Strategy](C:/Users/Administrator/Documents/Project-Agent-OS/docs/system/github-strategy.md).

For repository phase planning and issue structure, see [Repository Roadmap](C:/Users/Administrator/Documents/Project-Agent-OS/docs/system/repository-roadmap.md) and [Issue And Milestone Guide](C:/Users/Administrator/Documents/Project-Agent-OS/docs/system/issue-milestone-guide.md).

## Recommended Use Pattern

1. Create one folder for one real project.
2. Start one main thread with the project-scoped agent prompt.
3. Spawn new threads for sub-projects, experiments, or deep work.
4. After meaningful progress, write back stable conclusions to memory and SOP.
5. Use handoff summaries to move work between threads without context loss.

## AI Music Fit

This framework works especially well for AI music projects because they often involve:

1. Repeated generation and review loops.
2. Prompt iteration across multiple tools and models.
3. Asset accumulation across lyrics, structure, vocals, cover, packaging, and delivery.
4. Tight separation between internal experiments and public-facing outputs.

The included example project is generic AI music infrastructure, not tied to any specific brand.

AI music is an example application area, not the repository identity.

## First Run

1. Read [System Overview](C:/Users/Administrator/Documents/Project-Agent-OS/docs/system/system-overview.md).
2. Copy the prompt from [Project-Scoped Agent Prompt Spec](C:/Users/Administrator/Documents/Project-Agent-OS/docs/system/project-scoped-agent-prompt.md).
3. Create your project folder using [Workspace Blueprint](C:/Users/Administrator/Documents/Project-Agent-OS/templates/workspace-blueprint.md).
4. Initialize memory files from [Memory Templates](C:/Users/Administrator/Documents/Project-Agent-OS/templates/memory-templates.md).
5. Start working and keep handoff summaries in sync.

## Meta Repository Memory

This repository now uses its own `knowledge-base/` and `thread-summaries/` so the methodology is also applied to the repository itself.

这个元仓库已经开始自用自己的 memory 结构，避免“方法论只要求示例项目使用，自己却不使用”。

## Principle

The goal is not to make the assistant sound smart.

The goal is to make project progress durable.
