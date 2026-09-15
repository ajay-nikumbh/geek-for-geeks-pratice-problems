# Delete N After Every M in Linked List

| Field | Value |
|---|---|
| Topic | Linked List |
| Difficulty | Easy |
| Submissions | 64,805 |
| Accuracy | 32.83% |
| Companies | Amazon, Microsoft |
| Related Tags | Linked List |
| Problem Link | [https://www.geeksforgeeks.org/problems/delete-n-nodes-after-m-nodes-of-a-linked-list/1](https://www.geeksforgeeks.org/problems/delete-n-nodes-after-m-nodes-of-a-linked-list/1) |

## Problem Statement

Given the head of a **singly linked list** and two integers `M` and `N`, traverse the linked list in a repeating pattern:

- **Keep** the next `M` nodes.
- **Delete** the next `N` nodes.
- Repeat this pattern until the end of the list is reached.

Return the head of the modified linked list.

### Example 1

```text
Input:
List: 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 -> 9 -> 10
M = 2, N = 2

Process:
Keep   1, 2
Delete 3, 4
Keep   5, 6
Delete 7, 8
Keep   9, 10

Output:
1 -> 2 -> 5 -> 6 -> 9 -> 10
```

### Example 2

```text
Input:
List: 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8
M = 1, N = 2

Process:
Keep   1
Delete 2, 3
Keep   4
Delete 5, 6
Keep   7
Delete 8

Output:
1 -> 4 -> 7
```

---

# 1. Interview Intuition

This problem is a **generalization** of two very common linked-list patterns:

1. **Delete alternate nodes** — keep one, delete one, repeat.
2. **Remove every k-th node** — keep `k - 1`, delete `1`, repeat.

Here, instead of fixed constants, we get two parameters, `M` and `N`, and the list must be processed in a **repeating cycle**:

```text
keep M nodes -> delete N nodes -> keep M nodes -> delete N nodes -> ...
```

The key realization is that we cannot solve this with a single simple loop the way we delete one node. We need **two nested phases** inside one outer loop:

```text
while list is not fully processed:

    Phase A: walk forward M times, keeping nodes
             (remember the last kept node)

    Phase B: walk forward N times, deleting nodes
             (relink last kept node's `next` past them)
```

The outer loop keeps repeating this two-phase cycle until we run out of nodes. This "keep phase, then delete phase, repeat" shape is the entire trick of the problem — once you see it as two nested loops instead of one, the implementation becomes mechanical.

---

# 2. Core Linked List Idea

Picture the list broken into repeating blocks of size `M + N`:

```text
[ keep M nodes ][ delete N nodes ][ keep M nodes ][ delete N nodes ] ...
```

For `M = 2, N = 2`:

```text
1 -> 2 | 3 -> 4 | 5 -> 6 | 7 -> 8 | 9 -> 10
 keep     del      keep     del     keep
```

Each "keep" block ends with a node whose `next` pointer we will need to rewire — call it `lastKept`. Each "delete" block is a run of nodes that must be skipped entirely by pointing `lastKept.next` at whatever comes right after the deleted run:

```text
Before:
1 -> 2 -> 3 -> 4 -> 5 -> 6 -> ...
     ^         ^
  lastKept   next kept block starts here

After relinking:
1 -> 2 -------> 5 -> 6 -> ...
```

So the algorithm is really just: walk `M` steps forward (remembering where you stopped), then walk `N` steps forward while cutting those nodes out of the chain, and repeat.

---

# 3. Most Important Edge Case

There are four situations that break a naive implementation if not handled carefully.

## Case 1 — `N = 0` (nothing to delete)

```text
List: 1 -> 2 -> 3 -> 4 -> 5
M = 2, N = 0
```

Nothing should ever be removed — the list is returned unchanged. If the delete-phase loop is not guarded, it might still run zero times naturally (since it loops `N` times), but it's worth explicitly reasoning about this case so you don't accidentally write an infinite loop.

## Case 2 — `M = 0` (delete everything, or keep nothing per cycle)

```text
List: 1 -> 2 -> 3 -> 4 -> 5
M = 0, N = 2
```

If `M = 0`, we never advance during the "keep" phase, and we never establish a `lastKept` node before the head. Most implementations assume `M >= 1`, since GfG's constraints guarantee `M >= 1`. If `M = 0` were allowed, we'd need a dummy node so the delete phase can delete starting from the head itself, potentially leaving an **empty list**.

## Case 3 — List length is not a clean multiple of `(M + N)`

```text
List: 1 -> 2 -> 3 -> 4 -> 5
M = 2, N = 2
```

```text
Keep   1, 2
Delete 3, 4
Keep   5           <- only one node left, keep whatever remains
(no more nodes to delete)

Output: 1 -> 2 -> 5
```

The keep phase and delete phase must both stop early — using `current is not None` checks — rather than assuming a full `M` or `N` nodes are always available.

## Case 4 — List shorter than `M`

```text
List: 1 -> 2 -> NULL
M = 5, N = 2
```

We simply keep walking forward until `current` becomes `None`, then stop. Nothing is deleted because the delete phase never gets to run — the whole list is kept as-is.

```text
Output: 1 -> 2 -> NULL
```

---

# 4. Approach 1 — Brute Force Thinking

A brute-force approach converts the list into an array-like structure first:

1. Traverse the linked list and store all node values into an array.
2. Walk through the array in chunks of size `M + N`, keeping the first `M` values of each chunk and discarding the next `N`.
3. Build a brand-new linked list from the surviving values.

```text
Linked List:
1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 -> 9 -> 10

Array:
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

M = 2, N = 2 -> chunks of size 4:
[1, 2, 3, 4] -> keep [1, 2]
[5, 6, 7, 8] -> keep [5, 6]
[9, 10]      -> keep [9, 10]

Surviving values:
[1, 2, 5, 6, 9, 10]

Rebuild:
1 -> 2 -> 5 -> 6 -> 9 -> 10
```

### Complexity

```text
Time  = O(n)
Space = O(n)
```

This works, but it throws away the fact that a linked list can delete a run of nodes in `O(1)` per run using pure pointer relinking — no array, no rebuilding. Interviewers expect the **in-place pointer version**.

---

# 5. Optimal Approach — Two Nested Loops with Pointer Relinking

The optimal approach processes the list in a single forward pass using **two nested loops** inside one outer loop:

```text
current = head

while current is not None:

    # ---- Phase A: keep M nodes ----
    lastKept = current
    for i in range(1, M):
        if current is None:
            break
        current = current.next

    if current is None:
        break        # list ended while keeping — nothing more to delete

    # `current` now sits on the last kept node of this block
    toDelete = current.next

    # ---- Phase B: delete N nodes ----
    for i in range(N):
        if toDelete is None:
            break
        toDelete = toDelete.next

    # relink the last kept node to skip the deleted run
    lastKept.next = toDelete

    # move on to the next keep phase
    current = toDelete
```

### Why this works

- `lastKept` always tracks the last node we decided to **keep**, i.e. the node whose `next` pointer needs to be rewired.
- The inner `for` loop for deletion doesn't need to physically "remove" each node one by one — Python's garbage collector reclaims the deleted chain automatically once nothing points to it. We only need to find **where the deleted run ends** (`toDelete`), then do a single pointer update: `lastKept.next = toDelete`.
- Every `if current is None` / `if toDelete is None` check protects against the list ending mid-phase (Case 3 and Case 4 from the edge cases above).

---

# 6. Pointer Movement

Trace `M = 2, N = 2` on:

```text
1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 -> 9 -> 10 -> NULL
```

### Keep phase (advance M - 1 = 1 more step from current start)

```text
current
   |
   v
   1 -> 2 -> 3 -> 4 -> ...

after one advance (M=2 means 1 extra move):

        current
           |
           v
   1 -> 2 -> 3 -> 4 -> ...

lastKept = current = node "2"
```

### Delete phase (advance N = 2 steps from lastKept.next)

```text
toDelete
   |
   v
   3 -> 4 -> 5 -> ...

after two advances:

             toDelete
                |
                v
   3 -> 4 ->   5 -> ...
```

### Relink

```text
lastKept.next = toDelete

   1 -> 2 -------> 5 -> 6 -> ...
        (3, 4 are now unreachable)
```

### Continue outer loop

```text
current = toDelete  (node "5")
```

The exact same two phases repeat from node `5`, producing `5, 6` kept, `7, 8` deleted, then `9, 10` kept with nothing left to delete.

Final result:

```text
1 -> 2 -> 5 -> 6 -> 9 -> 10 -> NULL
```

---

# 7. Algorithm

### Step 1

If the list is empty or `N == 0`, return the head unchanged (nothing to delete).

### Step 2

Set `current = head`.

### Step 3 — Outer loop

Repeat while `current is not None`:

### Step 4 — Keep phase

Starting at `current`, advance `M - 1` more times (guarding against `None`), so that `current` ends on the **last node to keep** in this block. Call this node `lastKept`.

### Step 5

If `current` became `None` during the keep phase, the list ended exactly while keeping — stop, nothing more to delete.

### Step 6 — Delete phase

Starting from `lastKept.next`, advance `N` times (guarding against `None`) to find the first node that survives after the deleted run, call it `toDelete`.

### Step 7 — Relink

Set `lastKept.next = toDelete`, cutting the `N` deleted nodes out of the chain.

### Step 8

Set `current = toDelete` and repeat from Step 3.

### Step 9

Return `head` (the head never changes because `M >= 1` guarantees the first node is always kept).

---

# 8. Optimal Python Solution

```python
class Solution:

    # This function deletes N nodes after every M nodes, repeating till the list ends.
    def skipMdeleteN(self, head, M, N):

        # If the list is empty, there is nothing to process.
        if head is None:

            # Return the empty list as-is.
            return head

        # If N is zero, no node is ever deleted, so the list stays unchanged.
        if N == 0:

            # Return the original head untouched.
            return head

        # Start traversal from the head of the list.
        current = head

        # Outer loop keeps repeating the keep-M / delete-N cycle.
        while current is not None:

            # This will track the last node we decide to keep in this block.
            lastKept = current

            # We already have 1 kept node (current itself), so advance M - 1 more times.
            count = 1

            # Keep phase: move forward while we still owe nodes to keep.
            while count < M and lastKept.next is not None:

                # Move lastKept forward to the next node to keep.
                lastKept = lastKept.next

                # One more node has been kept.
                count += 1

            # If lastKept.next is None, the list ended right after the keep phase.
            if lastKept.next is None:

                # Nothing left to delete, so we can stop the outer loop.
                break

            # toDelete starts at the first node that must be removed.
            toDelete = lastKept.next

            # Delete phase: advance N times over the nodes to be deleted.
            count = 0

            # Keep moving forward until N nodes are skipped or the list ends.
            while count < N and toDelete is not None:

                # Move toDelete forward past this node (it gets dropped from the chain).
                toDelete = toDelete.next

                # One more node has been accounted for in the deleted run.
                count += 1

            # Relink lastKept directly to whatever survives after the deleted run.
            lastKept.next = toDelete

            # Move current to the start of the next keep phase.
            current = toDelete

        # Return the head, which never changes since M >= 1 keeps the first node.
        return head
```

---

# 9. Complete Dry Run

Consider:

```text
head = 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 -> 9 -> 10 -> NULL
M = 2, N = 2
```

## Cycle 1

```text
current = 1

Keep phase:
lastKept = 1, count = 1
count < M (1 < 2) and lastKept.next (2) exists -> advance
lastKept = 2, count = 2
count < M is now false (2 < 2 is False) -> stop keep phase

lastKept = 2
lastKept.next = 3 (not None, so we continue)

Delete phase:
toDelete = 3
count = 0 -> advance -> toDelete = 4, count = 1
count = 1 -> advance -> toDelete = 5, count = 2
count < N is now false (2 < 2 is False) -> stop delete phase

Relink: lastKept.next = toDelete
2.next = 5

List so far: 1 -> 2 -> 5 -> 6 -> 7 -> 8 -> 9 -> 10

current = toDelete = 5
```

## Cycle 2

```text
current = 5

Keep phase:
lastKept = 5, count = 1
advance -> lastKept = 6, count = 2 -> stop

lastKept.next = 7 (not None, continue)

Delete phase:
toDelete = 7 -> advance -> toDelete = 8, count = 1
advance -> toDelete = 9, count = 2 -> stop

Relink: 6.next = 9

List so far: 1 -> 2 -> 5 -> 6 -> 9 -> 10

current = toDelete = 9
```

## Cycle 3

```text
current = 9

Keep phase:
lastKept = 9, count = 1
advance -> lastKept = 10, count = 2 -> stop

lastKept.next = None
-> keep phase ended with lastKept.next being None
-> break out of the outer loop entirely
```

## Final Result

```text
1 -> 2 -> 5 -> 6 -> 9 -> 10 -> NULL
```

This matches the expected output exactly.

---

# 10. Complexity Analysis

Let:

```text
n = number of nodes in the list
```

The outer `while current is not None` loop, together with its two inner loops, together visit **every node in the list exactly once** — a node is either advanced over in the keep phase or advanced over in the delete phase, never both, never revisited.

```text
Time Complexity  = O(n)
Space Complexity = O(1)
```

Only a constant number of pointer variables (`current`, `lastKept`, `toDelete`, counters) are used regardless of list size.

### Final Complexity

| Metric | Complexity |
|---|---|
| Time | `O(n)` |
| Extra Space | `O(1)` |

---

# 11. Why This Is Optimal

At minimum, any correct solution must **inspect every node once** — you cannot know whether a node should be kept or deleted without visiting it, and you cannot know where a deleted run ends without walking through it.

The nested-loop structure might look like it costs more than `O(n)`, but it doesn't: the inner "keep" loop and the inner "delete" loop **never overlap** — together across the whole traversal, their combined iteration count equals exactly `n`, the total number of nodes. This is sometimes called an **amortized argument**: even though there are two loops inside one, no node is ever visited by more than one of them, so the total work across the entire run is still linear.

```text
Total iterations of keep-phase loop   +
Total iterations of delete-phase loop  =  n  (each node counted exactly once)
```

Since we must touch every node once, and we do exactly that, `O(n)` time with `O(1)` space is optimal.

---

# 12. Common Mistakes

## Mistake 1 — Forgetting Null Checks Inside the Delete-N Loop

```python
# WRONG — crashes if the list ends mid-deletion phase
for _ in range(N):
    toDelete = toDelete.next
```

If the list has fewer than `N` nodes remaining, `toDelete` becomes `None`, and calling `.next` on `None` crashes. Always guard:

```python
while count < N and toDelete is not None:
    toDelete = toDelete.next
    count += 1
```

---

## Mistake 2 — Off-by-One on the M Count

`current` (or `lastKept`) already represents **one kept node** before any advancing happens. Advancing `M` times would keep `M + 1` nodes. The loop must run only `M - 1` additional times:

```python
count = 1
while count < M and lastKept.next is not None:
    lastKept = lastKept.next
    count += 1
```

---

## Mistake 3 — Losing the "Last Kept Node" Reference

If you advance `current` directly through the keep phase without saving a separate `lastKept` pointer, you lose the node whose `next` pointer needs to be rewired once the delete phase finishes. Always keep `lastKept` as a distinct variable, untouched by the delete phase.

---

## Mistake 4 — Infinite Loop When `M = 0` Is Mishandled

If `M = 0` is allowed and the keep-phase loop is written as `while count < M`, the loop body never executes, `lastKept` stays equal to `current`, and if the delete logic isn't adjusted to actually consume nodes, the outer loop can spin forever without `current` ever advancing. Either explicitly assume `M >= 1` (as GfG's constraints guarantee) or use a dummy-node design that handles `M = 0` by deleting starting from the head.

