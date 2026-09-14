# Count Smaller in Array

> GfG Problem: [Count of Smaller Elements](https://www.geeksforgeeks.org/problems/count-of-smaller-elements5947/1)

**Note on interpretation:** The exact wording on the GfG problem page for this "Basics" level problem can vary slightly between versions. This article assumes the standard interpretation used throughout this repository's Basics section:

> Given an array `arr` of `n` integers, for **each element** `arr[i]`, find the **count of elements in the whole array that are strictly smaller** than `arr[i]`. Return (or print) the result as an array `result` of size `n`, where `result[i] = count of elements < arr[i]` in `arr`.

This is *not* the "count smaller elements to the right of self" variant (that is a different, harder problem, discussed separately in the Interview Follow-ups section) — here the comparison is against the **entire array**, not just elements to the right.

## Problem Statement (as per GfG problem page)

Given an array `arr[]` of `n` integers (possibly with duplicates, possibly negative), construct an array `result[]` such that `result[i]` is equal to the count of elements in `arr` that are strictly smaller than `arr[i]`.

### Example 1

```
Input:  arr = [7, 0, 1, 3]
Output: [3, 0, 1, 2]

Explanation:
- arr[0] = 7  -> elements smaller than 7: {0,1,3}      -> count = 3
- arr[1] = 0  -> elements smaller than 0: {}            -> count = 0
- arr[2] = 1  -> elements smaller than 1: {0}            -> count = 1
- arr[3] = 3  -> elements smaller than 3: {0,1}          -> count = 2
```

### Example 2

```
Input:  arr = [6, 5, 4, 8]
Output: [2, 1, 0, 3]

Explanation:
- 6 -> smaller: {5,4}      -> 2
- 5 -> smaller: {4}        -> 1
- 4 -> smaller: {}         -> 0
- 8 -> smaller: {6,5,4}    -> 3
```

## Constraints

```
1 <= n <= 10^5   (some GfG variants extend to 10^6)
-10^9 <= arr[i] <= 10^9   (negatives allowed, duplicates allowed)
```

A deep look at what these constraints actually force on the solution:

- **Array size up to `10^5` (or `10^6`).** This is the single most important constraint driving approach selection. Any algorithm with `O(n^2)` time complexity performs roughly `n^2` operations. At `n = 10^5`, that is `10^10` operations. Even at an optimistic `10^8`–`10^9` simple operations per second on modern judges, `10^10` operations takes **on the order of 10–100 seconds**, far beyond any typical 1–2 second time limit. This makes the brute force nested-loop approach **infeasible** for the upper constraint range, even though it is correct and useful to discuss first for building intuition. This constraint alone forces us toward a sub-quadratic approach — specifically something built on **sorting** (`O(n log n)`) or, under additional assumptions about value range, **counting** (`O(n + range)`).

- **Element range `-10^9` to `10^9` (large, signed).** Because the values can be very large in magnitude and can be negative, we **cannot** naively use a counting-sort / frequency-array approach over the raw value range — an array indexed from `-10^9` to `10^9` would need on the order of `2 × 10^9` slots, which is far too much memory (and would dominate the time budget just to initialize). This is why the general-purpose optimal solution for this problem uses **sorting + binary search**, not direct counting sort. Counting sort only becomes viable as an *alternative* when the problem additionally guarantees a small, bounded value range (e.g., `0 <= arr[i] <= 10^5`) — this is called out explicitly in the Optimal Approach section as a constraint-dependent optimization, not a general solution.

- **Duplicates and the "strictly smaller" semantics.** Because duplicates are allowed, we must be precise about what "smaller" means. This problem defines it as **strictly smaller** (`<`), not "smaller or equal" (`<=`). This distinction directly changes the counting logic:
  - If two elements are equal, neither counts toward the other's "smaller" count. E.g., for `arr = [5, 5, 5]`, every `result[i] = 0`, because no element is *strictly* less than `5`.
  - When using sorted-array + binary search, this is precisely why we use **`bisect_left`** (which finds the first position where the value could be inserted while keeping the array sorted, i.e., the index of the first occurrence of that value, i.e., exactly the count of elements strictly less than it) rather than `bisect_right` (which would give the count of elements `<=` the value, i.e., "smaller-or-equal" semantics minus one for self). Using the wrong bisect function is the most common bug when solving this problem — see the Better Approach section for a worked trace showing why `bisect_left` is correct here.

- **Negative numbers.** Sorting-based and binary-search-based approaches handle negative numbers transparently since they rely purely on relative ordering (comparisons), not on the values being used as array indices. This is another reason the sort + binary search approach is preferred as the general solution — it is agnostic to sign and magnitude. Only the *counting sort variant* (Optimal Approach, bounded-range case) is sensitive to negative numbers, since it needs an offset shift to use values as array indices.

## Visualization / Diagram

The core idea behind the efficient approaches: **sort a copy of the array once**, then for every original element, the count of strictly-smaller elements is exactly its **first (leftmost) index in the sorted array**.

```
Original array (index:  0   1   2   3):
arr        = [   7,   0,   1,   3  ]
                 |    |    |    |
                 |    |    |    |   (conceptually, we need: how many
                 |    |    |    |    elements come "before" this value
                 |    |    |    |    if everything were sorted?)
                 v    v    v    v

Sorted copy of arr (ascending):
sorted_arr = [   0,   1,   3,   7  ]
index         0    1    2    3

For each original value, binary-search its leftmost position in sorted_arr:

   value 7  -->  bisect_left(sorted_arr, 7) = 3   (0,1,3 are before it)
   value 0  -->  bisect_left(sorted_arr, 0) = 0   (nothing before it)
   value 1  -->  bisect_left(sorted_arr, 1) = 1   (only 0 is before it)
   value 3  -->  bisect_left(sorted_arr, 3) = 2   (0,1 are before it)

Mapping back to original order:
   index:   0   1   2   3
   arr:    [7,  0,  1,  3]
   result: [3,  0,  1,  2]
             ^   ^   ^   ^
             |   |   |   |
     leftmost-position-in-sorted-array for each original element
```

With duplicates, the "leftmost position" property is exactly what makes `bisect_left` correct:

```
arr        = [5, 3, 5, 1]
sorted_arr = [1, 3, 5, 5]
                        ^-- two 5's occupy indices 2 and 3

bisect_left(sorted_arr, 5) = 2   (first 5 found at index 2; there are
                                   exactly 2 elements strictly smaller: 1,3)
So BOTH occurrences of 5 in arr map to result value 2 — correct, since
"smaller" excludes equal elements regardless of duplicates.

result = [2, 1, 2, 0]
```

## Brute Force Approach

### Idea

For each element `arr[i]`, scan the **entire array** and count how many elements `arr[j]` satisfy `arr[j] < arr[i]`. This directly follows the problem definition with no preprocessing.

### Python Code

```python
class Solution:
    def countSmallerBrute(self, arr):
        # Store length of the array
        n = len(arr)
        # Initialize result array with zeros
        result = [0] * n
        # Outer loop: pick each element as the reference value
        for i in range(n):
            # Reset count of smaller elements for this reference value
            count = 0
            # Inner loop: scan the entire array
            for j in range(n):
                # Check if this element is strictly smaller than arr[i]
                if arr[j] < arr[i]:
                    # Increment the smaller-elements count
                    count += 1
            # Store the final count for index i
            result[i] = count
        # Return the fully populated result array
        return result


if __name__ == "__main__":
    # Create an instance of Solution
    sol = Solution()
    # Run and print the first example
    print(sol.countSmallerBrute([7, 0, 1, 3]))   # [3, 0, 1, 2]
    # Run and print the second example
    print(sol.countSmallerBrute([6, 5, 4, 8]))   # [2, 1, 0, 3]
```

### Worked Trace

`arr = [7, 0, 1, 3]`

```
i=0, arr[i]=7:
    j=0: arr[0]=7 -> 7<7? No
    j=1: arr[1]=0 -> 0<7? Yes -> count=1
    j=2: arr[2]=1 -> 1<7? Yes -> count=2
    j=3: arr[3]=3 -> 3<7? Yes -> count=3
    result[0] = 3

i=1, arr[i]=0:
    all elements 7,0,1,3 are >= 0 except none < 0
    result[1] = 0

i=2, arr[i]=1:
    only 0 < 1
    result[2] = 1

i=3, arr[i]=3:
    0 and 1 are < 3
    result[3] = 2

Final: [3, 0, 1, 2]
```

### Complexity

- **Time: `O(n^2)`.** For every one of the `n` elements, we perform a full linear scan of the other `n` elements — `n × n = n^2` comparisons in the worst case. As established in the Constraints section, at `n = 10^5` this is `~10^10` operations, which is far too slow for typical time limits (would take tens of seconds vs. the usual 1-2 second budget). This approach is only acceptable for very small `n` (roughly up to `10^3`–`10^4` depending on time limit).
- **Space: `O(n)`** for the `result` array itself (excluding input). No additional auxiliary structures are used, so this is the most space-efficient approach, but it is not time-competitive at scale.

## Better Approach

### Idea

Precompute a **sorted copy** of the array once — `O(n log n)`. Then, for each original element `arr[i]`, instead of scanning the whole array again, use **binary search** (`bisect_left`) on the sorted copy to directly find the count of elements strictly smaller than `arr[i]`. Binary search is valid here specifically because the array is sorted, so all elements smaller than a target value occupy a contiguous prefix — and `bisect_left` returns exactly the length of that prefix (the index of the first position where the value could be inserted to keep the array sorted).

### Python Code

```python
from bisect import bisect_left


class Solution:
    def countSmallerBetter(self, arr):
        # Build a sorted copy of the array once - O(n log n)
        sorted_arr = sorted(arr)
        # Initialize result list to collect counts
        result = []
        # Loop through each original element in input order
        for val in arr:
            # Binary search leftmost position of val in sorted_arr - O(log n)
            idx = bisect_left(sorted_arr, val)
            # That index equals the count of strictly smaller elements
            result.append(idx)
        # Return the final result list
        return result


if __name__ == "__main__":
    # Create an instance of Solution
    sol = Solution()
    # Run and print the first example
    print(sol.countSmallerBetter([7, 0, 1, 3]))   # [3, 0, 1, 2]
    # Run and print the second example
    print(sol.countSmallerBetter([5, 3, 5, 1]))   # [2, 1, 2, 0]
```

### Worked Trace

`arr = [7, 0, 1, 3]`

```
Step 1: sorted_arr = sorted([7, 0, 1, 3]) = [0, 1, 3, 7]

Step 2: for each original value, binary search leftmost insertion point

  val=7: bisect_left([0,1,3,7], 7)
         low=0, high=4
         mid=2 -> sorted_arr[2]=3 < 7 -> low=3
         mid=3 -> sorted_arr[3]=7, not < 7 -> high=3
         low==high==3 -> return 3
         result.append(3)

  val=0: bisect_left([0,1,3,7], 0)
         mid=2 -> 3 not < 0 -> high=2
         mid=1 -> 1 not < 0 -> high=1
         mid=0 -> 0 not < 0 -> high=0
         low==high==0 -> return 0
         result.append(0)

  val=1: bisect_left([0,1,3,7], 1) -> returns 1
         result.append(1)

  val=3: bisect_left([0,1,3,7], 3) -> returns 2
         result.append(2)

Final: [3, 0, 1, 2]   (matches brute force)
```

### Complexity

- **Time: `O(n log n)`.** Sorting the copy costs `O(n log n)`. Then, for each of the `n` original elements, a binary search over the sorted array of size `n` costs `O(log n)`, for a total query cost of `O(n log n)`. Combined: `O(n log n) + O(n log n) = O(n log n)` overall — a massive improvement over `O(n^2)`. At `n = 10^5`, `n log n ≈ 10^5 × 17 ≈ 1.7 × 10^6` operations — comfortably fast (milliseconds).
- **Space: `O(n)`** for the sorted copy of the array, plus `O(n)` for the result array — `O(n)` overall (constant factor of 2).

## Optimal Approach

### Is sort + binary search already optimal?

For a **comparison-based** algorithm (one that only learns information about elements by comparing them to each other, without assuming anything about the value domain), `O(n log n)` is provably optimal in the general case — this is the same lower bound that applies to comparison-based sorting. So the Better Approach above (sort + binary search) is, in general, **already asymptotically optimal** and is the recommended solution for the stated constraints (`arr[i]` up to `10^9` in magnitude).

However, if the problem gives us an **additional constraint** — a small, bounded value range — we can beat `O(n log n)` using a **non-comparison-based** technique: **counting sort with a prefix-count (cumulative frequency) array**.

### When this applies

This optimization is valid **only if** the value range is small and bounded, e.g., `0 <= arr[i] <= maxVal` where `maxVal` is on the order of `10^5` or so (comparable to `n`, not `10^9`). This is explicitly a **constraint-dependent** optimization — it is not a drop-in replacement for the general solution.

### Idea

1. Build a frequency array `freq[]` of size `maxVal + 1`, where `freq[v]` = number of times value `v` appears in `arr`.
2. Convert it into a **prefix sum (cumulative count) array** `prefix[]`, where `prefix[v]` = count of elements in `arr` that are `<= v`.
3. For each element `arr[i]`, the count of elements **strictly smaller** than `arr[i]` is `prefix[arr[i] - 1]` (or `0` if `arr[i] == 0`, handling the case where there's nothing below the minimum possible value).

For arrays that include negative numbers, shift every value by an `offset = -minVal` so all indices become non-negative before applying the same logic — this only remains efficient if `maxVal - minVal` stays small.

### Python Code

```python
class Solution:
    def countSmallerCountingSort(self, arr):
        # Handle empty array edge case
        if not arr:
            # Return empty result for empty input
            return []

        # Find the minimum value in the array
        min_val = min(arr)
        # Find the maximum value in the array
        max_val = max(arr)
        # Compute offset so the smallest value maps to index 0
        offset = -min_val
        # Compute size of the value range (must be small/bounded to help)
        range_size = max_val - min_val + 1

        # Initialize frequency array with zeros
        freq = [0] * range_size
        # Loop through array to populate frequency counts
        for val in arr:
            # Increment frequency at the shifted index for this value
            freq[val + offset] += 1

        # Initialize prefix (cumulative count) array with zeros
        prefix = [0] * range_size
        # Base case: prefix at index 0 equals freq at index 0
        prefix[0] = freq[0]
        # Loop to build cumulative counts from index 1 onward
        for i in range(1, range_size):
            # prefix[i] = count of elements <= (i - offset)
            prefix[i] = prefix[i - 1] + freq[i]

        # Initialize result list to collect final counts
        result = []
        # Loop through original array in input order
        for val in arr:
            # Compute shifted index for current value
            idx = val + offset
            # Elements strictly smaller than val = elements with value <= (val - 1)
            result.append(prefix[idx - 1] if idx > 0 else 0)
        # Return the final result list
        return result


if __name__ == "__main__":
    # Create an instance of Solution
    sol = Solution()
    # Run and print the first example
    print(sol.countSmallerCountingSort([7, 0, 1, 3]))   # [3, 0, 1, 2]
    # Run and print the second example
    print(sol.countSmallerCountingSort([5, 3, 5, 1]))   # [2, 1, 2, 0]
```

### Worked Trace

`arr = [7, 0, 1, 3]`

```
min_val = 0, max_val = 7, offset = 0, range_size = 8

freq (index 0..7): value -> count
  freq[0]=1 (value 0)
  freq[1]=1 (value 1)
  freq[2]=0
  freq[3]=1 (value 3)
  freq[4]=0
  freq[5]=0
  freq[6]=0
  freq[7]=1 (value 7)
  freq = [1,1,0,1,0,0,0,1]

prefix (cumulative counts, prefix[i] = count of elements <= i):
  prefix[0] = 1
  prefix[1] = 1+1 = 2
  prefix[2] = 2+0 = 2
  prefix[3] = 2+1 = 3
  prefix[4] = 3
  prefix[5] = 3
  prefix[6] = 3
  prefix[7] = 3+1 = 4
  prefix = [1,2,2,3,3,3,3,4]

For each element, count smaller = prefix[val - 1] (or 0 if val==0):
  val=7: idx=7>0 -> prefix[6] = 3   -> result: 3
  val=0: idx=0    -> 0                -> result: 0
  val=1: idx=1>0 -> prefix[0] = 1   -> result: 1
  val=3: idx=3>0 -> prefix[2] = 2   -> result: 2

Final: [3, 0, 1, 2]   (matches both previous approaches)
```

### Complexity and Tradeoff Discussion

- **Time: `O(n + range)`**, where `range = maxVal - minVal + 1`. Building the frequency array is `O(n)` (one pass over `arr`), building the prefix array is `O(range)`, and computing results is `O(n)`. Total: `O(n + range)`.
- **Space: `O(range)`** for the frequency/prefix arrays (in addition to `O(n)` for input/output).
- **The tradeoff, explicitly:**
  - If `range` is **small relative to `n log n`** (e.g., `range ~ 10^5` and `n ~ 10^5`, so `range ≈ n`), then `O(n + range) ≈ O(n)` **beats** `O(n log n)` — this is a genuine win.
  - If `range` is **large** (e.g., `10^9` as allowed by the general constraints of this problem), then `O(n + range)` becomes `O(n + 10^9)`, which is **drastically worse** than `O(n log n) ≈ O(1.7 × 10^6)` at `n = 10^5` — both in time (building a billion-sized array) and especially in **space** (a billion-element array will not fit in typical memory limits, e.g., 256 MB).
  - **Conclusion:** counting sort / prefix-count is a valuable optimization **only when the problem guarantees a small bounded value range**. Given this problem's stated constraints (`arr[i]` up to `10^9` in magnitude), the **sort + binary search approach is the recommended general solution**; the counting-sort approach should be mentioned as a follow-up optimization contingent on tighter value-range constraints, which is exactly how it's presented here.

## Edge Cases

- **Empty array (`n = 0`):** Result should be an empty array. All three approaches naturally handle this if the loops/comprehensions simply don't execute — worth an explicit early return for clarity and to avoid `min()`/`max()` errors on an empty sequence in the counting-sort approach.
- **Single element (`n = 1`):** `result = [0]` always — there are no other elements to be smaller than it, regardless of the element's value.
- **All elements equal (e.g., `[4, 4, 4, 4]`):** Every `result[i] = 0`, since "smaller" is strict (`<`), and no element is strictly less than another equal element. This is the key case that validates correct use of `bisect_left` over `bisect_right`.
- **All distinct, sorted ascending (e.g., `[1, 2, 3, 4]`):** `result = [0, 1, 2, 3]` — each element's count-of-smaller equals its own 0-based rank/index in the (already sorted) array.
- **All distinct, sorted descending (e.g., `[4, 3, 2, 1]`):** `result = [3, 2, 1, 0]` — same underlying logic, just reading ranks in reverse order relative to original positions.
- **Duplicates mixed with distinct values (e.g., `[3, 1, 3, 2, 1]`):** Sorted copy is `[1, 1, 2, 3, 3]`. `bisect_left` for `3` gives `3` (both 3's map to 3), for `1` gives `0` (both 1's map to 0), for `2` gives `2`. Result: `[3, 0, 3, 2, 0]`. This is the general case that exercises correct duplicate handling.
- **Negative numbers (e.g., `[-5, 0, -3, 2]`):** Sort/binary-search approach handles this transparently: `sorted = [-5, -3, 0, 2]`, giving `result = [0, 2, 1, 3]`. The counting-sort approach requires an explicit `offset` shift (`offset = -min_val = 5`) to map negatives into valid non-negative array indices — forgetting this offset is a common bug in that approach specifically.

## Interview Follow-ups

1. **"What if we instead want the count of smaller elements only to the *right* of each index (the classic 'Count Smaller Numbers After Self' problem)?"**
   This is a materially different and harder problem, because the comparison set shrinks as you move left to right, and a simple global sort+lookup no longer works directly (a value's "smaller count" depends on which elements haven't been processed yet). The standard efficient solutions are: (a) a **Binary Indexed Tree (Fenwick Tree) with coordinate compression**, processing the array from right to left and querying/updating counts as you go, in `O(n log n)`; or (b) a **modified merge sort** that counts cross-inversions during the merge step, also `O(n log n)`.

2. **"Can you solve this using a Binary Indexed Tree / Fenwick Tree instead of sort + binary search?"**
   Yes — compress the values (map them to ranks `0..n-1` via sorting, handling duplicates carefully), then build a Fenwick Tree over the rank space. Insert all elements first (or insert incrementally depending on the exact variant), then for each element query `fenwick.prefixSum(rank(arr[i]) - 1)` to get the count of strictly smaller elements. This is `O(n log n)` — asymptotically the same as sort + binary search — but is the standard technique to know because it **generalizes** to online/streaming variants and to the "smaller to the right" variant, where a static sorted array alone doesn't suffice.

3. **"How would you handle strictly-smaller vs. smaller-or-equal variants?"**
   This changes exactly one thing in the binary-search approach: use `bisect_left` for strictly-smaller (count of elements `< val`), and `bisect_right` (a.k.a. `bisect`) for smaller-or-equal (count of elements `<= val`, which conveniently also equals "smaller-or-equal count minus 1" would give strictly smaller if you're comparing an element to *other* elements excluding itself — worth clarifying explicitly with the interviewer which is wanted, since duplicates make the two answers diverge). In the counting-sort approach, this changes whether you look up `prefix[val - 1]` (strictly smaller) or `prefix[val]` (smaller-or-equal).

4. **"Can this be done online/streaming — i.e., elements arrive one at a time and you need running answers?"**
   Yes, using a **Fenwick Tree (or Binary Indexed Tree) over a coordinate-compressed value space**, or alternatively a **balanced BST / order-statistics tree** (like a Python `SortedList` from `sortedcontainers`, backed by a skip-list-like structure) that supports `O(log n)` insertion and `O(log n)` rank queries. Each new element is inserted and its current rank (count of smaller elements seen so far) is queried in `O(log n)`, giving `O(n log n)` total for `n` streamed elements. A raw sort-once approach doesn't work here since the "sorted array" would need to be rebuilt (or maintained sorted) after every insertion, which a plain Python list can't do efficiently (`O(n)` insertion cost per element via `list.insert`).

5. **"What if `n` is up to `10^6` and array values are guaranteed to be within `[0, 10^5]` — how does that change your approach?"**
   This is exactly the scenario where the counting-sort/prefix-count approach (Optimal Approach section) becomes strictly better than sort + binary search: `O(n + range) = O(10^6 + 10^5)` beats `O(n log n) = O(10^6 × 20) = O(2 × 10^7)` — both are fast enough in practice, but the counting approach avoids comparison overhead and log-factor entirely, and is the "expected" optimal answer once bounded-range is confirmed with the interviewer.

## Interview Explanation Tips

- **Start by restating the problem out loud and immediately clarify the ambiguity that trips people up**: "Smaller than each element — do we mean *strictly* smaller, or smaller-or-equal? And is this counting against the whole array, or only elements to the right/left of the current index?" Getting this confirmed upfront avoids solving the wrong problem, and signals to the interviewer that you're thinking about duplicate-handling correctness from the start rather than as an afterthought.
- **Narrate the brute force first, even though you know it's not the final answer.** It's the fastest way to prove you understand the requirement precisely, and it gives you a concrete baseline to optimize from. Explicitly state the `O(n^2)` complexity and *why* it's too slow given the stated constraints (walk through the "`10^5` squared is `10^10`, that's ~10+ seconds, too slow for a 1-2 second limit" reasoning) — this demonstrates constraint-driven design thinking, which interviewers specifically look for.
- **Bridge to the sort + binary search idea by pointing out the redundant work in brute force**: "Every time I ask 'how many elements are smaller than X', I'm redoing a linear scan I could answer instantly if the array were sorted — because in a sorted array, all smaller elements form a contiguous prefix, and finding the boundary of that prefix is just binary search." This is the key insight to say out loud.
- **When you introduce `bisect_left`, explicitly explain why it (and not `bisect_right`) is correct for "strictly smaller."** Walk through a tiny duplicate example (`[5, 5, 3]`) live if asked — this is the detail that separates a correct implementation from an off-by-one bug, and interviewers often probe here specifically.
- **Proactively mention the Fenwick Tree / Binary Indexed Tree as the "next level" technique**, even if you don't implement it, to show awareness of where this problem class goes: "If this needed to support elements arriving online, or if we needed 'smaller to the right' instead of the whole array, I'd reach for a Fenwick Tree with coordinate compression — it supports insert and prefix-count queries in `O(log n)` each, which a static sorted array can't do efficiently once you need mutations." This signals depth beyond the immediate problem without over-engineering the actual solution you're asked to code.
- **Close by discussing the counting-sort alternative as a conditional optimization, not a default** — this shows you understand that "optimal" depends on constraints, not just on always reaching for the fanciest technique: "If the interviewer tells me the value range is small and bounded, I'd switch to a prefix-count array for `O(n + range)`, which beats `O(n log n)` — but only because the range is small; if values can be up to `10^9`, that approach falls apart on memory, so sort + binary search is the right general-purpose choice here."
