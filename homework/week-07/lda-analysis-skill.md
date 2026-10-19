cae---
name: lda-analysis
description: "Explicitly invoked skill for concise LDA/QDA classification analysis and reporting."
---

# LDA analysis skill

Use only when explicitly requested. This skill is not automatic and should not run unless the user asks for it.

## Purpose
Produce a concise statistical report for a supervised classification problem using only classifiers based on LDA, QDA, or a probability blend of the two. Optional exploratory dimension reduction (for example PCA) is allowed only as a supporting diagnostic; the final model comparison must remain within LDA/QDA-based methods.

## Required inputs
The caller supplies the dataset, response variable, and predictors separately. Do not assume variable names, data structure, or observed results. Keep the analysis generic and dataset-agnostic.

## Analysis guidelines
- State the classification goal and define the candidate models clearly: LDA, QDA, and optionally a hybrid/blended model combining class probabilities from LDA and QDA.
- Check relevant assumptions for the chosen methods, including numeric predictors, class structure, missing values, and class balance.
- If appropriate, examine a lower-dimensional representation such as PCA only as a diagnostic aid for visualization or to reduce dimensionality before fitting LDA/QDA-based classifiers.
- Use a reproducible cross-validation strategy (for example K-fold or repeated holdout) with identical splits across candidate models.
- Report each model’s cross-validated classification performance, including estimated prediction error, accuracy, and a compact summary of the confusion information.
- Select the final model using the lowest estimated prediction error or the strongest defensible balance between accuracy and parsimony.

## Expected report structure
Write a short report of at most one printed page with:
1. A brief introduction describing the classification task.
2. One figure: a clean scatter, score, PCA projection, or class-separation plot that highlights the discriminative structure and the selected model comparison. Use clearly labeled axes and a readable legend.
3. One summary table: candidate models versus cross-validation results (for example error rate, accuracy, and any model-specific tuning or blend weight).
4. A short numerical results section reporting the final fitted model, selected parameters or blend weight, and estimated prediction error.
5. A short discussion of the main findings and limitations, such as class imbalance, high dimension, small sample size, or instability introduced by PCA or blending.

## Output requirements
- Keep the prose concise, factual, and readable.
- Include the key numerical results without unnecessary detail.
- Make the figure and table publication-ready and readable at one-page scale.
- Do not reference specific dataset names, variable names, or observed results from any real dataset.
- Stay within LDA, QDA, or combined LDA/QDA class-probability models only.
