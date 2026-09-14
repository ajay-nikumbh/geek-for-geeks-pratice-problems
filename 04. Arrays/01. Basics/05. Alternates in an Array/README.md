# Alternates in an Array

**GfG Link:** https://www.geeksforgeeks.org/problems/print-alternate-elements-of-an-array/1

## Problem Statement

Given an array `arr` of `n` integers, print (or return) the **alternate elements** of the array, starting from the **first element** — i.e., the elements present at indices `0, 2, 4, 6, ...` (0-indexed).

### Example 1

```
Input:  arr = [10, 20, 30, 40, 50]
Output: [10, 30, 50]

Explanation: Indices 0, 2, 4 hold values 10, 30, 50.
Indices 1, 3 (values 20, 40) are skipped.
```

### Example 2

```
Input:  arr = [5, 1, 8, 2, 9, 3, 7]
Output: [5, 8, 9, 7]

Explanation: Indices 0, 2, 4, 6 -> 5, 8, 9, 7
Indices 1, 3, 5 -> 1, 2, 3 are skipped.
```

---

## Constraints

```
1 <= n <= 10^6
1 <= arr[i] <= 10^6
```

**Deep dive:**

- **Size of `n` (up to 10^6):** This tells us the expected solution must run in **linear time O(n)** — anything with nested loops (O(n^2)) or unnecessary repeated work per element will likely time out for a million elements. It also hints that the solution should avoid extra passes over the array beyond what is strictly necessary; a single sweep collecting every other element is the natural fit.

