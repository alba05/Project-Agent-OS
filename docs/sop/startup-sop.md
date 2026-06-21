# Startup SOP

## Purpose

This SOP defines how to start a new project under Project-Agent-OS.

## Steps

### 1. Create The Project Workspace

Create a folder for one real project.

Inside it, create at minimum:

1. `knowledge-base/`
2. `sop/`
3. `thread-summaries/`
4. `scripts/`
5. `assets/` if needed
6. `deliverables/` if needed

### 2. Add The Project-Scoped Prompt

Use the prompt from:

`docs/system/project-scoped-agent-prompt.md`

This becomes the opening instruction for the main thread.

### 3. Initialize Memory

Create:

1. `knowledge-base/current-state.md`
2. `knowledge-base/open-loops.md`
3. `knowledge-base/decision-log.md`
4. `knowledge-base/sop-index.md`

### 4. Start The Main Thread

The main thread should:

1. Read the workspace files
2. Confirm current phase
3. Identify the next high-value action
4. Start producing reusable project artifacts

### 5. Add SOP Only When It Earns Its Place

Do not write SOP too early.

Write SOP when:

1. The task repeats
2. Quality drift matters
3. Another thread would benefit from fixed procedure

### 6. Create New Threads For Distinct Work Units

Examples:

1. Prompt system design
2. Visual exploration
3. Delivery operations
4. Review and QA

Each new thread should still write back to the same workspace memory.

### 7. Close The Session With Handoff

After meaningful progress:

1. Write a thread summary
2. Update current state if the phase shifted
3. Update open loops
4. Add or update SOP if a repeatable rule was discovered
