# Reusable Slash Command Patterns

These patterns are starting points. Adapt the syntax to the Claude Code version and command format used by the target project.

## 1. Inspect, then report

Use for audits, diagnostics, and status commands.

Structure:
1. Identify the target scope.
2. Inspect files or state without modifying them.
3. Compare observations against explicit criteria.
4. Report findings with evidence.
5. Suggest changes separately.

Default side effect: none.

## 2. Plan, then implement

Use when a workflow needs a deliberate implementation step.

Structure:
1. Gather requirements and inspect the project.
2. Identify affected files and constraints.
3. Present or record a concise plan when the task is non-trivial.
4. Make the smallest coherent change.
5. Run relevant checks.
6. Summarize changed files and results.

Do not treat the plan as approval for risky actions.

## 3. Validate an artifact

Use for configuration, documentation, migrations, or generated output.

Structure:
1. Locate the artifact.
2. Parse or inspect it.
3. Check required fields and invariants.
4. Verify related paths and dependencies.
5. Report exact failures and suggested corrections.

## 4. Argument-driven operation

Use when users need to supply a target, mode, or scope.

Define:
- argument name;
- accepted values;
- default;
- validation;
- behavior for missing or invalid values.

Never interpolate unchecked user input into a shell command.

## 5. Multi-stage workflow

Use when each stage depends on the previous stage's result.

Structure:
1. Preflight checks.
2. Analysis.
3. Proposed change.
4. Authorized execution.
5. Post-change validation.
6. Final report.

Stop if a stage fails in a way that invalidates later stages.

## Choosing a pattern

Choose the simplest pattern that meets the requirement. A command that only summarizes a diff does not need a multi-stage framework. A command that publishes a release should include preflight checks, explicit authorization, and post-publication verification.