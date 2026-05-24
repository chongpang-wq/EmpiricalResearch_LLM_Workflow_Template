# Intermediate Data README

This folder stores reproducible intermediate datasets, checkpoints, diagnostics, and inspection exports.

Intermediate data are not raw source files and are not final analysis-ready datasets.

## Core Rule

Every durable file in this folder should be reproducible from raw data using documented project code.

Do not manually edit intermediate data files and treat them as code-generated outputs.

## Test Folder

Use `test/` for:

- temporary inspection exports;
- merge diagnostics;
- duplicate checks;
- small samples for manual review;
- Excel-readable validation files.

Test files should not become hidden inputs to the main data pipeline unless explicitly converted into documented source inputs.

## Documentation Requirements

For reusable intermediate files, document:

- file name and path;
- generating script;
- source inputs;
- unit of observation;
- key identifiers;
- row count when known;
- main transformations;
- known limitations;
- whether it is safe to regenerate.

## Example Data Reminder

Do not copy template example data into this folder. Example files under `examples/data_documentation/` are for documentation format only and should be deleted after initialization unless retained with human approval.
