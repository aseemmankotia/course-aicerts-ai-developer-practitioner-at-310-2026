# Domain 4 Cheat Sheet: Practical Math & Stats for AI

## Matrix Multiplication Rule
| A shape | B shape | Valid? | Result shape |
|---|---|---|---|
| (m,n) | (n,q) | Yes | (m,q) |
| (m,n) | (p,q), p≠n | No | undefined |

- Inner dimensions MUST match (n=p).
- Matrix multiplication is **NOT commutative**: A×B ≠ B×A.
- Dot product of two vectors = sum of elementwise products; result of 0 = orthogonal (unrelated) vectors.
- In ML: rows = samples, columns = features. Input(samples,features) × Weights(features,outputs) = Output(samples,outputs).

## Probability Distributions
| Distribution | Data type | Use when |
|---|---|---|
| Normal | Continuous | Symmetric, bell-shaped data; 68-95-99.7 rule applies |
| Binomial | Discrete | Fixed n independent trials, two outcomes, constant p |
| Poisson | Discrete | Count of rare events over time/space, no fixed trial count |
| Uniform | Discrete/Continuous | All outcomes equally likely |

**Exam trap:** 'fixed number of trials' + 'success/failure' = Binomial, NOT Normal.

## Descriptive Statistics
| Measure | Formula | Robust to outliers? |
|---|---|---|
| Mean | Σx / n | No |
| Median | middle value (sorted) | Yes |
| Mode | most frequent value | N/A |
| Variance (population) | Σ(x-μ)² / N | No |
| Std Dev (population) | √(population variance) | No |
| Variance (sample) | Σ(x-x̄)² / (n-1) | No |
| Std Dev (sample) | √(sample variance) | No |

**Rule:** Use N for population, n-1 (Bessel's correction) for sample — exam tests this distinction heavily.

**Skewed data (income, outliers present)** → report median, not mean.

## Z-score
z = (x - μ) / σ
- Standardizes values to compare across distributions.
- |z| > 3 often flagged as an outlier.

## Correlation vs Causation
- Correlation coefficient (r) ranges from -1 to 1; measures strength/direction of linear association ONLY.
- High correlation (even r=0.9) **never proves causation**.
- Always consider confounding (third) variables before assuming a causal link.
- Classic exam example: ice cream sales ↔ drowning rates — both driven by hot weather, not each other.

## Quick Decision Guide
- Discrete count, fixed trials → **Binomial**
- Continuous, symmetric, bell curve → **Normal**
- Rare events over interval → **Poisson**
- Outliers present → use **median**, not mean
- Full population known → divide by **N**
- Working from a sample → divide by **n-1**
