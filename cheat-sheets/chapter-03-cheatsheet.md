# Domain 3 Cheat Sheet: Data Handling and Visualization

## Loading Data
| Source | Pandas Function |
|---|---|
| CSV | `pd.read_csv(path)` |
| JSON (flat) | `pd.read_json(path)` |
| JSON (nested) | `pd.json_normalize(data)` |
| SQL | `pd.read_sql(query, conn)` |

## Missing Data Decision Pattern
| Missingness | Pattern | Action |
|---|---|---|
| <5% | Random (MCAR) | Drop rows or impute mean/median/mode |
| 5-40% | Depends on importance | Impute (median for skewed/outlier-prone, mode for categorical) |
| >40-50% | Column unreliable | Drop the column |
| Non-random (MNAR) | Missingness is informative | Flag with indicator column + impute, don't just drop |

Detect: `df.isnull().sum()`, `df.isnull().mean()`

## Outlier Detection
- IQR rule: outlier if `x < Q1 - 1.5*IQR` or `x > Q3 + 1.5*IQR`
- Visual check: box plot
- Z-score rule (alternative): `|z| > 3` typically flagged

## Categorical Encoding
| Method | Use When | Risk |
|---|---|---|
| Label Encoding | Ordinal categories (order matters) | Implies false order if used on nominal data |
| One-Hot Encoding | Nominal categories (no order) | Multicollinearity if all columns kept — use `drop_first=True` |

Code: `pd.get_dummies(df['col'], drop_first=True)`

## Feature Scaling
| Method | Formula | Output Range | Use When |
|---|---|---|---|
| Standardization (StandardScaler) | (x-mean)/std | mean=0, std=1, unbounded | Gaussian-like data, outliers present |
| Normalization (MinMaxScaler) | (x-min)/(max-min) | [0,1] by default | Bounded input needed (e.g., neural nets), no major outliers |

## Plot Type Selection
| Data Question | Plot |
|---|---|
| Distribution of one numeric variable | Histogram |
| Distribution + outliers/quartiles of one variable | Box plot |
| Relationship between two numeric variables | Scatter plot |
| Correlation across many numeric variables | Heatmap |

## EDA Workflow (exam order)
1. Load data
2. Inspect shape, dtypes, `head()`
3. Detect missing values
4. Detect outliers
5. Visualize distributions
6. Check correlations
7. Encode categoricals / scale numerics

**Exam traps:** choosing label encoding for nominal data; imputing a column that's >50% missing instead of dropping it; using a scatter plot to show a single variable's distribution; forgetting `drop_first=True` with `get_dummies()`.
