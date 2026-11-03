## Chapter 6: Domain 6: Model Evaluation and Improvement — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Precision formula? | TP/(TP+FP). Exam tip: Precision answers 'Of all predicted positives, how many were correct?' Prioritize when false positives are costly (e.g., spam filter). |
| 2 | Recall formula? | TP/(TP+FN). Exam tip: Recall answers 'Of all actual positives, how many did we catch?' Prioritize when false negatives are costly (e.g., fraud or disease detection). |
| 3 | F1 score formula? | 2*(Precision*Recall)/(Precision+Recall) — the harmonic mean. Exam tip: F1 is pulled toward the lower of the two values, unlike a simple average. |
| 4 | Confusion matrix: what does a False Negative represent? | An actual positive predicted as negative (a missed detection). Exam tip: a high FN count means low recall — dangerous in medical or fraud scenarios. |
| 5 | AUC values: 1.0 vs 0.5 vs below 0.5 — what do they mean? | 1.0 = perfect classifier; 0.5 = no better than random guessing; below 0.5 = worse than random (predictions effectively inverted). Exam tip: AUC measures ranking ability across all thresholds. |
| 6 | What is the 'accuracy paradox'? | On imbalanced datasets, a model that always predicts the majority class can still show high accuracy while being useless for the minority class. Exam tip: always check precision/recall/F1 on imbalanced data, not just accuracy. |
| 7 | K-fold cross-validation vs single train/test split — when to prefer k-fold? | Prefer k-fold (commonly k=5 or k=10) on small/limited datasets for a more reliable, lower-variance performance estimate by averaging across multiple folds. Exam tip: a single split risks a lucky or unlucky partition. |
| 8 | Grid search vs random search — key tradeoff? | Grid search exhaustively evaluates every combination (cost grows exponentially with number of hyperparameters). Random search samples combinations randomly, scaling better and often finding near-optimal results faster. Exam tip: choose random search when tuning many hyperparameters under a limited compute budget. |
| 9 | What does SMOTE do? | Synthetic Minority Oversampling Technique — generates synthetic samples for the minority class to balance a skewed training set. Exam tip: used to address class imbalance instead of relying on accuracy alone. |
| 10 | Name 3 techniques for handling imbalanced datasets. | 1) Oversampling the minority class (e.g., SMOTE), 2) Undersampling the majority class, 3) Adjusting class weights in the loss function. Exam tip: also switch the evaluation metric to F1/recall/AUC instead of plain accuracy. |
| 11 | Confusion matrix layout — standard axis convention? | Typically rows = actual class, columns = predicted class (some tools reverse this). Exam tip: always verify axis labels on a given matrix before computing metrics — never assume orientation. |
| 12 | When does precision matter more than recall? | When false positives are costly — e.g., spam filtering (don't want good email marked as spam). Exam tip: recall matters more when false negatives are costly — e.g., cancer screening or fraud detection. |
