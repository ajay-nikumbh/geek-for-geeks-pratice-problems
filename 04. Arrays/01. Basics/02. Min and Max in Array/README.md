# Min and Max in Array

**GfG Link:** https://www.geeksforgeeks.org/problems/find-minimum-and-maximum-element-in-an-array4428/1

## 1. Problem Statement

Given an array `arr` of integers, find the **minimum** and **maximum** elements present in the array. Return both values (typically as a pair/pair-like structure: `{min, max}`).

### Example 1
```
Input:  arr = [3, 2, 1, 56, 10000, 167]
Output: min = 1, max = 10000
```

### Example 2
```
Input:  arr = [-5, -1, -100, -3, -2]
Output: min = -100, max = -1
```

Restated: scan the entire collection and identify the two extreme values — the smallest and the largest — in a single logical pass over the data.

---

## 2. Constraints — Deep Dive

Typical GfG constraints for this problem:

```
1 <= arr.size() <= 10^6
-10^6 <= arr[i] <= 10^6
```

Let's unpack what each of these actually means for how we should solve the problem.

### `1 <= arr.size() <= 10^6`
- **What it means:** The array has at least 1 element (no truly empty array to worry about in the GfG harness, though we still discuss the empty case as an edge case for general interviews) and can have up to one million elements.
- **How it restricts approach:** With `n` up to `10^6`, any algorithm with **O(n²)** complexity (e.g., comparing every pair of elements to find extremes, or bubble-sort-based extraction) would require up to `10^12` operations — completely infeasible within typical time limits (~1 second ≈ `10^8` operations). This constraint **forces us toward O(n) or O(n log n) approaches**. Since finding min/max doesn't inherently need ordering information beyond the two extremes, **O(n)** is both achievable and expected — sorting (O(n log n)) is a valid but sub-optimal approach.

### `-10^6 <= arr[i] <= 10^6`
- **What it means:** Array elements can be negative, zero, or positive, bounded within a fixed range.
- **How it restricts approach:** This is critical for **correct initialization** of our tracking variables. A naive mistake is to initialize `min_val = 0` and `max_val = 0` before scanning — this silently breaks when the entire array is negative (e.g., `[-5, -1, -100]`), since `0` would incorrectly remain the "max" candidate, or when all elements are positive, `0` would incorrectly remain the "min" candidate. The safe pattern is to **initialize both trackers with `arr[0]`** (the first element) and then scan starting from index 1, or initialize with `+infinity` / `-infinity` sentinels (e.g., `float('inf')` / `float('-inf')` in Python, or `INT_MAX` / `INT_MIN` in C++/Java) and scan the whole array. The known value range (`-10^6` to `10^6`) also tells us there's no overflow risk with standard 32-bit integers, so we don't need `long`/`long long` types here.

### Implicit constraint: no ties matter for min/max identity
- Only the **values** are asked for, not their indices — so duplicate min or max values (e.g., `[5, 5, 5]`) don't require special tie-breaking logic. This simplifies the algorithm: we don't need to track "first occurrence" or "last occurrence," just the value itself.

---

## 3. Visualization / Diagram

Single-pass simultaneous tracking of min and max as we scan left to right:

```
Array:   [  3,   2,   1,  56, 10000, 167 ]
Index:      0    1    2    3    4      5

Initialize: min = arr[0] = 3, max = arr[0] = 3   (start scan from index 1)

Step  Element   Compare to min     Compare to max     min   max
----  -------   ----------------   ----------------   ---   -----
 1       2      2 < 3 → min = 2    2 < 3 → no change    2     3
 2       1      1 < 2 → min = 1    1 < 3 → no change    1     3
 3      56      56 < 1 → no        56 > 3 → max = 56    1    56
 4   10000      10000 < 1 → no     10000 > 56 → max=..  1  10000
 5     167      167 < 1 → no       167 > 10000 → no     1  10000

Final:  min = 1, max = 10000
```

Pointer-style view — two "trackers" sliding along with the scan:

```
        min-tracker ↓                         max-tracker ↑
      [  3,    2,    1,   56,  10000,  167  ]
        │      │      │    │     │      │
        └──────┴──────┴────┴─────┴──────┘
        each element visited once; min & max
        updated independently at each step
```

