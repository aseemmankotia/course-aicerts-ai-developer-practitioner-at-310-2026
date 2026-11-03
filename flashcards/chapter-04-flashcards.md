## Chapter 4: Domain 4: Practical Mathematics and Statistics for AI — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Matrix multiplication shape rule for A(m×n) × B(p×q)? | Valid only if n=p (inner dimensions match). Result shape = m×q. Exam tip: check inner dimensions first — mismatch means multiplication is undefined. |
| 2 | Is matrix multiplication commutative (A×B = B×A)? | No — generally A×B ≠ B×A, even when both are defined. Exam tip: order matters; swapping matrices changes the result or may make it invalid. |
| 3 | Dot product formula for vectors A=[a1,a2,a3] and B=[b1,b2,b3]? | a1*b1 + a2*b2 + a3*b3 — sum of elementwise products. Exam tip: a dot product of 0 means the vectors are orthogonal (unrelated). |
| 4 | When does the Binomial distribution apply? | Fixed number of independent trials, each with two outcomes (success/failure) and constant probability p. Exam tip: look for 'n trials', 'fixed probability', 'yes/no' language in the scenario. |
| 5 | When does the Normal distribution apply? | Continuous data that is symmetric and bell-shaped around the mean. Exam tip: 68-95-99.7 rule — 68% of values within 1 SD, 95% within 2 SD, 99.7% within 3 SD. |
| 6 | Population standard deviation denominator vs sample standard deviation denominator? | Population: divide by N. Sample: divide by n-1 (Bessel's correction). Exam tip: the sample formula corrects for bias when estimating from a subset of the population. |
| 7 | Mean vs Median — which is robust to outliers? | Median. Mean is pulled toward extreme values; median reflects the middle value regardless of outliers. Exam tip: for skewed data (income, house prices), use median. |
| 8 | Mode definition | The most frequently occurring value in a dataset. Exam tip: a dataset can have no mode, one mode (unimodal), or multiple modes (multimodal). |
| 9 | Variance formula (population) | σ² = Σ(x - μ)² / N — average of squared deviations from the mean. Exam tip: variance is in squared units; standard deviation (√variance) restores original units. |
| 10 | Correlation vs Causation — key exam rule | High correlation (even r=0.9+) does NOT prove one variable causes the other. Watch for confounding (third) variables. Exam tip: classic example — ice cream sales and drownings both driven by hot weather. |
| 11 | Vectors/matrices in ML — what do rows and columns typically represent? | Rows = samples/observations, Columns = features. Weight matrices transform feature vectors into outputs via matrix multiplication. Exam tip: input shape (samples, features) × weights (features, outputs) = output (samples, outputs). |
| 12 | Z-score formula and meaning | z = (x - μ) / σ — number of standard deviations a value is from the mean. Exam tip: used to standardize data and flag outliers (\|z\| > 3 is commonly flagged). |
