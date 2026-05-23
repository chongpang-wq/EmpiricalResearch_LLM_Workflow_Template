# Result README

This folder stores generated tables, figures, regression exports, diagnostic outputs, and paper or presentation materials.

## Core Rule

LLM agents may create, modify, overwrite, or delete files in `result/` only with explicit human approval.

This includes indirect modification, such as running code that writes tables, figures, logs, or exports here.

## Reproducibility Rule

Durable results should be reproducible from project code, final data, and documented intermediate inputs.

Do not treat manually edited result files as the hidden source of truth.

## Subfolders

| Folder | Purpose |
|---|---|
| `table/` | Tables and regression exports. |
| `figure/` | Figures, maps, charts, and image outputs. |

## Documentation Requirements

For durable result files, document:

- generating script;
- input dataset;
- sample or model specification;
- date generated;
- output path;
- whether manual formatting was applied.

## Reporting After Result Generation

After approved result generation, report commands run, outputs created or overwritten, warnings, and validation checks.