- **Output size relates to `n` via `ceil(n/2)`:** If we pick indices `0, 2, 4, ...` up to `n-1`, the count of picked elements is:
  - `n/2` (rounded up) = `ceil(n/2)` = `(n + 1) / 2` using integer division.

  Why ceiling and not floor? Because index `0` is always included (it's even), so:
  - If `n` is **even** (e.g., n = 6: indices 0,1,2,3,4,5), the alternate indices are 0,2,4 → exactly `n/2` elements.
  - If `n` is **odd** (e.g., n = 7: indices 0,1,2,3,4,5,6), the alternate indices are 0,2,4,6 → `4` elements, which is `(7+1)/2 = 4 = ceil(7/2)`.

  So the output array must be sized `(n + 1) / 2` (integer division) to safely hold all alternate elements without resizing/reallocation — an important detail if you pre-allocate the result array for performance (avoids dynamic array growth overhead, which matters at `n = 10^6`).

- **Why index-based iteration must correctly handle both even and odd length arrays:** A naive off-by-one (e.g., looping `i < n - 1` instead of `i < n`) would silently drop the **last valid alternate index** when `n` is odd (since the last valid index `n-1` is even and must be included). Correct loop bounds are `i < n`, not `i < n - 1`.

- **Element range (`1 <= arr[i] <= 10^6`):** This is small enough that we don't need to worry about overflow (standard 32-bit int is more than sufficient), and it confirms the task is purely about **positional selection**, not value-based filtering — no comparisons against `arr[i]` are needed, only against the index `i`.

---

## Visualization / Diagram

```
Index:     0     1     2     3     4     5     6
Array:  [ 10 ,  20 ,  30 ,  40 ,  50 ,  60 ,  70 ]
          |            |            |            |
          v     x      v     x      v     x      v
        KEEP  SKIP    KEEP  SKIP   KEEP  SKIP    KEEP

Alternate (even) indices : 0     2     4     6
                            |     |     |     |
                            v     v     v     v
Result array            : [10,   30,   50,   70]
```

Stride pattern — the "pointer" jumps by 2 each time instead of moving by 1 and testing:

```
i=0 --(+2)--> i=2 --(+2)--> i=4 --(+2)--> i=6 --(+2)--> i=8 (>= n, stop)
```

---

## Brute Force Approach

### Idea

Walk through **every** index from `0` to `n-1` (a full linear scan), and for each index `i`, check whether it is even using the modulo operator: `i % 2 == 0`. If true, include `arr[i]` in the result.

This is "brute force" in the sense that we touch every index and perform a conditional check on each one, even though half of those checks are wasted (we already know which indices we want in advance).

### Python Code

```python
class Solution:
    def printAlternatesBrute(self, arr):
        # Store length of the array
        n = len(arr)
        # Initialize empty result list to collect alternate elements
        result = []
        # Loop through every single index from 0 to n-1
        for i in range(n):
            # Check if current index is even using modulo
            if i % 2 == 0:
                # Append element at this even index to result
                result.append(arr[i])
        # Return the collected alternate elements
        return result


if __name__ == "__main__":
    # Create an instance of Solution class
    sol = Solution()
    # Define the input array
    arr = [5, 1, 8, 2, 9, 3, 7]
    # Call the brute force method and print the result
    print(sol.printAlternatesBrute(arr))   # [5, 8, 9, 7]
```

### Worked Trace

`arr = [5, 1, 8, 2, 9, 3, 7]`, `n = 7`

| i | i % 2 | condition | action        | result so far      |
|---|-------|-----------|---------------|---------------------|
| 0 | 0     | true      | append arr[0]=5 | [5]                |
| 1 | 1     | false     | skip           | [5]                |
| 2 | 0     | true      | append arr[2]=8 | [5, 8]             |
| 3 | 1     | false     | skip           | [5, 8]             |
| 4 | 0     | true      | append arr[4]=9 | [5, 8, 9]          |
| 5 | 1     | false     | skip           | [5, 8, 9]          |
| 6 | 0     | true      | append arr[6]=7 | [5, 8, 9, 7]       |

Final result: `[5, 8, 9, 7]`

### Complexity

- **Time:** O(n) — one pass over all n elements, but with a modulo operation performed **n times** (once per index, including the skipped ones). The constant factor is higher than necessary.
- **Space:** O(n) for the output array in the worst case (n up to ~ n/2 elements stored, still O(n) asymptotically). If we were only *printing* instead of collecting into a result array, auxiliary space would be O(1).

---

## Better Approach

### Idea

Since we always want indices `0, 2, 4, ...`, there's no need to visit the odd indices at all or compute `i % 2` for every element. Instead, **step directly by 2** using the loop's stride: `for i in range(0, n, 2)`. This visits exactly the indices we want and nothing else — no wasted iterations, no modulo computation per element.

### Python Code

```python
class Solution:
    def printAlternatesBetter(self, arr):
        # Store length of the array
        n = len(arr)
        # Initialize empty result list to collect alternate elements
        result = []
        # Loop directly over even indices, stepping by 2 each time
        for i in range(0, n, 2):
            # Append element at this index to result
            result.append(arr[i])
        # Return the collected alternate elements
        return result


if __name__ == "__main__":
    # Create an instance of Solution class
    sol = Solution()
    # Define the input array
    arr = [5, 1, 8, 2, 9, 3, 7]
    # Call the better method and print the result
    print(sol.printAlternatesBetter(arr))   # [5, 8, 9, 7]
```

### Worked Trace

`arr = [5, 1, 8, 2, 9, 3, 7]`, `n = 7`

| i (loop var) | arr[i] | result so far   |
|--------------|--------|------------------|
| 0            | 5      | [5]              |
| 2            | 8      | [5, 8]           |
| 4            | 9      | [5, 8, 9]        |
| 6            | 7      | [5, 8, 9, 7]     |
| next would be 8 >= n=7, loop ends |

Final result: `[5, 8, 9, 7]` — same output, fewer operations.

### Complexity

- **Time:** O(n) asymptotically (we visit `ceil(n/2)` elements, which is still `O(n)`), **but the constant factor is roughly halved** compared to brute force:
  - Brute force: `n` loop iterations + `n` modulo checks + `~n/2` appends.
  - Better: `~n/2` loop iterations + `~n/2` appends, **zero** modulo operations.
  - This matters at scale (`n = 10^6`): eliminating a million modulo operations and a million wasted loop iterations is a real, measurable speedup even though Big-O stays O(n).
- **Space:** O(n) for the output array (specifically `ceil(n/2)` elements → still O(n) asymptotic class), or O(1) auxiliary if only printing/streaming values without storing them.

---

## Optimal Approach

### Why Step-2 Iteration Is Already Optimal

Any correct solution **must** touch at least `ceil(n/2)` elements — there is no way to know or produce `ceil(n/2)` output values while inspecting fewer than `ceil(n/2)` positions. So the **better approach's O(n) time (with ~n/2 actual element touches) is asymptotically optimal** — you cannot do better than visiting each required element exactly once.

The "optimal" step here isn't a different algorithm — it's choosing the most **idiomatic, low-overhead expression** of the same idea. In Python, this is array/list **slicing**: `arr[::2]`.

### Python Code

```python
class Solution:
    def printAlternatesOptimal(self, arr):
        # Slice the array with default start=0, default stop=n, step=2
        return arr[::2]


if __name__ == "__main__":
    # Create an instance of Solution class
    sol = Solution()
    # Define the input array
    arr = [5, 1, 8, 2, 9, 3, 7]
    # Call the optimal method and print the result
    print(sol.printAlternatesOptimal(arr))   # [5, 8, 9, 7]

    # Edge case: empty array should return empty list
    print(sol.printAlternatesOptimal([]))          # []
    # Edge case: single element array should return that element
    print(sol.printAlternatesOptimal([42]))         # [42]
    # Edge case: two element array should return only first element
    print(sol.printAlternatesOptimal([1, 2]))       # [1]
```

### How Slicing Works Internally

`arr[::2]` is syntactic sugar for `arr[0:len(arr):2]`. Internally (in CPython), slicing with a step:

1. Computes the exact length of the resulting slice up front: `ceil((stop - start) / step)` = `ceil(n / 2)`.
2. **Pre-allocates** a new list object of exactly that size (no dynamic resizing / amortized-growth overhead like repeated `.append()` calls might incur).
3. Copies elements directly from the source list at positions `0, 2, 4, ...` into the new list in a tight, optimized C-level loop (implemented in `listobject.c`'s slice-assignment machinery), avoiding Python-level loop overhead entirely.

This means `arr[::2]` still performs O(n/2) work (a copy is fundamentally required to produce a new array) — it is not "free" — but it avoids Python interpreter loop overhead, function-call overhead of repeated `.append()`, and is typically the fastest way to express this in Python.

### Complexity

- **Time:** O(n) — specifically O(n/2) element copies, which is the theoretical minimum for producing a new array of alternate elements. You cannot beat this without changing the problem (e.g., streaming output instead of returning an array).
- **Space:**
  - **O(n)** (specifically O(n/2)) if you must **return/store a new array** — this space is unavoidable because the result itself has `ceil(n/2)` elements; you cannot report `ceil(n/2)` values while using less than `ceil(n/2)` space to hold them (unless streaming).
  - **O(1)** auxiliary space if the task is only to **print/stream** values one at a time (no result array retained) — e.g., `for i in range(0, n, 2): print(arr[i])`.

---

## Edge Cases

| Case | Input | Expected Output | Notes |
|------|-------|------------------|-------|
| Empty array | `[]` | `[]` | `n = 0`; loop/slice naturally produces empty result, no special-casing needed. |
| Single element | `[7]` | `[7]` | Index 0 is always included; result equals the whole array. |
| Two elements | `[3, 9]` | `[3]` | Only index 0 qualifies (n even ⇒ n/2 = 1 output element). |
| Odd length array | `[1, 2, 3, 4, 5]` | `[1, 3, 5]` | Last index (4) is even and included — confirms loop bound must be `i < n`, not `i < n-1`. |
| Even length array | `[1, 2, 3, 4]` | `[1, 3]` | Last index (3) is odd and excluded. |
| All same elements | `[8, 8, 8, 8, 8]` | `[8, 8, 8]` | Selection is purely index-based; element values (even if identical) don't affect which are picked. |

---

## Interview Follow-ups

1. **"Now print elements at odd indices instead (1, 3, 5, ...)."**
   Trivial change: `arr[1::2]` (start = 1) or `for i in range(1, n, 2)`. Good follow-up to test whether the candidate understands the `start` parameter of the stride, not just the stride itself.

2. **"Print alternate elements starting from the end of the array instead of the beginning."**
   This requires care about indexing direction. One approach: reverse first then take alternates from the new start — `arr[::-1][::2]` — or directly index from the end: last index, then `last - 2`, `last - 4`, etc., i.e., `arr[n-1::-2]` in Python, which naturally walks backward in steps of 2 from the last index. Tests understanding of negative/reverse strides.

3. **"Can you do this without any extra space — i.e., compact the alternate elements in-place at the front of the original array?"**
   Yes: use a write-pointer `w = 0`, and for `i` in `range(0, n, 2)`: `arr[w] = arr[i]; w += 1`. This overwrites the front of the array in-place with the alternate elements, achieving true O(1) extra space (ignoring the two integer pointers) if in-place mutation of the input is allowed. Discuss the tradeoff: destroys original array data beyond index `w`.

4. **"Generalize this to print every k-th element instead of every 2nd."**
   Straightforward generalization: `arr[::k]` or `for i in range(0, n, k)`. Useful to discuss how the same stride-based reasoning (and the `ceil(n/k)` output-size formula) extends cleanly — shows the interviewer you see the general pattern, not just a memorized trick for k=2.

5. **"What if the array is a linked list instead of an array — how does the approach change?"**
   Random-access index math (`i % 2`, slicing) no longer applies directly since linked lists lack O(1) index access. Instead, you'd walk node-by-node with a boolean toggle (`take = not take`) or advance two pointers/hops at a time (`node = node.next.next`), still O(n) time but no slicing shortcut available — a good test of whether the candidate over-relies on array-specific tricks.

---

## Interview Explanation Tips

- **State the indexing convention explicitly and early.** This problem is a classic **miscommunication trap**: "alternate elements" can be interpreted as 0-indexed (indices 0, 2, 4, ...) or colloquially as "1st, 3rd, 5th..." in 1-indexed human terms — which, conveniently, are the *same* elements, but say so out loud anyway ("I'll treat the array as 0-indexed, so alternates means indices 0, 2, 4, ... which corresponds to the 1st, 3rd, 5th elements if we count from 1"). This avoids any ambiguity about whether the interviewer actually means indices 1, 3, 5 (0-indexed) when they say "alternate starting from second element" — always clarify the starting point before coding.

- **Explicitly call out edge cases before or while coding**, especially for small arrays: mention that an empty array should return an empty result, and a single-element array should return that one element (since index 0 is always "alternate #1"). Saying this out loud shows the interviewer you're thinking about boundary conditions proactively rather than being asked "what about n=0?" and scrambling.

- **Narrate the progression brute force → optimal** even if you'd jump straight to the slice/stride solution: mention that a naive approach would check `i % 2 == 0` for every index, but that computing the modulo for indices you're going to skip anyway is wasted work — then pivot to "instead, I can just step the loop by 2 directly," which demonstrates you recognize redundant computation and eliminate it deliberately rather than by luck.

- **Be precise about time/space claims.** Say clearly: "this is O(n) time because we still touch roughly n/2 elements, which is asymptotically O(n), but the constant factor is about half of the brute-force modulo approach." And for space: "O(n) if I'm returning a new array, since the result itself has ~n/2 elements and that's unavoidable — but O(1) auxiliary if I'm just streaming/printing the values without storing them." This shows you distinguish between *asymptotic class* and *practical constant-factor* improvements, and between *output space* (unavoidable) and *auxiliary space* (potentially optimizable).

- **If asked to optimize further, offer the in-place compaction variant** (see Follow-up 3) — this signals you can go beyond the "obvious" slicing answer and reason about space constraints when explicitly pushed.
