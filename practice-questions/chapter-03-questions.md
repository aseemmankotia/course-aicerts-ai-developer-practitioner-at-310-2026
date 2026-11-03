## Chapter 3: Domain 3: Data Handling and Visualization — Practice Questions

**Q1.** A dataset column 'sensor_reading' is missing in 68% of the 5,000 rows due to a broken sensor during data collection. Which approach is MOST appropriate before modeling?

A) Impute missing values using the column mean
B) Impute missing values using KNN imputation
C) Replace missing values with zero
D) Drop the column entirely

<details>
<summary>Answer</summary>

**Correct: D**

When over half the values are missing, any imputation method is mostly fabricating data; dropping the column preserves data integrity better than inventing the majority of its values.

**Why the others are wrong:**
- Mean imputation would fabricate 68% of the column's values, severely distorting its distribution and any relationship to the target.
- KNN imputation is more sophisticated but still estimates the majority of the data, making it unreliable at this missingness level.
- Zero-filling assumes zero is a meaningful reading and badly skews the data distribution.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A dataset is stored as a JSON file with nested objects, e.g. {'id':1,'address':{'city':'NY','zip':'10001'}}. Which pandas function correctly flattens this into separate 'address.city' and 'address.zip' columns?

A) pd.json_normalize()
B) pd.read_json()
C) pd.DataFrame.from_dict()
D) pd.concat()

<details>
<summary>Answer</summary>

**Correct: A**

json_normalize() is built specifically to flatten nested JSON structures into flat columns using dot notation.

**Why the others are wrong:**
- read_json() loads JSON into a DataFrame but keeps nested dict objects as single column values rather than flattening them.
- from_dict() converts a dict of arrays into a DataFrame but does not recursively flatten nested keys.
- concat() combines existing DataFrames; it has no role in parsing or flattening JSON.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** You one-hot encode a categorical column 'region' with 4 categories using pd.get_dummies(df['region']). To avoid introducing perfect multicollinearity into a linear regression model, which parameter should you set?

A) sparse=True
B) dummy_na=True
C) drop_first=True
D) prefix='region'

<details>
<summary>Answer</summary>

**Correct: C**

drop_first removes one category's dummy column, eliminating the linear dependency between dummy columns known as the dummy variable trap.

**Why the others are wrong:**
- sparse controls internal storage format, not multicollinearity.
- dummy_na adds a column for missing values; it does not address multicollinearity.
- prefix only renames columns for readability; it has no effect on multicollinearity.

</details>

---

**Q4.** An analyst wants to check a single numeric column ('order_value') for outliers and visualize its quartiles and median in one chart. Which plot type is the BEST choice?

A) Scatter plot
B) Heatmap
C) Box plot
D) Line plot

<details>
<summary>Answer</summary>

**Correct: C**

Box plots explicitly display the median, IQR (quartiles), and whiskers, and flag points beyond 1.5×IQR as outliers — exactly what's needed here.

**Why the others are wrong:**
- Scatter plots show relationships between two variables, not the distribution of one variable.
- Heatmaps visualize magnitude across a matrix of two dimensions (e.g., correlations), not a single variable's distribution.
- Line plots suit ordered/sequential data like time series, not a distribution summary.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** A dataset has 'income' ranging from $20,000 to $500,000 and 'age' ranging from 18 to 90. You are training a K-Nearest Neighbors model, which is distance-based. Which preprocessing step is MOST important before training?

A) One-hot encode both features
B) Apply feature scaling (standardization or normalization) to both features
C) Drop the 'income' feature
D) Apply label encoding to 'age'

<details>
<summary>Answer</summary>

**Correct: B**

Distance-based algorithms like KNN are sensitive to feature scale; without scaling, 'income' would dominate the distance calculation over 'age'.

**Why the others are wrong:**
- One-hot encoding applies to categorical variables, not continuous numeric ones like income and age.
- Dropping income discards potentially useful information instead of fixing the scale mismatch.
- Label encoding is for categorical variables; applying it to a continuous numeric variable like age destroys its numeric meaning.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** Which scikit-learn transformation rescales features to a fixed range of [0,1] by default?

A) StandardScaler
B) MinMaxScaler
C) LabelEncoder
D) OneHotEncoder

<details>
<summary>Answer</summary>

**Correct: B**

MinMaxScaler (normalization) linearly rescales each feature into a specified range, [0,1] by default.

**Why the others are wrong:**
- StandardScaler (standardization) transforms data to zero mean and unit variance, not a bounded [0,1] range.
- LabelEncoder assigns integer labels to categorical values; it does not rescale numeric ranges.
- OneHotEncoder creates binary indicator columns for categories and is unrelated to numeric scaling.

</details>

---

**Q7.** What is the key difference between label encoding and one-hot encoding for a nominal (unordered) categorical variable?

A) Label encoding creates one binary column per category; one-hot encoding assigns a single integer per category
B) Label encoding assigns a single integer per category, which can imply a false ordinal relationship; one-hot encoding creates a binary column per category, avoiding that implication
C) They produce identical results for nominal variables
D) One-hot encoding only works on numeric columns

<details>
<summary>Answer</summary>

**Correct: B**

This correctly states the core distinction tested on the exam: label encoding risks implying order where none exists, while one-hot encoding avoids it.

**Why the others are wrong:**
- This reverses the actual definitions of the two encoding methods.
- They are not identical — label encoding introduces an ordinal assumption that one-hot encoding avoids.
- One-hot encoding is specifically designed for categorical (often string) columns, not numeric-only data.

</details>

---

**Q8.** During EDA on a dataset with 15 numeric features, an analyst wants to quickly identify which pairs of features are highly correlated before building a regression model. Which visualization BEST supports this task?

A) Scatter plot of each pair individually (105 plots)
B) Box plot per feature
C) Histogram per feature
D) Correlation heatmap

<details>
<summary>Answer</summary>

**Correct: D**

A correlation heatmap displays the correlation coefficient for every feature pair in one color-coded matrix, making it fast to spot multicollinearity.

**Why the others are wrong:**
- Plotting 105 individual scatter plots is technically possible but impractical compared to a single heatmap.
- Box plots show distribution and outliers per feature, not pairwise relationships.
- Histograms show a single feature's distribution, not relationships between features.

</details>

---

