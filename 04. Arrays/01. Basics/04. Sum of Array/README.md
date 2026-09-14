# Sum of Array

**GfG Link:** https://www.geeksforgeeks.org/problems/sum-all-array-elements/1

## 1. Problem Statement

Given an array `arr[]` of `n` integers, find the sum of all the elements of the array.

### Example 1

```
Input:  arr[] = [1, 2, 3, 4, 5]
Output: 15
Explanation: 1 + 2 + 3 + 4 + 5 = 15
```

### Example 2

```
Input:  arr[] = [10, -2, 3, 100, -50]
Output: 61
Explanation: 10 + (-2) + 3 + 100 + (-50) = 61
```

---

## 2. Constraints — Deep Dive

Typical GfG constraints for this problem:

```
1 <= n <= 10^6
-10^9 <= arr[i] <= 10^9
```

At first glance this looks trivial — "just add the numbers" — but the constraints are exactly where the real engineering judgment is tested.

### 2.1 Why the sum can overflow a 32-bit `int`

A standard 32-bit signed integer (`int` in C/C++/Java) can hold values in the range:

```
-2,147,483,648  to  2,147,483,647   (≈ -2.1 x 10^9 to 2.1 x 10^9)
```

Now look at the worst case allowed by the constraints:

```
n = 10^6
each arr[i] = 10^9   (maximum magnitude)

max possible sum = n * max(arr[i]) = 10^6 * 10^9 = 10^15
```

`10^15` is **far** beyond what a 32-bit `int` can represent (`~2.1 x 10^9`). If you accumulate the sum in an `int`, you will silently overflow — the value wraps around (undefined behavior in C/C++, silent wraparound in Java) and you get a wrong, often negative or nonsensical, answer. This is a classic "silent failure" bug: the code compiles, runs without crashing, and passes small test cases, but fails on the large hidden test cases GfG uses specifically to catch this.

### 2.2 How array size AND element range together decide the accumulator type

This is the key insight interviewers want to hear explicitly:

- **Element magnitude alone** tells you the range of a *single* value.
- **Array size (n) alone** tells you how many terms you're adding.
- **The product of the two (n × max|arr[i]|)** tells you the range the *running sum* must be able to hold.

| n | max\|arr[i]\| | worst-case \|sum\| | Fits in 32-bit int? | Fits in 64-bit long? |
|---|---|---|---|---|
| 10 | 100 | 1,000 | Yes | Yes |
| 10^3 | 10^9 | 10^12 | No | Yes |
| 10^6 | 10^9 | 10^15 | No | Yes |
| 10^6 | 10^18 (hypothetical) | 10^24 | No | No — would need BigInteger |

So the correct accumulator type is chosen by computing `n_max * elementRange_max`, **not** by looking at either constraint alone. For this problem's constraints (`n ≤ 10^6`, `|arr[i]| ≤ 10^9`), the safe choice is:

- C++: `long long` (64-bit, range ≈ ±9.2 x 10^18)
- Java: `long`
- Python: no issue — Python integers are arbitrary-precision and grow automatically, so overflow is a non-issue there (but you should still *reason* about it out loud in an interview, since Python hides the problem rather than solving it conceptually).

### 2.3 Other constraint-driven considerations

- **n up to 10^6** rules out any approach worse than O(n) — anything quadratic (O(n²)) would be ~10^12 operations, far too slow (well beyond ~10^8 operations/sec budget for a ~1s time limit).
- **Negative numbers allowed** (`arr[i]` can be negative) means we cannot assume the sum only grows — it can also shrink, and cancellation can occur (e.g., all values summing near zero despite large individual magnitudes). This matters for overflow reasoning: you must bound using **absolute values**, not assume monotonic growth.
- **Empty array edge case**: many GfG variants guarantee `n >= 1`, but defensively you should handle `n = 0` → sum = 0.

---

## 3. Visualization / Diagram

Think of the sum as a single accumulator variable that "absorbs" each array element as we scan left to right.

