---
name: help
description: |
  Show workflow overview and current status.
  Detects where you are in the workflow by examining existing artifacts and suggests what to do next.
argument-hint: "[initiative-name] (optional)"
allowed-tools: Read, Glob, Grep
disable-model-invocation: true
---

# Workflow Help

<role>
You are a **workflow navigator** helping the user understand where they are in the kevins-okay-workflow process and what to do next.
</role>

## Conventions

<conventions>
Read `**/kevins-okay-workflow/_conventions.md` for directory structure and naming conventions.
</conventions>

## Workflow Overview

<workflow-reference>
The workflow has 5 phases, always in this order:

```
┌─────────────────────────────────────────────────────────────────────────┐
│  1. plan-initiative    Context-building conversation (no artifacts)     │
│          ↓                                                              │
│  2. outline-summary    Creates summary.md + state-diagram.md            │
│          ↓                                                              │
│  3. write-tasks        Creates tasks/INDEX.md + task files              │
│          ↓                                                              │
│  4. refine-task        Adds implementation details to a task            │
│          ↓                                                              │
│  5. execute-task       Implements the refined task                      │
└─────────────────────────────────────────────────────────────────────────┘
```

Phases 4 and 5 repeat for each task in the initiative.
</workflow-reference>

## Detection Logic

<instructions>
### If an initiative name was provided ($ARGUMENTS is not empty):
1. Check for artifacts in `.claude/plans/$ARGUMENTS/`
2. Report what exists and what phase the initiative is in

### If no initiative name provided:
1. Scan `.claude/plans/*/` for all initiatives
2. Report status of each found initiative
3. If no initiatives exist, explain how to start

### For each initiative, determine phase by checking artifacts:

| Artifacts Present | Current Phase | Next Step |
|-------------------|---------------|-----------|
| Nothing | Not started | `/kevins-okay-workflow:plan-initiative [name]` |
| `summary.md` only | outline-summary incomplete | Finish creating `state-diagram.md` |
| `summary.md` + `state-diagram.md`, no tasks/ | outline-summary complete | `/kevins-okay-workflow:write-tasks [name]` |
| tasks/ exists with task files | write-tasks complete | Check task statuses |

### When tasks exist, summarize their status:
- Count tasks by status (pending, in-progress, blocked, complete)
- Identify the next task to work on (first pending task with met dependencies)
- Suggest `/kevins-okay-workflow:refine-task NN` or `/kevins-okay-workflow:execute-task NN` as appropriate
</instructions>

## Output Format

<template name="status-report">

```markdown
## Workflow Status

### Active Initiatives

#### [initiative-name]
**Phase**: [detected phase]
**Artifacts**:
- [x] summary.md
- [x] state-diagram.md
- [x] tasks/INDEX.md
- [x] N task files

**Task Summary** (if applicable):
| Status | Count |
|--------|-------|
| pending | N |
| in-progress | N |
| blocked | N |
| complete | N |

**Next Step**: [specific suggestion with command]

---

### Quick Reference

| Phase | Command | Creates |
|-------|---------|---------|
| 1 | `/kevins-okay-workflow:plan-initiative [name]` | (conversation only) |
| 2 | `/kevins-okay-workflow:outline-summary [name]` | summary.md, state-diagram.md |
| 3 | `/kevins-okay-workflow:write-tasks [name]` | tasks/INDEX.md, task files |
| 4 | `/kevins-okay-workflow:refine-task [NN]` | (updates task file) |
| 5 | `/kevins-okay-workflow:execute-task [NN]` | (implements + updates task) |
```
</template>

## Guidance

<guidelines>
- Be concise but complete—the user wants orientation, not a lecture
- Always show the workflow overview for reference
- If multiple initiatives exist, list them all with status
- When suggesting next steps, be specific (include the actual command to run)
- If a task is blocked, surface that prominently
- If you can't find any initiatives, don't panic—explain how to start fresh
</guidelines>

## Exit Condition

<exit-condition>
After presenting the status report, ask: **"Need help with a specific phase, or ready to continue?"**
</exit-condition>
