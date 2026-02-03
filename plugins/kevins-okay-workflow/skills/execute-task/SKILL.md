---
name: execute-task
description: | 
   Execute a refined task specification. Follow the implementation details, write code, run tests, and update task status.
argument-hint: [task-file-path or task-number]
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, Task
---

# Execute Task: $ARGUMENTS

<role>
You are executing a refined task specification.  
Follow the implementation details precisely, adapting as needed when reality diverges from the plan.
</role>

## Conventions

<conventions>
Read `**/kevins-okay-workflow/_conventions.md` for directory structure and naming conventions.
</conventions>

## Setup

<instructions>
1. Locate and read the task file:
   - If given a number (e.g., "01"), look for `.claude/plans/*/tasks/NN-*.md` matching that number
   - If given a path, read directly

2. Verify the task is ready:
   - Status should be `pending` or `in-progress`
   - Implementation details should be present (from refinement phase)
   - Dependencies should be complete

3. Update status to `in-progress`
</instructions>

## Execution Flow

<workflow>
### 1. Pre-Flight Check
- [ ] Read the full task specification
- [ ] Verify dependent tasks are complete
- [ ] Confirm you have access to all referenced files
- [ ] Note any open questions that need resolution

### 2. Execute Implementation Steps
Follow the step-by-step approach from the refined task. For each step:
- Implement the change
- Verify it works (compile, lint, basic test)
- Note any deviations from the plan

### 3. Testing
- Run the tests specified in the task
- Add new tests as defined
- Verify existing tests still pass

### 4. Documentation
- Update code comments if needed
- Note any follow-up work discovered

### 5. Task Completion
Update the task file with completion notes (see template below).
</workflow>

<template name="completion-notes">

```markdown
**Status**: complete

## Execution Notes

### Completed: [date]

### Deviations from Plan
- [Any changes made vs. what was planned]

### Issues Encountered
- [Problems hit and how they were resolved]

### Follow-up Items
- [Anything that should be addressed later]
```
</template>

## Guidance

<guidelines>
- **Follow the plan**: The refinement phase already made the decisions. Execute them.
- **Document deviations**: If you need to diverge, note why.
- **Don't over-scope**: Stick to this task. New work goes in new tasks.
- **Test as you go**: Don't leave testing until the end.
- **Ask if blocked**: If something's unclear, pause and ask rather than guessing.
</guidelines>

## Exit Condition 

<exit-condition>
**If blocked:**
1. Update task status to `blocked`
2. Document the blocker in the task file
3. Suggest: **"Task blocked: [reason]. We may need to revisit `/kevins-okay-workflow:refine-task` or address a dependency."**

**If complete:**
1. Update task status to `complete`
2. Verify acceptance criteria are met
3. Suggest: **"Task complete. Check the execution notes for any follow-up items. Ready for the next task?"**
</exit-condition>
