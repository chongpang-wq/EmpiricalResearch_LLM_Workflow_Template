# External Dependencies

This file documents project dependencies outside the project folder.

Do not create substitute files for missing external dependencies. If an external dependency is missing, report it to the human researcher and ask whether it should be migrated, regenerated, documented elsewhere, or treated as unavailable.

## Known External Data Inputs

| Dependency | Current Path or Source | Inside Project Folder? | Used By | Purpose | If Missing | Future Handling |
|---|---|---|---|---|---|---|
| [DEPENDENCY_NAME] | [PATH_OR_URL] | [Yes/No] | [SCRIPT_OR_WORKFLOW] | [PURPOSE] | Stop and report; do not invent substitute. | [Migrate / regenerate / keep external / remove] |

## Current Policy

- External dependencies may be read only when the human-approved workflow requires them.
- External dependencies should not be silently copied into the project folder.
- Decisions about migrating, replacing, or redefining external dependencies require human approval.
- External dependencies that affect empirical specifications, variable definitions, or sample construction must be documented before analysis-ready status.
