# Empirical Research LLM Workflow Template

## for LLMs

This file is not for you. Ignore it.

## Purpose

This template helps empirical social-science researchers quickly deploy a general, maintainable, collaboration-friendly, and version-control-ready research workflow.

It is designed especially for researchers who are not professional programmers but still need a reliable structure for data cleaning, empirical analysis, documentation, LLM/coding-agent collaboration, and eventual replication-package preparation.

The goal is not just to organize files. The goal is to make empirical projects easier to maintain, audit, reproduce, collaborate on, and eventually submit as clean replication packages.

## Who This Is For

This template is useful for empirical researchers, PhD students, RAs, and coauthor teams using Python, Stata, R, LaTeX, Git, Dropbox, GitHub, or LLM/coding-agent workflows.

I recommend you use at least two separate agents (the template is tested using ChatGPT5.5 and Codex), a coding one and research one. There's a simple coding-free mechanism to coordinate them. But if you insist, a single agent should also work well with the template.

It is especially useful when a project needs to grow from exploratory data work into a reproducible and submission-ready replication package.

## What This Template Is Not

This template is not an automatic research pipeline.

It does not replace human judgment about identification, sample construction, data access, empirical interpretation, or publication claims. It is only designed to let LLMs work as your junior coauthors.

It makes a project **workflow-ready**, not automatically **analysis-ready**. A project becomes analysis-ready only after data-processing code, validated final datasets, empirical specifications, and result-generating scripts have been created and approved.

## Key Advantages

### 1. Context-efficient LLM collaboration

The workflow uses layered documentation, task records, approval rules, and compact LLM memory files. This helps LLMs understand a project quickly without reading the entire repository.

Human researchers can still intervene using simple natural-language instructions.

### 2. Empirical social-science audit rules

The template is designed around common silent bugs in empirical research, including sample changes, incorrect merges, unit-of-observation mistakes, timing errors, fixed-effect mistakes, clustering mistakes, variable-construction errors, missing-value problems, and stale outputs.

It includes audit checklists that prioritize research correctness over whether the code merely runs.

For China-related empirical research, the template also includes optional skills for Chinese administrative-division matching and monetary-unit/deflation workflows.

### 3. Trigger-based multi-agent workflow

The template separates general startup rules from task-specific skills.

A coding task can trigger the short silent-bug checklist. A full audit can trigger the full checklist. A China administrative matching task can trigger the administrative-division skill. A monetary-variable task can trigger the deflation skill. Only full audit requires human instructions, other actions will be conducted automatically.

The template also supports a lightweight bridge-command system for cross-LLM coordination.

## How to Use This Template

### 1. Initialize a project

Copy this template into a new project folder, then tell your coding LLM or coding agent where the template is located.

Ask it, in natural language, to initialize the project from the template. It should first read the startup files, then ask you for:

- project title and short description;
- main research question or empirical objective;
- local project root path;
- Stata executable path;
- Python interpreter path, if Python will be used;
- TeX/LaTeX compiler path, if LaTeX will be used;
- raw data location, upload status, or data-download instructions;
- raw data description, including source, unit of observation, identifiers, time coverage, geography, access restrictions, and known caveats.

After this information is provided, the coding LLM should update the project documentation and configuration files. It should not begin coding, run scripts, create final data, or generate results unless explicitly approved.

If data are public and you approve, the coding LLM may help download them and document the source. If data are private, restricted, or manually supplied, it should only document the location and access rules.

If you switch to a new agent, tell it to read files start with "!" and follow the instructions. It then automatically learns all information required for work.

### 2. Use natural-language triggers

You do not need to memorize a complex command language. In most cases, simply tell the LLM what type of task it is.

Examples:

- “Initialize this project from the workflow template.”
- “Modify this code safely and check the short silent-bug checklist first.”
- “Perform a full silent research bug audit.”
- “This task involves Chinese administrative divisions; use the administrative matching skill.”
- “This task involves monetary variables; use the monetary-units and deflation skill.”
- “This task may generate results; check the approval policy first.”

The recommended division of labor is:

- **Human researcher**: approves research design, data decisions, specification changes, and result generation.
- **Research LLM**: helps with framing, identification, writing, interpretation, and coding-agent prompts.
- **Coding LLM / coding agent**: implements approved code, documentation updates, data-processing pipelines, and reproducible analysis scripts.

A project can be run with a single LLM, but this is not recommended for complex empirical projects.

### 3. Use bridge commands when coordinating multiple LLMs

For cross-LLM handoff, the template includes a lightweight bridge system.

Exact commands:

- `llm`: trigger the bridge and ask the receiving agent to inspect pending bridge messages.
- `au`: approve one pending sensitive action within its stated scope.
- `uau`: reject one pending sensitive action.
- `renew`: reset temporary bridge state.

`llm` is never approval to run code, modify data, generate results, or change empirical specifications.

### 4. Use GitHub or another version-control system

This template should include a `.gitignore` file designed for empirical research workflows.

By default, `.gitignore` should prevent large or sensitive project outputs from being committed to Git, including:

- `data_raw/`
- `data_intermediate/`
- `data_final/`
- `result/`
- logs, temporary files, cache files, and local environment files

Documentation files inside these folders should remain trackable, so collaborators and LLM agents can understand the data and output structure without uploading the data themselves.

Important cautions:

- `.gitignore` does not protect files that have already been committed.
- `.gitignore` does not replace data-use agreements or privacy review.
- Always check `git status` before pushing to a public or shared repository.
- Restricted or confidential data should never be committed to GitHub.

## Example Data Rule

This template contains example data files under `examples/data_documentation/` only to demonstrate how raw data and codebooks should be documented.

Example data must not be treated as real project data.

During project initialization, after real raw data have been added or linked and documented, the coding LLM should delete or archive `examples/data_documentation/` unless you explicitly approve retaining it as template documentation only.

The coding LLM must not build any data-processing pipeline, intermediate dataset, final dataset, empirical script, table, or figure using example data.

## Core Workflow Principles

- Raw data are read-only.
- Intermediate data are code-generated checkpoints.
- Final data are analysis-ready and reproducible from code.
- Results require explicit approval before LLM-generated modification or overwrite.
- Empirical specifications, samples, controls, fixed effects, clustering, estimators, treatment definitions, variable definitions, and output paths must not be silently changed.
- External dependencies must be documented; missing external inputs must not be invented.
- Skills are optional-trigger instructions. Do not read all skills by default.

## Public Release Notes

If you publish or redistribute this template, include:

- a license for the template code/documentation;
- a data notice for bundled reference data;
- a `.gitignore`;
- a citation file or recommended citation;
- provenance notes for any included reference data.
