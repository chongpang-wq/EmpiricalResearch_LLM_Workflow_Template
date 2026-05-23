# Empirical Specification Registry

This file records approved empirical specifications.

A specification registry helps prevent silent research-design changes during coding, refactoring, or result generation.

## Registry Rule

Before a coding LLM changes code that affects empirical specifications, it must check this file. If the needed specification is missing or ambiguous, stop and ask the human researcher for approval or clarification.

## Template Entry

## SPEC-[SHORT-ID]-[NUMBER]

Purpose:
- [What this specification estimates.]

Unit of observation:
- [Unit]

Sample:
- [Sample restrictions]

Treatment / Main regressor:
- [Variables]

Outcome variables:
- [Variables]

Controls:
- [Controls]

Fixed effects:
- [Fixed effects]

Clustering:
- [Clustering level]

Estimator:
- [OLS / IV / logit / event study / etc.]

Input data:
- [Dataset]

Main scripts:
- [Scripts]

Output files:
- [Outputs]

Interpretation cautions:
- [Cautions]

Approval record:
- Approved by: [Human]
- Date: [Date]
- Notes: [Notes]

## Change Rule

Any change to sample restrictions, variable definitions, controls, fixed effects, clustering, estimators, treatment definitions, or output paths must be recorded here after human approval.
