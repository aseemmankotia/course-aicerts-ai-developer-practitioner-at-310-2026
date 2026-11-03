## Chapter 5: Domain 5: Machine Learning Fundamentals — Practice Questions

**Q1.** A retail company has a dataset of customer purchase histories with NO labeled categories. They want to automatically group customers into segments based on purchasing behavior for a marketing campaign. Which approach BEST meets this requirement?

A) Logistic regression trained on purchase amount to predict segment labels
B) A decision tree classifier using manually assigned segment labels
C) K-means clustering on the purchase feature set
D) K-nearest neighbors to classify customers against a labeled training set

<details>
<summary>Answer</summary>

**Correct: C**

No labels exist, so this is an unsupervised learning problem. K-means groups data into clusters based on feature similarity without needing labeled output.

**Why the others are wrong:**
- Logistic regression is supervised — it requires labeled target classes, which don't exist here.
- Decision trees are supervised classifiers and require pre-existing labels to train on.
- KNN is a supervised algorithm that classifies against a labeled training set, which is unavailable here.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A model achieves 99% accuracy on the training set but only 62% accuracy on the test set. What does this indicate?

A) Underfitting — the model is too simple to capture patterns
B) The model has high bias and needs more features
C) The train/test split was performed incorrectly
D) Overfitting — the model memorized training data and fails to generalize

<details>
<summary>Answer</summary>

**Correct: D**

A large gap between high training accuracy and low test accuracy is the classic signature of overfitting — the model fits noise and specific examples instead of generalizable patterns.

**Why the others are wrong:**
- Underfitting shows LOW accuracy on both training and test sets, not a large gap between them.
- High bias is associated with underfitting, not this scenario, which shows low bias and high variance.
- An incorrect split could skew results, but this specific pattern (train >> test) is the textbook definition of overfitting, not a split issue.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A robotics company wants an agent to learn to navigate a warehouse by receiving positive rewards for reaching a target and penalties for collisions, improving its behavior through trial and error with no labeled dataset. Which learning paradigm does this describe?

A) Reinforcement learning
B) Supervised learning
C) Unsupervised learning
D) Semi-supervised learning

<details>
<summary>Answer</summary>

**Correct: A**

Reinforcement learning involves an agent learning optimal actions through trial-and-error interactions with an environment, guided by rewards and penalties rather than labeled examples.

**Why the others are wrong:**
- Supervised learning requires labeled input-output pairs, which are absent in this reward-based scenario.
- Unsupervised learning finds structure in unlabeled data but does not involve rewards, penalties, or sequential decision-making.
- Semi-supervised learning combines small amounts of labeled data with large amounts of unlabeled data — not applicable here since no labels exist at all.

</details>

---

**Q4.** A team needs to predict a continuous numeric value (house price) from features like square footage and number of bedrooms. Which algorithm is the MOST appropriate starting point?

A) K-means clustering
B) Logistic regression
C) K-nearest neighbors for classification
D) Linear regression

<details>
<summary>Answer</summary>

**Correct: D**

Linear regression is designed to predict continuous numeric outputs from input features, making it the standard baseline for price prediction tasks.

**Why the others are wrong:**
- K-means is an unsupervised clustering algorithm and does not predict continuous target values.
- Logistic regression predicts categorical/class probabilities (e.g., yes/no), not continuous numeric values — a common point of confusion due to the similar name.
- KNN for classification predicts discrete class labels, not continuous numeric outputs.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** Which of the following is the standard purpose of splitting data into separate training, validation, and test sets?

A) To reduce the total amount of data the model needs to process
B) To train on all available data simultaneously for maximum accuracy
C) To train the model, tune hyperparameters without leaking test data, and get an unbiased final performance estimate
D) To create multiple copies of the same dataset for redundancy

<details>
<summary>Answer</summary>

**Correct: C**

Training data fits the model, validation data tunes hyperparameters and selects models, and the test set — untouched until the end — gives an unbiased estimate of real-world generalization performance.

**Why the others are wrong:**
- Splitting data does not reduce overall processing volume; it partitions the same dataset for different purposes.
- Training on all data simultaneously prevents any unbiased evaluation and risks undetected overfitting.
- The split is not about redundancy — each subset serves a distinct, non-overlapping evaluation purpose.

</details>

---

**Q6.** In scikit-learn, which code sequence correctly represents the standard supervised learning workflow?

A) model.predict(X_test) then model.fit(X_train, y_train)
B) model.fit(X_test, y_test) then model.predict(X_train)
C) model.fit(X_train, y_train) then model.predict(X_test)
D) model.predict(X_train, y_train) then model.fit(X_test)

<details>
<summary>Answer</summary>

**Correct: C**

The correct order is fit() on training data (features and labels) to learn parameters, then predict() on unseen test features to generate outputs.

**Why the others are wrong:**
- Calling predict() before fit() will raise a NotFittedError since the model has no learned parameters yet.
- Fitting on the test set contaminates evaluation and causes data leakage — the model should never be trained on test data.
- predict() does not accept a labels argument (y_train) — it only takes feature inputs, making this call invalid.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A model has high bias and low variance. Which statement BEST describes its likely behavior?

A) It performs very well on training data but poorly on new data
B) It performs poorly on both training and test data because it is too simple to capture underlying patterns
C) It perfectly memorizes training data with no generalization capability
D) It performs well on both training and test data with no errors

<details>
<summary>Answer</summary>

**Correct: B**

High bias means the model makes overly simplistic assumptions (underfitting), leading to poor performance on both training and test sets.

**Why the others are wrong:**
- Good training performance with poor test performance describes high variance (overfitting), not high bias.
- Perfect memorization with no generalization describes a high-variance, overfit model, not a high-bias one.
- High bias models underperform on training data as well — they cannot fit the data well in the first place.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** A dataset has labeled categories, and the team needs to classify new emails as 'spam' or 'not spam' using features like word frequency. Which type of algorithm is required?

A) Unsupervised clustering algorithm
B) Reinforcement learning agent
C) Dimensionality reduction algorithm
D) Supervised classification algorithm such as logistic regression or decision tree

<details>
<summary>Answer</summary>

**Correct: D**

Since labeled categories (spam/not spam) exist and the goal is to predict a discrete class, a supervised classification algorithm like logistic regression or a decision tree is required.

**Why the others are wrong:**
- Unsupervised clustering does not use existing labels and is unnecessary when labeled categories are already available.
- Reinforcement learning requires sequential decisions and rewards, not a static labeled dataset.
- Dimensionality reduction is a preprocessing technique, not a classification method — it would not produce spam/not-spam predictions on its own.

</details>

---

