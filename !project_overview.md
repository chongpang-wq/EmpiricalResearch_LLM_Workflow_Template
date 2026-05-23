# Project Overview: [PROJECT_TITLE]

This file is the project-level research overview. It should be updated during initialization and throughout the project as the research design becomes clearer.

## Purpose

Use this document to summarize the project's research question, motivation, conceptual mechanism, data structure, empirical strategy, and paper framing.

Do not use this document as a full transcript or code inventory. Keep it focused on research logic.

## 1. Project Description

[Fill after the human researcher provides the project description.]

## 2. Core Research Question

[Fill after initialization.]

## 3. Main Mechanism or Hypothesis

[Describe the main causal chain, mechanism, or empirical relationship.]

```text
[Cause / shock / treatment]
        ->
[Intermediate mechanism]
        ->
[Outcome]
```

## 4. Data Sources

[Summarize the main datasets after raw data are added or linked.]

For each important data source, record:

- source name;
- raw-data location;
- unit of observation;
- key identifiers;
- time coverage;
- geographic coverage;
- source documentation;
- access or citation restrictions;
- known caveats.

## 5. Identification Strategy

[Describe the empirical strategy after the human researcher approves it.]

Do not invent an identification strategy. If unclear, list open questions in `open_questions.md`.

## 6. Main Variables

### Treatment / Main Regressors

[Fill later.]

### Outcomes

[Fill later.]

### Controls / Fixed Effects / Clustering

[Fill only after approved.]

## 7. Current Empirical Narrative

[Fill after preliminary results exist.]

## 8. What Not To Claim

Update this section as the project matures.

Default cautions:

- Do not interpret correlations as causal without an approved design.
- Do not claim mechanisms that are not directly tested or supported.
- Do not ignore unit-of-observation, sample-selection, or clustering issues.
- Do not treat manually edited outputs as the source of truth.
- Do not use example data for analysis.

## 9. Suggested Paper Structure

[Fill when the project is ready for writing.]

## 10. Open Research Questions

Keep durable open questions in `open_questions.md`. Use this section only for a short summary.

## 11. Guide for Future LLM Assistance

Future LLMs should:

- read startup documentation first;
- preserve approval boundaries;
- distinguish research advice from implementation;
- avoid silent specification changes;
- keep project documentation layered;
- update `!llm_record.md` after materially useful conversations or approved changes.
