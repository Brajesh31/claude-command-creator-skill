# Slash Command Best Practices

## Start with a narrow job

A command should solve one repeatable problem. A command named `/release-check` should validate release readiness, not also publish a release, announce it, and clean the repository unless those actions are explicitly part of its contract.

Separate workflows when they have different risk levels or require different approvals.

## Write descriptions for discovery

A useful description answers:
- What does the command do?
- When should it be used?
- What input or context does it need?

Prefer concrete language. Avoid lists of every possible synonym.

## Make behavior predictable

Document:
- required and optional arguments;
- defaults;
- files and systems read;
- files and systems changed;
- commands that may be run;
- expected output;
- failure handling.

When the command infers a value, say how it chooses that value and what it does when the inference is ambiguous.

## Keep the command body focused

Use a short, ordered procedure. Put long reference material in companion documents only when it is useful to more than one step or too detailed for the main workflow.

Do not create reference files that merely repeat the command body.

## Design safe defaults

- Prefer inspection before modification.
- Limit edits to the stated scope.
- Preserve uncommitted user work.
- Do not expose secrets in logs or output.
- Do not run destructive commands without explicit authorization.
- Confirm before actions that publish, deploy, delete, spend money, or affect external users.

A user request to create a command is not automatically permission to execute that command.

## Make failure visible

Commands should stop or report when a prerequisite is missing. Do not silently skip required validation. Distinguish:
- completed successfully;
- partially completed;
- blocked by missing information or tools;
- failed during execution.

## Use arguments carefully

Arguments are useful for values that change from invocation to invocation. They are not a substitute for a clear workflow.

For each argument, specify its format, whether it is required, and the behavior when omitted. Validate values before using them in shell commands or paths.

## Verify references and compatibility

Check that referenced files exist. Check the installed Claude Code command syntax rather than copying syntax from an unrelated version. Keep examples consistent with the target project.

## Review before delivery

Inspect the final command file and diff. Remove duplicated instructions, stale paths, unsupported frontmatter, and claims about behavior that the command cannot guarantee.