```
Array:        [  4  ,   -2  ,   9   ,   1   ,  -5  ]
Index:            0       1      2       3      4

accumulator starts at 0

step 0: acc = 0 + 4   = 4
step 1: acc = 4 + (-2)= 2
step 2: acc = 2 + 9   = 11
step 3: acc = 11 + 1  = 12
step 4: acc = 12 + (-5)= 7

Final sum = 7
```

Visual "conveyor belt" view — one accumulator register, one pass:

```
   +---+     +---+     +---+     +---+     +---+
   | 4 | --> |-2 | --> | 9 | --> | 1 | --> |-5 |
   +---+     +---+     +---+     +---+     +---+
     |         |         |         |         |
     v         v         v         v         v
   acc=4     acc=2    acc=11    acc=12     acc=7
```

### Trace Table

| Index i | arr[i] | acc before | acc after |
|---|---|---|---|
| 0 | 4 | 0 | 4 |
| 1 | -2 | 4 | 2 |
| 2 | 9 | 2 | 11 |
| 3 | 1 | 11 | 12 |
| 4 | -5 | 12 | 7 |

Result: **7**

---

## 4. Brute Force Approach

Unlike most array problems, there isn't really a "bad" brute-force way to sum an array — a single linear scan **is** the natural approach. The only meaningfully "different" (and arguably worse) alternative is a **recursive** summation, which we present here as the brute/alternative approach because it trades stack space for a superficially "elegant" formulation.

### Idea

Define `sum(arr, i)` = `arr[i] + sum(arr, i+1)`, with base case `sum(arr, n) = 0`. Each recursive call handles one element and delegates the rest to a smaller subproblem.

### Python Code

```python
def array_sum_recursive(arr, i=0):
    # Base case: no elements left to add
    if i == len(arr):
        return 0
    # Add current element to the sum of the rest of the array
    return arr[i] + array_sum_recursive(arr, i + 1)
```

### Worked Trace

For `arr = [4, -2, 9, 1, -5]`:

```
array_sum_recursive(arr, 0)
= 4 + array_sum_recursive(arr, 1)
= 4 + (-2 + array_sum_recursive(arr, 2))
= 4 + (-2 + (9 + array_sum_recursive(arr, 3)))
= 4 + (-2 + (9 + (1 + array_sum_recursive(arr, 4))))
= 4 + (-2 + (9 + (1 + (-5 + array_sum_recursive(arr, 5)))))
= 4 + (-2 + (9 + (1 + (-5 + 0))))
= 4 + (-2 + (9 + (1 + -5)))
= 4 + (-2 + (9 + -4))
= 4 + (-2 + 5)
= 4 + 3
= 7
```

The calls stack up (build downward) until the base case, then unwind and add as they return.

### Complexity

- **Time: O(n)** — each element is visited exactly once across the n+1 calls.
- **Space: O(n)** — this is the important part to explain. Each recursive call is **not** free: it pushes a new stack frame onto the call stack, containing the return address, the local variables (`arr` reference, `i`), and bookkeeping info. Since the recursion goes `n` levels deep before hitting the base case (it is not tail-call optimized in Python, and most languages/compilers don't guarantee tail-call optimization either), all `n` frames coexist on the stack simultaneously at the deepest point. That is O(n) auxiliary space — and for `n` up to 10^6, this **will** blow the default recursion limit / stack size in most languages (Python's default recursion limit is ~1000; even in C++/Java with larger stacks, 10^6 deep recursion risks a `StackOverflowError` / segfault).

This is precisely why recursion is presented here as the "brute force / alternative" rather than a recommended approach — it is correct but strictly worse than iteration for this problem's constraints.

---

## 5. Better Approach — Iterative Accumulator

### Idea

Walk through the array once with a single loop, maintaining a running total in one variable. No function-call overhead, no stack growth — just a register-like accumulator updated in place.

### Code

```python
def array_sum_iterative(arr):
    total = 0  # use a 64-bit-safe type; Python ints handle this automatically
    for x in arr:
        total += x
    return total
```

