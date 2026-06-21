# Methodology Glossary

## Purpose

This glossary defines the stable terms used across Project-Agent-OS so the repository can be operated consistently across multiple threads, projects, and contributors.

## Core Terms

### Project-Agent-OS

The repository-level operating methodology for running long-lived AI project work through:

`Agent + Workspace + Memory + SOP + Thread Handoff`

It is a reusable system layer, not a client project.

### Project-Scoped Agent

An execution agent bound to one workspace for one project context.

It should:

1. Read local context before acting.
2. Make the smallest correct next move.
3. Write stable conclusions back into repository files.

### Workspace

The owned project environment for one real project.

The workspace contains the project files, assets, scripts, SOPs, and memory that define the current operating reality.

### Memory

The durable project context stored in local files rather than chat history.

Memory exists to preserve continuity across threads and time.

### Knowledge Base

The compact memory surface inside a workspace.

In the base pattern, it includes:

1. `current-state.md`
2. `open-loops.md`
3. `decision-log.md`
4. `sop-index.md`

### Current State

A short description of the project's present phase, main line of work, and currently stable conclusions.

### Open Loops

The active unfinished work, pending decisions, and next recommended step.

### Decision Log

A compact log of decisions that should not be silently re-decided in later threads.

### SOP

Standard operating procedure for repeated work where drift is costly.

SOP should capture how a recurring task is done, not everything that happened in one thread.

### SOP Index

The list of SOP files the workspace currently relies on.

It helps a new thread discover which procedures are already stable.

### Thread Summary

A thread-specific record of meaningful work completed, stable conclusions, important files, open loops, and recommended next step.

Thread summaries are the bridge between chat activity and durable project memory.

### Thread Handoff

The protocol used to let a future thread continue work with minimal re-explanation.

Handoff is thread-specific. Memory is project-wide.

### Stable Conclusion

A conclusion that is reliable enough to be reused by future work without needing to be rediscovered from chat.

Stable conclusions belong in memory, SOP, templates, or repository docs.

### Writeback

The act of converting stable conclusions from thread work into local repository files.

Writeback is what turns a useful thread into durable project progress.

## Repository Layers

### Core Methodology

The reusable operating model, definitions, and base templates that apply across projects.

In this repository, that primarily lives in:

1. `README.md`
2. `docs/`
3. `templates/`

### Optional Examples

Illustrative project folders that show how the system can be applied in a domain without redefining the core method.

In this repository, `examples/ai-music-project/` is an example layer, not the system identity.

### Sample Layer

A lighter-weight layer for temporary or operational samples produced by auxiliary threads.

Sample-layer outputs are useful for validation, reference, or review, but should not automatically be treated as stable repository method.

They should remain in sample or example space until reviewed by the main thread.

### Temporary Experiments

Exploratory materials, trials, or drafts that may inform the methodology later but are not yet part of the stable operating system.

Temporary experiments should not be mistaken for core rules until their conclusions are written back into durable docs or templates.

## Relationship Map

```text
Project-Agent-OS
  -> project-scoped agent operates inside one workspace
  -> workspace stores project memory and SOP
  -> thread work produces stable conclusions
  -> stable conclusions are written back
  -> handoff lets the next thread continue with less drift
```

## Decision Rule

If a term affects how future threads should interpret the repository, define it in the docs instead of leaving it implicit in chat.
