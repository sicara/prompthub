# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains a collection of specialized Claude Code commands called "Classy Claude Commands" (CCC). These are custom command definitions stored in `.claude/commands/` that extend Claude Code's capabilities for specific development workflows.

## Command Structure

All commands are defined as Markdown files in `.claude/commands/` directory:

- Each command file follows a structured format with Description, Arguments, Instructions, and Output sections
- Commands are designed to be composable and workflow-oriented
- Focus on Python development patterns, testing, and documentation generation

## Available Commands

### Core Development Commands
- `prime.md` - Systematic project understanding workflow (reads README, PLANNING.md, TASK.md, analyzes structure)
- `load_context.md` - Builds global context by reading all .md files in a repository
- `code_review.md` - Comprehensive code review with TASK.md integration and priority-based findings
- `fix_from_traceback.md` - Error analysis and fix implementation with approval workflow

### Python-Specific Commands
- `coverage.md` - Achieves 100% test coverage using uv and pytest
- `implement_notion_ticket.md` - Converts Notion tickets into detailed implementation plans for Python projects
- `write_docstrings.md` - Adds comprehensive docstrings to Python code

### Documentation Commands
- `create_mermaid_docs.md` - Generates Mermaid flowcharts for complex Python functions in README
- `create_flowchart.md` - Creates visual flowcharts for code analysis
- `update_changelog.md` - Maintains project changelogs

## Development Workflow Patterns

### Python Project Focus
Commands assume Python development environment with:
- `uv` for package management and virtual environments
- `pytest` for testing framework
- `coverage` library for test coverage analysis
- Standard Python project structure (main.py, app.py, manage.py, etc.)

### Approval-Based Workflows
Several commands follow a "plan-then-execute" pattern:
1. Analyze the request/problem
2. Generate detailed implementation plan
3. Wait for explicit user approval
4. Execute the plan with code changes

### Documentation Integration
Commands maintain consistency through:
- TASK.md for tracking implementation status and priorities
- PLANNING.md for architecture and design decisions
- README.md updates with generated documentation

## Command Usage Philosophy

- **Systematic Analysis**: Commands start by understanding existing codebase structure
- **Explicit Planning**: Complex changes require approval before implementation
- **Test-Driven**: Testing and coverage are integral to most workflows
- **Documentation-First**: Generated code includes proper documentation
- **Risk Assessment**: Commands consider backward compatibility and deployment impacts

## File Organization

The repository uses a simple structure:
```
.claude/
  commands/           # All command definitions
    *.md             # Individual command files
.gitignore           # Python-focused gitignore
README.md            # Basic project description
LICENSE              # MIT license
```

## Integration Points

Commands are designed to work with:
- Git repositories with standard Python project layouts
- CI/CD pipelines that use pytest and coverage
- Documentation systems that render Mermaid diagrams
- Project management tools like Notion for ticket tracking