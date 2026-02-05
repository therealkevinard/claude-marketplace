---
name: write-tasks
description: | 
    Prepares a step-wise execution plan with interdependencies. 
    Each task is written to its own markdown file with enough context to support a cold-start session.
argument-hint: [initiative-name]
allowed-tools: Read, Write, Glob, Grep
---

# Write Tasks: $ARGUMENTS

<role>
You are a **staff engineer/architect** breaking down the planned work into executable tasks.   
Each task must be self-contained enough to be picked up in a fresh session.   
Prescriptive templates are a starting point - include any and all additional context you judge important for cold-start. 
</role>

## Conventions

<conventions>
Read `**/kevins-okay-workflow/_conventions.md` for directory structure and naming conventions.
</conventions>

## Prerequisites

<instructions>
Read the planning artifacts first:
- `.claude/plans/$ARGUMENTS/summary.md`
- `.claude/plans/$ARGUMENTS/state-diagram.md`
</instructions>

## Artifacts to Produce

### Artifact 1: Task Files

<artifact>
Write each task to: `.claude/plans/$ARGUMENTS/tasks/NN-task-name.md`

Where `NN` is a zero-padded sequence number (01, 02, 03...).

<template name="task-file">

```markdown
# Task NN: [Task Title]

**Status**: pending | in-progress | blocked | complete
**Depends on**: [list of task numbers, or "none"]
**Blocks**: [list of task numbers, or "none"]

## Objective
[One sentence: what this task accomplishes]

## Context

### Why This Task
[How it fits into the larger initiative]

### Relevant Background
[Key findings from planning that inform this task]

### Current State
[What exists today that this task touches]

## Scope

### In Scope
- [Specific thing 1]
- [Specific thing 2]

### Out of Scope
- [Explicitly excluded thing]

## Approach (High-Level)
[General strategy—not implementation details. Those come in refinement.]

## Key Files & Locations
- `path/to/relevant/file.go` - [why it's relevant]
- `path/to/another/file.go` - [why it's relevant]

## Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2

## Open Questions
- [Anything uncertain that should be resolved during refinement]

## Notes
[Any other context that would help a cold-start session]
```
</template>
</artifact>

### Artifact 2: Execution Plan Index

<artifact>
Write to: `.claude/plans/$ARGUMENTS/tasks/INDEX.md`

<template name="index">

```markdown
# $ARGUMENTS - Execution Plan

## Task Overview

| # | Task | Depends On  |
|---|------|-------------|
| 01 | [Title] | - |
| 02 | [Title] | 01 |
| 03 | [Title] | 01, 02 |

## Dependency Graph

\`\`\`mermaid
graph TD
    T01[01: Title] --> T02[02: Title]
    T01 --> T03[03: Title]
    T02 --> T03
\`\`\`

## Critical Path
[Which tasks are on the critical path and why]

## Parallelization Opportunities
[Which tasks can run in parallel]
```
</template>
</artifact>

## Guidance

<guidelines>
- **Task granularity**: Each task should be completable in roughly one focused session (2-4 hours of work). Too big = break it down. Too small = combine.
- **Dependencies**: Be explicit. If task 03 can't start until 01 and 02 are done, say so.
- **Cold-start friendly**: Someone (or future-you) should be able to pick up any task without reading the full conversation history.
- **High-level approach**: Save detailed implementation for the refinement phase. This is the "what" and "why", not the "how exactly".
</guidelines>

## Exit Condition

<exit-condition>
After writing all task files and the INDEX, suggest: **"Execution plan created with N tasks. Pick a task and run `/kevins-okay-workflow:refine-task NN` to add implementation details."**
</exit-condition>
