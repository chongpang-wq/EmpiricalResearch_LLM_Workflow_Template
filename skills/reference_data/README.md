# Reference Data README

This folder stores reference data used by optional-trigger skills.

Current reference files:

- `code_year_region.csv`: reference data for Chinese administrative division matching.
- `exchange_rate.csv`: reference data for monetary units, exchange rates, and deflation workflows.

These files are part of the workflow template and should be used only when the corresponding skill is triggered.

Do not modify, overwrite, rename, or delete these reference files without explicit human approval.

Do not invent replacement reference data.

When a coding LLM uses a reference file from this folder, it must report:

- which file was used;
- why it was needed;
- how it was used;
- any missing coverage or matching risks.

# Data Notice

This template includes small reference datasets used by optional-trigger skills.

## `skills/reference_data/code_year_region.csv`

Source repository:

- GitHub: `CallMeNP/GB2260`
- Description: GB/T 2260 administrative division codes of the People's Republic of China, including historical yearly changes.
- Upstream stated source: Ministry of Civil Affairs of the People's Republic of China, civil affairs data, administrative division codes.
- Coverage note from upstream README: county level and above, 6-digit codes; data collected through June 2019.
- Columns: `code`, `year`, `region`.

Users should verify the upstream repository license and cite both the upstream repository and the original official source when using this file.

## `skills/reference_data/exchange_rate.csv`

Source:

- World Bank World Development Indicators.
- Indicator: GDP deflator, `NY.GDP.DEFL.ZS`.
- Source file last updated: 2026-04-08.

Users should comply with World Bank data terms of use and cite World Bank WDI when using this file.

## General Rule

Reference data are included only to support optional workflow skills. They should not be treated as project-specific research data.

Users should verify data sources, licenses, update dates, and coverage before publication.