Pairwise (tournament) visualization used in the Optimal Approach — elements grouped 2 at a time:

```
Array: [ 3, 2, 1, 56, 10000, 167 ]

Pair 1: (3, 2)      → local min=2, local max=3
Pair 2: (1, 56)     → local min=1, local max=56
Pair 3: (10000,167) → local min=167, local max=10000

Combine all local mins → overall min = min(2, 1, 167) = 1
Combine all local maxs → overall max = max(3, 56, 10000) = 10000
```

---

## 4. Brute Force Approach

### Idea
Perform **two separate full scans**: one to find the minimum, another to find the maximum. Alternatively, **sort** the array and pick the first and last elements. Both are "brute force" in the sense that they do more work than necessary — either scanning the array twice, or paying for a full ordering when only two values are needed.

### Python Code (Two-Pass Version)
```python
def get_min_max_bruteforce(arr):
    n = len(arr)
    if n == 0:
        return None, None

    # Pass 1: find minimum
    min_val = arr[0]
    for i in range(1, n):
        if arr[i] < min_val:
            min_val = arr[i]

    # Pass 2: find maximum
    max_val = arr[0]
    for i in range(1, n):
        if arr[i] > max_val:
            max_val = arr[i]

    return min_val, max_val
```

### Python Code (Sort-Based Version)
```python
def get_min_max_sort(arr):
    if not arr:
        return None, None
    sorted_arr = sorted(arr)
    return sorted_arr[0], sorted_arr[-1]
```

### Worked Trace (Two-Pass) — `arr = [3, 2, 1, 56, 10000, 167]`

**Pass 1 (find min):**
```
min_val = 3
i=1: arr[1]=2 < 3  → min_val = 2
i=2: arr[2]=1 < 2  → min_val = 1
i=3: arr[3]=56 < 1?  No
i=4: arr[4]=10000 < 1? No
i=5: arr[5]=167 < 1? No
Result: min_val = 1
```

**Pass 2 (find max):**
```
max_val = 3
i=1: arr[1]=2 > 3?  No
i=2: arr[2]=1 > 3?  No
i=3: arr[3]=56 > 3  → max_val = 56
i=4: arr[4]=10000 > 56 → max_val = 10000
i=5: arr[5]=167 > 10000? No
Result: max_val = 10000
```

Final: `min = 1, max = 10000` ✓

### Time Complexity
- **Two-pass version: O(n)** technically, but performs **2n comparisons** (n-1 for min pass + n-1 for max pass ≈ 2n). It's linear but with a worse constant factor than the optimal approach.
- **Sort-based version: O(n log n)** — dominated by the sorting step (comparison sort), which is strictly worse than linear scanning for this problem since we only need 2 extreme values, not a full ordering.

### Space Complexity
- **Two-pass version: O(1)** — only uses a few scalar variables (`min_val`, `max_val`, loop index), no extra data structures.
- **Sort-based version: O(n)** or **O(log n)** depending on the sort implementation — Python's `sorted()` creates a new list (O(n) auxiliary space); in-place sorts like quicksort still need O(log n) recursion stack space.

---

## 5. Better Approach

### Idea
Instead of two separate passes, do **one single pass** through the array and update **both** `min_val` and `max_val` at every element using two independent `if` checks. This halves the number of array traversals (from 2 passes to 1 pass) while still performing roughly the same total number of comparisons (~2n), just consolidated into one loop.

### Python Code
```python
def get_min_max_single_pass(arr):
    n = len(arr)
    if n == 0:
        return None, None

    min_val = arr[0]
    max_val = arr[0]

    for i in range(1, n):
        if arr[i] < min_val:
            min_val = arr[i]
        if arr[i] > max_val:        # separate, independent check
            max_val = arr[i]

    return min_val, max_val
```

### Worked Trace — `arr = [3, 2, 1, 56, 10000, 167]`

