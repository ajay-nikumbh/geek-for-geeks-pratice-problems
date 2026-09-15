# Remove All Duplicates in a Linked List

> **Topic:** Linked List  
> **Difficulty:** Medium  
> **Submissions:** 48,912  
> **Accuracy:** 41.27%  
> **Companies:** Microsoft  
> **Related Tags:** Linked List  
> **Problem Link:** https://www.geeksforgeeks.org/problems/remove-all-occurences-of-duplicates-in-a-linked-list/1

---

## Problem Statement

Given the head of a **sorted singly linked list**, remove **every node** whose value occurs **more than once** in the list.

Only values that appear **exactly once** in the original list should remain.

This is different from the common "remove duplicates, keep one copy" problem. Here, if a value is duplicated even once, **all of its occurrences are deleted entirely** — not just the extra copies.

Return the head of the modified linked list.

### Example 1

```text
Input:  1 -> 2 -> 3 -> 3 -> 4 -> 4 -> 5 -> NULL
Output: 1 -> 2 -> 5 -> NULL
```

Explanation:

- `1` appears once -> kept
- `2` appears once -> kept
- `3` appears twice -> **fully removed**
- `4` appears twice -> **fully removed**
- `5` appears once -> kept

### Example 2

```text
Input:  1 -> 1 -> 1 -> 2 -> 3 -> NULL
Output: 2 -> 3 -> NULL
```

Explanation:

- `1` appears three times -> fully removed, including the head
- `2` appears once -> kept
- `3` appears once -> kept

Compare this with the well-known variant "remove duplicates, keep one occurrence," which on Example 1 would produce:

```text
1 -> 2 -> 3 -> 4 -> 5 -> NULL
```

That variant keeps the first copy of every value. **This problem keeps nothing from a duplicated value.**

---

# 1. Interview Intuition

The list is **sorted**. That single fact is what makes this problem tractable without extra memory.

> In a sorted linked list, all occurrences of the same value are guaranteed to sit **consecutively**.

So instead of counting values globally, we only need to compare **adjacent nodes**. If `current.value == current.next.value`, we have found the start of a duplicate run. We can then walk forward through the entire run, and once we exit it, we know exactly which nodes to cut out.

But there is a second, subtler issue: **the head itself might be a duplicate**.

```text
1 -> 1 -> 1 -> 2 -> 3 -> NULL
```

Here the first three nodes must all disappear, and the new head becomes `2`. If we only tracked pointers starting at `head`, we would have no "previous" node to fix when the head itself is removed — exactly the same problem we see in ordinary head-deletion, except here it can also happen **in the middle of processing**, not just once at the start.

The clean fix is a **dummy node** placed before `head`:

```text
dummy -> 1 -> 1 -> 1 -> 2 -> 3 -> NULL
```

Now `previous` starts at `dummy`, not at `head`. Whether the duplicate run happens to include the head or not, the logic is identical — `previous.next` is simply pointed past the entire run.

The second key idea is **when `previous` is allowed to move**:

> `previous` only advances when the node it is about to step onto is confirmed to be **unique** (not part of any duplicate run).

If a run of duplicates is detected, `previous` stays exactly where it is, and only `previous.next` gets rewired — to skip the whole run. This is the opposite of the "keep one copy" problem, where `previous` would advance to the first copy before skipping the rest.

---

# 2. Core Linked List Idea

Consider the list:

```text
dummy -> 1 -> 2 -> 3 -> 3 -> 4 -> 4 -> 5 -> NULL
```

We scan with two pointers: `previous` (starts at `dummy`) and `current` (starts at `head`, i.e. `1`).

```text
dummy -> 1 -> 2 -> 3 -> 3 -> 4 -> 4 -> 5 -> NULL
 ^        ^
 |        |
previous current
```

`1` is not equal to `current.next` (`2`), so it's unique. Both pointers move forward together:

```text
dummy -> 1 -> 2 -> 3 -> 3 -> 4 -> 4 -> 5 -> NULL
          ^    ^
          |    |
      previous current
```

`2` is not equal to `current.next` (`3`), so it's unique too. Advance both again:

```text
dummy -> 1 -> 2 -> 3 -> 3 -> 4 -> 4 -> 5 -> NULL
               ^    ^
               |    |
           previous current
```

Now `current.value == current.next.value` (`3 == 3`). This is a duplicate run. **`previous` does NOT move.** Instead, `current` walks through the entire run of `3`s:

```text
dummy -> 1 -> 2 -> 3 -> 3 -> 4 -> 4 -> 5 -> NULL
               ^         ^
               |         |
           previous   current (now at first 4, past the run of 3s)
```

We relink:

```text
previous.next = current      # 2.next = 4
```

```text
dummy -> 1 -> 2 --------> 4 -> 4 -> 5 -> NULL
               ^          ^
               |          |
           previous    current
```

The run of `4`s begins immediately (`current.value == current.next.value`, `4 == 4`). Same treatment — `previous` stays at `2`, `current` walks past both `4`s to reach `5`:

```text
dummy -> 1 -> 2 --------> 4 -> 4 -> 5 -> NULL
               ^                    ^
               |                    |
           previous              current

previous.next = current      # 2.next = 5
```

```text
dummy -> 1 -> 2 -----------------> 5 -> NULL
               ^                    ^
               |                    |
           previous              current
```

`5` has no next node to compare against, so it's unique. Advance both, loop ends.

Final list (via `dummy.next`):

```text
1 -> 2 -> 5 -> NULL
```

---

# 3. Most Important Edge Case

## Case A — Every Node Is a Duplicate

```text
Input:  1 -> 1 -> 2 -> 2 -> NULL
Output: NULL
```

`previous` (at `dummy`) never advances past the initial position because every run gets fully skipped. At the end, `dummy.next` correctly points to `None`.

## Case B — No Duplicates At All

```text
Input:  1 -> 2 -> 3 -> NULL
Output: 1 -> 2 -> 3 -> NULL
```

Every node is unique, so `previous` and `current` advance together the whole way. The list is untouched.

## Case C — Duplicates at the Very Start

```text
Input:  1 -> 1 -> 2 -> 3 -> NULL
Output: 2 -> 3 -> NULL
```

The head itself must be discarded. This is exactly why the dummy node matters: `previous` starts at `dummy`, so `previous.next = current` naturally becomes the new head once the run of `1`s is skipped. Without a dummy node, we would need special-case code to reassign `head` directly.

## Case D — Duplicates at the Very End

```text
Input:  1 -> 2 -> 3 -> 3 -> NULL
Output: 1 -> 2 -> NULL
```

When the inner loop walks through the trailing run of `3`s, `current` eventually becomes `None` (it runs off the end of the list). The relinking step `previous.next = current` correctly sets `2.next = None`, terminating the list properly.

---

# 4. Approach 1 — Brute Force Thinking

A straightforward approach that does **not** depend on the list being sorted:

1. Traverse the list once and count how many times each value occurs, using a hash map.
2. Traverse the list a second time, keeping only nodes whose value has a count of exactly `1`, and rebuild the list (or relink in place).

```text
Linked List:
1 -> 1 -> 2 -> 3 -> 3 -> NULL

Pass 1 — count map:
{1: 2, 2: 1, 3: 2}

Pass 2 — keep values with count == 1:
2

Result:
2 -> NULL
```

### Why this works even if the list is unsorted

Because we are counting **all** occurrences globally rather than relying on adjacency, this approach handles:

```text
3 -> 1 -> 3 -> 2 -> 1 -> NULL
```

just as easily, producing:

```text
2 -> NULL
```

The optimal approach below, by contrast, **requires the list to be sorted** — it cannot detect that two `3`s are duplicates if they are not adjacent.

### Complexity

```text
Time  = O(n)   (two linear passes)
Space = O(n)   (hash map storing up to n distinct values)
```

This is a fine fallback answer, but for a **sorted** list an interviewer will expect you to avoid the extra space.

---

# 5. Optimal Approach — Dummy Node + Consecutive Run Detection (Sorted List)

Because the list is sorted, duplicate values form contiguous runs. We exploit this with three pointers:

- `dummy` — a sentinel node placed before `head`, so there is always a valid "previous" node.
- `previous` — the last node **confirmed unique** so far; it starts at `dummy`.
- `current` — the node currently being examined; it starts at `head`.

