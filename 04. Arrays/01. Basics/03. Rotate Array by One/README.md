# Rotate Array by One

**GfG Link:** https://www.geeksforgeeks.org/problems/cyclically-rotate-an-array-by-one2614/1

## Problem Statement

Given an array `arr` of `n` integers, rotate the array cyclically to the **right** by one position — the last element moves to the front, and every other element shifts one position to the right. The rotation should be done **in-place**.

### Example 1

```
Input:  arr = [1, 2, 3, 4, 5]
Output: [5, 1, 2, 3, 4]
```
Explanation: The last element `5` moves to index 0. Elements `1, 2, 3, 4` each shift one position to the right.

### Example 2

```
Input:  arr = [9, 8, 7, 6]
Output: [6, 9, 8, 7]
```
Explanation: `6` (last element) moves to the front; `9, 8, 7` shift right by one.

---

## Constraints

```
1 <= arr.size() <= 10^5   (typical GfG bound; some variants go up to 10^6)
0 <= arr[i] <= 10^6
```

**Deep dive:**

- **Size of `n` (up to 1e5–1e6):** This is large enough that any `O(n^2)` approach (e.g., rotating by repeatedly moving one element at a time using nested loops, or naive "shift everything by calling a rotate-by-1 function k times where k could be as large as n") would be far too slow — up to `10^10` to `10^12` operations, which will not run within typical time limits (~1 second for ~1e8 operations). This pushes us firmly toward a **single-pass, O(n)** solution.

- **"In-place, O(1) extra space expected":** This is the constraint that shapes the entire problem. It explicitly rules out the naive idea of allocating a brand-new array of size `n`, populating it in the rotated order, and copying it back — because that uses `O(n)` auxiliary space, not `O(1)`. GfG problems that say "in-place" almost always intend for you to:
  1. Modify the **original array's memory** directly (no new array of comparable size).
  2. Use **only a constant number of extra variables** (like one temp variable to hold a displaced element) — not proportional to `n`.

  The brute force (extra array) approach is still valid as a *first working solution* to reason about correctness, but it will not satisfy the space constraint of the problem, so it is not accepted as the final/optimal answer in an interview or on the judge.

- **How `n` size affects the choice:** Since we only need to rotate by **one** position (not by an arbitrary `k`), there's a very elegant `O(n)` time, `O(1)` space technique: save the last element in a temp variable, then shift every other element right by one (from the end toward the start, to avoid overwriting values before they're used), then drop the saved value into index 0. No auxiliary array of size `n` is needed regardless of how large `n` is — this makes the algorithm scale linearly and use constant memory even at `n = 10^6`.

---

## Visualization / Diagram

**Before rotation:**

```
Index:   0    1    2    3    4
Array: [ 1  , 2  , 3  , 4  , 5 ]
```

**Each element shifts one position to the right; the last element wraps around to the front:**

```
 ┌────────────────────────────────────────┐
 │                                        │
 ▼                                        │
[ 1 ]  [ 2 ]  [ 3 ]  [ 4 ]  [ 5 ]          │
  │      │      │      │      └───────────┘
  │      │      │      │      (5 wraps to front)
  ▼      ▼      ▼      ▼
[idx1] [idx2] [idx3] [idx4]
```

**After rotation:**

```
Index:   0    1    2    3    4
Array: [ 5  , 1  , 2  , 3  , 4 ]
```

Visually, think of it as a conveyor belt: everyone steps one seat to the right, and the person at the last seat walks around to sit in seat 0.

```
Before:  1 -> 2 -> 3 -> 4 -> 5
                              \
After:   5    1    2    3     4
         ^____|____|____|_____|
         (each moved one step right; 5 wrapped from end to start)
```

---

## Brute Force Approach

### Idea

Create a new temporary array of the same size. Place the last element of the original array at index `0` of the new array, then copy the remaining `n-1` elements (from index `0` to `n-2` of the original) into indices `1` to `n-1` of the new array. Finally, copy the new array back into the original array (or just return/print the new array, depending on requirements).

### Python Code

