# Remove Every k'th in Linked List

> **Topic:** Linked List  
> **Difficulty:** Easy  
> **Submissions:** 104,504  
> **Accuracy:** 29.88%  
> **Companies:** —  
> **Related Tags:** Linked List  
> **Problem Link:** https://www.geeksforgeeks.org/problems/remove-every-kth-node/1  

---

## Problem Statement

Given the head of a **singly linked list** and an integer `k`, delete every **k-th node** from the list.

The position is **1-indexed**, so the nodes to be deleted are the nodes at positions:

```text
k, 2k, 3k, 4k, ...
```

Return the head of the modified linked list.

### Example 1

```text
Input:
List = 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8
k = 3

Positions:  1  2  3  4  5  6  7  8
Delete positions 3 and 6 (values 3 and 6).

Output:
1 -> 2 -> 4 -> 5 -> 7 -> 8
```

### Example 2

```text
Input:
List = 1 -> 2 -> 3 -> 4 -> 5
k = 2

Positions:  1  2  3  4  5
Delete positions 2 and 4 (values 2 and 4).

Output:
1 -> 3 -> 5
```

---

# 1. Interview Intuition

This problem is really the **"Delete node at position x"** idea applied **repeatedly and periodically**, in a single pass.

> Instead of deleting one fixed position, we delete a node **every time our position counter hits a multiple of `k`**.

Recall the basic deletion trick:

```text
In a singly linked list, to delete a node, you must reach the node
just BEFORE it, because only that node's `next` pointer can be
changed to skip over the target.
```

So the natural idea is:

- Walk through the list while counting positions: `1, 2, 3, 4, ...`
- Keep a `previous` pointer trailing one step behind `current`.
- Whenever the counter reaches `k`, the current node is the one to delete — use `previous.next = current.next` to bypass it.
- Reset the counter back to `0` (or `1`) and continue.

Because deletion is periodic, we are essentially running the "delete node at position x" logic over and over, but folded into **one traversal** instead of restarting from the head each time.

```text
1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8
          ^                 ^
       delete             delete
     (position 3)       (position 6)
```

---

# 2. Core Linked List Idea

Think of the traversal as a counter ticking `1, 2, 3, 1, 2, 3, ...` alongside the nodes.

```text
Node:      1     2     3     4     5     6     7     8
Counter:   1     2     3     1     2     3     1     2
                       (del)             (del)
```

Every time the counter reaches `k`, we are standing at a node that must be removed.

Visual walk with `k = 3`:

```text
count=1        count=2        count=3 -> DELETE
  |              |              |
  v              v              v
  1  ---------> 2  ---------> 3  ---------> 4
```

After deleting `3`, the counter resets and restarts from `1` at node `4`:

```text
count=1        count=2        count=3 -> DELETE
  |              |              |
  v              v              v
  4  ---------> 5  ---------> 6  ---------> 7
```

The pattern repeats: **count up to `k`, delete, reset, repeat** — until the list ends.

---

# 3. Most Important Edge Case

## Case A — `k = 1` (delete every node)

```text
Input:  1 -> 2 -> 3 -> 4
k = 1

Every single node is at a position that is a multiple of 1.
```

Result:

```text
Output: NULL (empty list)
```

This is the trickiest edge case because the **head itself** keeps getting deleted repeatedly.

## Case B — `k` greater than the list length

```text
Input:  1 -> 2 -> 3
k = 10

No position reaches a multiple of 10.
```

Result:

```text
Output: 1 -> 2 -> 3   (unchanged)
```

## Case C — List length is an exact multiple of `k`

```text
Input:  1 -> 2 -> 3 -> 4 -> 5 -> 6
k = 3

Delete positions 3 and 6.
```

Result:

```text
Output: 1 -> 2 -> 4 -> 5
```

Here the **last node** also happens to be deleted — the loop must correctly stop without dereferencing a `None` node afterward.

## Case D — List length is NOT an exact multiple of `k`

```text
Input:  1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7
k = 3

Delete positions 3 and 6.
```

Result:

```text
Output: 1 -> 2 -> 4 -> 5 -> 7
```

The leftover nodes after the last deleted position (`7` here) simply remain untouched.

---

# 4. Approach 1 — Brute Force Thinking

A straightforward first idea:

1. Traverse the linked list and store every value in an array.
2. Remove every element whose 1-indexed position is a multiple of `k`.
3. Rebuild a brand-new linked list from the remaining values.

```text
Linked List:
1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8

Convert to array:
[1, 2, 3, 4, 5, 6, 7, 8]

Remove indices that are multiples of k (k = 3):
remove index 3 (value 3), index 6 (value 6)

Remaining:
[1, 2, 4, 5, 7, 8]

Rebuild linked list:
1 -> 2 -> 4 -> 5 -> 7 -> 8
```

### Complexity

```text
Time  = O(n)
Space = O(n)
```

> This is not "brute force" in the sense of being slower asymptotically — the time is still linear. It is wasteful because it allocates an entire new array **and** an entire new set of linked-list nodes, when the deletion can be done **in place** with existing nodes and a handful of pointers.

In an interview, this approach signals that you understand the problem, but the interviewer will expect you to eliminate the extra `O(n)` space next.

---

# 5. Optimal Approach — Single Pass Counter + Pointer Deletion

We only need three things while walking the list:

```text
current   -> the node we are currently inspecting
previous  -> the node right before `current`
counter   -> how many nodes we have advanced past since the last deletion (or start)
```

### The rule

- Move `current` forward, incrementing `counter` each time.
- When `counter` reaches `k`, the node at `current` must be deleted:
  - Update `previous.next = current.next` (this bypasses `current`, exactly like the classic "delete node at position x" trick).
  - Move `current` to `current.next` (the node that took its place).
  - Reset `counter` back to `0`.
  - Do **not** move `previous` — it stays where it is, since the node right after it is now the new "next" node to examine.
- When `counter` has **not** reached `k`, no deletion happens:
  - Move `previous` forward to `current`.
  - Move `current` forward to `current.next`.

> The key insight: `previous` only advances when we **don't** delete. When we delete, `previous` must stay put, because the node it points to has changed — its `next` pointer now skips the freshly removed node.

### Special handling for `k == 1`

If `k == 1`, every node (starting with the head) must be deleted, so the answer is simply an empty list. This is handled as a dedicated first check so we never have to juggle "delete the head while inside the main loop" logic.

---

# 6. Pointer Movement

Take:

```text
1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 -> NULL
k = 3
```

### Step-by-step counter and pointers

```text
Start:
previous = None
current  = 1
counter  = 0

-----------------------------------------
current = 1, counter becomes 1 (no delete)
previous = 1
current  = 2

-----------------------------------------
current = 2, counter becomes 2 (no delete)
previous = 2
current  = 3

-----------------------------------------
current = 3, counter becomes 3 -> DELETE 3

previous.next = current.next
   2.next = 4

previous stays at 2
current moves to 4
counter resets to 0
```

Visual:

```text
Before deleting 3:

1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8
     ^    ^
  previous current


After deleting 3:

1 -> 2 --------> 4 -> 5 -> 6 -> 7 -> 8
     ^           ^
  previous     current
```

Continuing:

```text
current = 4, counter becomes 1 (no delete)
previous = 4
current  = 5

-----------------------------------------
current = 5, counter becomes 2 (no delete)
previous = 5
current  = 6

-----------------------------------------
current = 6, counter becomes 3 -> DELETE 6

previous.next = current.next
   5.next = 7

previous stays at 5
current moves to 7
counter resets to 0
```

Visual:

```text
Before deleting 6:

4 -> 5 -> 6 -> 7 -> 8
     ^    ^
  previous current


After deleting 6:

4 -> 5 --------> 7 -> 8
     ^           ^
  previous     current
```

Final remaining walk (`7`, then `8`) never reaches `counter == k` again, so the list ends unchanged from here:

```text
Final list:
1 -> 2 -> 4 -> 5 -> 7 -> 8 -> NULL
```

---

# 7. Algorithm

### Step 1

If the list is empty (`head is None`), return `None`.

### Step 2

If `k == 1`, every node must be deleted, so return `None` directly.

### Step 3

Initialize:

```text
current  = head
previous = None
counter  = 0
```

### Step 4

Traverse while `current` is not `None`:

- Increment `counter`.
- If `counter == k`:
  - Set `previous.next = current.next`.
  - Move `current = current.next`.
  - Reset `counter = 0`.
