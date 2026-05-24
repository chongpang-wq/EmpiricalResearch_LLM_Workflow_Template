# Empirical Research LLM Workflow Template

## Purpose

This template exists to help empirical social-science researchers quickly deploy a general, maintainable, collaboration-friendly, and version-control-ready research workflow.

It is designed especially for researchers who are not professional programmers but need a reliable structure for data cleaning, empirical analysis, documentation, LLM/coding-agent collaboration, and eventual replication-package preparation.

The goal is not merely to organize files. The goal is to make empirical projects easier to maintain, audit, reproduce, collaborate on, and eventually submit as clean replication packages.

In particular, this template helps researchers:

- separate raw data, intermediate data, final analysis data, code, and results;
- document data sources, variable construction, empirical specifications, and external dependencies;
- prevent silent empirical bugs in samples, merges, timing, fixed effects, clustering, variable definitions, missing values, and outputs;
- coordinate human researchers, research-oriented LLMs, and coding LLMs or coding agents;
- support multi-person collaboration and version control;
- move gradually from exploratory analysis to a submission-ready replication package.

## Who This Is For

This template is for empirical social-science researchers using Python, Stata, R, LaTeX, Git, Dropbox, GitHub, or LLM/coding-agent workflows.

It is especially useful for:

- PhD students and research assistants;
- small coauthor teams;
- researchers who want reproducible workflows but are not professional software engineers;
- projects that need to grow from exploratory analysis into replication packages;
- empirical researchers who want to use LLMs/Codex/Claude Code safely without allowing silent changes to research design.

## What This Template Is Not

This template is not an automatic research pipeline.

It does not replace human judgment about identification, sample construction, data access, empirical interpretation, or publication claims.

It makes a project **workflow-ready**, not automatically **analysis-ready**. A project becomes analysis-ready only after data-processing code, validated final datasets, empirical specifications, and result-generating scripts have been created and approved.

## Key Advantages

### 1. Context-efficient LLM collaboration

This workflow uses layered documentation, task records, approval rules, and compact LLM memory files to help LLMs quickly understand a project without loading the entire repository into context.

Instead of asking an LLM to read every file, the workflow tells it which startup documents to read first, when to inspect lower-level README files, and when to trigger specialized skills. This keeps context use low while preserving project rules, approval boundaries, and modification records.

Human researchers can still intervene using simple natural-language instructions. They do not need to understand the full codebase to approve, redirect, or constrain an LLM/coding-agent task.

### 2. Empirical social-science audit rules

The template is designed around common silent bugs in empirical social-science research: sample changes, incorrect merges, unit-of-observation mistakes, timing errors, fixed-effect mistakes, clustering mistakes, variable-construction errors, missing-value problems, and stale outputs.

It includes empirical-code audit checklists that prioritize research correctness over whether the code merely runs.

For China-related empirical research, the template also includes optional skills for Chinese administrative-division matching and monetary-unit/deflation workflows.

### 3. Trigger-based cross-LLM collaboration

The workflow uses simple trigger rules to coordinate human researchers, research-oriented LLMs, and coding LLMs/Codex.

Rather than asking every LLM to read every rule every time, the template separates general startup rules from task-specific skills. For example, a coding task can trigger the silent-bug checklist, an administrative matching task can trigger the China administrative-division skill, and a monetary-variable task can trigger the deflation skill.

For cross-LLM handoff, the template also supports a lightweight bridge-command system:

- `llm`: trigger the bridge and read pending messages;
- `au`: approve a pending sensitive action;
- `uau`: reject a pending sensitive action;
- `renew`: reset temporary bridge state.

These commands make cross-LLM collaboration easier, safer, and more auditable.

## Startup Files

When a new project is initialized from this template, read these files first:

1. `README.md` — human-facing landing page and quick overview.
2. `INITIALIZE_PROJECT.md` — project initialization protocol.
3. `!technical_readme.md` — folder map, LLM startup rules, and workflow rules.
4. `!project_overview.md` — project-level research overview placeholder.
5. `!llm_record.md` — compact LLM memory placeholder.
6. `approval_policy.md` — approval boundaries for actions.

Files beginning with `!` are startup files intended to appear near the top of folder listings.

## How to Use This Template

### 1. Initialize a new project

Copy this template into the new project folder, then tell your coding LLM or coding agent where the template is located.

The coding LLM should first read:

- `README.md`
- `INITIALIZE_PROJECT.md`
- `!technical_readme.md`
- `approval_policy.md`

Then it should ask the human researcher for the required initialization information, including:

- project title and short project description;
- main research question or empirical objective;
- local project root path;
- Stata executable path;
- Python interpreter path, if Python will be used;
- TeX/LaTeX compiler path, if LaTeX will be used;
- raw data location, upload status, or data-download instructions;
- raw data description, including source, unit of observation, identifiers, time coverage, geography, access restrictions, and known caveats.