```python
class Solution:
    def rotateArrayByOneBrute(self, arr):
        # Get the number of elements in the array
        n = len(arr)
        # If array has 0 or 1 elements, nothing to rotate
        if n <= 1:
            # Return the array unchanged
            return arr

        # Create a new temporary array of same size, filled with 0s (O(n) space)
        temp = [0] * n
        # Place the last element of arr at index 0 of temp
        temp[0] = arr[n - 1]

        # Loop through all indices except the last one
        for i in range(n - 1):
            # Shift each element right by one position into temp
            temp[i + 1] = arr[i]

        # Loop through every index to copy temp back into arr
        for i in range(n):
            # Copy element from temp into original array to keep it in-place
            arr[i] = temp[i]

        # Return the rotated array
        return arr
```

### Worked Trace

`arr = [1, 2, 3, 4, 5]`, `n = 5`

1. `temp = [0, 0, 0, 0, 0]`
2. `temp[0] = arr[4] = 5` → `temp = [5, 0, 0, 0, 0]`
3. Loop `i = 0..3`:
   - `i=0`: `temp[1] = arr[0] = 1` → `temp = [5, 1, 0, 0, 0]`
   - `i=1`: `temp[2] = arr[1] = 2` → `temp = [5, 1, 2, 0, 0]`
   - `i=2`: `temp[3] = arr[2] = 3` → `temp = [5, 1, 2, 3, 0]`
   - `i=3`: `temp[4] = arr[3] = 4` → `temp = [5, 1, 2, 3, 4]`
4. Copy back: `arr = [5, 1, 2, 3, 4]`

**Result:** `[5, 1, 2, 3, 4]` ✔ matches expected output.

### Complexity

- **Time:** `O(n)` — one pass to fill `temp`, one pass to copy back = `2n` operations → `O(n)`.
- **Space:** `O(n)` — the `temp` array holds `n` elements, which is auxiliary space proportional to input size. This is what fails the "in-place, O(1) extra space" requirement, even though the time complexity is already optimal.

---

## Better Approach

### Idea

