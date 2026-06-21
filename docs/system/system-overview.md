# System Overview

## Definition

Project-Agent-OS is a project operating model where an AI agent is bound to a workspace and continuously grounded by local memory, SOPs, and handoff files.

It treats the repository as the persistent execution surface.

For stable terminology, see `docs/system/methodology-glossary.md`.

## The Five Components

### 1. Agent

The agent is not a generic assistant. It is a project-scoped execution role.

Its job is to:

1. Read local context before acting.
2. Prefer the smallest correct next move.
3. Convert stable progress into reusable artifacts.
4. Distinguish between internal material and public output.

### 2. Workspace

The workspace is the boundary of responsibility.

It contains:

1. Docs
2. Scripts
3. Assets
4. SOP
5. Knowledge base
6. Thread summaries

A thread should behave as if it is operating inside one owned project environment, not floating across unrelated tasks.

### 3. Memory

Memory is the durable layer between chat sessions.

It should capture:

1. Current state
2. Open loops
3. Key decisions
4. Stable summaries
5. Cross-thread consensus

Memory is not raw transcript storage.

### 4. SOP

SOP turns repeated work into stable procedure.

SOP should exist whenever a task repeats often enough that drift is costly, such as:

1. Prompt packaging
2. Generation review
3. Delivery formatting
4. Batch tracking
5. Repository closeout

### 5. Thread Handoff

Thread handoff is the mechanism that lets one thread stop and another continue without losing project state.

A good handoff includes:

1. What was done
2. What is stable
3. What remains open
4. What files matter
5. What not to re-decide unless necessary

## Operating Model

```text
Project folder
  -> project-scoped prompt
  -> active thread executes
  -> stable output written back to memory/SOP/docs/templates
  -> new thread reads memory/SOP
  -> work continues with less drift
```

## Why This Matters

Without a system like this, AI project work usually becomes:

1. Chat-centric
2. Context-fragile
3. Hard to review
4. Hard to resume
5. Hard to scale across threads

With Project-Agent-OS, the project becomes the source of truth and the thread becomes a temporary worker attached to it.
