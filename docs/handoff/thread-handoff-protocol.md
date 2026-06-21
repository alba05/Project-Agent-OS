# Thread Handoff Protocol

## Goal

A new thread should be able to continue real work with minimal re-explanation.

## When To Write A Handoff

Write a handoff when:

1. A work session ends after meaningful progress.
2. A subproject is being moved to another thread.
3. The thread accumulated non-trivial decisions or constraints.
4. A future continuation would otherwise lose momentum.

## Required Sections

Each handoff should contain:

1. Thread ID or label
2. Objective
3. Work completed
4. Stable conclusions
5. Important files
6. Open loops
7. Next recommended action

## Handoff Quality Rules

1. Do not paste raw chat logs.
2. Do not describe every micro-step.
3. Do state what has already been decided.
4. Do state what should not be re-opened without reason.
5. Do point to the exact files that matter.

## Minimal Template

```text
# Thread Handoff

## Objective

## Completed

## Stable Conclusions

## Important Files

## Open Loops

## Next Step
```

## Relationship To Memory

Thread handoff is not the same as the full memory layer.

1. Handoff is thread-specific.
2. Memory is project-wide.
3. Stable handoff conclusions should often be promoted into current state, open loops, SOP, or decision logs.
