# Template: Retrospective Summary

Write to: `.claude/plans/$ARGUMENTS/retrospective/summary.md`

This is the primary durable document. It tells the story of the initiative in a way
that someone unfamiliar with the work can understand.

---

```markdown
# $ARGUMENTS — Retrospective Summary

**Initiative dates**: [start] — [end]
**Status**: [completed | partially completed | closed]

## What We Set Out to Do
[Concise restatement of the original problem and goals, drawn from summary.md]

## What We Actually Did
[Narrative of what happened. Focus on outcomes, not process.
Reference specific tasks by number where helpful.]

## Key Decisions
[Decisions that shaped the work. For decisions with formal ADRs, reference them:
"See ADR-001: [title]"]

- **[Decision]**: [Why we chose this path. What we considered.]
- **[Decision]**: [Brief rationale. Reference ADR if applicable.]

## Pivots and Surprises
[Moments where the plan changed. What we discovered during execution
that we didn't know during planning. These are the most valuable
retrospective insights.]

- **[Pivot]**: [What changed and why]
- **[Surprise]**: [What we discovered]

## Planned vs. Actual

### Scope Changes
- [What was added that wasn't originally planned]
- [What was dropped or deferred]

### Approach Changes
- [Where execution diverged from the refined plan, and why]

## Outcomes
[What was delivered. Concrete results.]

## Follow-Up Items
[Consolidated from task execution notes. Work identified but not completed.]

- [ ] [Item from task NN]
- [ ] [Item from task NN]

## Lessons Learned
[What went well, what didn't, what we'd do differently.
Be honest — this section is the most useful for future initiatives.]

### What Worked
- [Thing that went well and why]

### What Didn't
- [Thing that didn't work and why]

### What We'd Do Differently
- [Specific, actionable insight]
```