---

## Mistake 5 — Not Handling `N = 0`

If `N = 0` isn't special-cased and the delete loop is written incorrectly (e.g., a `do-while` style that always removes at least one node), the list gets corrupted even though nothing should have been deleted. A `while count < N` loop naturally does zero iterations when `N = 0`, but it's worth verifying this explicitly.

---

# 13. Visual Cheat Sheet

## One Full Cycle

```text
Before:

lastKeptStart
     |
     v
... -> [keep 1] -> [keep 2] -> ... -> [keep M] -> [del 1] -> ... -> [del N] -> [next kept] -> ...
                                          ^                                        ^
                                       lastKept                                 toDelete (after N advances)

Operation:

lastKept.next = toDelete

After:

... -> [keep M] ------------------------------------------------> [next kept] -> ...
```

## Whole List Pattern

```text
[keep M][delete N][keep M][delete N][keep M][delete N] ... until list ends
```

## Boundary Cases

```text
List shorter than M          -> keep everything, delete nothing
List ends inside delete run  -> lastKept.next becomes None (tail is truncated)
N = 0                        -> list unchanged
```

---

# 14. Interview Explanation in 30 Seconds

A strong interview explanation would be:

> This is a generalized "keep some, delete some, repeat" pattern. I use one outer loop that repeats until the list ends. Inside each cycle, I have two inner phases: first I advance `M - 1` steps to find the last node I want to keep, then I advance `N` steps from there to find the first surviving node after the deleted run. A single pointer update, `lastKept.next = toDelete`, removes the whole deleted block at once. I guard every inner loop against `None` so the traversal never crashes when the list doesn't divide evenly into `M + N` blocks. Even though there are nested loops, every node is visited exactly once overall, so the total time is `O(n)` with `O(1)` extra space.

