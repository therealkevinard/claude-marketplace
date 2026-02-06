# Template: Architecture Decision Record

Write to: `.claude/plans/$ARGUMENTS/retrospective/adr-NNN-short-title.md`

File an ADR when a decision meets **any** of these criteria:
- Introduced a new architectural pattern or technology
- Chose between meaningfully different approaches
- Changed an existing architectural convention
- Has consequences that will constrain future work

Use sequential numbering: `adr-001`, `adr-002`, etc.

---

```markdown
# ADR-NNN: [Decision Title]

**Date**: [date of the decision, not the retrospective]
**Status**: accepted
**Initiative**: $ARGUMENTS

## Context
[What situation or problem prompted this decision.
Include relevant constraints and forces at play.]

## Decision
[What we decided to do. Be specific.]

## Alternatives Considered
- **[Alternative A]**: [Brief description. Why it was rejected.]
- **[Alternative B]**: [Brief description. Why it was rejected.]

## Consequences

### Positive
- [Good outcome of this decision]

### Negative
- [Tradeoff or cost accepted]

### Neutral
- [Notable side-effect that isn't clearly good or bad]
```