```
Init: min_val = 3, max_val = 3

i=1, arr[1]=2:
   2 < 3?  Yes → min_val = 2
   2 > 3?  No
   → min=2, max=3

i=2, arr[2]=1:
   1 < 2?  Yes → min_val = 1
   1 > 3?  No
   → min=1, max=3

i=3, arr[3]=56:
   56 < 1?  No
   56 > 3?  Yes → max_val = 56
   → min=1, max=56

i=4, arr[4]=10000:
   10000 < 1?  No
   10000 > 56?  Yes → max_val = 10000
   → min=1, max=10000

i=5, arr[5]=167:
   167 < 1?  No
   167 > 10000?  No
   → min=1, max=10000

Final: min=1, max=10000 ✓
```

### Time Complexity
**O(n)** — single pass over `n-1` elements (index 1 to n-1), with **2 comparisons per element** in the worst case → approximately **2(n-1) ≈ 2n comparisons** total. This is the same comparison count as the brute force two-pass approach, but achieved in **one traversal** instead of two — better cache locality and only one loop overhead, though asymptotically it's still O(n) either way. This is a practical improvement, not an asymptotic one.

### Space Complexity
**O(1)** — only `min_val`, `max_val`, and the loop index are stored; no auxiliary arrays or recursion.

---

## 6. Optimal Approach — Pairwise Comparison (Tournament Method)

### Idea
The key insight: when we do 2 independent comparisons per element (`arr[i] < min` and `arr[i] > max`), we're doing more comparisons than strictly necessary. The **pairwise/tournament technique** reduces the total comparison count from **~2n down to ~3n/2**:

1. Process elements **two at a time** (in pairs).
2. **First compare the pair against each other** (1 comparison) to determine which is the "smaller" and which is the "larger" of the two.
3. Then compare the **smaller** of the pair only against the running `min_val` (1 comparison), and the **larger** of the pair only against the running `max_val` (1 comparison).
4. This gives **3 comparisons per 2 elements** = **1.5 comparisons per element**, instead of 2 comparisons per element.

Over `n` elements (n/2 pairs), total comparisons ≈ `3 * (n/2) = 1.5n`, versus `2n` in the naive single/two-pass approach — roughly a **25% reduction** in comparison operations.

### Python Code
```python
def get_min_max_pairwise(arr):
    n = len(arr)
    if n == 0:
        return None, None
    if n == 1:
        return arr[0], arr[0]

    # Initialize min/max from the first pair (or first element if n is odd)
    if arr[0] < arr[1]:
        min_val, max_val = arr[0], arr[1]
    else:
        min_val, max_val = arr[1], arr[0]

    i = 2
    # Process remaining elements in pairs
    while i < n - 1:
        # Step 1: compare the pair against each other
        if arr[i] < arr[i + 1]:
            local_min, local_max = arr[i], arr[i + 1]
        else:
            local_min, local_max = arr[i + 1], arr[i]

        # Step 2 & 3: compare local extremes against running extremes
        if local_min < min_val:
            min_val = local_min
        if local_max > max_val:
            max_val = local_max

        i += 2

    # If n is odd, one element is left over — compare it directly
    if i == n - 1:
        if arr[i] < min_val:
            min_val = arr[i]
        elif arr[i] > max_val:
            max_val = arr[i]

    return min_val, max_val
```

### Step-by-Step Trace — `arr = [3, 2, 1, 56, 10000, 167]` (n = 6, even)

**Initialization (pair index 0,1 → elements 3, 2):**
```
arr[0]=3, arr[1]=2
3 < 2?  No → min_val = 2, max_val = 3
```

**i = 2, pair (arr[2]=1, arr[3]=56):**
```
1 < 56?  Yes → local_min = 1, local_max = 56
Compare local_min to min_val: 1 < 2?  Yes → min_val = 1
Compare local_max to max_val: 56 > 3?  Yes → max_val = 56
→ min=1, max=56
```

**i = 4, pair (arr[4]=10000, arr[5]=167):**
```
10000 < 167?  No → local_min = 167, local_max = 10000
Compare local_min to min_val: 167 < 1?  No
Compare local_max to max_val: 10000 > 56?  Yes → max_val = 10000
→ min=1, max=10000
```

