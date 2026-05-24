# Raw Data README

This folder stores original raw data sources for the project.

## Core Rule: Raw Data Are Read-Only

Raw data must never be modified, renamed, moved, deleted, overwritten, or manually edited.

Do not create derived, cleaned, merged, or analysis-ready files inside `data_raw/`.

Adding new raw data requires explicit human approval.

## Required Documentation for Each Raw Data Source

For each source, document:

- source name;
- date added;
- original source or download location;
- file format;
- whether files are original archives, extracted files, documentation, or user-created source inputs;
- access restrictions and citation requirements;
- unit of observation;
- key identifiers;
- time coverage;
- geographic coverage;
- major variable groups;
- codebooks, questionnaires, or data dictionaries;
- known limitations and caveats.

## Where to Put Non-Raw Outputs

- Use `data_intermediate/` for reproducible intermediate checkpoints and diagnostics.
- Use `data_intermediate/test/` for inspection exports.
- Use `data_final/` for analysis-ready datasets.

## Example Data Reminder

Template example files under `examples/data_documentation/` demonstrate how to document data. They are not raw data and must be deleted during initialization unless retained with explicit human approval.