### The core decision at each step

```text
if current.next exists AND current.next.value == current.value:
    # current begins a duplicate run
    duplicate_value = current.value
    # walk current forward through the ENTIRE run
    while current is not None AND current.value == duplicate_value:
        current = current.next
    # current now points to the first node AFTER the run (or None)
    previous.next = current      # cut out the whole run
    # previous does NOT move — it stays just before the (now-connected) next segment
else:
    # current is not part of a duplicate run — it's unique
    previous = previous.next     # advance previous onto current
    current = current.next       # advance current normally
```

The crucial asymmetry: in the duplicate branch, `previous` is frozen while `current` sprints ahead through the whole run. In the unique branch, both pointers move together, one step at a time.

This is what makes the algorithm remove **all** copies rather than leaving one behind — `previous` never gets attached to a value that turned out to be duplicated.

---

# 6. Pointer Movement

Full dry run skeleton on:

```text
dummy -> 1 -> 2 -> 3 -> 3 -> 4 -> 4 -> 5 -> NULL
```

**State 0 — initial**

```text
dummy -> 1 -> 2 -> 3 -> 3 -> 4 -> 4 -> 5 -> NULL
 ^        ^
prev     curr
```

`curr.next.value (2) != curr.value (1)` -> unique. **Both pointers advance.**

**State 1**

```text
dummy -> 1 -> 2 -> 3 -> 3 -> 4 -> 4 -> 5 -> NULL
          ^    ^
         prev curr
```

`curr.next.value (3) != curr.value (2)` -> unique. **Both pointers advance.**

**State 2**

```text
dummy -> 1 -> 2 -> 3 -> 3 -> 4 -> 4 -> 5 -> NULL
               ^    ^
              prev curr
```

`curr.next.value (3) == curr.value (3)` -> **duplicate run detected.** `prev` freezes here. Inner loop walks `curr` through both `3`s.

**State 3 — inner loop finishes**

```text
dummy -> 1 -> 2 -> 3 -> 3 -> 4 -> 4 -> 5 -> NULL
               ^         ^
              prev      curr (first 4)
```

Relink: `prev.next = curr` -> `2.next = 4`. **`prev` still does not move.**

```text
dummy -> 1 -> 2 --------> 4 -> 4 -> 5 -> NULL
               ^          ^
              prev       curr
```

`curr.next.value (4) == curr.value (4)` -> **another duplicate run**, immediately. Inner loop walks `curr` through both `4`s.

**State 4 — inner loop finishes**

```text
dummy -> 1 -> 2 --------> 4 -> 4 -> 5 -> NULL
               ^                    ^
              prev                curr (5)
```

Relink: `prev.next = curr` -> `2.next = 5`. **`prev` still frozen at `2`.**

```text
dummy -> 1 -> 2 -----------------> 5 -> NULL
               ^                    ^
              prev                curr
```

`curr.next` is `None`, so the duplicate-check condition is false -> `5` is unique. **Both pointers advance.**

**State 5**

```text
dummy -> 1 -> 2 -----------------> 5 -> NULL
                                    ^    ^
                                   prev curr(None)
```

`curr` is `None` — outer loop ends.

Result via `dummy.next`:

```text
1 -> 2 -> 5 -> NULL
```

Notice the pattern across the whole run: **`prev` only ever moves onto a node it has personally verified is not the start of a duplicate run.** It stayed at `2` through two separate relinking operations before finally being allowed to move again.

---

# 7. Algorithm

### Step 1 — Dummy Setup

Create a dummy node and point it at `head`:

```text
dummy.next = head
previous   = dummy
current    = head
```

### Step 2 — Main Loop Structure

While `current` is not `None`, examine whether `current` begins a duplicate run:

```text
while current is not None:
    if current.next is not None and current.next.value == current.value:
        # duplicate branch — Step 3
    else:
        # unique branch — Step 5
```

### Step 3 — Duplicate-Run Detection Sub-Loop

Record the duplicated value, then advance `current` past every node carrying that value:

```text
duplicate_value = current.value

while current is not None and current.value == duplicate_value:
    current = current.next
```

