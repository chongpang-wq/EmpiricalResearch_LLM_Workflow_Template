# Empirical Analysis Code README

This folder stores empirical analysis scripts, including regressions, mechanisms, robustness checks, tables, and figures.

Use this folder only after analysis-ready data have been created in `data_final/`.

## Core Rules

- Result generation requires explicit human approval.
- Output tables and figures should be written to `result/`, not to this folder.
- Do not silently change empirical specifications, sample restrictions, controls, fixed effects, clustering, estimators, treatment definitions, variable definitions, or output paths.
- If a specification changes, document it in `spec_registry.md`.

## Recommended Files

| File | Purpose |
|---|---|
| `specification_map.md` | Maps analysis scripts to research blocks, inputs, outputs, and cautions. |
| `spec_registry.md` | Records approved empirical specifications. |
| `main.do` or equivalent | Optional sequential runner after scripts exist. |
| `pre_process.do` or equivalent | Optional shared preprocessing script after final data exist. |

## Specification Discipline

Before interpreting results, check:

- unit of observation;
- sample restrictions;
- treatment definition;
- outcome definition;
- controls;
- fixed effects;
- clustering;
- estimator;
- input dataset;
- output path.

## Reporting After Runs

After any approved run, report changed outputs, commands run, logs, warnings, and validation checks.