After the human researcher provides this information, the coding LLM should update the project documentation and configuration files, such as:

- `!project_overview.md`
- `!llm_record.md`
- `config/paths.yaml`
- `data_raw/readme_data_raw.md`
- `external_dependencies.md`

If the data are public and the researcher approves, the coding LLM may help download the data and document the source. If the data are private, restricted, or manually supplied, the coding LLM should only document the location and access rules.

After project metadata, local paths, and raw-data documentation are recorded, the project is **workflow-ready**.

### 2. Use trigger-based commands

This template is designed around simple trigger-based commands. The goal is to avoid asking every LLM to read every rule every time.

Common triggers include:

| Trigger | What it does |
|---|---|
| Initialize project | Ask for project information, interpreter paths, raw data, and data notes; then fill startup documentation. |
| Modify code | Read the short silent-bug checklist before editing empirical code. |
| Audit code | Read the full silent-bug checklist and produce a structured research-bug audit. |
| Administrative matching | Read the China administrative-division matching skill and use reference data only when needed. |
| Monetary variables | Read the monetary-units and deflation skill before handling currency, nominal/real values, exchange rates, or deflators. |
| Generate results | Check approval policy before running scripts that write tables, figures, logs, or exports. |
| Bridge LLMs | Send exactly `llm` to trigger the bridge protocol in `llm_bridge/`. |

A project can be run with a single LLM, but this is not recommended for complex empirical projects.

The recommended division of labor is:

- **Human researcher**: approves research design, data decisions, specification changes, and result generation.
- **Research LLM**: helps with research framing, identification strategy, writing, interpretation, and coding-agent prompts.
- **Coding LLM / coding agent**: implements approved code, documentation updates, data-processing pipelines, and reproducible analysis scripts.

This division reduces the risk that an implementation-focused agent silently changes the research design, while still allowing the human researcher to intervene using simple natural-language instructions.

### 3. Use GitHub or another version-control system

This template should include a `.gitignore` file designed for empirical research workflows.

By default, `.gitignore` should prevent large or sensitive project outputs from being committed to Git, including:

- `data_raw/`
- `data_intermediate/`
- `data_final/`
- `result/`
- logs, temporary files, cache files, and local environment files

Documentation files inside these folders should remain trackable, so collaborators and LLM agents can still understand the data and output structure without uploading the data themselves.

This makes it easier and faster to create a GitHub repository for version control: users can usually create a repository directly from the project folder, while keeping raw data and generated data outside Git.

Important cautions:

- `.gitignore` does not protect files that have already been committed.
- `.gitignore` does not replace data-use agreements or privacy review.
- Users should always check `git status` before pushing to a public or shared repository.
- Restricted or confidential data should never be committed to GitHub.

## Prompt Templates

The following prompt templates are written for researchers who want to control LLM/coding-agent work through simple natural-language instructions.

They are optional. You can copy, paste, and modify them.

### Initialize a new project

Use this prompt after copying the template into a new project folder:

```text
Initialize this project from the empirical research workflow template.

Template location:
[PASTE_TEMPLATE_OR_PROJECT_FOLDER_PATH]

First read:
- README.md
- INITIALIZE_PROJECT.md
- !technical_readme.md
- approval_policy.md

Then ask me for the required project metadata, local interpreter paths, and raw-data information.

Do not begin coding yet.
Do not run any scripts.
Do not create intermediate data, final data, tables, figures, or result files.
Update documentation only after I provide the required information.
```

### Provide project information during initialization

Use this prompt when the coding LLM asks for project metadata:

```text
Project title:
[PROJECT_TITLE]

Short project description:
[ONE_PARAGRAPH_DESCRIPTION]

Main research question or empirical objective:
[QUESTION_OR_OBJECTIVE]

Main data sources:
[DATA_SOURCE_LIST]

Local project root path:
[LOCAL_PROJECT_ROOT]

Stata executable path:
[STATA_PATH_OR_NOT_USED]

Python interpreter path:
[PYTHON_PATH_OR_NOT_USED]

TeX/LaTeX compiler path:
[TEX_PATH_OR_NOT_USED]

Raw data location or download instructions:
[RAW_DATA_LOCATION_OR_PUBLIC_DOWNLOAD_INSTRUCTIONS]

Raw data notes:
- source:
- unit of observation:
- key identifiers:
- time coverage:
- geographic coverage:
- access restrictions:
- known caveats:

Expected durable outputs:
[OUTPUTS]

Special approval rules:
[RULES_OR_NONE]
```

### Ask a coding LLM to modify code safely

Use this prompt before an approved coding task:

```text
Modify the code for the following task:

[TASK_DESCRIPTION]

Before editing, read:
- approval_policy.md
- skills/short_silent_bug_checklist.md
- relevant folder-level README files

Do not silently change:
- sample restrictions
- variable definitions
- controls
- fixed effects
- clustering
- estimators
- treatment definitions
- output paths

If any such change seems necessary, stop and ask for approval.

After editing, report:
- files changed
- analytical changes
- non-analytical refactors
- commands run
- outputs created or overwritten
- validation checks
- remaining risks
```

### Ask for a full silent research bug audit

Use this prompt when you want a structured empirical-code audit:

```text
Perform a full silent research bug audit.

Read:
- approval_policy.md
- skills/full_silent_bug_checklist.md
- relevant code and documentation files

Focus on research correctness, not code style.

Report each relevant item as:
- Pass
- Risk
- Fail
- Not checked

Prioritize:
- sample changes
- merges
- unit of observation
- variable construction
- timing and exposure windows
- fixed effects
- clustering
- weights
- missing values
- stale outputs
- consistency with the documented specification

Do not modify files unless I explicitly approve it.
```

### Trigger Chinese administrative-division matching rules

Use this prompt when a task involves Chinese region codes or names:

```text
This task involves Chinese administrative divisions.

Before matching, merging, or cleaning region codes or names, read:
- skills/china_administrative_zone.md
- skills/reference_data/README.md

Do not assume a code is an official administrative code just because it looks like one.

Confirm:
- code type
- administrative level
- year
- province/prefecture/county distinction
- boundary changes
- duplicate names
- lost leading zeros

If you use reference_data/code_year_region.csv, report why it was needed and how it was used.
```

### Trigger monetary-units and deflation rules

Use this prompt when a task involves money, exchange rates, real/nominal values, or deflation:

```text
This task involves monetary variables.

Before reading, constructing, converting, deflating, logging, or interpreting monetary values, read:
- skills/monetary_units_deflation_SKILL.md
- skills/reference_data/README.md

Confirm:
- currency
- unit
- nominal vs real
- time basis
- exchange-rate direction
- deflator source
- base year
- missing coverage

Do not guess exchange rates or deflators.
Do not treat missing exchange rates or deflators as 1.
Do not deflate a variable twice.
```

### Ask a research LLM to prepare a coding-agent task

Use this prompt when you want a research-oriented LLM to write a precise coding prompt:

```text
Please convert the following research request into a coding-agent-ready task.

Research request:
[REQUEST]

The coding task should include:
- goal
- files to read
- files allowed to modify
- files forbidden to modify
- approval boundaries
- specification constraints
- expected output
- validation checks
- reporting requirements

The task must not allow silent changes to sample restrictions, variable definitions, fixed effects, clustering, estimators, treatment definitions, or output paths.
```

### Trigger bridge communication between research LLM and coding LLM

Use this exact command when you want the receiving agent to inspect the bridge:

```text
llm
```

`llm` means: read `llm_bridge/README.md` and check the relevant bridge inbox/cache.

`llm` does **not** approve code execution, file modification, data modification, result generation, or specification changes.

### Approve or reject a pending sensitive action

Use these exact commands only after a coding LLM/Codex has shown a pending sensitive-action risk notice.

Approve the pending sensitive action:

```text
au
```

Reject the pending sensitive action:

```text
uau
```

Reset temporary bridge state:

```text
renew
```

`au` approves only the pending action within the exact stated scope. It is not blanket approval for extra files, extra commands, new results, or specification changes.

## Example Data Rule

This template contains example data files under `examples/data_documentation/` only to demonstrate how raw data and codebooks should be documented.

Example data must not be treated as real project data.

During project initialization, after the human researcher has added or linked real raw data and provided the required data description, the coding LLM must delete or archive `examples/data_documentation/` unless the human explicitly approves retaining it as template documentation only.

The coding LLM must not build any data-processing pipeline, intermediate dataset, final dataset, empirical script, table, or figure using example data.

The project should not be marked workflow-ready until the example data folder has either been removed, archived, or explicitly retained with human approval recorded in `!llm_record.md`.

## Core Workflow Principles

- Raw data are read-only.
- Intermediate data are code-generated checkpoints.
- Final data are analysis-ready and fully reproducible from code.
- Results should be reproducible and require explicit approval before LLM-generated modification or overwrite.
- Empirical specifications, samples, controls, fixed effects, clustering, estimators, treatment definitions, variable definitions, and output paths must not be silently changed.
- External dependencies must be documented; missing external inputs must not be invented.
- Skills are optional-trigger instructions. Do not read all skills by default.

## Public Release Notes

If you publish this template, include:

- a license for the template code/documentation;
- a data notice for bundled reference data;
- a `.gitignore`;
- a citation file or recommended citation;
- provenance notes for any included reference data.

