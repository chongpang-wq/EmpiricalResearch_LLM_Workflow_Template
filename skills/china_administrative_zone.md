# China Administrative Division Matching Skill

Use only for matching or merging Chinese administrative units.

## `reference_data/code_year_region.csv`

`reference_data/code_year_region.csv` is the complete China year-region administrative division list available for this template.

Use it only when an administrative-division match fails and code-based search of this reference file may help resolve the match.

When using `reference_data/code_year_region.csv`, the agent must report this to the human researcher, including why it was needed and how it was used.

## Core Rules

1. Do not assume a code is an administrative division code just because it looks like one. First verify whether it is:
   - official administrative code;
   - statistical code;
   - survey/internal code;
   - truncated/transformed code;
   - historical code from a specific year.

2. Prefer verified codes over names. Preferred order:
   - verified code + year;
   - harmonized code at the correct administrative level;
   - province + standardized name;
   - reviewed fuzzy match;
   - manual crosswalk.

3. Always confirm the administrative level on both sides:
   - province;
   - prefecture/city;
   - county/district;
   - municipality special case.

## Code Cautions

Check for:

- numeric/string conversion errors;
- lost leading zeros;
- 6-digit vs truncated codes;
- county codes mistaken for prefecture codes;
- mixed province/prefecture/county levels;
- boundary-year mismatch.

For municipalities, codes may appear in different formats. In particular, the fourth digit may be `0` or `1` depending on source or transformation. Do not treat them as different places without checking the coding rule.

## Name Matching Cautions

If matching by name, preserve:

- original name;
- cleaned name;
- matched name;
- province;
- administrative level;
- match method.

Watch for duplicate names across provinces, prefecture-level vs county-level cities, county-to-district changes, renamed places, and suffix removal errors.

## Manual Crosswalk Rule

Any manual fix must be recorded in a crosswalk, not hidden in code.

Record at least:

- source dataset/year/code/name;
- target year/code/name;
- administrative level;
- match type;
- confidence;
- reason or note.

## Required Merge Report

After any administrative match, report:

```text
Code variables used:
Code type verified? yes/no/uncertain
Administrative levels:
Match method:
Matched:
Unmatched:
Duplicates:
Many-to-many cases:
Manual fixes:
Remaining risks:
```
