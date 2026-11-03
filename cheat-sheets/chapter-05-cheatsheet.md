# Domain 5 Cheat Sheet: Machine Learning Fundamentals (9%)

## Learning Paradigms
| Type | Data | Goal | Example Algorithms |
|---|---|---|---|
| Supervised | Labeled | Predict output from input | Linear/Logistic Regression, Decision Tree, KNN |
| Unsupervised | Unlabeled | Find structure/groups | K-means, PCA |
| Reinforcement | None (rewards) | Learn optimal actions via trial/error | Q-learning, policy gradients |

**Exam rule:** Labels present → supervised. No labels, grouping → unsupervised. Rewards/agent/environment → reinforcement.

## Algorithm Quick Reference
| Algorithm | Supervised? | Task | Notes |
|---|---|---|---|
| Linear Regression | Yes | Continuous prediction | Predicts numbers (price, temp) |
| Logistic Regression | Yes | Classification | Despite name, predicts classes via sigmoid |
| Decision Tree | Yes | Classification/Regression | Interpretable, prone to overfitting if unpruned |
| K-Nearest Neighbors (KNN) | Yes | Classification/Regression | Distance-based, needs feature scaling |
| K-Means | No | Clustering | Requires specifying k clusters upfront |

## Train/Validation/Test Split
| Set | Purpose | Typical Ratio |
|---|---|---|
| Train | Fit model parameters | 60–80% |
| Validation | Tune hyperparameters, model selection | 10–20% |
| Test | Final unbiased performance estimate | 10–20% |

**Exam rule:** Test set must NEVER be used during training or tuning — using it early causes data leakage.

## Overfitting vs Underfitting
| Symptom | Train Accuracy | Test Accuracy | Root Cause |
|---|---|---|---|
| Overfitting | High | Low | Model too complex (high variance) |
| Underfitting | Low | Low | Model too simple (high bias) |
| Good fit | High | High (close to train) | Balanced complexity |

## Bias-Variance Tradeoff
- **High Bias** → Underfitting → model misses patterns.
- **High Variance** → Overfitting → model fits noise.
- Goal: minimize total error by balancing both (e.g., via regularization, pruning, cross-validation).

## scikit-learn Fit/Predict Workflow
```python
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

model = LogisticRegression()
model.fit(X_train, y_train)      # learn parameters
predictions = model.predict(X_test)  # apply to new data
score = model.score(X_test, y_test)  # evaluate accuracy
```
**Exam note:** `fit()` always comes before `predict()`. Calling `predict()` on an unfitted model raises `NotFittedError`.

## Common Exam Traps
1. Confusing logistic regression (classification) with linear regression (regression) due to the name.
2. Thinking overfitting means poor performance everywhere — it actually means a LARGE gap between train and test accuracy.
3. Forgetting that k-means requires choosing the number of clusters (k) in advance — it does not discover k automatically.
