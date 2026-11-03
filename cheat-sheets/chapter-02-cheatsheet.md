## Chapter 2 Cheat Sheet: Python Programming for AI

### Core Data Structures
| Structure | Ordered | Mutable | Duplicates | Hashable | Use Case |
|---|---|---|---|---|---|
| list | Yes | Yes | Yes | No | General sequences |
| tuple | Yes | No | Yes | Yes | Fixed records, dict keys |
| set | No | Yes | No | No | Fast membership/uniqueness |
| dict | Yes (insertion) | Yes | Keys unique | Keys only | Key-value lookup O(1) |

### Comprehension Syntax
```python
[x**2 for x in range(10) if x % 2 == 0]      # list comp with filter
{x: x**2 for x in range(10)}                  # dict comp
{x**2 for x in range(10)}                     # set comp
[x if x % 2 == 0 else -x for x in range(10)]  # conditional expr BEFORE for
```

### Numpy Broadcasting Rules
1. Compare shapes trailing-dimension first.
2. Dimensions compatible if equal, or one is 1.
3. Missing leading dims treated as size 1.
| Shape A | Shape B | Result | Valid? |
|---|---|---|---|
| (5,3) | (3,) | (5,3) | ✅ |
| (5,3) | (5,1) | (5,3) | ✅ |
| (5,3) | (4,) | — | ❌ error |

### Dtype Sizes (bytes/element)
| dtype | Bytes |
|---|---|
| int8/uint8 | 1 |
| float16 | 2 |
| int32/float32 | 4 |
| int64/float64 | 8 |
`arr.nbytes = len(arr) * bytes_per_element`

### Vectorization vs Loops
| Approach | Speed (large arrays) | Why |
|---|---|---|
| Python for-loop | Slowest | Per-element interpreter overhead |
| list comprehension | Slow-medium | Still interpreted, no C speedup |
| numpy vectorized op | Fastest | Runs in compiled C, SIMD-friendly |
**Rule:** given a choice, always pick the vectorized numpy/pandas expression over an explicit loop.

### pandas Essentials
```python
df[df['col'] > 100]                       # filter
df.groupby('region')['sales'].sum()       # group + aggregate
df.sort_values('sales', ascending=False)  # sort
df.merge(other, on='key', how='left')     # join
```
| Merge `how` | Keeps |
|---|---|
| inner | Only matching rows both sides |
| left | All left rows, NaN if no match |
| right | All right rows, NaN if no match |
| outer | All rows from both, NaN where missing |

### CSV / JSON I/O
```python
pd.read_csv('f.csv'); df.to_csv('f.csv', index=False)
pd.read_json('f.json'); df.to_json('f.json')
import json; json.load(f); json.dump(obj, f)
```

### Common Exam Traps
- Forgetting `index=False` when writing CSV → extra unnamed column.
- Confusing `set` comprehension `{}` with `dict` comprehension (needs `key: value`).
- Using a mutable list as a dict key → TypeError (unhashable type).
- Assuming a Python for-loop over a numpy array is as fast as a vectorized op — it is NOT.
