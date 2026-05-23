# Project Initialization Protocol

This file tells a coding LLM how to initialize a new empirical research project from this workflow template.

## Initialization Rule

When this template is copied into a new project, do not begin coding immediately.

First ask the human researcher for the required initialization inputs. Then update documentation only, unless the human explicitly approves code, data, or result actions.

## Required Questions for the Human Researcher

Ask for:

1. Project title.
2. One-paragraph project description.
3. Main research question or planned objective.
4. Key mechanism, hypothesis, or empirical relationship if known.
5. Main data sources.
6. Raw data location or upload status.
7. Raw data description: source, format, unit of observation, key identifiers, time coverage, geography, variable groups, codebooks, citation/access restrictions, and known caveats.
8. Local project root path.
9. Python interpreter path, if Python will be used.
10. Stata executable path, if Stata will be used.
11. Preferred language or languages: Python, Stata, R, or other.
12. Expected durable outputs.
13. External dependencies.
14. Any special approval rules.

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

Before marking a project workflow-ready, delete `examples/data_documentation/` after real raw data have been added or linked and the raw-data README has been drafted.

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
- example data have been deleted or explicitly retained with human approval;
- remaining placeholders are listed in `!llm_record.md` or `open_questions.md`.

Workflow-ready does not mean analysis-ready.
