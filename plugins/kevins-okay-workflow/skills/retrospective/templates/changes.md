# Template: Change Log

Write to: `.claude/plans/$ARGUMENTS/retrospective/changes.md`

A concrete record of what changed in the codebase. Useful for understanding the
blast radius of the initiative and for anyone touching these areas later.

---

```markdown
# $ARGUMENTS — Change Log

## Systems Affected
[High-level list of systems/services/modules that were modified]

## Changes by Area

### [Area/Module 1]

| File/Path | Change Type | Description |
|-----------|-------------|-------------|
| `path/to/file` | added/modified/removed | [What changed and why] |

### [Area/Module 2]

| File/Path | Change Type | Description |
|-----------|-------------|-------------|
| `path/to/file` | added/modified/removed | [What changed and why] |

## Interface Changes
[Any API, schema, config, or contract changes that affect consumers]

## Migration Notes
[If applicable: data migrations, config changes, deployment considerations]
```