```cpp
// C++ — note the accumulator type chosen per the constraint analysis above
long long arraySum(const vector<int>& arr) {
    long long total = 0;   // long long, NOT int — avoids overflow for n<=1e6, |arr[i]|<=1e9
    for (int x : arr) {
        total += x;
    }
    return total;
}
```

### Trace

Same as the diagram in Section 3 — `acc` updates from 0 → 4 → 2 → 11 → 12 → 7, one loop iteration at a time, with no recursive calls involved.

### Complexity

- **Time: O(n)** — one pass, one addition per element.
- **Space: O(1)** — this is the key improvement over recursion. There is exactly one accumulator variable and one loop counter, regardless of `n`. No call stack grows because there are no nested function calls — the loop is a flat, iterative control structure handled by the CPU's instruction pointer jumping back to the loop start, not by pushing new stack frames. This is why iteration is strictly better than the recursive version for this problem: same time complexity, but constant space instead of linear space, and no risk of stack overflow for large `n`.

---

## 6. Optimal Approach

The iterative single-pass accumulator from Section 5 **is** the optimal approach — there is no algorithmic technique that improves on it for this problem. We restate it here as "optimal" and add the deeper discussion an interview may probe.

### Confirmed Optimal

```python
def array_sum_optimal(arr):
    total = 0
    for x in arr:
        total += x
    return total

# Equivalent, using the built-in:
def array_sum_builtin(arr):
    return sum(arr)
```

### How built-in `sum()` functions work internally