---

# 15. Interviewer Follow-Up Questions

## Q1. What if M or N can be 0?

If `N = 0`, nothing is ever deleted — return the list unchanged (the inner delete loop naturally runs zero times). If `M = 0` were allowed, the first "kept" node would not exist, so you'd need a dummy node pointing before the head to act as `lastKept`, allowing the very first block of nodes to be deleted too. Most versions of this problem (including this GfG problem) guarantee `M >= 1`.

---

## Q2. Can this be done recursively?

Yes. A recursive version processes one `(keep M, delete N)` block per call:

```python
def skipMdeleteN(self, head, M, N):
    if head is None:
        return None

    current = head
    for _ in range(M - 1):
        if current is None or current.next is None:
            return head
        current = current.next

    toDelete = current.next
    for _ in range(N):
        if toDelete is None:
            break
        toDelete = toDelete.next

    current.next = self.skipMdeleteN(toDelete, M, N) if toDelete else None
    return head
```

This is elegant but uses `O(n / (M + N))` recursion depth — extra stack space compared to the `O(1)`-space iterative version.

---

## Q3. How is this different from "remove every k-th node"?

"Remove every k-th node" is the special case where you keep `k - 1` nodes and delete exactly `1` node, repeating. In this problem's terms, that's `M = k - 1, N = 1`. This problem generalizes it by allowing an arbitrary run of deletions (`N`) instead of always deleting a single node.

