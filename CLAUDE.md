# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a Claude Code plugin marketplace—a collection of plugins that extend Claude Code with custom skills. Plugins are installed by users via `claude plugins add-marketplace` and `claude plugins install`.

## Structure

```
.claude-plugin/marketplace.json    # Marketplace registry (lists available plugins)
plugins/
└── plugin-name/
    ├── .claude-plugin/plugin.json # Plugin metadata (name, version, skills path)
    ├── skills/
    │   └── skill-name/
    │       └── SKILL.md           # Skill definition (frontmatter + instructions)
    ├── _conventions.md            # Shared conventions for the plugin's skills
    └── README.md
```

## Plugin Architecture

**Marketplace registration** (`/.claude-plugin/marketplace.json`): Lists plugins with name, source path, and description.

**Plugin metadata** (`plugin.json`): Defines name, version, author, and skills directory.

**Skill definitions** (`SKILL.md`): Frontmatter defines the skill interface:
- `name`: Skill identifier
- `description`: What the skill does (shown to users)
- `argument-hint`: Expected arguments
- `allowed-tools`: Tools the skill can use
- `disable-model-invocation`: If true, skill provides guidance without executing

The body contains structured instructions using tags like `<role>`, `<workflow>`, `<template>`, `<guidelines>`, and `<exit-condition>`.

## kevins-okay-workflow Plugin

A 5-phase workflow for complex initiatives with planning-heavy artifacts:

1. **plan-initiative** → Context-building conversation (no artifacts)
2. **outline-summary** → Creates `summary.md` and `state-diagram.md`
3. **write-tasks** → Creates task files and `INDEX.md`
4. **refine-task** → Adds implementation details to a task
5. **execute-task** → Implements the refined task

Artifacts live in `.claude/plans/[initiative-name]/` with tasks in a `tasks/` subdirectory.

See `plugins/kevins-okay-workflow/_conventions.md` for naming rules (kebab-case initiative names, zero-padded task numbers, status values).

## Development

**Test locally:**
```bash
claude --plugin-dir ./plugins/kevins-okay-workflow
```

**Install to a project:**
```bash
claude plugin install ./plugins/kevins-okay-workflow --scope project
```

No build, lint, or test commands—plugins are pure markdown definitions.
