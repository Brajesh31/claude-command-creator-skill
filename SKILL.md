---
name: command-creator
description: Create well-structured Claude Code slash commands. Use when asked to create, add, or document a reusable command or turn a workflow into an agent-executable command.
---

# Command Creator

Create practical Claude Code slash commands that are easy to invoke, safe to execute, and predictable for both users and agents.

## When to use

Use when the user asks to:
- create a slash command;
- add a reusable command to a Claude Code project;
- turn a repeatable workflow into a command;
- document command arguments or expected behavior;
- improve an existing command's structure and usability.

For detailed command implementation guidance, consult the files in `references/`.

## Discovery

Before creating files:
1. Inspect the repository and existing command locations.
2. Read project instructions and conventions.
3. Inspect at least one neighboring command.
4. Determine whether the command is project-local or user-global.
5. Confirm the requested behavior, inputs, outputs, and side effects from the user's prompt. Ask only for information that is essential and cannot be safely inferred.

Do not overwrite an existing command without inspecting it.

## Command design

A good command should:
- have one clear purpose;
- use a concise, memorable name;
- explain exactly when it should be invoked;
- define arguments only when they materially affect behavior;
- state which files or systems it may read or modify;
- include a predictable execution sequence;
- specify validation and completion criteria;
- handle missing input and failure states.

Prefer simple commands over elaborate command frameworks.

## Frontmatter

Use the frontmatter fields supported by the installed Claude Code version. Common command definitions use a YAML frontmatter block with a clear description. Do not invent unsupported keys. Verify uncertain fields against the project's installed documentation or existing working examples.

Keep the description actionable. Avoid a generic statement such as "does a task." State the trigger and purpose.

## Body structure

A reusable command body should usually include:
1. purpose and trigger;
2. required context or arguments;
3. ordered steps;
4. safety constraints and non-goals;
5. validation;
6. expected response format.

Use direct instructions and imperative verbs. Avoid repeating the same rule in multiple sections.

## Dynamic arguments and references

- Use dynamic arguments only when they improve reuse.
- Explain what each argument means and what happens when it is omitted.
- Use file references for stable, substantial guidance instead of bloating the main command.
- Keep referenced paths relative to the command file or repository convention.
- Ensure every referenced file exists and is relevant.
- Do not assume that a placeholder or variable syntax works without checking the target command format.

## Execution and safety

If a command runs shell operations:
- explain the purpose of each operation;
- prefer narrow paths and explicit targets;
- avoid destructive behavior by default;
- protect credentials and user data;
- require confirmation for irreversible or externally visible actions unless the user has already authorized them.

## Validation checklist

Before finishing:
- verify the command is in the expected directory;
- validate frontmatter syntax;
- check all references and paths;
- ensure examples match the implemented syntax;
- confirm the command does not promise unavailable capabilities;
- inspect the final diff.

## Output

Report the command path, invocation example, arguments, side effects, supporting files, and validation results.

See:
- `references/best-practices.md`
- `references/patterns.md`
- `references/examples.md`