Loop ends (i = 6, no leftover element since n is even).

**Final: min = 1, max = 10000** ✓

**Comparison count check:** Init pair: 1 comparison. Pair 2: 1 (pair) + 2 (vs running) = 3. Pair 3: 1 + 2 = 3. Total = 1 + 3 + 3 = **7 comparisons** for n=6 elements — versus the naive approach's `2*(6-1) = 10` comparisons. This matches the theoretical `~3n/2 = 9` upper bound (actual count is often slightly lower due to the initialization step).

### Time Complexity
**O(n)** — still linear in the number of elements, since every element is touched a constant number of times. The improvement over the "Better Approach" is **not asymptotic** (both are O(n)) but is a **constant-factor improvement in the actual number of comparison operations**: ~1.5n instead of ~2n. This matters in:
- Interview settings where the interviewer explicitly asks "can you minimize the number of comparisons?"
- Performance-critical code where comparisons are expensive (e.g., comparing large objects, strings, or custom comparators).
- It's a classic example of **why comparison-counting matters even when Big-O stays the same** — this is provably the information-theoretic optimal comparison count for the min-max problem (see Interview Follow-ups).

### Space Complexity
**O(1)** — only a fixed set of scalar variables (`min_val`, `max_val`, `local_min`, `local_max`, loop index `i`) regardless of input size.

---

## 7. Edge Cases

| Case | Example | Expected Behavior |
|---|---|---|
| **Empty array** | `arr = []` | No min/max exists — should return `None`/`null`/throw an exception or a sentinel, depending on problem spec. GfG's constraint (`n >= 1`) usually rules this out, but production code must guard it. |
| **Single element** | `arr = [42]` | `min = max = 42`. Both trackers equal the only element; no comparisons needed. |
| **All elements identical** | `arr = [7, 7, 7, 7]` | `min = max = 7`. Every comparison is "equal," so trackers never update after initialization — correct by construction since `<` and `>` are strict. |
| **All negative** | `arr = [-9, -3, -50, -1]` | `min = -50, max = -1`. Critical to verify initialization doesn't default to `0` — must init from `arr[0]` or `±infinity`, never `0`. |
| **Two elements** | `arr = [5, 2]` | `min = 2, max = 5`. Base case for the pairwise method — exactly 1 comparison needed. |
| **Already sorted (ascending)** | `arr = [1, 2, 3, 4, 5]` | `min = 1 (first), max = 5 (last)`. No algorithmic issue, but worth checking no off-by-one bug skips the last element. |
| **Already sorted (descending)** | `arr = [5, 4, 3, 2, 1]` | `min = 1, max = 5`. Ensures the algorithm doesn't assume any particular order. |
| **Overflow considerations** | Values near `INT_MAX`/`INT_MIN` in fixed-width-integer languages (C++/Java) | With GfG's constraint of `±10^6`, standard 32-bit `int` is safe (max int ~2.1 × 10^9). In general, always confirm the value range against the language's integer width before assuming no overflow — this becomes relevant if constraints were `±10^9` or larger with intermediate sums (not applicable here since we only compare, never sum). |
| **Odd-length array (pairwise method)** | `arr = [4, 1, 9]` (n=3) | Must correctly handle the leftover unpaired element after the main pairwise loop — verify it's compared against both `min_val` and `max_val` (using `elif` is a subtle but valid optimization since it can't be both the new min and new max unless n was originally 1). |

---

## 8. Interview Follow-ups

**Q1: Can you minimize the number of comparisons below 3n/2?**
No — it's a well-known result in comparison-based algorithm theory that finding both the min and max of `n` elements requires **at least `⌈3n/2⌉ - 2` comparisons** in the worst case. The pairwise/tournament method achieves this lower bound, making it provably optimal in terms of comparison count, not just asymptotically optimal.

**Q2: How would you find min/max in a 2D array (matrix)?**
Treat it as a flattened 1D scan: iterate over every row and every column (or flatten conceptually) applying the same single-pass or pairwise tracking logic. Time complexity becomes **O(rows × cols)**, which is still linear in the total number of elements. No need to actually flatten the array in memory — just nest the loops and update the same `min_val`/`max_val` trackers.