Avoid the extra array entirely. Save the **last element** in a single temp variable. Then shift every element right by one position **starting from the end of the array and moving toward the start** (this order is crucial — shifting from the end means we overwrite `arr[i]` only after we've already read it and moved it to `arr[i+1]`, so no data is lost). Finally, place the saved last element into index `0`.

### Python Code

```python
class Solution:
    def rotateArrayByOne(self, arr):
        # Get the number of elements in the array
        n = len(arr)
        # If array has 0 or 1 elements, nothing to rotate
        if n <= 1:
            # Return the array unchanged
            return arr

        # Save the last element in a temp variable, O(1) extra space
        last = arr[n - 1]

        # Loop from second-last index down to the first index
        for i in range(n - 2, -1, -1):
            # Shift current element one position to the right
            arr[i + 1] = arr[i]

        # Place the saved last element at the front of the array
        arr[0] = last

        # Return the rotated array
        return arr
```

### Step-by-Step Trace (with array state at each step)

`arr = [1, 2, 3, 4, 5]`, `n = 5`

| Step | Action | Array State |
|------|--------|-------------|
| Start | — | `[1, 2, 3, 4, 5]` |
| Save `last` | `last = arr[4] = 5` | `[1, 2, 3, 4, 5]` (unchanged, `last=5`) |
| `i=3` | `arr[4] = arr[3] = 4` | `[1, 2, 3, 4, 4]` |
| `i=2` | `arr[3] = arr[2] = 3` | `[1, 2, 3, 3, 4]` |
| `i=1` | `arr[2] = arr[1] = 2` | `[1, 2, 2, 3, 4]` |
| `i=0` | `arr[1] = arr[0] = 1` | `[1, 1, 2, 3, 4]` |
| Place `last` | `arr[0] = last = 5` | `[5, 1, 2, 3, 4]` |

**Result:** `[5, 1, 2, 3, 4]` ✔ correct, and achieved with **zero extra arrays**.

### Complexity

- **Time:** `O(n)` — single pass through the array (n-1 shifts + 1 assignment).
- **Space:** `O(1)` — only one extra variable (`last`) is used, regardless of how large `n` is. This is what makes it strictly better than the brute force: **same time complexity, but truly constant auxiliary space**, satisfying the "in-place" requirement of the problem.

---

## Optimal Approach

### Why the single-temp-variable shift IS optimal

For rotating by exactly **one** position, the in-place shifting approach above is already optimal:

- **Time `O(n)`** is a hard lower bound — every element (except possibly one) must move to a new position, so you cannot do better than visiting each element at least once.
- **Space `O(1)`** is the best possible for an in-place rotation — you cannot rotate without at least one temporary holding spot for the element being displaced.

So for this specific problem (rotate by 1), **the "Better Approach" above is also the "Optimal Approach."** There is no asymptotically faster or lower-space algorithm.

### Generalizing to Rotate-by-k: The Reversal Algorithm

If the problem were generalized to **rotate right by `k` positions** (instead of just 1), doing `k` separate "rotate by one" passes would cost `O(n*k)` time — too slow for large `k`. The standard optimal technique for that generalized problem is the **Reversal Algorithm**, which still achieves `O(n)` time and `O(1)` space:

To rotate an array **right** by `k` positions (with `k = k % n` to handle `k > n`):

1. Reverse the entire array.
2. Reverse the first `k` elements.
3. Reverse the remaining `n - k` elements.

```python
class Solution:
    def reverse(self, arr, start, end):
        # Loop while the two pointers haven't crossed
        while start < end:
            # Swap elements at start and end positions
            arr[start], arr[end] = arr[end], arr[start]
            # Move start pointer forward
            start += 1
            # Move end pointer backward
            end -= 1

    def rotateRightByK(self, arr, k):
        # Get the number of elements in the array
        n = len(arr)
        # If array is empty, there is nothing to rotate
        if n == 0:
            # Return the array unchanged
            return arr
        # Normalize k to handle cases where k > n
        k = k % n
        # If normalized k is 0, no rotation is needed
        if k == 0:
            # Return the array unchanged
            return arr

        # Reverse the whole array first
        self.reverse(arr, 0, n - 1)
        # Reverse the first k elements
        self.reverse(arr, 0, k - 1)
        # Reverse the remaining n-k elements
        self.reverse(arr, k, n - 1)
        # Return the rotated array
        return arr
```

**Quick check with `k = 1` on `[1, 2, 3, 4, 5]`:**

1. Reverse whole: `[5, 4, 3, 2, 1]`
2. Reverse first `k=1` element: `[5, 4, 3, 2, 1]` (single element, no change)
3. Reverse remaining `n-k=4` elements (indices 1..4): `[5, 1, 2, 3, 4]`

**Result:** `[5, 1, 2, 3, 4]` — matches the rotate-by-one output exactly. This confirms the reversal algorithm is a strict generalization: rotate-by-one is just the special case `k = 1`.

- **Time:** `O(n)` — three reversal passes, each touching at most `n` elements, so total work is `O(n) + O(k) + O(n-k) = O(2n) = O(n)`.
- **Space:** `O(1)` — reversal is done via in-place swaps using only index variables.

**Takeaway:** For rotate-by-one specifically, use the simple single-temp-variable shift — it's simpler code and equally optimal. Mention the reversal algorithm to show you understand how the technique scales to the more general "rotate by k" problem.

---

## Edge Cases

| Case | Behavior | Notes |
|------|----------|-------|
| **Empty array** (`n = 0`) | Return/leave as is | No elements to rotate; guard with `if n <= 1: return arr` to avoid index errors like `arr[n-1]` on an empty list. |
| **Single element** (`n = 1`) | No change | Rotating a single element by one position yields the same array; the loop `range(n-2, -1, -1)` naturally does nothing when `n=1`, but still guard explicitly for clarity and to avoid `arr[n-1]` edge issues if `n=0`. |
| **Two elements** (`n = 2`) | Simple swap | `[a, b]` → `[b, a]`. Trace: `last = b`, shift `arr[1] = arr[0]` → `[a, a]`, then `arr[0] = last` → `[b, a]`. Works correctly as a natural special case of the general algorithm. |
| **Duplicate elements** | Works identically | The algorithm operates purely on **positions**, not values, so duplicates (e.g., `[2, 2, 2, 3]` → `[3, 2, 2, 2]`) are handled with no special-casing needed. |
| **Very large array** (`n ~ 10^5`–`10^6`) | Still `O(n)` time, `O(1)` space | The in-place shift approach scales linearly with no extra memory overhead, making it suitable even at the upper constraint bound; the brute-force extra-array approach would still work but doubles memory footprint unnecessarily. |

---

## Interview Follow-ups

**Q1: How would you rotate the array by `k` positions instead of just 1?**
A: Use the **reversal algorithm**: normalize `k = k % n` (to handle `k > n`), reverse the whole array, then reverse the first `k` elements, then reverse the remaining `n-k` elements. This achieves `O(n)` time and `O(1)` space for any `k`. (Alternative: use a `O(n)` extra-space juggling/cyclic-replacement algorithm, or an extra array — but reversal is the standard optimal in-place technique.)

**Q2: How would you rotate the array to the left instead of the right?**
A: Left rotation by one means the **first** element moves to the end, and everything else shifts left by one. Mirror the logic: save `first = arr[0]`, then shift `arr[i] = arr[i+1]` for `i` from `0` to `n-2` (left to right this time, since we're shifting values *toward* the start), and finally set `arr[n-1] = first`. For left rotation by `k`, the reversal algorithm generalizes too: reverse first `k` elements, reverse remaining `n-k` elements, then reverse the whole array (this is the mirror of the right-rotation reversal order).

**Q3: Can you rotate by k positions in O(1) extra space? Walk through the reversal algorithm.**
A: Yes — this is exactly the reversal algorithm described above. The key insight is that reversing three specific sub-segments (whole array, then the two logical partitions) achieves the rotation using only in-place swaps, with no auxiliary array. Time is `O(n)`, space is `O(1)`, since reversal only needs two pointers and a temp variable for swapping, not proportional to `n`.

**Q4: What if `k > n`? Does the algorithm break?**
A: No, as long as you normalize with `k = k % n` before applying any rotation logic. Rotating by `n` positions returns the array to its original state, so rotating by `k` is equivalent to rotating by `k % n`. Skipping this normalization would cause unnecessary (or in a naive per-step implementation, extremely slow) work, or out-of-bounds indexing in a hand-rolled version.

**Q5: Why not just use array slicing (e.g., `arr = [arr[-1]] + arr[:-1]` in Python)? Isn't that simpler?**
A: It's simpler to write, but it creates a **new list object** under the hood — `O(n)` extra space — which violates the "in-place, O(1) extra space" constraint of this problem. It's a good brute-force/one-liner to mention, but you should explicitly call out that it doesn't meet the space requirement, and then present the temp-variable shifting (or reversal) approach as the compliant solution.

---

## Interview Explanation Tips

- **State the goal out loud first:** "I need to move the last element to the front and shift everyone else right by one — and I need to do this without allocating a new array, since the problem asks for O(1) extra space."

- **Call out the common mistake early:** Many candidates jump straight to creating a new array (`temp = [0]*n` or slicing) because it's the most intuitive way to think about "building the rotated result." Explicitly say: *"A naive approach would build a new array — but that's O(n) space, so let me instead do this in-place using a single temp variable."* This shows the interviewer you understand *why* the constraint matters, not just that you memorized a trick.

- **Explain the shift direction carefully:** Emphasize that you must shift starting from the **end** of the array moving toward the start. If you shifted from the start instead (`arr[i] = arr[i-1]` going forward), you'd overwrite values before reading them, corrupting the array. Walking through this on a whiteboard with a small example (like `n=4`) makes the "why end-to-start" reasoning concrete and convincing.

- **Connect it to the general pattern:** After solving rotate-by-one, proactively mention: *"If this were rotate-by-k, I'd generalize this idea using the reversal algorithm — reverse the whole array, then reverse the first k and remaining n-k segments separately. Rotate-by-one is just the k=1 special case of that same idea."* This signals depth and that you're not just pattern-matching a memorized solution, but understand the underlying principle of in-place array manipulation.

- **Mention complexity explicitly and justify optimality:** State clearly, "Time is O(n) because every element is touched once; space is O(1) because only one temp variable is used — and this is optimal because you can't rotate an array without visiting every element, and you can't avoid needing at least one temporary slot to hold a displaced value."