- Else:
  - Move `previous = current`.
  - Move `current = current.next`.

### Step 5

Return `head` (the head itself never changes for `k > 1`, since position `1` is never deleted unless `k == 1`).

---

# 8. Optimal Python Solution

```python
class Solution:

    # This function deletes every k-th node from the linked list.
    def deleteKthNode(self, head, k):

        # If the list is empty, there is nothing to delete.
        if head is None:

            # Return the empty list as-is.
            return None

        # Special case: deleting every 1st node means deleting everything.
        if k == 1:

            # The entire list becomes empty.
            return None

        # Pointer that walks through the list, node by node.
        current = head

        # Pointer that trails just behind `current`.
        previous = None

        # Counts how many nodes we have advanced through since the last deletion.
        counter = 0

        # Continue until we run off the end of the list.
        while current is not None:

            # We have visited one more node in this "round" of counting.
            counter += 1

            # Check whether this node lands on a multiple of k.
            if counter == k:

                # Bypass the current node using the previous node's pointer.
                previous.next = current.next

                # Move current forward to the node that replaced the deleted one.
                current = current.next

                # Reset the counter to start a fresh round of counting.
                counter = 0

            else:

                # No deletion this time, so previous catches up to current.
                previous = current

                # Advance current to the next node.
                current = current.next

        # The head is unaffected whenever k > 1, so return it unchanged.
        return head
```

---

# 9. Complete Dry Run

Consider:

```text
head = 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 -> NULL
k = 3
```

## Initial State

```text
current  = 1
previous = None
counter  = 0
```

## Iteration Table

| Step | current (before) | counter | Action | previous (after) | current (after) |
|---|---|---|---|---|---|
| 1 | 1 | 1 | no delete | 1 | 2 |
| 2 | 2 | 2 | no delete | 2 | 3 |
| 3 | 3 | 3 | **DELETE 3**, `2.next = 4`, reset counter | 2 | 4 |
| 4 | 4 | 1 | no delete | 4 | 5 |
| 5 | 5 | 2 | no delete | 5 | 6 |
| 6 | 6 | 3 | **DELETE 6**, `5.next = 7`, reset counter | 5 | 7 |
| 7 | 7 | 1 | no delete | 7 | 8 |
| 8 | 8 | 2 | no delete | 8 | None |
| 9 | None | — | loop ends | — | — |

## Final List

```text
1 -> 2 -> 4 -> 5 -> 7 -> 8 -> NULL
```

This matches the expected output exactly.

---

# 10. Complexity Analysis

Let:

```text
n = number of nodes in the list
```

We visit every node **exactly once**, performing constant-time work (a comparison, maybe one pointer update) at each node.

```text
Time Complexity = O(n)
```

We use only a fixed number of extra variables (`current`, `previous`, `counter`), regardless of list size.

```text
Space Complexity = O(1)
```

### Final Complexity

| Metric | Complexity |
|---|---|
| Time | `O(n)` |
| Extra Space | `O(1)` |

---

# 11. Why This Is Optimal

Every node in the list must be **examined at least once** to know whether it lands on a multiple of `k` — there is no way to know a node's position without counting up to it in a singly linked list.

> Since a full traversal is unavoidable, and each node requires only constant-time work, `O(n)` time and `O(1)` space is the best possible complexity for this problem.

There is no algorithmic shortcut analogous to binary search here, because linked lists don't support random access — we cannot "jump" to position `k`, `2k`, `3k` without walking through the nodes in between.

---

# 12. Common Mistakes

## Mistake 1 — Forgetting to Reset the Counter After Deletion

```python
if counter == k:
    previous.next = current.next
    current = current.next
    # BUG: forgot counter = 0
```

Without resetting, the counter keeps climbing past `k` and the next deletion will happen at the wrong position (or never).

---

## Mistake 2 — Off-by-One on Which Node Counts as "kth"

Some implementations mistakenly delete the node **after** reaching `counter == k` instead of the node **at** `counter == k`. Always double check with a small dry run (`k = 1` deleting the very first node visited is a good sanity test).

---

## Mistake 3 — Advancing `previous` Even When Deleting

```python
if counter == k:
    previous.next = current.next
    previous = current      # BUG: previous should NOT move here
    current = current.next
```