When this sub-loop ends, `current` is either `None` or the first node with a different (larger, since sorted) value.

### Step 4 — Relinking

Skip the entire run in one pointer update, and **do not move `previous`**:

```text
previous.next = current
```

### Step 5 — Non-Duplicate Advance Case

If `current` was not the start of a duplicate run, both pointers move forward by exactly one node:

```text
previous = previous.next
current  = current.next
```

### Step 6 — Return

```text
return dummy.next
```

---

# 8. Optimal Python Solution

```python
class Solution:

    # Remove every node whose value occurs more than once in a sorted list.
    def removeDuplicates(self, head):

        # Create a dummy node so the head can be safely replaced.
        dummy = Node(0)

        # Connect the dummy node to the front of the list.
        dummy.next = head

        # previous tracks the last node confirmed to be unique.
        previous = dummy

        # current is the node being examined right now.
        current = head

        # Continue until we have examined every node.
        while current is not None:

            # Check whether current starts a run of duplicate values.
            if current.next is not None and current.next.val == current.val:

                # Remember the value that is being duplicated.
                duplicate_value = current.val

                # Walk current forward through the entire run of this value.
                while current is not None and current.val == duplicate_value:

                    # Move current one node further into (or past) the run.
                    current = current.next

                # Cut out the whole run in a single pointer update.
                previous.next = current

                # previous stays put — it must not attach to a duplicated value.

            else:

                # current holds a value that appears exactly once so far.
                # Advance previous onto current, confirming current as unique.
                previous = previous.next

                # Advance current to examine the next node.
                current = current.next

        # dummy.next is the head of the list with all duplicates removed.
        return dummy.next
```

---

# 9. Complete Dry Run

Input:

```text
1 -> 2 -> 3 -> 3 -> 4 -> 4 -> 5 -> NULL
```

Setup:

```text
dummy.next = 1
previous   = dummy
current    = 1
```

### Iteration 1

```text
current = 1, current.next = 2
1 != 2  -> not a duplicate
previous = previous.next   # previous = 1
current  = current.next    # current  = 2
```

```text
dummy -> [1] -> 2 -> 3 -> 3 -> 4 -> 4 -> 5
           ^    ^
        previous current
```

### Iteration 2

```text
current = 2, current.next = 3
2 != 3  -> not a duplicate
previous = previous.next   # previous = 2
current  = current.next    # current  = 3 (first 3)
```

```text
dummy -> 1 -> [2] -> 3 -> 3 -> 4 -> 4 -> 5
                ^     ^
             previous current
```

### Iteration 3

```text
current = 3 (first), current.next = 3 (second)
3 == 3  -> duplicate run begins
duplicate_value = 3

  inner loop:
    current = 3 (first) -> current = current.next = 3 (second)
    current = 3 (second) -> current = current.next = 4 (first)
    current.val (4) != duplicate_value (3) -> stop inner loop

previous.next = current    # 2.next = 4 (first)
previous stays at 2
```

```text
dummy -> 1 -> [2] ----------> [4] -> 4 -> 5
                ^               ^
             previous         current
```

### Iteration 4

```text
current = 4 (first), current.next = 4 (second)
4 == 4  -> duplicate run begins
duplicate_value = 4

  inner loop:
    current = 4 (first) -> current = current.next = 4 (second)
    current = 4 (second) -> current = current.next = 5
    current.val (5) != duplicate_value (4) -> stop inner loop

previous.next = current    # 2.next = 5
previous stays at 2
```

```text
dummy -> 1 -> [2] -------------------> [5] -> NULL
                ^                        ^
             previous                 current
```

### Iteration 5

```text
current = 5, current.next = None
condition "current.next is not None and ..." is False -> not a duplicate
previous = previous.next   # previous = 5
current  = current.next    # current  = None
```

```text
dummy -> 1 -> 2 -------------------> [5] -> NULL
                                        ^
                                previous, current = None
```

### Loop Ends

`current is None` -> exit outer loop.

Return `dummy.next`:

```text
1 -> 2 -> 5 -> NULL
```

This matches the expected output exactly — `3` and `4` were fully removed, `1`, `2`, and `5` survived because they each appeared exactly once.

