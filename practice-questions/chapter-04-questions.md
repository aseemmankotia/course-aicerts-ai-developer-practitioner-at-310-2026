## Chapter 4: Domain 4: Practical Mathematics and Statistics for AI — Practice Questions

**Q1.** A data scientist has matrix A with shape (3,4) representing 3 samples with 4 features, and wants to compute A×W to produce 3 samples with 2 output predictions. What shape must W have?

A) (2,4)
B) (3,2)
C) (4,3)
D) (4,2)

<details>
<summary>Answer</summary>

**Correct: D**

Inner dimensions must match: A is (3,4), so W must start with 4 rows. Output shape is (3,2), so W must end with 2 columns → (4,2).

**Why the others are wrong:**
- (2,4): inner dimensions don't match (A's columns=4, W's rows=2) — multiplication undefined
- (3,2): inner dimensions don't match (4 vs 3) — multiplication undefined
- (4,3): valid inner dimensions but produces output shape (3,3), not (3,2)

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** An ML engineer is modeling the number of successes in 50 independent yes/no trials, each with a fixed probability of success. Which distribution best models this scenario?

A) Normal
B) Poisson
C) Binomial
D) Uniform

<details>
<summary>Answer</summary>

**Correct: C**

A fixed number of independent Bernoulli (yes/no) trials with constant probability of success is the definition of a Binomial distribution.

**Why the others are wrong:**
- Normal: models continuous, symmetric data like heights — not discrete trial counts
- Poisson: models count of rare events over a time/space interval without a fixed number of trials
- Uniform: assumes all outcomes are equally likely, which doesn't apply to success/failure trials

</details>

---

**Q3.** A dataset of exam scores is symmetric, bell-shaped, and 95% of scores fall within 2 standard deviations of the mean. Which distribution does this describe?

A) Binomial
B) Normal
C) Poisson
D) Exponential

<details>
<summary>Answer</summary>

**Correct: B**

A symmetric bell curve following the 68-95-99.7 rule is the defining characteristic of a Normal distribution.

**Why the others are wrong:**
- Binomial: discrete distribution for fixed trials, not continuous symmetric data
- Poisson: models rare event counts, typically right-skewed, not symmetric
- Exponential: models time between events, is skewed, not bell-shaped

</details>

---

**Q4.** A dataset of household incomes contains a few extremely high outliers alongside mostly moderate incomes. Which measure BEST represents the 'typical' household income?

A) Mean
B) Mode
C) Median
D) Variance

<details>
<summary>Answer</summary>

**Correct: C**

Median is robust to outliers because it reflects the middle value and is unaffected by extreme values.

**Why the others are wrong:**
- Mean: gets pulled upward by extreme high outliers, producing a misleading 'typical' value
- Mode: may not exist or may not represent the center of the distribution
- Variance: measures spread, not central tendency, so it doesn't answer the question

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** A data scientist has access to the entire population of 10,000 customer records and computes standard deviation to describe purchase amount variability. Which denominator should be used?

A) n-1
B) n+1
C) n
D) sqrt(n)

<details>
<summary>Answer</summary>

**Correct: C**

When the full population is available, population standard deviation uses N (the full count) as the denominator.

**Why the others are wrong:**
- n-1: Bessel's correction is used only for sample standard deviation to estimate population variance from a subset
- n+1: not a standard statistical formula
- sqrt(n): used in standard error of the mean calculations, not the standard deviation formula itself

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** A study finds ice cream sales and drowning incidents are highly correlated (r=0.9). What is the MOST accurate interpretation?

A) Ice cream sales cause drowning incidents
B) Drowning incidents cause increased ice cream sales
C) Both are likely influenced by a third variable (hot weather); correlation does not imply causation
D) The correlation coefficient proves a causal relationship exists

<details>
<summary>Answer</summary>

**Correct: C**

This is a classic confounding variable scenario — hot weather increases both ice cream sales and swimming (and thus drowning risk). High correlation never proves causation.

**Why the others are wrong:**
- Assumes direct causation without any mechanistic evidence
- Reverses an implausible causal direction with no supporting evidence
- Misinterprets correlation coefficients, which only measure association strength, not causal proof

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A recommendation system represents two product vectors as A=[2,0,1] and B=[0,1,-2]. What is the dot product of A and B?

A) -2
B) 0
C) 2
D) 3

<details>
<summary>Answer</summary>

**Correct: A**

Dot product = (2×0) + (0×1) + (1×-2) = 0 + 0 - 2 = -2.

**Why the others are wrong:**
- 0 would mean the vectors are orthogonal, which is not the case given the actual elementwise products
- 2 results from a sign error when multiplying the last pair of elements
- 3 results from incorrectly summing the elements instead of their products

</details>

---

**Q8.** When calculating sample variance from a random sample of 20 observations to estimate the population variance, which correction is applied to the denominator?

A) Divide by n = 20
B) Divide by n+1 = 21
C) Divide by sqrt(n)
D) Divide by n-1 = 19

<details>
<summary>Answer</summary>

**Correct: D**

Sample variance uses n-1 (Bessel's correction) in the denominator to produce an unbiased estimator of the true population variance.

**Why the others are wrong:**
- Dividing by n is used for population variance when the full population is known, not for a sample estimate
- n+1 is not a recognized statistical correction
- sqrt(n) is used in standard error calculations, not in the variance formula

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

