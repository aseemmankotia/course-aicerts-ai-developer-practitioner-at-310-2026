## Chapter 2: Domain 2: Python Programming for AI — Practice Questions

**Q1.** You have two numpy arrays: `a` with shape (5, 3) and `b` with shape (3,). You run `a + b`. What is the resulting shape and why?

A) (5, 3) — b is broadcast across each row of a
B) Error — shapes must match exactly
C) (3, 5) — numpy transposes a to align dimensions
D) (5,) — only the first dimension survives

<details>
<summary>Answer</summary>

**Correct: A**

Broadcasting rule: dimensions are compared from the trailing axis. (5,3) vs (3,) — the last axis matches (3==3), and the missing leading dimension in b is treated as size 1 and stretched to 5. Result shape is (5,3).

**Why the others are wrong:**
- Shapes don't need to match exactly — that's the entire point of broadcasting rules.
- Numpy never silently transposes arrays to force alignment; broadcasting only pads missing leading dimensions with size 1.
- This confuses broadcasting with a reduction operation like `.sum(axis=1)`; element-wise addition preserves the larger shape.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A data scientist needs to apply a mathematical transformation to every element of a 10-million-row numpy array as fast as possible. Which approach should they use?

A) A vectorized numpy expression such as `arr = np.sqrt(arr)` or `arr * 2`
B) A Python `for` loop with array indexing (`for i in range(len(arr)): arr[i] = f(arr[i])`)
C) A list comprehension that wraps the array in `list()` first
D) The built-in `map()` function applied directly to the numpy array

<details>
<summary>Answer</summary>

**Correct: A**

Vectorized numpy operations push the loop into compiled C code, avoiding per-element Python interpreter overhead. This is orders of magnitude faster than explicit Python loops for large arrays — exactly what the exam tests under 'vectorization vs explicit loops'.

**Why the others are wrong:**
- Explicit Python for-loops over array elements incur interpreter overhead per element and are the slowest option at scale.
- Converting to a list first discards numpy's contiguous memory layout and adds conversion overhead on top of still iterating in Python.
- map() still calls the Python function once per element and returns an iterator/list, giving no vectorization benefit.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** You have a pandas DataFrame `df` with columns `region`, `product`, and `sales`. You need the total sales per region, sorted descending. Which single line of code BEST accomplishes this?

A) `df.sort_values('sales', ascending=False)`
B) `df[df['sales'] > 0].groupby('product').mean()`
C) `df.groupby('region')['sales'].sum().sort_values(ascending=False)`
D) `df.pivot_table(index='product', values='sales')`

<details>
<summary>Answer</summary>

**Correct: C**

groupby('region')['sales'].sum() aggregates sales by region, and chaining sort_values(ascending=False) orders the results from highest to lowest — exactly matching the requirement.

**Why the others are wrong:**
- This sorts individual sales rows, it does not aggregate totals per region.
- Groups by product instead of region and computes mean instead of sum, and includes an irrelevant filter.
- pivot_table here groups by product instead of region, not the requested aggregation.

</details>

---

**Q4.** A developer needs to store 1 million unique float values and check membership (`value in collection`) as fast as possible, with no need for ordering or duplicates. Which Python data structure should they use?

A) list
B) set
C) tuple
D) dict with None as the value for every key

<details>
<summary>Answer</summary>

**Correct: B**

set provides O(1) average-case membership testing via hashing and automatically enforces uniqueness, which is exactly what's needed and is simpler than a dict.

**Why the others are wrong:**
- list membership testing is O(n), far too slow at 1 million elements, and allows duplicates.
- tuple has the same O(n) membership-check cost as a list and also allows duplicates.
- A dict with dummy values technically works and is also O(1), but it wastes memory storing unneeded values — set is the correct, purpose-built structure.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** You need to combine two pandas DataFrames, `orders` and `customers`, keeping ALL rows from `orders` even if there is no matching customer record. Which merge call is correct?

A) `orders.merge(customers, on='customer_id', how='inner')`
B) `orders.merge(customers, on='customer_id', how='right')`
C) `orders.merge(customers, on='customer_id', how='left')`
D) `pd.concat([orders, customers], axis=1)`

<details>
<summary>Answer</summary>

**Correct: C**

how='left' keeps every row from the left DataFrame (orders) and fills unmatched customer columns with NaN — exactly the 'keep all orders' requirement.

**Why the others are wrong:**
- inner join drops any order rows that lack a matching customer_id, violating the 'keep ALL orders' requirement.
- right join keeps all rows from customers instead of orders, the opposite of what's needed.
- concat along axis=1 naively glues columns together by positional index, not by matching keys, producing incorrect/misaligned data.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** What does `np.array([1, 2, 3], dtype=np.float32).nbytes` return?

A) 3
B) 24
C) 4
D) 12

<details>
<summary>Answer</summary>

**Correct: D**

float32 uses 4 bytes per element. With 3 elements, nbytes = 3 × 4 = 12.

**Why the others are wrong:**
- 3 is the element count, not byte count — confusing len(arr) with nbytes.
- 24 would be correct if dtype were float64 (8 bytes × 3), not float32.
- 4 is the per-element byte size, not the total array size.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** You want to create a list of the squares of all even numbers from 0 to 9 using a single line of idiomatic Python. Which expression is correct?

A) `[x for x in range(10) if x**2 % 2 == 0]`
B) `{x**2 for x in range(10) if x % 2 == 0}`
C) `[x**2 if x % 2 == 0 for x in range(10)]`
D) `[x**2 for x in range(10) if x % 2 == 0]`

<details>
<summary>Answer</summary>

**Correct: D**

This list comprehension correctly filters for even x first with the trailing `if`, then squares each matching value — valid comprehension syntax producing [0, 4, 16, 36, 64].

**Why the others are wrong:**
- This squares the condition check rather than the filter condition on x itself, producing a different (and here, identical by coincidence but logically wrong) filter logic, and returns x not x**2.
- This uses set comprehension syntax ({...}), which would produce an unordered set of unique values, not a list — doesn't match the 'list' requirement.
- This has invalid comprehension syntax: a conditional expression (if/else) must come before the `for`, not a filter `if` without an `else` placed before `for` — this raises a SyntaxError.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** Which statement about Python tuples versus lists is correct?

A) Tuples are immutable, making them hashable and usable as dict keys; lists are mutable and cannot be used as dict keys
B) Tuples support item assignment after creation, lists do not
C) Tuples are mutable and lists are immutable
D) Tuples and lists have identical performance characteristics and are interchangeable in all cases

<details>
<summary>Answer</summary>

**Correct: A**

Tuples are immutable, which gives them a stable hash value, allowing them to be used as dictionary keys or set members. Lists are mutable and unhashable, so they cannot be used as dict keys.

**Why the others are wrong:**
- This reverses the actual behavior — tuples do NOT support item assignment; lists do.
- This is the exact opposite of the truth — tuples are immutable, lists are mutable.
- They are not interchangeable: mutability, hashability, and typical use cases (fixed records vs. dynamic collections) differ significantly.

</details>

---