---

## Q4. What's the amortized argument for the nested loop being O(n), not O(n × something)?

Even though there's a loop inside a loop, the **inner loops never re-examine a node that a previous iteration already touched**. Every node belongs to exactly one keep-block or one delete-block, and each node is advanced over exactly once across the entire run. So summing the work of all inner-loop iterations across every outer-loop cycle still totals `n`, not `n × (M + N)`. This is analogous to how a two-pointer sliding window is `O(n)` even though it "looks like" nested loops.

---

## Q5. Does the head ever change?

No, as long as `M >= 1`. The first `M` nodes (or fewer, if the list is shorter than `M`) are always kept, so the original head is always still the head after processing.

---

## Q6. What happens if M + N is larger than the list length?

The keep phase simply keeps walking until `current` hits `None`, at which point the outer loop breaks — nothing is ever deleted because the delete phase never gets a chance to run. The whole list is returned unchanged.

---

# 16. Comparison Table — Family of Periodic Deletion Problems

| Problem | Keep Count | Delete Count | Relationship |
|---|---|---|---|
| Delete Alternate Nodes | 1 | 1 | Special case: `M = 1, N = 1` |
| Remove Every k-th Node | `k - 1` | 1 | Special case: `M = k - 1, N = 1` |
| **Delete N After Every M (this problem)** | `M` | `N` | General form |