---

# 10. Complexity Analysis

Let:

```text
n = number of nodes in the list
```

### Time Complexity

At first glance the nested `while` loops look like they might be `O(n^2)`, but look closely at what the inner loop actually consumes: every node it walks through is a node that the outer loop will **never visit again** (it has been skipped entirely). Across the whole run of the algorithm, the outer loop and inner loop together visit each node **exactly once**.

```text
Time Complexity = O(n)
```

### Space Complexity

Only a fixed number of pointers (`dummy`, `previous`, `current`, `duplicate_value`) are used, regardless of `n`.

```text
Space Complexity = O(1)
```

### Comparison Table

| Approach | Time | Space | Requires Sorted Input? |
|---|---|---|---|
| Brute Force (hash map count) | `O(n)` | `O(n)` | No |
| Optimal (dummy node + run detection) | `O(n)` | `O(1)` | Yes |

---

# 11. Why This Is Optimal

For a **sorted** linked list, `O(n)` time and `O(1)` space is the best possible result:

- We must inspect every node at least once to know whether it is duplicated, so `O(n)` time is a hard lower bound.
- Because the list is sorted, duplicates are guaranteed to be adjacent — we never need a hash map or any auxiliary storage to detect them. A simple adjacent-value comparison is sufficient.

Contrast this with an **unsorted** list:

- Values that are duplicated may be arbitrarily far apart, so adjacency comparison alone cannot detect them.
- To solve it in `O(n)` time, you genuinely need `O(n)` extra space (a hash map counting occurrences, as in the brute-force approach).
- Alternatively, you could sort the list first (turning it into this exact problem), but that costs `O(n log n)` time, which is strictly worse.

So the dummy-node/run-detection technique is optimal **specifically because it exploits the sortedness** of the input — it is not a general-purpose duplicate-removal algorithm.

---

# 12. Common Mistakes

## Mistake 1 — Forgetting the Dummy Node

Without a dummy node, if the head's value is duplicated, there is no "previous" node to redirect. You would need extra branching to detect and update `head` directly, and it's easy to get wrong when the duplicate run happens to be at the very front. The dummy node removes this special case entirely.

## Mistake 2 — Advancing `previous` Even When Skipping a Run

This is the single most common bug for this specific problem:

```python
# WRONG
if current.next is not None and current.next.val == current.val:
    duplicate_value = current.val
    while current is not None and current.val == duplicate_value:
        current = current.next
    previous.next = current
    previous = previous.next   # BUG: this re-attaches previous to the run!
```

If `previous` moves forward here, it ends up pointing at whatever `previous.next` was **before** you cut the run out — which may not be what you intended, and in some pointer orderings will silently leave one copy of the duplicated value in the list. Remember: this problem requires removing **all** copies, so `previous` must stay frozen throughout the entire duplicate branch.

## Mistake 3 — Off-by-One in the Inner While Loop Condition

```python
# WRONG — only skips ONE duplicate, not the whole run
if current.next is not None and current.next.val == current.val:
    current = current.next.next
    previous.next = current
```

This only works for runs of exactly two duplicates. If a value appears three or more times, this leaves a dangling duplicate node in the list. The inner loop must continue **while the value matches**, not just skip a fixed number of nodes.

## Mistake 4 — Not Handling a Duplicate Run That Extends to the End

```text
1 -> 2 -> 3 -> 3 -> NULL
```

When the inner loop walks through the trailing `3`s, `current` becomes `None`. Code that assumes `current` is always a valid node afterward (for example, trying to read `current.val` again before checking for `None`) will crash. The relinking step `previous.next = current` handles this correctly as long as the loop condition explicitly checks `current is not None` before touching `current.val`.

## Mistake 5 — Confusing This With "Keep One Copy"

It is very easy to accidentally write the well-known "delete duplicates, keep one" solution instead, especially since the two problems look almost identical at first glance. Always double check: does a value that appears twice get **zero** copies in the output, or **one**? This problem requires zero.

---

# 13. Visual Cheat Sheet

## Unique Node — Both Pointers Advance

