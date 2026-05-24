# Project Initialization Protocol

This file tells a coding LLM or coding agent how to initialize a new empirical research project from this workflow template.

## Initialization Rule

When this template is copied into a new project, do not begin coding immediately.

First ask the human researcher for the required initialization inputs. Then update documentation only, unless the human explicitly approves code, data, or result actions.

## Required Questions for the Human Researcher

Ask for:

1. Project title.
2. One-paragraph project description.
3. Main research question or planned empirical objective.
4. Key mechanism, hypothesis, or empirical relationship if known.
5. Main data sources.
6. Raw data location, upload status, or data-download instructions.
7. Raw data description: source, format, unit of observation, key identifiers, time coverage, geography, variable groups, codebooks, citation/access restrictions, and known caveats.
8. Local project root path.
9. Stata executable path, if Stata will be used.
10. Python interpreter path, if Python will be used.
11. TeX/LaTeX compiler path, if LaTeX will be used.
12. Preferred language or languages: Python, Stata, R, LaTeX, or other.
13. Expected durable outputs.
14. External dependencies.
15. Any special approval rules.

## Public vs Private Data

If the data are public and the human researcher approves, the coding LLM may help download the data and document the source.

If the data are private, restricted, manually supplied, or subject to a data-use agreement, the coding LLM should only document the location, access rules, and restrictions. It must not upload, redistribute, or expose the data.

Do not invent raw data, metadata, codebooks, external dependencies, exchange rates, deflators, or administrative crosswalks.

## Files to Update During Initialization

After receiving the human inputs, update only the relevant documentation files, such as:

- `!project_overview.md`
- `!technical_readme.md`
- `!llm_record.md`
- `project_inventory.md`
- `external_dependencies.md`
- `config/paths.yaml`
- `data_raw/readme_data_raw.md`
- source-specific raw data README files, only if the human approves creating them

Do not create new code, final data, intermediate data, tables, or figures unless explicitly approved.

## Example Data Cleanup Rule

This template contains example files under:

`examples/data_documentation/`

These files demonstrate how data documentation and codebooks should be written. They are not project data.

Before marking a project workflow-ready, delete or archive `examples/data_documentation/` after real raw data have been added or linked and the raw-data README has been drafted.

If the human researcher explicitly wants to keep example files, record that approval in `!llm_record.md` and clearly mark the example folder as template documentation only.

Never use example data for project analysis, code development, intermediate data generation, final data generation, table generation, or figure generation.

## Prohibited Initialization Actions Without Explicit Approval

Do not:

- modify raw data;
- create final datasets;
- run analysis code;
- generate result files;
- invent missing metadata;
- silently choose empirical specifications;
- silently change samples, controls, fixed effects, clustering, estimators, treatment definitions, variable definitions, or output paths;
- modify anything under `skills/`.

## Workflow-Ready Checklist

A project is workflow-ready only when:

- project title and description are documented;
- local paths and interpreter paths are recorded;
- real raw data are added, linked, or explicitly documented as pending;
- raw data README is drafted;
- external dependencies are documented;
- approval boundaries are clear;
- example data have been deleted, archived, or explicitly retained with human approval;
- remaining placeholders are listed in `!llm_record.md` or `open_questions.md`.

Workflow-ready does not mean analysis-ready.

A project becomes analysis-ready only after data-processing code, validated final datasets, empirical specifications, and result-generating scripts have been created and approved.

