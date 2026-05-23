# Monetary Units and Deflation Skill

Use this skill when code reads, constructs, merges, compares, converts, deflates, logs, or interprets monetary variables.

## Core Rules

1. Always confirm the currency and unit before calculation:
   - currency: RMB, USD, EUR, HKD, local currency, etc.
   - unit: yuan, thousand, ten-thousand, million, billion, 100 million, etc.
   - price basis: nominal/current price vs real/constant price.
   - time basis: year, month, fiscal year, survey wave.

2. Never guess exchange rates or deflators.

3. If exchange-rate data are not already available in the project, use code to fetch or read from a reliable source and document:
   - source;
   - download date;
   - currency pair;
   - direction, e.g. local currency per USD;
   - year/frequency.

4. For historical economic variables, do not use real-time exchange rates unless explicitly requested. Prefer annual average or official annual exchange rates.

## Deflation Rule

Always distinguish:

- nominal level;
- real level;
- nominal growth;
- real growth;
- price index / deflator;
- already-deflated variables.

Do not deflate a variable twice.

If project data do not already provide deflators, use code to read the country-level GDP deflator panel in:

```text
reference_data/exchange_rate.csv
```

The GDP deflator source should be documented as:

```text
World Bank World Development Indicators
```

If required country-year deflator coverage is missing, report the missing coverage instead of fabricating values.

## Common Silent Bugs

Check for:

- mixing yuan, ten-thousand yuan, and 100 million yuan;
- mixing RMB and USD;
- using USD per local currency as if it were local currency per USD;
- logging zero or negative monetary values without explanation;
- comparing nominal values across years;
- using GDP deflator when CPI or another deflator is conceptually required;
- treating real growth and nominal growth as the same;
- merging exchange-rate or deflator data by the wrong year or country code;
- silently treating missing exchange rates or deflators as 1.

## Required Report

After monetary conversion or deflation, report briefly:

```text
Variable:
Original currency/unit:
Target currency/unit:
Nominal or real:
Exchange rate source:
Deflator source:
Base year:
Formula used:
Missing coverage:
Remaining risks:
```
