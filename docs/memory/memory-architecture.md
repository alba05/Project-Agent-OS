# Memory Architecture

## Purpose

The memory layer exists so a project can survive across multiple threads, interruptions, and phases of work.

## Memory Types

### 1. Current State

One short file describing:

1. What phase the project is in
2. What the main line of work is
3. What is currently stable

### 2. Open Loops

One short file describing:

1. What is not done
2. What decisions are pending
3. What the most natural next step is

### 3. Thread Summaries

Each important thread gets one summary file with:

1. Topic
2. Work completed
3. Stable conclusions
4. Remaining next steps

### 4. Decision Log

A compact record of important decisions that should not be silently re-litigated.

### 5. SOP Index

A list of stable operating procedures the project already relies on.

## Memory Rules

1. Store conclusions, not raw transcripts.
2. Prefer short structured files over long narrative dumps.
3. Update memory only when a conclusion is stable enough to reuse.
4. Keep current state and open loops small and current.
5. Use thread summaries as the bridge between chats and stable memory.

## Minimal Recommended Memory Layout

```text
knowledge-base/
  current-state.md
  open-loops.md
  decision-log.md
  sop-index.md
thread-summaries/
  thread-<id>.md
```

## Writeback Trigger

Write memory updates when:

1. A repeated pattern becomes stable.
2. A naming or structural decision is settled.
3. A phase of work ends.
4. A new thread would otherwise need to rediscover important context.