All three problems share the exact same nested-loop skeleton — only the values plugged into `M` and `N` differ. Recognizing this lets you solve all three with **one reusable mental template**.

---

# 17. Pattern Recognition

Whenever a linked-list problem describes a **repeating cycle of keep/skip and delete/remove** behavior — "every other node", "every k-th node", "keep some then remove some" — recognize it as an instance of this general periodic-deletion pattern:

```text
outer loop:
    keep phase   -> advance M times, remember lastKept
    delete phase -> advance N times, find toDelete
    relink       -> lastKept.next = toDelete
    continue from toDelete
```

Once you identify a problem as belonging to this family, the implementation is a direct plug-in of `M` and `N` into this same template.

---

# 18. Final Solution

```python
class Solution:

    # This function deletes N nodes after every M nodes, repeating till the list ends.
    def skipMdeleteN(self, head, M, N):

        # If the list is empty, there is nothing to process.
        if head is None:

            # Return the empty list as-is.
            return head

        # If N is zero, no node is ever deleted, so the list stays unchanged.
        if N == 0:

            # Return the original head untouched.
            return head

        # Start traversal from the head of the list.
        current = head

        # Outer loop keeps repeating the keep-M / delete-N cycle.
        while current is not None:

            # This will track the last node we decide to keep in this block.
            lastKept = current

            # We already have 1 kept node (current itself), so advance M - 1 more times.
            count = 1

            # Keep phase: move forward while we still owe nodes to keep.
            while count < M and lastKept.next is not None:

                # Move lastKept forward to the next node to keep.
                lastKept = lastKept.next

                # One more node has been kept.
                count += 1

            # If lastKept.next is None, the list ended right after the keep phase.
            if lastKept.next is None:

                # Nothing left to delete, so we can stop the outer loop.
                break

            # toDelete starts at the first node that must be removed.
            toDelete = lastKept.next

            # Delete phase: advance N times over the nodes to be deleted.
            count = 0

            # Keep moving forward until N nodes are skipped or the list ends.
            while count < N and toDelete is not None:

                # Move toDelete forward past this node (it gets dropped from the chain).
                toDelete = toDelete.next

                # One more node has been accounted for in the deleted run.
                count += 1

            # Relink lastKept directly to whatever survives after the deleted run.
            lastKept.next = toDelete

            # Move current to the start of the next keep phase.
            current = toDelete

        # Return the head, which never changes since M >= 1 keeps the first node.
        return head
```

