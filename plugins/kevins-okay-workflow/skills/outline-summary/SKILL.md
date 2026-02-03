---
name: outline-summary
description: | 
  Creates initial planning artifacts from a context-building conversation.  
  Produces a markdown summary and a mermaid diagram showing before/after states.
argument-hint: [initiative-name]
allowed-tools: Read, Write, Glob, Grep
---

# Documentation Phase: $ARGUMENTS

<role>
You are a **staff engineer/architect** synthesizing the planning conversation into durable artifacts.   
These artifacts will support all later stages by providing the big-picture overview. 
</role>

## Conventions

<conventions>
Read `**/kevins-okay-workflow/_conventions.md` for directory structure and naming conventions.
</conventions>

## Workflow

<workflow>
1. **Review the planning conversation**: Identify key findings, pivots, and decisions made
2. **Create the summary**: Write `.claude/plans/$ARGUMENTS/summary.md` capturing the problem statement, current/desired state, and open questions
3. **Create the state diagram**: Write `.claude/plans/$ARGUMENTS/state-diagram.md` with before/after mermaid diagrams
4. **Verify completeness**: Ensure both artifacts could be understood by someone who wasn't in the conversation
</workflow>

## Artifacts to Produce

### Artifact 1: Conversation Summary

<artifact>
Write to: `.claude/plans/$ARGUMENTS/summary.md`

<template name="conversation-summary">

```markdown
# $ARGUMENTS - Planning Summary

**Date**: [today]
**Participants**: [user, claude]

## Problem Statement
[Concise statement of what we're solving and why]

## Current State
[How things work today, including relevant code/systems]

## Desired State
[What we want to achieve]

## Key Findings
- Finding 1
- Finding 2

## Pivots & Surprises
[Moments where understanding shifted or something unexpected emerged]

## Constraints
- [Timeline, resources, dependencies, etc.]

## Open Questions
- [Things still uncertain or needing validation]

## Risks
- [What could go wrong]
```
</template>
</artifact>

### Artifact 2: System State Diagram

<artifact>
Write to: `.claude/plans/$ARGUMENTS/state-diagram.md`

<template name="state-diagram">

```markdown
# $ARGUMENTS - State Diagram

## Before State

\`\`\`mermaid
[diagram showing current architecture/flow]
\`\`\`

### Notes on Current State
[Brief explanation of what the diagram shows]

## After State

\`\`\`mermaid
[diagram showing proposed architecture/flow]
\`\`\`

### Notes on Proposed State
[Brief explanation of what changes and why]

## Delta Summary
[Bullet points of what components are changing between states]
[Summarize behavioral changes, with a focus on wins and trade-offs]
```
</template>
</artifact>

## Guidance

<guidelines>
- Be specific. Reference actual files, services, and patterns from the codebase.
- The summary should be readable by someone who wasn't in the conversation.
- The mermaid diagrams should be simple enough to render cleanly — avoid over-complexity, but illustrate the change thoroughly and accurately.
- Capture the *essence* of pivots and surprises, not just facts.
</guidelines>

## Exit Condition

<exit-condition>
After writing both artifacts, suggest: **"Artifacts created. Ready to move to `/kevins-okay-workflow:write-tasks` to create the execution plan?"**
</exit-condition>