```text
Before:

previous  current
   |         |
   v         v
   2 ------> 5 -> ...        (5 != next value, or no next value)

Operation:

previous = previous.next
current  = current.next


After:

            previous  current
               |         |
               v         v
   2 --------> 5 ------> ...
```

## Duplicate Run — Only `current` Moves, Then One Relink

```text
Before:

previous          current
   |                 |
   v                 v
   2 ------> 3 ----> 3 ----> 4 -> ...


Inner loop walks current past the whole run:

previous                          current
   |                                 |
   v                                 v
   2 ------> 3 ----> 3 ----> 4 ----> ...


Operation:

previous.next = current


After:

previous                current
   |                        |
   v                        v
   2 ----------------->     4 -> ...

previous did NOT move.
```

## Head Is Part Of A Duplicate Run

```text
Before:

dummy -> 1 -> 1 -> 1 -> 2 -> 3 -> NULL
 ^
previous

Inner loop walks current past all three 1s:

dummy -> 1 -> 1 -> 1 -> 2 -> 3 -> NULL
 ^                       ^
previous               current

Operation:

previous.next = current   # dummy.next = 2

After:

dummy ------------------> 2 -> 3 -> NULL

Return dummy.next -> new head is 2.
```

---

# 14. Interview Explanation in 30 Seconds

> Since the list is sorted, duplicates are always consecutive, so I only need to compare a node with its immediate neighbor. I use a dummy node before the head so I always have a valid `previous` pointer, even if the head itself turns out to be duplicated. I scan with `current`: if `current.next` has the same value as `current`, I've found a duplicate run, so I walk `current` all the way through it and then do `previous.next = current` to cut the whole run out — without moving `previous`. If `current` is not part of a run, I advance both `previous` and `current` together, confirming that node as unique. This runs in `O(n)` time with `O(1)` extra space.

---

# 15. Interviewer Follow-Up Questions

## Q1. What if the list is NOT sorted — how does your approach change?

Adjacent-node comparison no longer works, because two copies of the same value could be anywhere in the list. Two options: (1) use a hash map to count occurrences in one pass, then filter in a second pass — `O(n)` time, `O(n)` space; or (2) sort the list first, which turns it into this exact problem, but costs `O(n log n)` time. Option 1 is generally preferred if you need to preserve original relative order among the surviving unique elements.

## Q2. How is this different from "remove duplicates keeping one occurrence"?

In "keep one occurrence," `previous` advances to the **first** copy of a duplicated value and then skips only the extras — one copy survives. Here, `previous` never advances onto a duplicated value at all; the entire run, including the first occurrence, is cut out. The pointer choreography differs specifically in whether `previous` is allowed to move during a duplicate run.

## Q3. Can you do this with O(1) space if the list is unsorted?

Generally no. Without sortedness, you cannot tell whether a node's value is duplicated without either remembering values you've already seen (extra space) or sorting the list first (extra time). `O(1)` space is only achievable here because sortedness guarantees adjacency.

## Q4. Can you write a recursive version?

Yes. A recursive formulation typically looks at the head: if `head.next` exists and shares `head`'s value, recursively skip past the entire duplicate run and recurse on what remains; otherwise, keep `head` and set `head.next` to the recursive result on the rest of the list. It achieves the same `O(n)` time but uses `O(n)` call-stack space, which is why the iterative dummy-node version is preferred in an interview setting.

## Q5. Why is the dummy node necessary here specifically, more so than in simple position-based deletion?

In simple position-based deletion, the head is only a special case if you're asked to delete position 1 — a single, predictable check. Here, whether the head needs to be removed is **not known in advance** — it depends on whether the head's value happens to be duplicated, which can only be discovered during the scan. Wrapping the head in a dummy node from the very start means the algorithm never needs to ask "is this affecting the head?" — the uniform `previous.next` update handles it automatically, whether the affected run is at the front, middle, or anywhere else.

---

# 16. Comparison: "Keep One Copy" vs "Keep None" (This Problem)

