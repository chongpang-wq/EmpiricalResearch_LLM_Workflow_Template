# Full Silent Research Bug Checklist

Use this checklist only when the human researcher explicitly asks for a comprehensive empirical-code audit.

The purpose is to detect silent research bugs: errors that do not stop code from running but may change the empirical meaning, sample, estimates, standard errors, tables, figures, or interpretation.

## Review Principles

For every item, report one of: Pass, Risk, Fail, or Not checked. Do not claim an item is checked unless there is direct evidence from code, logs, output, or documentation.

## Audit Areas

1. Sample and observation loss
   - What changes N?
   - Are all drops intentional and documented?
   - Does the regression sample match the stated design?

2. Merge, append, and duplicate risks
   - Are merge keys correct?
   - Are key variables unique on the intended side?
   - Are unmatched rows and duplicates inspected?
   - Avoid many-to-many merges unless explicitly justified.

3. Unit of observation
   - What is the unit before and after collapse, reshape, merge, or aggregation?
   - Are weights and clusters consistent with the unit?

4. Specification consistency
   - Does code match the reported equation?
   - Are outcome, treatment, controls, fixed effects, clustering, weights, sample, and estimator consistent with documentation?

5. Fixed effects
   - Is A x B FE coded as interaction FE rather than A FE plus B FE?
   - Are singleton drops reported?
   - Are treatment variables absorbed by fixed effects?

6. Clustering and standard errors
   - Is clustering at the treatment variation level?
   - Are there too few clusters?
   - Do table notes match the code?

7. Variable construction
   - Are logs, directions, labels, missing codes, baseline years, denominators, and transformations correct?
   - Are percent and proportion variables mixed?

8. Missing values and special codes
   - Are special missing codes converted correctly?
   - Are missing values recoded as zero only with justification?
   - In Stata, avoid comparisons that treat missing values as very large numbers.

9. Weights
   - Are weight type and level correct?
   - Are weights appropriate after aggregation?
   - Are weighted and unweighted results clearly distinguished?

10. Time, panels, leads, lags, and exposure windows
    - Are panel IDs and time variables correct?
    - Are leads/lags generated after sorting?
    - Are event time signs and exposure windows correct?

11. Treatment and control group construction
    - Are treatment timing, never-treated, not-yet-treated, and control groups handled correctly?
    - Are treatment reversals or multiple treatments documented?

12. Outcome and model compatibility
    - Are binary, ordered, count, fractional, log, and PPML models used with compatible outcomes?

13. Controls and bad controls
    - Are controls pre-treatment?
    - Are mediators, colliders, or post-treatment variables included without justification?

14. Numerical and estimation issues
    - Check non-convergence, dropped variables, absorption, separation, weak IV, implausible coefficients, and suspicious fit.

15. IV and first-stage diagnostics
    - Are endogenous variables and instruments correctly specified?
    - Are first-stage diagnostics reported?
    - Are first and second stage samples consistent?

16. Event studies and dynamic effects
    - Are reference periods, lead/lag labels, bins, and pre-trend tests correct?

17. Robustness, placebo, and falsification tests
    - Does each robustness test implement the stated change?
    - Is a placebo truly placebo?

18. Output, tables, and figures
    - Do labels, notes, standard errors, stars, sample sizes, and figure axes match the code?
    - Are stale outputs avoided?

19. Reproducibility and file dependencies
    - Is there a clear run order?
    - Are paths, packages, seeds, intermediate files, and external dependencies documented?

20. Stata-specific risks
    - Missing values in comparisons.
    - Factor-variable syntax.
    - Sorting before by-group lag/lead generation.
    - Empty or overwritten macros.

21. Python-specific risks
    - Chained assignment.
    - Default inner joins.
    - `fillna(0)` without justification.
    - Lag/lead without sorting.
    - ID precision loss or lost leading zeros.

22. China empirical research risks
    - Administrative boundary changes.
    - Code/name matching ambiguity.
    - Monetary units, RMB/USD conversion, nominal vs real values, and deflation.

## Required Audit Report

For each issue found, report:

- file and line or code block;
- risk type;
- why it matters for research interpretation;
- suggested fix;
- whether the fix is analytical or non-analytical;
- whether human approval is required.
