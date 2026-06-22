# Project-Agent-OS

Project-Agent-OS is a repo-native workflow for running long-lived project agents with stable memory, reusable SOPs, and thread handoff discipline.

Project-Agent-OS 是一套仓库级工作方法，用来把长期 AI 项目协作从“零散聊天记录”升级为“可续接、可写回、可复用的项目操作系统”。

It is designed for teams or solo operators who want to turn AI chats into a persistent project operating system instead of a pile of disconnected conversations.

它适合团队或个人操作者，用 `Agent + Workspace + Memory + SOP + Thread Handoff` 这套结构来运行长期项目。

## What This Repo Is

- A reusable repository-level operating methodology for long-lived AI project work
- A framework for turning thread work into durable project memory
- A meta-layer system, not a client project or brand workspace

## 这个仓库是什么

- 一套可复用的、仓库级 AI 项目运行方法
- 一种把线程工作写回为长期项目记忆的框架
- 一个方法论层，不是客户项目，也不是品牌执行工作区

## Core Formula / 核心公式

`Agent + Workspace + Memory + SOP + Thread Handoff`

Each project gets:

1. A dedicated workspace folder.
2. A project-scoped agent prompt.
3. A local memory structure.
4. Stable SOPs for repeatable work.
5. A handoff protocol across multiple threads.

简要理解：
先有工作区，再有项目级 Agent，再逐步把 memory、SOP 和 handoff 补齐，不需要一开始一次做完全部层。

## What This Solves / 解决的问题

Typical AI chat workflows break when:

1. Each new thread starts from zero.
2. Good decisions stay trapped in chat history.
3. SOPs are implicit and drift over time.
4. Multiple threads cannot coordinate around one project state.
5. Agents answer well but do not operate like durable collaborators.

Project-Agent-OS fixes that by making the repository itself the project memory surface.

Project-Agent-OS 通过把仓库本身变成项目记忆载体，来解决这些问题。

执行顺序上，通常先解决“信息不丢”和“线程可续接”，再逐步优化 SOP 和结构。

## System Layers / 系统层

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

简要顺序：
`Agent -> Workspace -> Memory -> SOP -> Thread Handoff`

也就是说，先让线程在正确边界内工作，再让结论沉淀，最后再解决跨线程续接。

## Repository Structure / 仓库结构

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

建议阅读顺序：
先读 `System Overview`，再读 `Project-Scoped Agent Prompt Spec`，然后看 `Memory Architecture` 和 `Thread Handoff Protocol`。

## Documentation Layers / 文档分层

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

简要理解：
`README` 负责总览，`docs/` 负责规则，`templates/` 负责起步，`examples/` 负责演示，不建议把四层混写在一起。

## Recommended Use Pattern / 推荐用法

1. Create one folder for one real project.
2. Start one main thread with the project-scoped agent prompt.
3. Spawn new threads for sub-projects, experiments, or deep work.
4. After meaningful progress, write back stable conclusions to memory and SOP.
5. Use handoff summaries to move work between threads without context loss.

大致执行顺序：
先开主线程，再做项目工作，再写回 memory，最后用 handoff 把上下文交给后续线程。

## Example Layer / 示例层

The repository includes optional examples to show how the method can be applied in a real domain.

仓库包含可选示例层，用来展示这套方法如何落到真实领域。

Current example:

- [AI Music Project Example](C:/Users/Administrator/Documents/Project-Agent-OS/examples/ai-music-project/README.md)

Rule:

1. Examples help demonstrate the method.
2. Examples do not redefine the method.
3. Heavy operational sample assets can remain local by default and do not need to enter the public repository automatically.

简要说明：
先有方法论，再有示例；示例是帮助理解，不是反过来决定主仓库应该长成什么样。

## AI Music Fit / 为什么适合 AI 音乐

This framework works especially well for AI music projects because they often involve:

1. Repeated generation and review loops.
2. Prompt iteration across multiple tools and models.
3. Asset accumulation across lyrics, structure, vocals, cover, packaging, and delivery.
4. Tight separation between internal experiments and public-facing outputs.

The included example project is generic AI music infrastructure, not tied to any specific brand.

AI music is an example application area, not the repository identity.

简要说明：
这里可以从 AI 音乐切入理解方法，但不要把仓库误认为“只服务 AI 音乐”的项目。

## First Run / 快速开始

1. Read [System Overview](C:/Users/Administrator/Documents/Project-Agent-OS/docs/system/system-overview.md).
2. Copy the prompt from [Project-Scoped Agent Prompt Spec](C:/Users/Administrator/Documents/Project-Agent-OS/docs/system/project-scoped-agent-prompt.md).
3. Create your project folder using [Workspace Blueprint](C:/Users/Administrator/Documents/Project-Agent-OS/templates/workspace-blueprint.md).
4. Initialize memory files from [Memory Templates](C:/Users/Administrator/Documents/Project-Agent-OS/templates/memory-templates.md).
5. Start working and keep handoff summaries in sync.

最简顺序：
先看系统说明，再建工作区，再初始化 memory，然后开始工作，最后保持 handoff 更新。

## Meta Repository Memory / 元仓库自用记忆

This repository now uses its own `knowledge-base/` and `thread-summaries/` so the methodology is also applied to the repository itself.

这个元仓库已经开始自用自己的 memory 结构，避免“方法论只要求示例项目使用，自己却不使用”。

简要说明：
如果某条规则已经影响后续线程，就优先写回本仓库 memory，而不是只留在聊天里。

## Principle / 原则

The goal is not to make the assistant sound smart.

The goal is to make project progress durable.

一句话理解：
优先让项目可持续推进，其次才是让单次回答看起来完整或漂亮。
