# Codex Instructions

Before editing or reviewing empirical code, prioritize silent research bugs over style issues. Do not approve code merely because it runs. Check the following before approving code:

1. Sample: What changes N? Are drops intentional?
2. Merge: Are keys correct? Are unmatched rows and duplicates inspected?
3. Unit: What is the unit before and after collapse/reshape/merge?
4. Variables: Are logs, directions, labels, and missing codes correct?
5. Timing: Are leads, lags, windows, cohorts, and policy years aligned?
6. Specification: Does code match the reported equation?
7. Fixed effects: Is A x B FE coded as interaction FE, not A FE + B FE?
8. Clustering: Is clustering at the treatment variation level?
9. Weights: Are weights correct for the observation level?
10. Estimation: Any non-convergence, absorption, weak IV, or suspicious fit?
