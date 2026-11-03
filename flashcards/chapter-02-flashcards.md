## Chapter 2: Domain 2: Python Programming for AI — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Numpy broadcasting rule: when can two arrays be combined in element-wise ops? | Compare shapes from the trailing dimension backward. Dimensions are compatible if equal OR one of them is 1. Missing leading dimensions are treated as 1. Exam tip: (5,3) + (3,) works; (5,3) + (4,) does not. |
| 2 | numpy array vs Python list for numerical computation — which and why? | numpy array: contiguous memory, fixed dtype, supports vectorized C-level operations. Python list: flexible types but slow element-wise math (interpreter overhead per element). Exam tip: always pick numpy for bulk numeric ops. |
| 3 | Vectorized op vs explicit for-loop performance on large numpy arrays? | Vectorized ops (e.g., `arr * 2`, `np.sqrt(arr)`) run in compiled C and are orders of magnitude faster than Python for-loops, which pay per-element interpreter overhead. Exam tip: 'fastest' answer = vectorized expression, not a loop. |
| 4 | Syntax: create a numpy array with a specific dtype | `np.array([1,2,3], dtype=np.float32)`. Exam tip: float32 = 4 bytes/element, float64 = 8 bytes/element — know how to compute `.nbytes`. |
| 5 | pandas: filter rows where column 'sales' > 100 | `df[df['sales'] > 100]`. Exam tip: boolean indexing — the condition inside brackets returns a Boolean Series used as a mask. |
| 6 | pandas: group by 'region' and sum 'sales' | `df.groupby('region')['sales'].sum()`. Exam tip: groupby + aggregation is the standard pattern tested for 'summarize by category' scenarios. |
| 7 | pandas merge how='left' vs how='inner' vs how='right' | left = keep all left rows; right = keep all right rows; inner = keep only matching rows in both. Exam tip: 'keep all records from table A even without a match' → how='left'. |
| 8 | list vs tuple vs set vs dict — core distinguishing trait each | list: ordered, mutable, allows duplicates. tuple: ordered, immutable, hashable. set: unordered, unique elements, O(1) membership. dict: key-value pairs, O(1) lookup by key. Exam tip: fast membership test with uniqueness → set. |
| 9 | List comprehension syntax with filter condition | `[expr for item in iterable if condition]`. Exam tip: filter `if` goes after the `for`, no `else` needed; conditional expressions (`x if c else y`) go BEFORE the `for`. |
| 10 | Reading/writing CSV in pandas | Read: `pd.read_csv('file.csv')`. Write: `df.to_csv('file.csv', index=False)`. Exam tip: forgetting `index=False` writes an unwanted extra index column. |
| 11 | Reading/writing JSON in Python/pandas | pandas: `pd.read_json('file.json')` / `df.to_json('file.json')`. Standard lib: `json.load(f)` / `json.dump(obj, f)`. Exam tip: use pandas for tabular JSON, `json` module for nested/non-tabular structures. |
| 12 | Why can tuples be dict keys but lists cannot? | Tuples are immutable → hashable → valid dict keys/set members. Lists are mutable → unhashable → raise TypeError if used as a dict key. |