Language built-ins (`sum()` in Python, `Arrays.stream(arr).sum()` in Java, `accumulate()` in C++'s `<numeric>`) are **not** magic — internally they still perform the same O(n) linear scan with an accumulator. The advantage of using them is:

1. **Micro-optimized inner loop** — often implemented in C (e.g., CPython's `sum()` avoids per-iteration Python bytecode dispatch overhead for numeric types), so the constant factor is smaller even though the asymptotic complexity is identical.
2. **Readability and correctness** — less code, fewer chances for an off-by-one or wrong-initial-value bug.
3. They still face the **same overflow considerations** — a Java `IntStream.sum()` returns an `int` and can overflow; you'd want `LongStream.sum()` instead.

### Footnote: Parallel / SIMD summation for very large arrays

For very large arrays (think n in the hundreds of millions, e.g. in HPC or data-processing systems), a single sequential pass, while asymptotically optimal, can be sped up in **wall-clock time** (not complexity class) using:

- **SIMD (Single Instruction, Multiple Data)**: modern CPUs can add multiple array elements per instruction using vector registers (e.g., AVX2 can sum 8 `int32` values per instruction). Compilers often auto-vectorize a simple summation loop like this one.
- **Parallel reduction**: split the array into chunks, sum each chunk on a separate thread/core, then sum the partial results (a classic "map-reduce" style reduction, executing in O(n/p + log p) time with `p` processors).
- These do **not** change the asymptotic complexity (still Θ(n) total work) — they only reduce the constant factor / wall-clock time via parallel hardware. This is not required for a typical interview answer to this problem, but mentioning it shows awareness of how summation is actually optimized in real large-scale systems (e.g., MapReduce word-count-style aggregations, GPU reductions).

### Why O(n) Is a Hard Lower Bound

You cannot compute the sum of `n` unknown elements without reading every one of them at least once — if you skipped even a single element, an adversary could set that element to any value and change the true sum without your algorithm noticing. Therefore **Ω(n)** is a fundamental information-theoretic lower bound for this problem, and since our approach achieves **O(n)**, it is asymptotically optimal — you cannot beat linear time in the general (unsorted, arbitrary elements) case.

### Complexity Summary

- **Time: O(n)** — provably optimal (matches the Ω(n) lower bound).
- **Space: O(1)** — only a constant number of scalar variables used, independent of input size.

---

## 7. Edge Cases

| Case | Example | Expected Behavior |
|---|---|---|
| Empty array | `arr = []` | Sum = 0 (identity element of addition; loop body never executes, `total` stays 0) |
| Single element | `arr = [42]` | Sum = 42 |
| All negative numbers | `arr = [-1, -2, -3]` | Sum = -6 (accumulator correctly goes negative; ensure signed type is used) |
| Mixed positive/negative | `arr = [100, -100, 50]` | Sum = 50 (cancellation can hide large intermediate magnitudes — still must use a wide-enough type since intermediate partial sums could be large even if the final answer is small) |
| Overflow scenario | `n = 10^6`, all `arr[i] = 10^9` | True sum = 10^15 — must use `long`/`long long` (64-bit); using `int` (32-bit) silently overflows/wraps to an incorrect value |
| All zeros | `arr = [0, 0, 0, 0]` | Sum = 0 |

---

## 8. Interview Follow-ups

1. **"If the array is known to be a sequence of consecutive integers (e.g., 1 to n), can you compute the sum in O(1)?"**
   Yes — use the arithmetic series formula `sum = n * (first + last) / 2` (e.g., Gauss's formula for `1..n` is `n*(n+1)/2`). This only applies when the structure (consecutive/arithmetic progression) is guaranteed; for an arbitrary unsorted array, O(n) is required (per the lower-bound argument above).

2. **"Can you compute a running sum / prefix sum as you go, instead of just the final total?"**
   Yes — maintain an array `prefix[i] = arr[0] + arr[1] + ... + arr[i]`, built in the same O(n) single pass (`prefix[i] = prefix[i-1] + arr[i]`). This is a natural and very common extension of this exact problem.

3. **"How would you answer multiple range-sum queries (sum of arr[l..r]) efficiently?"**
   Precompute the prefix sum array once in O(n), then each query `sum(l, r) = prefix[r] - prefix[l-1]` in O(1). This turns what would be O(n) per naive query into O(1) per query after an O(n) one-time preprocessing cost — a classic prefix-sum technique.

4. **"How would you parallelize summation for a huge array across multiple cores/machines?"**
   Split the array into contiguous chunks, sum each chunk independently (in parallel, e.g. via threads, `fork/join`, or a MapReduce-style job), then combine (reduce) the partial sums — a tree-style reduction taking O(n/p + log p) with `p` workers. Mention SIMD vectorization as a lower-level, single-core version of the same idea.

5. **"What if the array is a stream and you can't store it all in memory — can you still compute the sum?"**
   Yes — summation only needs O(1) state (the running total), so it can be computed in a single streaming pass without ever storing the full array, which is exactly why the iterative accumulator approach generalizes naturally to streaming/online settings.

---

## 9. Interview Explanation Tips

- **Don't rush past "trivial" problems.** Even for something as simple as summing an array, interviewers are listening for structured reasoning: state the approach, then immediately state time and space complexity, without being asked.
- **Proactively raise overflow.** This is the single most valuable thing you can say for this problem. Explicitly compute the worst case (`n_max * max|arr[i]|`) and state why you chose `long`/`long long` over `int`. This signals real engineering maturity, not just "can code a for-loop."
- **Justify the lower bound.** When asked "can this be done faster than O(n)?", give the adversary argument: any unread element could silently change the answer, so you must touch every element at least once — hence Ω(n), matching your O(n) solution.
- **Mention recursion vs iteration space tradeoffs if asked to write it differently.** Explain that recursion isn't "wrong," but it costs O(n) stack space due to frames staying alive until the base case unwinds, whereas iteration is O(1) space — a good way to demonstrate you understand *why*, not just *that*, one is better.
- **Bridge to prefix sums.** Since interviewers often use this as a warm-up, proactively mention that the natural next step is the prefix-sum technique for range queries — showing you can see where a "trivial" problem is heading before they ask.
- **State edge cases out loud** (empty array, all negatives, all zeros) even if not asked — it shows you think defensively about input space, not just the happy path.
