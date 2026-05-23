# Data Process Code README

This folder stores code that builds reproducible intermediate and final datasets from raw data.

## Workflow

```text
data_raw/
        ->
data_intermediate/
        ->
data_final/
```

## Core Rules

- Read from `data_raw/`; never modify raw data.
- Write reproducible checkpoints to `data_intermediate/`.
- Write analysis-ready datasets to `data_final/`.
- Do not write generated datasets into `code/data_process/`.
- Do not manually edit intermediate or final datasets.
- If a data value, variable, sample rule, merge rule, or output structure changes, update code and regenerate outputs.

## Standard Intermediate-Reuse Switch

Data-processing scripts should define a top-level switch when applicable:

```python
USE_INTERMEDIATE = False
```

- `False`: run the full pipeline.
- `True`: reuse safe existing intermediate checkpoints without changing data definitions.

This switch must not change variable definitions, sample restrictions, merge rules, or output definitions.

## Validation Expectations

When relevant, scripts should check:

- row counts before and after merges;
- duplicate keys;
- missing key IDs;
- unmatched observations;
- value ranges;
- unit and currency consistency;
- geographic code consistency.

## Documentation Responsibilities

When durable outputs are created or changed, update the relevant README files and record important project memory in `!llm_record.md`.
