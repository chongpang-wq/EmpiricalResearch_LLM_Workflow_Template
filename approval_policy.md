# Approval Policy

This file defines approval boundaries for empirical research projects initialized from this template.

## No Approval Needed

A research-oriented LLM or coding LLM may usually do the following without additional approval:

- read Markdown documentation;
- summarize project structure;
- explain workflow rules;
- draft research advice;
- draft Codex-ready prompts;
- inspect code or documentation when the user asks for review, without modifying files.

## Explicit Human Approval Required

The following actions require explicit human approval before execution:

- create, modify, overwrite, move, rename, or delete project files;
- run code that writes outputs;
- create or overwrite files in `data_intermediate/`, `data_final/`, or `result/`;
- add new raw data or raw-data folders;
- create source-specific README files when not already present;
- generate tables, figures, logs, or exports;
- change empirical specifications, samples, controls, fixed effects, clustering, estimators, treatment definitions, variable definitions, or output paths;
- use or modify external dependencies;
- modify anything under `skills/`.

## Strictly Forbidden Without Special Approval

Do not:

- modify raw data;
- manually edit final datasets;
- invent missing external dependencies;
- use example data as real project data;
- silently change analytical definitions;
- claim a project is analysis-ready before data-processing code, validated final data, empirical specifications, and result scripts exist.

## Required Reporting After Approved Mutations

After any approved mutation, report:

- changed files and folders;
- commands run;
- outputs created or overwritten;
- analytical changes versus non-analytical refactors;
- validation checks performed;
- unresolved risks or missing dependencies;
- how to revert the change.

## Example Data Approval Rule

Template example data under `examples/data_documentation/` must be deleted during initialization after real raw data are added or linked and documented. Retaining example data inside an initialized project requires explicit human approval and must be recorded in `!llm_record.md`.
