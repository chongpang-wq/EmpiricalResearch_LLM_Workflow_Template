# Tasks README

This folder stores task-level work orders, execution notes, review notes, and approval records.

Use task files when a coding LLM or research LLM is asked to perform a durable project action.

## Recommended Task Ticket Structure

```md
# Task: [TITLE]

Date:
Requester:
Agent:

## Goal

## Files allowed to read

## Files allowed to modify

## Files forbidden to modify

## Approval status

## Specification constraints

Do not change without explicit approval:
- sample restrictions
- variable definitions
- controls
- fixed effects
- clustering
- estimators
- treatment definitions
- output paths

## Expected report

- changed files
- commands run
- outputs created
- checks performed
- unresolved issues
```

## Rule

For any task that may modify files, run code, generate outputs, or affect empirical design, use `approval_policy.md` before acting.
