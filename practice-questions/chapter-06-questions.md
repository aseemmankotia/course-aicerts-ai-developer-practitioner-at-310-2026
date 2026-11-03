## Chapter 6: Domain 6: Model Evaluation and Improvement — Practice Questions

**Q1.** A company builds a model to detect fraudulent credit card transactions, where only 0.5% of transactions are fraudulent. The business wants to minimize missed fraud cases even if it means more false alarms. Which metric should be prioritized?

A) Precision
B) Accuracy
C) Specificity
D) Recall

<details>
<summary>Answer</summary>

**Correct: D**

Recall = TP/(TP+FN) measures the proportion of actual fraud correctly caught. Minimizing missed fraud (false negatives) requires maximizing recall, even at the cost of more false positives.

**Why the others are wrong:**
- Precision focuses on minimizing false positives, which directly conflicts with tolerating more false alarms.
- Accuracy is misleading on a 99.5%/0.5% imbalanced dataset — predicting 'not fraud' for everything yields ~99.5% accuracy while catching zero fraud.
- Specificity measures the true negative rate, which is not aligned with catching fraud cases.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A team builds a spam filter and wants to minimize legitimate emails being incorrectly marked as spam. Which metric should be prioritized?

A) Recall
B) F1 Score
C) AUC
D) Precision

<details>
<summary>Answer</summary>

**Correct: D**

Precision = TP/(TP+FP) directly measures how many predicted-positive (spam) results are actually correct, controlling false positives (good emails flagged as spam).

**Why the others are wrong:**
- Recall focuses on catching all spam, which would increase false positives, the opposite of the goal.
- F1 balances both precision and recall equally rather than specifically prioritizing precision.
- AUC evaluates overall ranking across all thresholds, not a specific false-positive tradeoff.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A binary classifier produces this confusion matrix: TP=85, FP=15, FN=5, TN=895. What is the model's precision?

A) 85%
B) 94.4%
C) 98%
D) 15%

<details>
<summary>Answer</summary>

**Correct: A**

Precision = TP/(TP+FP) = 85/(85+15) = 85/100 = 85%.

**Why the others are wrong:**
- 94.4% is the recall value (85/90), not precision.
- 98% is the overall accuracy ((85+895)/1000), not precision.
- 15% is the false discovery rate's complement component confusion, not the precision formula.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A data scientist has only 500 labeled samples and needs a reliable estimate of model performance before deployment. Which evaluation approach is best?

A) A single 80/20 train/test split
B) Train and test on the full dataset with no holdout
C) A single 50/50 split repeated twice
D) 5-fold or 10-fold cross-validation

<details>
<summary>Answer</summary>

**Correct: D**

K-fold cross-validation trains and evaluates the model across multiple folds and averages the results, reducing variance and giving a more reliable performance estimate when data is limited.

**Why the others are wrong:**
- A single split on only 500 samples has high variance — the estimate depends heavily on which samples happen to land in the test set.
- Training and testing on the same data gives no estimate of generalization and will overstate performance.
- A 50/50 split repeated twice is not a standard technique and still suffers from high variance with half the data held out each run.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** A team needs to tune 6 hyperparameters, each with a wide range of possible values, and has a limited compute budget. Which hyperparameter search strategy is most efficient?

A) Grid search
B) Manual tuning by trial and error
C) Random search
D) Exhaustive search across the full parameter space

<details>
<summary>Answer</summary>

**Correct: C**

Random search samples combinations from the hyperparameter space rather than evaluating every combination, scaling much better than grid search in high-dimensional spaces and often finding near-optimal settings faster within a fixed compute budget.

**Why the others are wrong:**
- Grid search evaluates every combination, scaling exponentially with the number of hyperparameters — infeasible with 6 wide-ranged parameters.
- Manual tuning doesn't scale, is error-prone, and wastes compute budget on guesswork.
- Exhaustive search over a wide range with 6 hyperparameters is computationally infeasible, essentially identical to grid search at scale.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** A dataset has 98% negative class and 2% positive class. A model trained without adjustment predicts the negative class for every sample, achieving 98% accuracy. Which technique BEST addresses this imbalance?

A) Increase the learning rate
B) Report accuracy as the sole evaluation metric
C) Reduce the number of training epochs
D) Use SMOTE to oversample the minority class

<details>
<summary>Answer</summary>

**Correct: D**

SMOTE (Synthetic Minority Oversampling Technique) generates synthetic samples for the minority class, balancing the training distribution so the model can learn minority-class patterns instead of defaulting to the majority class.

**Why the others are wrong:**
- Learning rate controls optimization speed and does not address class imbalance.
- Reporting accuracy alone is exactly the problem — the accuracy paradox masks poor minority-class performance.
- Reducing training epochs does not address the underlying class distribution imbalance.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** What does an AUC (Area Under the ROC Curve) value of 0.5 indicate about a binary classifier?

A) The model perfectly separates both classes
B) The model performs no better than random guessing
C) The model has high precision but low recall
D) The model is overfitting the training data

<details>
<summary>Answer</summary>

**Correct: B**

An AUC of 0.5 means the classifier's true positive rate and false positive rate trade off exactly as random chance would — it has no discriminative ability between classes.

**Why the others are wrong:**
- Perfect separation corresponds to an AUC of 1.0, not 0.5.
- AUC summarizes performance across all thresholds and does not directly indicate the precision/recall balance at a single threshold.
- Overfitting is not directly indicated by a specific AUC value; AUC alone doesn't reveal train-vs-test gap.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** A model achieves 90% precision and 30% recall on a validation set. What is the approximate F1 score?

A) 60%
B) 45%
C) 30%
D) 90%

<details>
<summary>Answer</summary>

**Correct: B**

F1 = 2*(Precision*Recall)/(Precision+Recall) = 2*(0.9*0.3)/(0.9+0.3) = 0.54/1.2 ≈ 0.45, or 45%. The harmonic mean is pulled toward the lower value.

**Why the others are wrong:**
- 60% is the simple arithmetic average of the two values, not the harmonic mean used by F1.
- 30% is just the recall value, ignoring the contribution of precision.
- 90% is just the precision value, ignoring the poor recall score entirely.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

