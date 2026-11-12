# Slash Command Design Examples

The examples below illustrate structure and intent. Confirm the command syntax supported by the installed Claude Code version before using them verbatim.

## Example: review the current diff

**Purpose:** Inspect uncommitted changes and identify concrete risks.

**Invocation concept:** `/review-diff`

**Procedure:**
1. Inspect the repository status and diff.
2. Read relevant surrounding code.
3. Identify correctness, security, and test gaps.
4. Report findings with file and line references.
5. Do not modify files or create commits.

**Output:** Findings by severity, checks performed, and unresolved questions.

## Example: create a focused test

**Purpose:** Add a regression test for a reported bug.

**Inputs:** Bug description and optional target module.

**Procedure:**
1. Locate the implementation and existing test conventions.
2. Reproduce the expected behavior from the report.
3. Add the smallest test that fails before the fix.
4. Run the focused test.
5. Do not alter production code unless the user asks for a fix.

**Safety:** Preserve existing tests and unrelated changes.

## Example: validate environment configuration

**Purpose:** Check that required configuration keys are present without revealing their values.

**Procedure:**
1. Read the documented list of required keys.
2. Check whether each key is set.
3. Report present or missing status only.
4. Never print secret values or write them to logs.

**Output:** A concise checklist of configuration status.

## Example: prepare a release summary

**Purpose:** Summarize verified changes for a release candidate.

**Procedure:**
1. Identify the intended comparison range.
2. Review merged changes and associated issue references.
3. Group user-visible changes into categories.
4. Exclude speculative or duplicate entries.
5. Produce a draft summary for review.

**Boundary:** Drafting a summary does not authorize publishing a release.

## Example: command quality review

A command review should ask:
- Is the trigger clear?
- Does the command have one primary job?
- Are inputs and defaults explained?
- Are side effects explicit?
- Are destructive operations guarded?
- Are references valid?
- Can a user understand the expected output?
- Are unsupported syntax and duplicate instructions absent?

These examples are intentionally small. Extend them only when the real workflow requires additional steps.