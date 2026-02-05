# Workflow Conventions (Internal)

This file defines shared conventions for all skills in this plugin.

## Directory Structure

All artifacts live under `.claude/plans/[initiative-name]/`:

```
.claude/plans/[initiative-name]/
├── summary.md              # Planning conversation synthesis (outline-summary)
├── state-diagram.md        # Before/after mermaid diagrams (outline-summary)
└── tasks/
    ├── INDEX.md            # Task overview and dependency graph (write-tasks)
    ├── 01-task-name.md     # Individual task files (write-tasks)
    ├── 02-task-name.md
    └── ...
```

## Variable Mapping

| Skill Variable | Meaning | Example |
|----------------|---------|---------|
| `$ARGUMENTS` | The initiative name passed by user | `auth-refactor` |
| `[initiative-name]` | Same as $ARGUMENTS | `auth-refactor` |
| `[task-number]` | Zero-padded task sequence | `01`, `02`, `03` |

The initiative name becomes the folder name: `.claude/plans/$ARGUMENTS/`

## File Naming

- **Initiative folders**: lowercase, kebab-case (e.g., `auth-refactor`, `api-v2-migration`)
- **Task files**: `NN-short-description.md` where NN is zero-padded (e.g., `01-setup-interfaces.md`)
- **Task descriptions**: lowercase, kebab-case, max 3-4 words

## Task Status Values

Tasks use these status values consistently:

| Status | Meaning |
|--------|---------|
| `pending` | Not started, may have unmet dependencies |
| `in-progress` | Currently being worked |
| `blocked` | Cannot proceed, blocker documented |
| `complete` | Done, acceptance criteria met |

## Cross-Skill References

When one skill references another's artifacts:

| Producer Skill | Artifact | Consumer Skills |
|----------------|----------|-----------------|
| `outline-summary` | `summary.md` | `write-tasks`, `help` |
| `outline-summary` | `state-diagram.md` | `write-tasks`, `help` |
| `write-tasks` | `tasks/INDEX.md` | `refine-task`, `execute-task`, `help` |
| `write-tasks` | `tasks/NN-*.md` | `refine-task`, `execute-task`, `help` |
| `refine-task` | (updates task file) | `execute-task` |

Note: `help` is a read-only consumer that scans artifacts to determine workflow status.

## Locating This File

Skills should reference this file using a glob pattern that works regardless of install location:

```
**/kevins-okay-workflow/_conventions.md
```