**Q3: How would you find the kth smallest/largest element instead of just min/max?**
That's a different problem — use **Quickselect** (average O(n), worst O(n²)) or a **min-heap/max-heap of size k** (O(n log k)) for the general kth-order-statistic problem. Finding just min (k=1) or max (k=n) is a special case solvable in O(n) without needing a heap or partitioning.

**Q4: How would you handle this for streaming data (numbers arriving one at a time, can't store the whole array)?**
Maintain running `min_val` and `max_val` variables, initialized on the first element received, and update them with each new incoming value using the same 2-comparison check per new element (O(1) per update, O(n) total, O(1) space) — this is essentially the "Better Approach" applied incrementally, which is naturally suited to streams since it never needs random access or a second pass.

**Q5: Can you parallelize finding min/max for very large arrays?**
Yes — split the array into chunks, find local min/max of each chunk independently (embarrassingly parallel, e.g., via map-reduce or multi-threading), then combine the per-chunk results with a final reduction pass comparing all local mins together and all local maxs together. This is effectively the pairwise technique generalized to large chunks instead of pairs of 2.

**Q6: What if the array can have duplicate min or max values — do we need their indices or count?**
Not for this problem as stated (only values matter), but if asked to also return the **index** or **frequency** of the min/max, track an additional `min_index`/`max_index` (or a counter) alongside the value comparisons — this adds no extra asymptotic cost, just extra state updated in the same comparison branches.

---

## 9. Interview Explanation Tips

**How to explain it out loud:**
1. Start by stating the **naive baseline**: "The simplest approach is two separate scans — one for min, one for max — giving O(n) time but 2n comparisons, or O(1) extra space."
2. Immediately mention the **single-pass optimization**: "We can merge both scans into one loop, checking `arr[i] < min` and `arr[i] > max` independently at each step — still O(n) and O(1) space, and same ~2n comparisons, but only one traversal."
3. Then introduce the **pairwise/tournament trick** as the "polish" that shows deeper understanding: "If we process elements two at a time, compare them to each other first, then only compare the smaller one against the running min and the larger one against the running max, we cut total comparisons from 2n down to about 1.5n."
4. Close with the **why this matters**: mention the information-theoretic lower bound of `3n/2 - 2` comparisons — this signals you understand that the pairwise method isn't just a trick, it's asymptotically tight and optimal.

**Why interviewers ask about the pairwise/tournament method specifically:**
- It tests whether you understand the difference between **Big-O time complexity** and **actual operation count** — both single-pass and pairwise are O(n), so a candidate who stops at "it's O(n), done" misses the deeper optimization the interviewer is fishing for.
- It's a classic example of amortized/algorithmic thinking: restructuring *how* comparisons are grouped (pairs vs. individual elements) reduces redundant work without changing the asymptotic class.
- It often leads into a discussion of comparison-based lower bounds, which signals CS theory fluency (similar in spirit to why comparison sorts have an Ω(n log n) lower bound).

**Common mistakes to avoid:**
- **Initializing `min_val`/`max_val` to `0`** instead of `arr[0]` or `±infinity` — silently breaks on all-negative or all-positive arrays.
- **Using `elif` instead of two independent `if` statements** in the single-pass approach — a single element can never be both a new min AND a new max (except when n=1), so `elif` is actually a valid micro-optimization there, but candidates sometimes use `elif` incorrectly in ways that skip necessary max updates when reasoning through the logic on the fly. Be precise about when `elif` is safe.
- **Forgetting the leftover element** when array length is odd in the pairwise method — off-by-one bugs are common here since the main loop processes pairs and needs a final cleanup step.
- **Claiming pairwise is "faster" in Big-O terms** — it is NOT asymptotically faster (still O(n)); the correct framing is "fewer constant-factor comparisons," not a complexity class improvement. Misstating this is a common interview red flag.
- **Sorting the array "just to be safe"** — jumping to O(n log n) sort-based extraction when O(n) suffices shows a lack of awareness that sorting does strictly more work (full ordering) than the problem requires (only 2 extreme values).
