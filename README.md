# Empirical Research LLM Workflow Template

This folder is a reusable workflow template for empirical research projects that use a human researcher, a research-oriented LLM, and a coding LLM/Codex.

The template is designed to make a new project **workflow-ready**, not automatically analysis-ready.

## Startup Files

When a new project is initialized from this template, read these files first:

1. `INITIALIZE_PROJECT.md` — project initialization protocol.
2. `!technical_readme.md` — folder map and workflow rules.
3. `!project_overview.md` — project-level research overview placeholder.
4. `!llm_record.md` — compact LLM memory placeholder.
5. `approval_policy.md` — approval boundaries for actions.

## Required Human Inputs During Initialization

The coding LLM must ask the human researcher for:

- project title;
- one-paragraph project description;
- main research question or planned research objective;
- local project root path;
- Python interpreter path, if Python is used;
- Stata executable path, if Stata is used;
- preferred code language or languages;
- raw data location or upload status;
- raw data description, including source, unit, key identifiers, time coverage, geography, and access restrictions;
- external dependencies, if any;
- expected outputs, such as cleaned data, tables, figures, slides, or paper drafts.

## Example Data Rule

This template contains example data files under `examples/data_documentation/` only to demonstrate how raw data and codebooks should be documented.

Example data must not be treated as real project data.

During project initialization, after the human researcher has added or linked real raw data and provided the required data description, the coding LLM must delete `examples/data_documentation/` unless the human explicitly approves retaining it as template documentation only.

The coding LLM must not build any data-processing pipeline, intermediate dataset, final dataset, empirical script, table, or figure using example data.

The project should not be marked workflow-ready until the example data folder has either been removed or explicitly retained with human approval recorded in `!llm_record.md`.

## Core Workflow Principles

- Raw data are read-only.
- Intermediate data are code-generated checkpoints.
- Final data are analysis-ready and fully reproducible from code.
- Results should be reproducible and require explicit approval before LLM-generated modification or overwrite.
- Empirical specifications, samples, controls, fixed effects, clustering, estimators, treatment definitions, variable definitions, and output paths must not be silently changed.
- External dependencies must be documented; missing external inputs must not be invented.
- Skills are optional-trigger instructions. Do not read all skills by default.

## Workflow-Ready vs Analysis-Ready

A project is workflow-ready when folder structure, rules, project description, paths, raw-data documentation, and approval boundaries are in place.

A project is analysis-ready only after data-processing code, validated final datasets, empirical specifications, and result-generating scripts have been created and approved.