---

# 19. Interview Takeaways

Remember these points:

```text
1. This problem generalizes "delete alternate" (M=1, N=1)
   and "remove every k-th node" (M=k-1, N=1).

2. Use one outer loop with two inner phases:
   keep M nodes, then delete N nodes.

3. Track a `lastKept` pointer — it owns the `next`
   pointer that must be rewired after deletion.

4. Guard every inner loop with a None check to handle
   lists whose length isn't a clean multiple of (M + N).

5. A single pointer update removes an entire deleted run:
   lastKept.next = toDelete

6. Despite nested loops, every node is visited exactly
   once overall — the algorithm is O(n), not O(n * k).

7. Time  = O(n)
   Space = O(1)
```

The key sentence to remember is:

> **A repeating keep/delete cycle on a linked list is just one outer loop with two inner phases — the node at the boundary between "keep" and "delete" is the one whose `next` pointer must change.**

---

## Related Problems to Practice

After this problem, practice these linked-list patterns:

1. Delete alternate nodes of a linked list.
2. Remove every k-th node from a linked list.
3. Delete N nodes after M nodes (variations with different M, N).
4. Remove N-th node from end.
5. Reverse nodes in groups of `k`.
6. Rotate a linked list.
7. Partition a linked list around a value.
8. Merge two sorted linked lists.
9. Remove duplicates from an unsorted/sorted linked list.
10. Detect and remove a loop in a linked list.

These problems build directly on the same "traverse in phases, relink pointers" fundamentals used here.
