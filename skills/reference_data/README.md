# Reference Data README

This folder stores reference data used by optional-trigger skills.

Current reference files:

- `code_year_region.csv`: reference data for Chinese administrative division matching.
- `exchange_rate.csv`: reference data for monetary units, exchange rates, and deflation workflows.

## Source Notes

`code_year_region.csv` is based on the public GitHub repository `CallMeNP/GB2260`, which documents GB/T 2260 administrative division codes of the People's Republic of China and states that its upstream source is Ministry of Civil Affairs administrative division code data.

`exchange_rate.csv` is based on World Bank World Development Indicators GDP deflator data.

Users should verify data sources, licenses, update dates, and coverage before publication.

## Use Rule

These files are part of the workflow template and should be used only when the corresponding skill is triggered.

Do not modify, overwrite, rename, or delete these reference files without explicit human approval.

Do not invent replacement reference data.

When a coding LLM uses a reference file from this folder, it must report:

- which file was used;
- why it was needed;
- how it was used;
- any missing coverage or matching risks.