| Aspect | Remove Duplicates, Keep One | Remove Duplicates, Keep None (this problem) |
|---|---|---|
| Result for `1->1->2` | `1->2` | `2` |
| Does `previous` ever touch the first copy? | Yes — advances onto it | No — never advances onto any node in the run |
| Dummy node required? | Not strictly (head is never removed since at least one copy always survives) | Yes — the head itself may need to disappear entirely |
| Pointer update on a run | `current.next = skip-ahead past duplicates`, `previous` becomes that first copy | `previous.next = current` (node after the whole run); `previous` stays frozen |
| Inner loop purpose | Skip extra copies only | Skip the entire run, including the first copy |
| Typical bug | Off-by-one, skipping one too many/few | Accidentally advancing `previous` into the run |

---

# 17. Pattern Recognition

This problem is an instance of a broader, very common pattern:

> **Consecutive-run detection on a sorted structure, paired with a dummy node to elegantly absorb head-mutation cases.**

Whenever you see a sorted array or linked list and a task like "remove/collapse runs of equal elements," the first question to ask is:

```text
"Can I detect this run just by comparing adjacent elements?"
```

If the structure is sorted, the answer is almost always yes, and the two-pointer (`previous`/`current`, or `slow`/`fast`) technique applies directly.

This pattern connects to several array problems, such as:

- Remove duplicates from a sorted array, keeping only elements that appear once (the array analogue of this exact problem).
- Remove duplicates from a sorted array, keeping at most one/two copies (the array analogue of the "keep one" linked-list variant).
- Collapsing consecutive duplicate characters in a sorted or run-length-encoded string.

Recognizing "sorted + duplicate handling" as a signal for "adjacent comparison, no hashing needed" is a shortcut that saves real time in interviews.

---

# 18. Final Solution

```python
class Solution:

    # Remove every node whose value occurs more than once in a sorted list.
    def removeDuplicates(self, head):

        # Create a dummy node so the head can be safely replaced if needed.
        dummy = Node(0)

        # Connect the dummy node to the front of the original list.
        dummy.next = head

        # previous tracks the last node confirmed to be unique.
        previous = dummy

        # current is the node currently being examined.
        current = head

        # Scan until every node has been examined.
        while current is not None:

            # Check whether current is the start of a duplicate run.
            if current.next is not None and current.next.val == current.val:

                # Remember which value is being duplicated.
                duplicate_value = current.val

                # Advance current through the entire run of this value.
                while current is not None and current.val == duplicate_value:

                    # Step current one node further into (or past) the run.
                    current = current.next

                # Cut the whole run out with a single pointer update.
                previous.next = current

                # previous intentionally does not move here.

            else:

                # current's value appears exactly once so far — it's unique.
                previous = previous.next

                # Move on to examine the next node.
                current = current.next

        # dummy.next is the new head after all duplicates are removed.
        return dummy.next
```

---

# 19. Interview Takeaways

```text
1. Sorted list => duplicates are always consecutive.

2. Adjacent-node comparison replaces the need for a hash map.

3. A dummy node is essential here because the head's fate
   is unknown until the scan discovers it.

4. previous only advances onto nodes proven to be unique.

5. During a duplicate run, previous freezes; only current
   and previous.next change.

6. Total node visits across the nested loops is bounded by n,
   so time complexity is O(n), not O(n^2).

7. Space complexity is O(1) for the sorted-list approach,
   versus O(n) for the general (unsorted) hash-map approach.

8. This is fundamentally different from "keep one occurrence" —
   here, a duplicated value contributes ZERO nodes to the result.
```

The key sentence to remember is:

> **When a sorted structure requires collapsing or removing runs of equal values, compare adjacent elements and use a dummy node so that even the head can be safely rewritten.**

---

## Related Problems to Practice

After this problem, practice these linked-list and array patterns:

1. Remove duplicates from a sorted linked list (keep one occurrence).
2. Remove duplicates from a sorted array (keep one occurrence).
3. Remove duplicates from a sorted array II (keep at most two occurrences).
4. Delete all occurrences of a given key in a linked list.
5. Delete a node without access to the head pointer.
6. Merge two sorted linked lists.
7. Remove N-th node from end of a linked list.
8. Segregate evens and odds in a linked list.
9. Partition list around a value `x`.
10. Reverse nodes in groups of `k`.

These problems reinforce the same core skills: dummy-node usage, careful pointer choreography, and recognizing when sortedness lets you avoid extra memory.
