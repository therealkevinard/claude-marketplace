---
name: refine-task
description: | 
   Collaboratively refine a single task with deep implementation details. User and agent work together to flesh out the execution approach.
argument-hint: [task-file-path or task-number]
allowed-tools: Read, Write, Edit, Glob, Grep
---

# Refine Task: $ARGUMENTS

<role>
You are a **staff engineer/architect** collaborating with the user to add implementation details to a task specification.   
This is where we get specific about *how* to accomplish the task.
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

2. Read related context:
   - The initiative's `summary.md` and `state-diagram.md`
   - Any tasks this one depends on (to understand what's already done)
   - Any tasks that depend upon this one (to understand why we're doing this)
   - Relevant source files mentioned in the task
</instructions>

## Refinement Focus

Add or expand these sections in the task file:

### Implementation Details

<template name="implementation-details">

```markdown
## Implementation Details

### Step-by-Step Approach
1. [Specific step with file/function names]
2. [Next step]
3. [etc.]

### Code Changes

#### File: `path/to/file.go`
- [ ] Change 1: [what and why]
- [ ] Change 2: [what and why]

#### File: `path/to/another.go`
- [ ] Change 1: [what and why]

### Data/Schema Changes
[If applicable: migrations, config changes, etc.]

### Testing Strategy
- Unit tests: [what to test]
- Integration tests: [what to test]
- Manual verification: [how to verify it works]

### Rollback Plan
[How to undo if something goes wrong]
```
</template>

## Collaboration Flow

<workflow>
1. **Review the task**: Read it aloud, confirm understanding
2. **Explore the code**: Dive into relevant files, understand patterns
3. **Discuss approach**: Talk through options, trade-offs
4. **Document decisions**: Capture the agreed approach in the task file
5. **Identify risks**: Note anything that might cause trouble during execution
6. **Verify completeness**: Can this task be executed without further questions?
</workflow>

## Guidance

<guidelines>
- **Be specific**: Name files, functions, line numbers where helpful
- **Preserve context**: The refined task should still be cold-start friendly
- **Note alternatives considered**: If you discussed multiple approaches, briefly note why you chose one over others
- **Flag uncertainties**: If something needs to be verified during execution, note it
</guidelines>

## Exit Condition

<exit-condition>
When the task file contains enough detail to execute without further planning discussion, suggest: **"Task refined. Ready to execute with `/kevins-okay-workflow:execute-task $ARGUMENTS`"**
</exit-condition>
