---
name: SVM_Analysis
description: Use when explicitly asked to assess, tune, evaluate, and report a support vector machine analysis.
metadata:
  version: "1.0.0"
---

# SVM Analysis

1. Check sample size, response type, predictor types, missingness, class balance, scaling needs, and whether a margin-based or nonlinear boundary is plausible. State limitations that affect SVM suitability.
2. Consider a linear kernel as a baseline and nonlinear kernels only when justified. Explain each kernel considered and identify all fixed settings.
3. Tune relevant parameters, including `C` and kernel-specific parameters such as polynomial degree or RBF `gamma`. Use a bounded, reproducible search and a common stratified cross-validation split for candidates.
4. Put imputation, encoding, feature selection, and scaling inside a scikit-learn `Pipeline` so every transform is fitted using only its training fold. Do not preprocess the full data before splitting.
5. Select the model using training data only, preferably cross-validation. Keep a stratified holdout test set untouched until selection is complete; evaluate the chosen model on it once. Never use test results to revise or choose a model.
6. Report the selection metric and relevant final test metrics, including uncertainty or class-specific performance when useful. Compare the selected model with a simple baseline and interpret results without causal claims.
7. Include a compact table of candidate settings and selection scores and a figure that makes the choice and performance evidence clear. Ensure they agree with the computed results.
8. Write a concise report with the data, procedure, key numerical results, interpretation, and reason for preferring the final model. Keep the report to at most one printed page at 11-point font; prioritize selection evidence over background.
9. Make code and randomness reproducible. Verify reported values against executable output, and clearly distinguish cross-validation selection results from final test performance.
