# Domain 6: Model Evaluation and Improvement (9%)

## Core Metrics
| Metric | Formula | Answers |
|---|---|---|
| Accuracy | (TP+TN)/Total | Overall correctness — misleading on imbalanced data |
| Precision | TP/(TP+FP) | Of predicted positives, how many were right? |
| Recall (Sensitivity) | TP/(TP+FN) | Of actual positives, how many were caught? |
| F1 Score | 2*(P*R)/(P+R) | Harmonic mean — balances P and R |
| Specificity | TN/(TN+FP) | Of actual negatives, how many correctly identified? |

## Precision vs Recall — When Each Matters
| Prioritize | Scenario | Risk if wrong |
|---|---|---|
| Recall | Fraud, cancer screening, security threats | Missed positives (FN) are costly |
| Precision | Spam filtering, content recommendations | False alarms (FP) are costly |
| F1 | Balanced need for both | Neither FP nor FN dominates |

## Confusion Matrix (2x2)
```
              Predicted Pos   Predicted Neg
Actual Pos        TP               FN
Actual Neg        FP               TN
```
- Rows = actual, Columns = predicted (verify per tool — convention varies).
- High FN → low recall. High FP → low precision.

## ROC Curve & AUC
| AUC Value | Meaning |
|---|---|
| 1.0 | Perfect classifier |
| 0.5 | Random guessing, no skill |
| < 0.5 | Worse than random (inverted predictions) |
- ROC plots True Positive Rate (Recall) vs False Positive Rate across all thresholds.
- AUC is threshold-independent; use when comparing overall model discrimination ability.

## K-Fold Cross-Validation vs Single Split
| Approach | Best When | Tradeoff |
|---|---|---|
| Single train/test split | Large datasets, fast iteration | High variance on small data |
| K-fold (k=5 or k=10) | Small/limited datasets | More reliable estimate, more compute |
- Stratified k-fold preserves class proportions in each fold — use for imbalanced data.

## Hyperparameter Tuning
| Method | How it works | Best for |
|---|---|---|
| Grid search | Tries every combination | Few hyperparameters, small ranges |
| Random search | Samples combinations randomly | Many hyperparameters, wide ranges, limited compute |
- Grid search cost grows exponentially with number of hyperparameters — exam trap.

## Handling Imbalanced Datasets
| Technique | What it does |
|---|---|
| Oversampling (SMOTE) | Generates synthetic minority-class samples |
| Undersampling | Removes majority-class samples |
| Class weighting | Penalizes misclassifying minority class more heavily in the loss function |
| Metric change | Use F1/Recall/AUC instead of accuracy |

## Exam Traps
- Accuracy paradox: high accuracy on imbalanced data can hide a useless model.
- Confusing precision and recall formulas (TP+FP vs TP+FN denominators).
- F1 is a harmonic mean, NOT a simple average — gets pulled toward the lower score.
- Grid search is not always 'more thorough and better' — it's inefficient in high dimensions.
- Single train/test split on small datasets gives an unreliable, high-variance estimate.
