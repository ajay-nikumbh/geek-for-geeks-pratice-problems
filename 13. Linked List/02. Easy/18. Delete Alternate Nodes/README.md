# Delete Alternate Nodes

| Field | Value |
|---|---|
| Topic | Linked List |
| Difficulty | Easy |
| Submissions | 91,473 |
| Accuracy | 56.09% |
| Companies | Morgan Stanley |
| Related Tags | Linked List |
| Problem Link | [https://www.geeksforgeeks.org/problems/delete-alternate-nodes/1](https://www.geeksforgeeks.org/problems/delete-alternate-nodes/1) |

## Problem Statement

Given the head of a **singly linked list**, delete every **alternate node**, starting from the **second node**.

In other words:

- Keep node 1, delete node 2.
- Keep node 3, delete node 4.
- Keep node 5, delete node 6.
- and so on.

Return the head of the modified linked list.

### Example 1

```text
Input:  1 -> 2 -> 3 -> 4 -> 5 -> NULL
Output: 1 -> 3 -> 5 -> NULL
```

### Example 2

```text
Input:  10 -> 20 -> 30 -> 40 -> NULL
Output: 10 -> 30 -> NULL
```

---

# 1. Interview Intuition

At first glance this looks like a variant of the position-based deletion problem — but it is actually **simpler**.

In "delete at position `x`", the position to delete could be anywhere, and we had to compute how many steps to move before reaching the correct node.

Here, the pattern is completely **fixed and regular**:

```text
keep -> delete -> keep -> delete -> keep -> delete -> ...
```

There is no need to count positions or receive an index from outside. The structure of the deletion itself tells us what to do at every step.

So instead of thinking "how far do I move to reach position `x`," the right question here is:

> "If I stand on a node I want to keep, the very next node is always the one I must delete."

That means we only ever need **two adjacent pointers**:

```text
current       -> the node we keep
current.next  -> the node we delete
```

We repeatedly bypass `current.next`, then jump `current` forward to the next node we are keeping. No counters, no index arithmetic — just a repeating local pattern.

---

# 2. Core Linked List Idea

Think of the list as pairs of nodes: (keep, delete), (keep, delete), ...

```text
1 -> 2 -> 3 -> 4 -> 5 -> NULL
K    D    K    D    K
```

- `1` is kept.
- `2` is deleted.
- `3` is kept.
- `4` is deleted.
- `5` is kept (nothing after it, so it is simply the end).

Visually, deleting one pair looks like the same "bypass" operation we always use in linked lists:

```text
Before:

1 --------> 2 --------> 3

After:

1 --------------------> 3

(2 is no longer reachable)
```

The entire problem is just this single bypass operation, applied again and again as we slide down the list two nodes at a time.

---

# 3. Most Important Edge Case

There are several small but easy-to-miss situations:

## Case 1 — Empty List

```text
head = NULL
```

There is nothing to keep or delete. Return `NULL` immediately.

## Case 2 — Single Node

```text
1 -> NULL
```

There is no second node to delete. The list is unchanged:

```text
1 -> NULL
```

## Case 3 — Exactly Two Nodes

```text
1 -> 2 -> NULL
```

Node `2` is the alternate node and must be deleted:

```text
1 -> NULL
```

## Case 4 — Odd Length List

```text
1 -> 2 -> 3 -> 4 -> 5 -> NULL
```

The last node (`5`) has no following node, so after deleting `4`, the loop simply stops because `current.next` becomes `None`.

## Case 5 — Even Length List

```text
1 -> 2 -> 3 -> 4 -> NULL
```

Every node pairs up perfectly:

```text
1 -> 3 -> NULL
```

These "does a next node exist" checks are exactly where bugs creep in, especially for odd-length lists — we will see this in the Common Mistakes section.

---

# 4. Approach 1 — Brute Force Thinking

A brute-force approach could be:

1. Traverse the list and store every value in an array.
2. Keep only the values at even indices (`0`, `2`, `4`, ...) using 0-indexing.
3. Build a brand-new linked list from the kept values.

Example:

```text
Linked List:

1 -> 2 -> 3 -> 4 -> 5

Convert to array (0-indexed):

index:  0  1  2  3  4
value:  1  2  3  4  5

Keep even indices (0, 2, 4):

[1, 3, 5]

Rebuild:

1 -> 3 -> 5
```

### Complexity

If there are `n` nodes:

```text
Time  = O(n)
Space = O(n)
```

The time complexity is already optimal, but the extra array and the freshly built list are unnecessary. The existing nodes can be reused directly with pointer manipulation — an interviewer will expect the **in-place** version.

---

# 5. Optimal Approach — In-Place Pointer Skipping

We do not need extra memory at all. We can delete alternate nodes by rewiring `next` pointers as we walk down the list.

Maintain a single pointer:

```text
current
```

While both `current` and `current.next` exist:

1. Save the node that must be deleted:

```text
node_to_delete = current.next
```

2. Bypass it by connecting `current` directly to the node after it:

```text
current.next = current.next.next
```

3. Advance `current` to the node we just kept:

```text
current = current.next
```

### Why this correctly alternates

After step 2, `current.next` now points to the **next node to keep** (the node that used to be two steps ahead). When we then do `current = current.next` in step 3, `current` lands exactly on that kept node — putting us right back at the start of the pattern: "the node right after `current` is the one to delete."

This is why only two lines of pointer surgery, repeated in a loop, are enough to alternately keep and delete every node — the loop condition `current and current.next` naturally stops us the moment there is no more node left to delete.

---

# 6. Pointer Movement

Let's trace the pointer positions on:

```text
1 -> 2 -> 3 -> 4 -> 5 -> 6 -> NULL
```

Start:

```text
current
   |
   v
   1 -> 2 -> 3 -> 4 -> 5 -> 6 -> NULL
```

`current.next` is `2`, so delete it:

```text
current.next = current.next.next   =>   1.next = 3
```

```text
1 -> 3 -> 4 -> 5 -> 6 -> NULL
```

Advance `current`:

```text
         current
            |
            v
1 ->        3 -> 4 -> 5 -> 6 -> NULL
```

`current.next` is `4`, so delete it:

```text
3.next = 5
```

```text
1 -> 3 -> 5 -> 6 -> NULL
```

Advance `current`:

```text
                  current
                     |
                     v
1 -> 3 ->            5 -> 6 -> NULL
```

`current.next` is `6`, so delete it:

```text
5.next = None
```

```text
1 -> 3 -> 5 -> NULL
```

Advance `current`:

```text
                          current
                             |
                             v
1 -> 3 -> 5 ->               NULL
```

Now `current.next` is `None`, so the loop stops.

Final list:

```text
1 -> 3 -> 5 -> NULL
```

---

# 7. Algorithm

### Step 1

If the linked list is empty:

```text
head == None
```

return `None`.

### Step 2

Start from the head:

```text
current = head
```

### Step 3

Loop while both a current node and its next node exist:

```text
while current is not None and current.next is not None:
```

### Step 4

Bypass the alternate node:

```text
current.next = current.next.next
```

### Step 5

Advance `current` to the node we just kept:

```text
current = current.next
```

### Step 6

Return `head`.

---

# 8. Optimal Python Solution

```python
class Solution:

    # This function deletes every alternate node starting from the second node.
    def deleteAlternateNodes(self, head):

        # If the linked list is empty, there is nothing to delete.
        if head is None:

            # Return the empty list as-is.
            return None

        # Start traversal from the head node.
        current = head

        # Continue as long as there is a current node and a node after it to delete.
        while current is not None and current.next is not None:

            # The node right after current is the alternate node to delete.
            node_to_delete = current.next

            # Bypass the alternate node by linking current to the node after it.
            current.next = node_to_delete.next

            # Move current forward to the node we just decided to keep.
            current = current.next

        # Return the head of the modified linked list.
        return head
```

---

# 9. Complete Dry Run

Consider:

```text
head = 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> NULL
```

## Initial State

```text
current = 1
1 -> 2 -> 3 -> 4 -> 5 -> 6 -> NULL
^
|
current
```

`current` is `1`, `current.next` is `2` — the loop condition holds.

## Iteration 1

```text
node_to_delete = 2
current.next   = node_to_delete.next = 3

1.next = 3
```

List becomes:

```text
1 -> 3 -> 4 -> 5 -> 6 -> NULL
```

Advance:

```text
current = current.next = 3
```

## Iteration 2

```text
current = 3
node_to_delete = 4
current.next   = node_to_delete.next = 5

3.next = 5
```

List becomes:

```text
1 -> 3 -> 5 -> 6 -> NULL
```

Advance:

```text
current = current.next = 5
```

## Iteration 3

```text
current = 5
node_to_delete = 6
current.next   = node_to_delete.next = None

5.next = None
```

List becomes:

```text
1 -> 3 -> 5 -> NULL
```

Advance:

```text
current = current.next = None
```

## Loop Termination

```text
current is None
```

The loop condition `current is not None and current.next is not None` fails, so the loop stops.

## Final Result

```text
1 -> 3 -> 5 -> NULL
```

This matches the expected output exactly.

---

# 10. Complexity Analysis

Let:

```text
n = number of nodes
```

Each iteration of the loop advances `current` by two original nodes (one kept, one deleted). So the loop runs approximately:

```text
n / 2
```

times.

```text
Time Complexity = O(n)
```

Only a constant number of pointer variables are used (`current`, `node_to_delete`), regardless of list size.

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

Could we do better than `O(n)`?

No — every single node in the list must be examined at least once to decide whether it is kept or deleted. There is no way to know the structure of the second half of the list without walking through the first half of a singly linked list.

Also, no extra memory is required. We are not building a new list or storing extra values — we are simply rewiring the existing `next` pointers in place, so `O(1)` space is the best possible.

This makes the pointer-skipping approach optimal in both time and space.

---

# 12. Common Mistakes

## Mistake 1 — Not Checking `current.next` Before Accessing `current.next.next`

Wrong:

```python
while current is not None:
    current.next = current.next.next   # crashes if current.next is None
    current = current.next
```

On an odd-length list, the last kept node has `current.next = None`. Accessing `current.next.next` in that state throws a **null pointer / attribute error**.

Correct:

```python
while current is not None and current.next is not None:
    current.next = current.next.next
    current = current.next
```

---

## Mistake 2 — Advancing `current` Incorrectly

Wrong:

```python
current = current.next.next   # skips too far if current.next just became None
```

After deleting the alternate node, `current.next` already points to the next node to keep. The safe and correct move is:

```python
current = current.next
```

Advancing by "two nodes from the original list" using stale pointers can cause you to skip over the keep/delete pattern entirely once `next` pointers have already been rewired.

---

## Mistake 3 — Not Handling a Single-Node List

For:

```text
1 -> NULL
```

`current.next` is `None` from the very first check, so the loop body never executes. This is actually handled correctly by the loop condition — but if you forget the `current.next is not None` check and only test `current is not None`, you will crash trying to delete a node that does not exist.

---

## Mistake 4 — Forgetting the Empty List Case

```python
if head is None:
    return None
```

Without this check, `current = head` would simply be `None`, and the `while` loop would not execute — which actually works fine here since Python handles `None.next` access safely inside the guarded condition. Still, it's good practice to make the empty-list case explicit and return early.

---

## Mistake 5 — Returning `current` Instead of `head`

By the end of the loop, `current` has moved all the way to the last kept node — not the start of the list.

Wrong:

```python
return current
```

Correct:

```python
return head
```

---

# 13. Visual Cheat Sheet

## One Delete Step

```text
Before:

current      target
   |            |
   v            v
   A ---------> B ---------> C


Operation:

current.next = current.next.next


After:

   A ---------------------> C

(B removed, current still points to A)
```

## Advancing After Deletion

```text
Before advance:

current
   |
   v
   A -------------------> C


Operation:

current = current.next


After advance:

           current
              |
              v
   A -------> C
```

## Full Pattern on a 6-Node List

```text
1 -> 2 -> 3 -> 4 -> 5 -> 6 -> NULL
K    D    K    D    K    D

Result:

1 -> 3 -> 5 -> NULL
```

---

# 14. Interview Explanation in 30 Seconds

A strong interview explanation would be:

> Since we always delete the node immediately after the one we keep, I only need two adjacent pointers: `current` and `current.next`. I bypass `current.next` by linking `current` directly to `current.next.next`, then move `current` forward to the node I just kept. I repeat this while both `current` and `current.next` exist, which naturally handles odd-length lists. This runs in `O(n)` time and `O(1)` space, with no extra data structures.

---

# 15. Interviewer Follow-Up Questions

## Q1. What if we needed to delete alternate nodes starting from the FIRST node instead?

Then the head itself is the first node to delete, so we need to update `head` before entering the loop:

```python
class Solution:
    def deleteAlternateNodes(self, head):
        # If the list has fewer than 1 node, nothing to do.
        if head is None:
            return None

        # The new head is the second node (first node is deleted).
        head = head.next

        # Continue the same pattern from here.
        current = head
        while current is not None and current.next is not None:
            current.next = current.next.next
            current = current.next

        return head
```

This is a nice way to test whether the candidate truly understands *why* the pattern works, rather than having memorized the original solution.

---

## Q2. Can you write a recursive version?

Yes:

```python
class Solution:

    # Recursively delete every alternate node starting from the second node.
    def deleteAlternateNodes(self, head):

        # Base case: if there is no node or no node after it, nothing to delete here.
        if head is None or head.next is None:
            return head

        # The node right after head is the one to delete.
        node_to_delete = head.next

        # Bypass it by connecting head to the node after the deleted one.
        head.next = node_to_delete.next

        # Recurse on the rest of the list starting from the newly kept next node.
        self.deleteAlternateNodes(head.next)

        # Return the (unchanged) head of this sub-list.
        return head
```

This uses `O(n)` recursion stack space, so the iterative version is preferred when space matters.

---

## Q3. What about a doubly linked list — do you need to fix `prev` pointers too?

Yes. In a doubly linked list, deleting a node means fixing links on **both sides**:

```text
A <-> B <-> C
```

To delete `B`:

```python
A.next = C
C.prev = A
```

Forgetting `C.prev = A` leaves a dangling backward pointer to a deleted node, which is a very common mistake when adapting singly linked list logic to doubly linked lists.

---

## Q4. Can you restore the deleted nodes as a separate list?

Yes — instead of discarding `node_to_delete`, link the deleted nodes together into their own list:

```python
class Solution:

    # Delete alternate nodes but also return the removed nodes as a separate list.
    def deleteAlternateNodes(self, head):

        if head is None:
            return head, None

        current = head
        deleted_head = None
        deleted_tail = None

        while current is not None and current.next is not None:

            # Detach the alternate node.
            node_to_delete = current.next
            current.next = node_to_delete.next
            node_to_delete.next = None

            # Attach it to the deleted list.
            if deleted_head is None:
                deleted_head = node_to_delete
                deleted_tail = node_to_delete
            else:
                deleted_tail.next = node_to_delete
                deleted_tail = node_to_delete

            current = current.next

        return head, deleted_head
```

This shows the interviewer that you can extend the base pattern to track additional state without changing its core structure.

---

# 16. Comparison — Iterative vs Recursive

| Aspect | Iterative | Recursive |
|---|---|---|
| Time Complexity | `O(n)` | `O(n)` |
| Space Complexity | `O(1)` | `O(n)` (call stack) |
| Readability | Simple loop | Elegant, mirrors the pattern directly |
| Risk on Large Lists | None | Possible stack overflow on very long lists |
| Interview Preference | Usually preferred | Good to mention as an alternative |

---

# 17. Pattern Recognition

This problem belongs to a broader family: **periodic / regular-interval deletion** in a linked list.

```text
Delete every alternate node   → delete every 2nd node
Delete every 3rd node         → a natural generalization
Remove every k-th node        → the general version of this pattern
```

The general k-th version simply changes the "how many nodes to keep before deleting one" count:

```text
keep (k - 1) nodes, delete 1 node, repeat
```

Delete Alternate Nodes is the special case where `k = 2` — which is exactly why the solution is simpler than the general position-based deletion problem: there is no external index to track, just a fixed, repeating rhythm baked into the algorithm itself.

Recognizing this connection means that once you can solve this problem cleanly, extending it to "delete every k-th node" is a small, natural step rather than a completely new problem.

---

# 18. Final Solution

```python
class Solution:

    # Delete every alternate node starting from the second node.
    def deleteAlternateNodes(self, head):

        # An empty list has nothing to delete.
        if head is None:
            return None

        # Start traversal from the head.
        current = head

        # Continue while there is a node to keep and a node after it to delete.
        while current is not None and current.next is not None:

            # The node right after current is the alternate node to remove.
            node_to_delete = current.next

            # Bypass the alternate node.
            current.next = node_to_delete.next

            # Move current forward to the next kept node.
            current = current.next

        # Return the head of the modified linked list.
        return head
```

---

# 19. Interview Takeaways

Remember these points:

```text
1. The deletion pattern here is fixed and regular — no index tracking needed.

2. Only two adjacent pointers are required: current and current.next.

3. Bypass with one line:

   current.next = current.next.next

4. Always guard with "current.next is not None" before touching
   current.next.next — this is the #1 source of bugs on odd-length lists.

5. Advance using the already-updated current.next, not a stale two-step jump.

6. Single node and empty list are handled naturally by the loop condition.

7. Time  = O(n)
8. Space = O(1)
```

The key sentence to remember is:

> **When a deletion pattern repeats at a fixed interval, you rarely need to count positions — you only need to look one step ahead and bypass it, then slide forward.**

---

## Related Problems to Practice

After this problem, practice these linked-list patterns:

1. Linked List Delete at Position.
2. Remove N-th node from end.
3. Delete middle node of a linked list.
4. Remove duplicates from a sorted linked list.
5. Reverse a linked list.
6. Reverse nodes in groups of `k`.
7. Rotate a linked list.
8. Merge two sorted linked lists.
9. Detect and remove a loop in a linked list.
10. Segregate even and odd nodes in a linked list.

These problems reinforce the same core idea of walking a singly linked list while carefully rewiring `next` pointers.