If `previous` is advanced to the just-deleted node, the next `previous.next` assignment will corrupt the list, because `previous` no longer points to a node that is actually still linked in.

---

## Mistake 4 — Losing the Head Reference

```python
def deleteKthNode(self, head, k):
    current = head
    ...
    # BUG: never returns head, or reassigns head incorrectly mid-loop
```

Since deletions for `k > 1` never touch position `1`, `head` should be returned unchanged at the end. Only the `k == 1` special case affects the head, and that is handled upfront by returning `None`.

---

## Mistake 5 — Not Handling `k == 1` Separately

Without a dedicated check, the main loop would try to set `previous.next` while `previous` is still `None` (since the very first node, at counter `1`, would need deleting) — causing a `NoneType has no attribute 'next'` error.

---

# 13. Visual Cheat Sheet

## Normal Round (no deletion)

```text
Before:

previous  current
   |         |
   v         v
   A ------> B ------> C

counter increments, no structural change

After:

previous            current
   |                   |
   v                   v
   A ------> B ------> C
             (previous now = B on next tick)
```

---

## Deletion Round (counter hits k)

```text
Before:

previous  current
   |         |
   v         v
   A ------> B ------> C

Operation:
previous.next = current.next   ->  A.next = C

After:

previous          current
   |                 |
   v                 v
   A ---------------> C

previous stays at A, current jumps to C, counter resets to 0
```

---

## k = 1 (delete everything)

```text
Before:
1 -> 2 -> 3 -> 4 -> NULL

After:
NULL
```

---

# 14. Interview Explanation in 30 Seconds

> I walk the list once with a counter that increments at every node. I also keep a `previous` pointer trailing behind `current`. Whenever the counter reaches `k`, the current node must be deleted, so I set `previous.next = current.next` to bypass it, move `current` forward, and reset the counter — without moving `previous`, since it still correctly points to the node before the new `current`. If the counter has not reached `k`, I simply advance both `previous` and `current`. As a special case, `k == 1` deletes the entire list, so I return `None` immediately. This runs in `O(n)` time and `O(1)` space.

---

# 15. Interviewer Follow-Up Questions

## Q1. What if the head itself needs deleting, such as when `k = 1`?

Handled as a dedicated early check: `k == 1` means every node is a multiple of `1`, so the result is always an empty list, and we return `None` without entering the main loop at all.

---

## Q2. How would a dummy node simplify this?

A dummy node placed before the head lets `previous` start at `dummy` instead of `None`. This removes the need for a special `k == 1` branch, because even a deletion at position `1` can update `dummy.next` safely. The final answer becomes `dummy.next`.

```python
class Solution:

    # Delete every k-th node using a dummy node to unify head handling.
    def deleteKthNode(self, head, k):

        # Create a dummy node that sits before the real head.
        dummy = Node(0)

        # Link the dummy node to the original list.
        dummy.next = head

        # previous now safely starts at the dummy node.
        previous = dummy

        # current still starts at the real head.
        current = head

        # Counter tracks progress toward the next multiple of k.
        counter = 0

        # Walk through every node exactly once.
        while current is not None:

            # One more node visited in this counting round.
            counter += 1

            # Check if this node must be deleted.
            if counter == k:

                # Bypass current using previous's pointer.
                previous.next = current.next

                # Move current to the node that replaced the deleted one.
                current = current.next

                # Restart the counting round.
                counter = 0

            else:

                # No deletion, so previous advances to current.
                previous = current

                # current moves forward.
                current = current.next

        # Return the node right after the dummy as the new head.
        return dummy.next
```

---

## Q3. Is there a recursive version?

Yes. A recursive helper can track position implicitly through the call stack:

```python
class Solution:

    # Public entry point.
    def deleteKthNode(self, head, k):

        # Delegate to the recursive helper starting at position 1.
        return self._delete(head, k, 1)

    # Recursively deletes every k-th node, tracking the current position.
    def _delete(self, node, k, position):

        # Base case: reached the end of the list.
        if node is None:

            # Nothing more to process.
            return None

        # If this position is a multiple of k, skip this node entirely.
        if position % k == 0:

            # Recurse on the rest of the list, restarting position count conceptually,
            # but since we use absolute position, just move to node.next.
            return self._delete(node.next, k, position + 1)

        # Otherwise keep this node and process the rest of the list.
        node.next = self._delete(node.next, k, position + 1)

        # Return this node as part of the resulting list.
        return node
```

