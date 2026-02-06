# Template: Trade Study

Write to: `.claude/plans/$ARGUMENTS/retrospective/trade-study-short-title.md`

File a trade study when the initiative involved **formal evaluation of alternatives**
with distinct criteria and tradeoffs. This is more detailed than an ADR's
"alternatives considered" section — use it when the analysis itself has reference value.

---

```markdown
# Trade Study: [Topic]

**Date**: [date]
**Initiative**: $ARGUMENTS
**Decision**: [Which option was selected]

## Objective
[What we were trying to solve or choose between]

## Options Evaluated

### Option A: [Name]
[Description of the approach]

**Pros:**
- [Advantage]

**Cons:**
- [Disadvantage]

### Option B: [Name]
[Description of the approach]

**Pros:**
- [Advantage]

**Cons:**
- [Disadvantage]

## Evaluation Criteria
[What mattered most in making this decision]

| Criterion | Weight | Option A | Option B |
|-----------|--------|----------|----------|
| [Criterion] | high/med/low | [rating] | [rating] |

## Recommendation and Rationale
[Why the selected option won. What tipped the scales.]

## Risks of Selected Approach
[Known risks accepted with the chosen option]
```
