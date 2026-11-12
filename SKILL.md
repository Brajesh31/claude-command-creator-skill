---
name: command-creator
description: Create reusable Claude Code slash commands as clear, testable Markdown workflows. Use when asked to create, design, document, or improve a slash command.
---

# Command Creator

Guide the creation of reusable Claude Code slash commands stored as Markdown files. A good command turns a repeated workflow into precise instructions that Claude Code can execute consistently.

## When to use

Use this skill when a user wants to:
- Create a new slash command.
- Convert a repeated workflow into a reusable command.
- Add argument handling, file references, or tool restrictions.
- Improve an existing command's clarity or reliability.

## Bundled references

Read the relevant files in `references/` when needed:
- `patterns.md`: common command workflow patterns.
- `examples.md`: complete command examples.
- `best-practices.md`: writing guidance and quality checks.

## Workflow

### 1. Understand the command

Establish:
- The command's single primary responsibility.
- Its name and concise description.
- Required and optional arguments.
- Expected inputs, outputs, and side effects.
- Required tools, files, and permissions.
- Success criteria and error handling.

Ask only for information that is necessary. Use sensible defaults for non-essential details and state assumptions.

### 2. Choose a location

- Project command: `.claude/commands/`.
- User command: `~/.claude/commands/`.
- Plugin command: the plugin's `commands/` directory.

Use the current Claude Code documentation and the user's requested scope to confirm the appropriate location. Do not assume that a plugin command belongs in a project or user directory.

### 3. Design the command

Use Markdown with optional YAML frontmatter. Include only fields supported by the user's Claude Code version. Common fields include:
- `description`
- `argument-hint`
- `allowed-tools`
- `model`
- `disable-model-invocation`

Write instructions for the agent, not promotional copy for the user. Use imperative steps and explicit expected outcomes.

### 4. Handle arguments and references

- Document argument syntax and validate required values.
- Use positional arguments or the full argument string consistently.
- Explain behavior for missing or invalid inputs.
- Reference files only when their paths are known and relevant.
- Avoid shell interpolation of untrusted input; quote and validate values.

### 5. Apply safety boundaries

- Request confirmation before destructive operations, external publication, deployment, or irreversible changes.
- Restrict tools to the minimum required.
- Never embed credentials or secrets in the command.
- Define a safe failure path and do not conceal command errors.

### 6. Create and validate

- Check for an existing command with the same name before writing.
- Create the Markdown file in the agreed location.
- Review frontmatter and Markdown structure.
- Test argument handling and the workflow where a safe test environment exists.
- Report the path, invocation syntax, assumptions, and validation results.

## Quality checklist

A command is ready when it has one clear purpose, a usable description, documented arguments, explicit steps, bounded permissions, safe error handling, and a verifiable result.
