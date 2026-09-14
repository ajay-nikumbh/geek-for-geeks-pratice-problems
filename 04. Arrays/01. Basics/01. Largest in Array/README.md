# Largest Element in Array

**GfG Link:** [Largest Element in Array](https://www.geeksforgeeks.org/problems/largest-element-in-array4009/1)

## Problem Statement

Given an array `arr[]` of integers, find and return the largest element present in the array.

There is exactly one array, no sorting order is guaranteed, and elements may repeat. You must return the maximum value contained in the array.

### Example 1

```
Input:  arr[] = [1, 8, 7, 56, 90]
Output: 90
Explanation: 90 is the largest element in the given array.
```

### Example 2

```
Input:  arr[] = [5, 5, 5, 5]
Output: 5
Explanation: All elements are equal, so the largest element is 5 itself.
```

---

## Constraints

GfG typically states constraints like:

```
1 <= arr.size() <= 10^6
0 <= arr[i] <= 10^6      (variant without negatives)
        or
-10^6 <= arr[i] <= 10^6  (variant with negatives)
```

Let's break down what each part actually means for how you should solve this:

- **`1 <= arr.size() <= 10^6`** — The array is never empty (minimum size is 1), so you don't need to handle a "no elements" edge case defensively inside the algorithm itself (though many implementations still guard for it for robustness). More importantly, the upper bound of `10^6` tells you the intended time complexity. An `O(n log n)` sort-based solution (~10^6 * 20 ≈ 2*10^7 operations) will pass comfortably within typical 1-second limits. But it also signals that a truly optimal `O(n)` solution exists and is expected — using anything worse than `O(n log n)`, like an `O(n^2)` approach (pairwise comparisons, bubble-sort-style scans), would result in ~10^12 operations and a **Time Limit Exceeded (TLE)**.

- **Element range (`arr[i]` can be 0 to 10^6, or negative to positive 10^6)** — This is the most important constraint for correctness, not just performance. If negative numbers are allowed, you **cannot initialize your "max so far" variable to `0`**, because if the entire array is negative (e.g., `[-5, -3, -9]`), a max initialized to `0` would incorrectly return `0` (which isn't even in the array) instead of `-3`. The safe initialization strategies are:
  - Initialize `max = arr[0]` and start scanning from index `1`, or
  - Initialize `max = float('-inf')` (negative infinity) and scan from index `0`.

  Both approaches work regardless of whether the array is all-positive, all-negative, or mixed — this is a common interview trap.

- **Data type / overflow** — In Python this is a non-issue since integers are arbitrary precision. In C++/Java, if `arr[i]` can be as large as `10^6` (or larger in some GfG variants), a standard `int` is sufficient (max `int` is ~2.1 * 10^9). Overflow would only become a concern if you were *summing* elements, not just comparing them, so simple max-finding is safe from overflow regardless of language.

- **Single array, in-place read only** — No mention of modifying the array, so sorting (which mutates or requires extra space for a copy) is a valid but not the most elegant approach — it does more work than necessary just to answer "what's the max."

**Bottom line:** the constraints permit `O(n log n)` but *reward* `O(n)`, and they implicitly require careful initialization of the running maximum because negative values (or values that could all be zero/negative) must not be silently ignored by a naive `max = 0` starting point.

---

## Visualization / Diagram

Think of it as a single pointer sweeping left to right, carrying a "best so far" value forward. Here's a trace for `arr = [3, 9, 2, 15, 7]`:

```
Array:      [  3,    9,    2,   15,    7  ]
Index:         0     1     2     3     4

Step 0: max_so_far = arr[0] = 3   (initialization)

Step 1: i=1 -> compare 9 vs max(3)   -> 9 > 3   -> max_so_far = 9
                 ┌───┐
        [ 3,    [9],   2,   15,    7 ]
                  ^
                 new max

Step 2: i=2 -> compare 2 vs max(9)   -> 2 < 9   -> max_so_far stays 9
        [ 3,     9,   [2],  15,    7 ]
                        ^
                    no change

Step 3: i=3 -> compare 15 vs max(9)  -> 15 > 9  -> max_so_far = 15
        [ 3,     9,    2,  [15],   7 ]
                              ^
                          new max

Step 4: i=4 -> compare 7 vs max(15)  -> 7 < 15  -> max_so_far stays 15
        [ 3,     9,    2,   15,   [7] ]
                                     ^
                                 no change

Final answer: max_so_far = 15
```

This "running max carried forward" is exactly what the optimal linear scan does — one variable, one pass, constant extra memory.

---

## Brute Force Approach

### Idea

For every element, check whether it is greater than or equal to every other element in the array. If an element wins all comparisons, it's the largest. This is the "compare everything against everything" mindset — it doesn't use any running state, it just re-verifies each candidate from scratch.

### Code (Python)

```python
def largest_brute_force(arr):
    n = len(arr)
    if n == 0:
        return None  # defensive guard, though GfG guarantees n >= 1

    for i in range(n):
        is_largest = True
        for j in range(n):
            if arr[j] > arr[i]:
                is_largest = False
                break
        if is_largest:
            return arr[i]
    return None
```

### Trace Example

`arr = [3, 9, 2, 15, 7]`

- `i=0` (value 3): compare against all → 9 > 3, fails → not largest.
- `i=1` (value 9): compare against all → 15 > 9, fails → not largest.
- `i=2` (value 2): fails immediately (9 > 2).
- `i=3` (value 15): compare against all → nothing beats 15 → **is_largest = True → return 15**.

Output: `15` (matches expected).

### Time Complexity

For each of the `n` elements (outer loop), we scan all `n` elements again (inner loop) to confirm it's the maximum. That's `n * n = O(n^2)` comparisons in the worst case (e.g., a strictly increasing array forces the inner loop to run fully for almost every outer iteration before failing late, and the true max element requires a full inner scan of `n` to confirm). With `n` up to `10^6`, this is `10^12` operations — far too slow, guaranteed TLE.

### Space Complexity

`O(1)` — only a couple of scalar variables (`is_largest`, loop indices) are used; no auxiliary data structure grows with input size.

---

## Better Approach (Sorting-Based)

### Idea

Sort the array in ascending order. The largest element is now trivially the last element of the sorted array. This is "better" than brute force because sorting is `O(n log n)` instead of `O(n^2)`, but it's still doing far more work than necessary — you don't need the *entire order* of the array, just its maximum.

### Code (Python)

```python
def largest_sorting(arr):
    if not arr:
        return None
    sorted_arr = sorted(arr)   # O(n log n), returns a new sorted list
    return sorted_arr[-1]
```

### Trace Example

`arr = [3, 9, 2, 15, 7]`

1. Sort → `[2, 3, 7, 9, 15]`
2. Last element → `15`

Output: `15`.

### Time Complexity

`sorted()` uses Timsort, which runs in `O(n log n)` in the average and worst case. Comparison-based sorting algorithms are provably bounded below by `O(n log n)` (you cannot sort faster using only comparisons — there are `n!` possible orderings, and each comparison gives at most 1 bit of information, so you need at least `log2(n!) ≈ n log n` comparisons). Accessing the last element afterward is `O(1)`.

### Space Complexity

`O(n)` — Python's `sorted()` creates a new list rather than sorting in place (`list.sort()` would be in-place but still needs `O(log n)` auxiliary stack space for Timsort's internal merge operations, and here we used `sorted()` which explicitly copies). Either way, this approach uses more memory than necessary just to find one value.

---

## Optimal Approach (Single Pass Linear Scan)

### Idea

You don't need the whole array sorted or need to re-verify each candidate — you only need to remember the biggest value you've seen *so far* as you walk through the array once. Initialize a running maximum to the first element, then compare each subsequent element against it, updating whenever you find something bigger.

### Code (Python)

```python
def largest_optimal(arr):
    if not arr:
        return None  # GfG guarantees n >= 1, but guard for general use

    max_so_far = arr[0]        # safe init: handles negatives correctly
    for i in range(1, len(arr)):
        if arr[i] > max_so_far:
            max_so_far = arr[i]

    return max_so_far
```

Equivalent one-liner using Python's built-in (also `O(n)` internally):

```python
def largest_optimal_builtin(arr):
    return max(arr)
```

### Working Example Trace

`arr = [3, 9, 2, 15, 7]`

| Step | i | arr[i] | Comparison       | max_so_far |
|------|---|--------|------------------|------------|
| init | - | -      | -                | 3          |
| 1    | 1 | 9      | 9 > 3 → update   | 9          |
| 2    | 2 | 2      | 2 > 9 → no       | 9          |
| 3    | 3 | 15     | 15 > 9 → update  | 15         |
| 4    | 4 | 7      | 7 > 15 → no      | 15         |

Final `max_so_far = 15` → **Output: 15**.

A second trace with negatives, `arr = [-8, -3, -20, -1]`:

| Step | i | arr[i] | Comparison        | max_so_far |
|------|---|--------|--------------------|------------|
| init | - | -      | -                  | -8         |
| 1    | 1 | -3     | -3 > -8 → update   | -3         |
| 2    | 2 | -20    | -20 > -3 → no      | -3         |
| 3    | 3 | -1     | -1 > -3 → update   | -1         |

Final `max_so_far = -1` → **Output: -1** (correctly handled because we initialized from `arr[0]`, not `0`).

### Time Complexity: O(n)

Each element is visited exactly once, and at each visit a constant amount of work is done (one comparison, and possibly one assignment). Total work is directly proportional to `n`, giving `O(n)`. This is optimal — you cannot determine the maximum of an unsorted collection without examining every element at least once (if you skip even one element, it could secretly be the largest), so `O(n)` is the theoretical lower bound for this problem, and this algorithm meets it exactly.

### Space Complexity: O(1)

Only one extra variable (`max_so_far`) and a loop counter are used, regardless of how large the input array is. No auxiliary array, no recursion stack, no copying — memory usage is constant with respect to `n`.

---

## Edge Cases

- **Empty array** — GfG's constraints guarantee `arr.size() >= 1`, so this technically won't occur in the judge, but defensive code should decide a policy (return `None`, raise an exception, or return `float('-inf')`) rather than crash with an `IndexError` on `arr[0]`.
- **Single element array** — `arr = [42]`. The loop body never executes; `max_so_far` stays `arr[0] = 42`, which is correctly the answer. Good sanity check that initialization alone must be correct.
- **All elements same** — `arr = [7, 7, 7, 7]`. Every comparison `arr[i] > max_so_far` is `False` (strict `>`, not `>=`), so `max_so_far` never changes from the initial `7`. Still correct — demonstrates why strict `>` (not `>=`) is fine and slightly more efficient (avoids needless reassignment).
- **All negative numbers** — `arr = [-50, -10, -99]`. This is the classic trap: if you initialize `max_so_far = 0` instead of `arr[0]`, you'd incorrectly return `0`. Must initialize from an actual array element or `-infinity`.
- **Duplicates of the maximum** — `arr = [5, 9, 9, 3]`. Multiple elements tie for largest; since we use strict `>`, the *first* occurrence of `9` sets `max_so_far`, and the second `9` doesn't trigger a redundant update. The answer `9` is correct either way — GfG only asks for the value, not its index or count.
- **Very large array (10^6 elements)** — Tests whether your solution is truly `O(n)`/`O(n log n)` and not accidentally `O(n^2)`. Also worth confirming your language's I/O (reading the array) is fast enough — in Python, avoid slow input parsing (use `sys.stdin` for competitive judges) though GfG's function-based grading usually handles I/O for you.
- **Overflow** — Not a concern in Python (arbitrary precision integers). In C++/Java, only relevant if you were summing/multiplying values; pure max-finding via comparison never overflows regardless of element magnitude, as long as the values fit in the declared type to begin with.
- **Negative numbers mixed with positive** — `arr = [-5, 3, -1, 8, -20]`. Straightforward for the linear scan since it just compares raw values; no special-casing needed beyond the initialization rule already covered.

---

## Interview Follow-ups

1. **"What if the array is a stream (infinite/unknown size) and you can't store it all in memory?"**
   Maintain a single `max_so_far` variable and update it as each new element arrives, exactly like the optimal approach but without ever storing the full array — this is naturally an `O(1)`-space streaming algorithm already; no change needed to the core idea, just the input model.

2. **"Can you find the largest element without using any extra variable?"**
   Strictly speaking you need *some* state to remember the best-seen value, but you can avoid a *named* extra variable by reusing `arr[0]` in place as the accumulator (e.g., `arr[0] = max(arr[0], arr[i])` during the scan) if mutating the input is allowed — though this destroys the original array's first element, which is usually undesirable and rarely truly required in interviews; it's more of a trick question to test whether you understand space trade-offs.

3. **"How would you find the 2nd largest element as well?"**
   Track two running variables, `max1` and `max2`, both initialized carefully (e.g., to `-infinity` or the first two elements in sorted order). On each element: if it's greater than `max1`, shift `max1` into `max2` and update `max1`; else if it's greater than `max2` (and not equal to `max1`, if duplicates shouldn't count), update `max2`. Still `O(n)` time, `O(1)` space.

4. **"What if you can't use comparison operators (`>`, `<`)?"**
   You can simulate comparison using subtraction and sign-bit inspection: for integers `a` and `b`, `a - b`'s sign (via bitwise shift on the sign bit, e.g. `(a - b) >> 31` in 32-bit two's complement) tells you which is larger without an explicit `>` operator. This is more of a bit-manipulation trivia question than a practical technique, and it has overflow caveats when `a` and `b` have very different magnitudes or opposite signs — worth mentioning that caveat if asked.

5. **"Does your solution work if the array contains only one distinct repeated value, or is already sorted (ascending/descending)?"**
   Yes — the linear scan doesn't assume any ordering or distinctness; it examines every element unconditionally, so best-case and worst-case are both `O(n)` (no early-exit optimization is possible or needed, since you must inspect all `n` elements to be certain none is larger).

---

## Interview Explanation Tips

- **Start by restating the problem and clarifying constraints out loud**: "So I need to find the maximum value in an unsorted array of integers. Can the array contain negative numbers? Can it be empty?" — asking about negatives signals to the interviewer that you already know it affects your initialization strategy, which is a strong early signal.

- **Mention brute force first, briefly, then dismiss it with reasoning** — don't skip straight to optimal. Say something like: "The naive way would be to compare every element against every other element, which is `O(n^2)` — that won't scale for large inputs, so let's do better." This shows you can reason about complexity trade-offs, not just recite a memorized answer.

- **Justify why sorting is unnecessary** — a common mid-tier answer is "I'll just sort and take the last element." Preempt the interviewer's follow-up by volunteering: "Sorting would work and is `O(n log n)`, but since I only need the maximum — not the full order — I can do it in a single `O(n)` pass with a running maximum, which is both faster and uses `O(1)` extra space."

- **Explicitly call out the initialization pitfall** — say out loud: "I'll initialize my max to the first element of the array rather than 0, because if all elements are negative, initializing to 0 would give a wrong answer that isn't even in the array." Interviewers specifically listen for this; it's one of the most common silent bugs candidates introduce.

- **Common mistakes to avoid / mention you're avoiding**:
  - Initializing `max = 0` blindly (breaks on all-negative arrays).
  - Using `>=` instead of `>` in the update condition — not wrong, but slightly wasteful (extra writes on ties) and can subtly change behavior if you're also tracking an index/position of the max (using `>=` would make you track the *last* occurrence instead of the first).
  - Forgetting to handle (or explicitly state you're assuming away) the empty-array case.
  - Off-by-one errors when starting the loop at index `0` after already using `arr[0]` as the seed — should start iterating from index `1` to avoid a redundant self-comparison (harmless here, but shows precision).

- **Close with complexity statement unprompted**: "This runs in `O(n)` time since we touch each element exactly once, and `O(1)` space since we only keep a single running variable — this is optimal because any correct algorithm must inspect every element at least once to guarantee correctness."