This uses `O(n)` call-stack space, so the iterative version is preferred when space matters.

---

## Q4. What about a circular linked list?

The same counter-and-bypass logic applies, but the traversal must stop after making exactly one full loop around the list (tracking a fixed node count or comparing back to the starting node), otherwise the loop never terminates naturally the way a `None`-terminated list does. Special care is also needed if the node originally used to detect "one full loop" is itself deleted.

---

# 16. Comparison — Recursive vs Iterative

| Aspect | Iterative (counter + pointers) | Recursive |
|---|---|---|
| Time Complexity | `O(n)` | `O(n)` |
| Space Complexity | `O(1)` | `O(n)` (call stack) |
| Code Clarity | Slightly more pointer bookkeeping | Very concise |
| Risk | Must manage `previous`/`counter` carefully | Risk of stack overflow on very long lists |
| Interview Preference | Preferred for its `O(1)` space | Good as a follow-up alternative |

---

# 17. Pattern Recognition

This problem is an instance of a broader pattern:

> **Counter-driven periodic deletion** — walk the list once, maintain a position counter, and trigger a structural change (deletion, marking, transformation) whenever the counter satisfies some periodic condition (a multiple of `k`, alternating parity, etc.).

The same skeleton — `previous`, `current`, and a counter — reappears in problems like:

- Reversing nodes in groups of `k`.
- Deleting every alternate node.
- Rotating a list by `k` positions.
- Splitting a list into chunks of size `k`.

Whenever you see **"every k-th"**, **"every alternate"**, or **"in groups of k"** in a linked-list problem, reach for this counter + previous/current pointer template first.

---

# 18. Final Solution

```python
class Solution:

    # Deletes every k-th node (1-indexed) from a singly linked list.
    def deleteKthNode(self, head, k):

        # If the list is empty, there is nothing to delete.
        if head is None:

            # Return the empty list as-is.
            return None

        # If k is 1, every node gets deleted, leaving an empty list.
        if k == 1:

            # The result is simply an empty list.
            return None

        # Pointer that walks through the list.
        current = head

        # Pointer that trails just behind current.
        previous = None

        # Tracks position within the current counting round.
        counter = 0

        # Traverse the entire list exactly once.
        while current is not None:

            # One more node visited in this round.
            counter += 1

            # This node lands on a multiple of k, so delete it.
            if counter == k:

                # Bypass current using previous's next pointer.
                previous.next = current.next

                # Advance current to the node that replaced the deleted one.
                current = current.next

                # Restart the counting round.
                counter = 0

            else:

                # No deletion, so previous catches up to current.
                previous = current

                # Advance current to the next node.
                current = current.next

        # The head is unaffected for k > 1, so return it unchanged.
        return head
```

---

# 19. Interview Takeaways

```text
1. This problem is periodic deletion built on top of the classic
   "delete node at position x" trick.

2. Maintain three things while traversing: current, previous, counter.

3. On hitting counter == k:
      previous.next = current.next
      current = current.next
      counter = 0
   (previous does NOT move on a deletion round.)

4. On NOT hitting counter == k:
      previous = current
      current = current.next

5. k == 1 is a dedicated edge case: the whole list becomes empty.

6. A dummy node can eliminate the k == 1 special case entirely.

7. Time  = O(n)
   Space = O(1)
```

The key sentence to remember is:

> **Deleting every k-th node is just "delete node at position x" applied repeatedly in a single traversal, using a resettable counter to know when x has been reached again.**

---

## Related Problems to Practice

After this problem, practice these linked-list patterns:

1. Delete a node at a given position.
2. Delete every alternate node of a linked list.
3. Reverse nodes in groups of `k`.
4. Rotate a linked list by `k` places.
5. Remove N-th node from end of list.
6. Split a circular linked list into two halves.
7. Delete middle node of a linked list.
8. Remove duplicates from a sorted linked list.
9. Merge two sorted linked lists.
10. Detect and remove a loop in a linked list.

These problems reinforce the same `previous`/`current` pointer bookkeeping combined with position-aware traversal.
