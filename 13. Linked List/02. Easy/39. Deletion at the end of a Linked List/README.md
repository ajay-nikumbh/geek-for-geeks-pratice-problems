# Deletion at the end of a Linked List

| Topic | Difficulty | Submissions | Accuracy | Companies | Related Tags | Problem Link |
|---|---|---|---|---|---|---|
| Linked List | Easy | 18,330 | 51.25% | — | Linked List | [https://www.geeksforgeeks.org/problems/deletion-at-the-end-of-a-linked-list/1](https://www.geeksforgeeks.org/problems/deletion-at-the-end-of-a-linked-list/1) |

## Problem Statement

Given the head of a **singly linked list**, delete the **last node** of the linked list and return the head of the modified list.

### Example 1

```text
Input:  10 -> 20 -> 30 -> NULL
Output: 10 -> 20 -> NULL
```

### Example 2

```text
Input:  5 -> NULL
Output: NULL
```

# 1. Interview Intuition

At first glance, deleting the last node feels similar to deleting the head — but it is actually the opposite in terms of difficulty.

> Deleting the **head** is `O(1)` because we already hold a direct reference to it.
> Deleting the **last node** requires traversal, because a singly linked list only lets you move **forward**.

Suppose we have:

```text
10 -> 20 -> 30 -> 40 -> NULL
```

and we want to remove `40`.

To remove `40`, we must change the `next` pointer of the node **before** it — `30`.

```text
30.next = None
```

But we do not have a shortcut to `30`. There is no `prev` pointer in a singly linked list. The only way to reach `30` is to start at `head` and walk node by node until we land on the second-to-last node.

```text
10 -> 20 -> 30 -> 40 -> NULL
             ^      ^
             |      |
        second-last last
```

### Contrast with Arrays

This is an important interview talking point:

```text
Array:              arr.pop()             -> O(1)
Singly Linked List:  delete last node      -> O(n)
```

An array supports **backward and index-based access** — the last element lives at a known index (`len(arr) - 1`), so popping it is instant.

A singly linked list has **no index and no backward pointer**. The only information any node carries is "who comes after me," never "who comes before me." So even though we are only removing *one* node, we are forced to visit *all* the nodes before it just to find the one whose `next` pointer must change.

This is exactly the kind of trade-off interviewers want you to articulate: linked lists trade `O(1)` insertion/deletion **once you're at the right spot** for `O(n)` cost in **finding** that spot when no direct reference exists.

# 2. Core Linked List Idea

The core operation is simple once you reach the right node:

```text
second_last.next = None
```

Visual walkthrough for:

```text
10 -> 20 -> 30 -> 40 -> NULL
```

**Step 1 — Traverse to the second-to-last node:**

```text
10 -> 20 -> 30 -> 40 -> NULL
             ^
             |
         current (this is the second-to-last node)
```

**Step 2 — Cut the link to the last node:**

```text
current.next = None
```

**Result:**

```text
10 -> 20 -> 30 -> NULL

              40 is now orphaned (unreachable from the list)
```

`40` still technically exists in memory for a moment, but since nothing points to it anymore, it is no longer part of the list and will eventually be garbage collected.

# 3. Most Important Edge Case

## Case 1 — Empty List

```text
head = None
```

There is nothing to delete. We simply return `None`.

```python
if head is None:
    return None
```

## Case 2 — Single Node List

```text
5 -> NULL
```

This is the trickiest case. The single node `5` is **both** the head and the last node.

There is no "second-to-last" node to walk to — the loop we use for the general case would never even execute, or worse, would crash trying to dereference something that doesn't exist.

After deleting the only node, the list becomes completely empty:

```text
Before:
head
 |
 v
5 -> NULL

After:
head = None
```

So this case must be detected and handled **before** entering the main traversal logic:

```python
if head.next is None:
    return None
```

If you forget this check, your lookahead logic (`current.next.next`) will try to access `.next` on a `None` value, causing a null pointer / `AttributeError` crash.

# 4. Approach 1 — Brute Force Thinking

A brute-force way to think about this:

1. Traverse the entire list once to count the number of nodes, `n`.
2. Traverse again from the head, moving `n - 2` steps to reach the second-to-last node.
3. Set that node's `next` to `None`.

Example:

```text
List: 10 -> 20 -> 30 -> 40

Pass 1: count nodes -> n = 4

Pass 2: move (n - 2) = 2 steps from head
        10 -> 20 -> 30   (stop here)

Set 30.next = None

Result: 10 -> 20 -> 30 -> NULL
```

### Complexity

```text
Time  = O(n) + O(n) = O(n)   (two passes, but still linear)
Space = O(1)
```

This works and is still technically `O(n)`, but it does **two full traversals** where **one** is enough. Interviewers usually push for the single-pass version, since it is strictly better and not any harder to write.

# 5. Optimal Approach — Single Pass Lookahead

Instead of counting the length first, we can detect "am I the second-to-last node?" while we are still moving, using a **lookahead** check.

The key idea:

> While traversing with a pointer `current`, check `current.next.next`.
> If `current.next.next` is `None`, that means `current.next` is the **last** node — so `current` itself is the **second-to-last** node.

```python
while current.next.next is not None:
    current = current.next
```

This loop stops exactly when `current` is the second-to-last node — no length counting required, and no second traversal.

### Why the Lookahead Works

Think of it this way:

```text
current -> current.next -> current.next.next
```

- If `current.next.next` exists, then `current.next` is **not** the last node yet (it has something after it), so we keep moving.
- If `current.next.next` is `None`, then `current.next` has nothing after it — `current.next` **is** the last node, and `current` is exactly the node we need.

This "look one node ahead" trick is a very common linked-list pattern (it also shows up in fast/slow pointer problems, cycle detection, and N-th-from-end problems).

# 6. Pointer Movement

Consider:

```text
10 -> 20 -> 30 -> 40 -> NULL
```

**Start:**

```text
current
   |
   v
  10 -> 20 -> 30 -> 40 -> NULL
```

Check: `current.next.next` = `30` (not `None`) → keep moving.

**After 1 move:**

```text
      current
         |
         v
10 ->   20 -> 30 -> 40 -> NULL
```

Check: `current.next.next` = `40` (not `None`) → keep moving.

**After 2 moves:**

```text
             current
                |
                v
10 -> 20 ->   30 -> 40 -> NULL
```

Check: `current.next.next` = `None` → **stop here**.

`current` is now `30`, the second-to-last node. Perform:

```text
current.next = None
```

**Final list:**

```text
10 -> 20 -> 30 -> NULL
```

# 7. Algorithm

### Step 1

If the list is empty:

```text
head is None
```

return `None`.

### Step 2

If the list has only one node:

```text
head.next is None
```

return `None` (deleting the only node empties the list).

### Step 3

Otherwise, start traversal:

```text
current = head
```

### Step 4

While the node after `current.next` exists (i.e. `current.next.next is not None`), move `current` forward.

### Step 5

Once the loop ends, `current` is the second-to-last node. Cut the link:

```text
current.next = None
```

### Step 6

Return `head`.

# 8. Optimal Python Solution

```python
class Solution:

    # This function deletes the last node of the linked list.
    def deleteLast(self, head):

        # If the linked list is empty, there is nothing to delete.
        if head is None:

            # Return the empty list itself.
            return None

        # Special case: only one node in the list.
        if head.next is None:

            # Deleting the only node makes the list empty.
            return None

        # Start traversal from the head node.
        current = head

        # Move current forward while it is not yet the second-to-last node.
        # current.next.next tells us whether current.next is the last node.
        while current.next.next is not None:

            # Advance current one step forward.
            current = current.next

        # At this point, current is the second-to-last node.
        # Cut the link to the last node, orphaning it from the list.
        current.next = None

        # Return the unchanged head of the modified list.
        return head
```

# 9. Complete Dry Run

Consider:

```text
head = 10 -> 20 -> 30 -> 40 -> NULL
```

## Initial Checks

```text
head is None?        -> False
head.next is None?   -> False (10 -> 20 -> ... , more than one node)
```

Neither special case applies, so we enter the main loop.

## Loop Execution

**Initial state:**

```text
current = 10

current.next        = 20
current.next.next   = 30   (not None -> continue)
```

**Move 1:**

```text
current = 20

current.next        = 30
current.next.next   = 40   (not None -> continue)
```

**Move 2:**

```text
current = 30

current.next        = 40
current.next.next   = None   (stop the loop)
```

## Final Step

```text
current = 30
current.next = None
```

Since `30.next` was `40`, and we just set it to `None`, node `40` is no longer reachable.

## Result

```text
10 -> 20 -> 30 -> NULL
```

# 10. Dry Run — Single Node List

Input:

```text
head = 5 -> NULL
```

## Check

```text
head is None?        -> False
head.next is None?   -> True   (5 has no next node)
```

Since `head.next is None`, we hit the special case immediately and return `None` **without entering the loop at all**.

```text
Before:
head
 |
 v
5 -> NULL

After:
head = None
```

This confirms why the single-node check must come **before** the `while current.next.next is not None` loop — if it didn't, the very first check `current.next.next` would try to call `.next` on `None` (since `current.next` would already be `None`), crashing the program.

# 11. Complexity Analysis

Let:

```text
n = number of nodes
```

To find the second-to-last node, we must traverse:

```text
n - 2 nodes (approximately)
```

Therefore:

```text
Time Complexity = O(n)
```

Only a constant number of pointer variables (`current`) are used:

```text
Space Complexity = O(1)
```

### Final Complexity

| Metric | Complexity |
|---|---|
| Time | `O(n)` |
| Extra Space | `O(1)` |

# 12. Why This Is Optimal

Could we make this faster than `O(n)`?

For a **singly** linked list — no.

Since each node only knows its `next` pointer and not its previous one, the only way to find the second-to-last node is to start at the head and walk all the way to the end. There is no shortcut.

```text
head -> node2 -> node3 -> ... -> second_last -> last -> NULL
```

We are forced to pass through every node except the last one.

### Interview Insight — What If It Were a Doubly Linked List?

This is a great insight to bring up proactively in an interview:

> If this were a **doubly linked list** with a maintained `tail` pointer, deleting the last node would be `O(1)`.

Why? Because in a doubly linked list, every node has a `prev` pointer:

```text
tail.prev -> new_tail
new_tail.next = None
tail = new_tail
```

We would not need to traverse at all — `tail.prev` gives us direct backward access to the second-to-last node.

The `O(n)` cost in our problem exists specifically **because** we are working with a **singly** linked list with no backward references. This distinction — singly vs. doubly linked list — is one of the most common follow-up threads interviewers pull on.

# 13. Common Mistakes

## Mistake 1 — Forgetting the Single-Node Case

Without checking `head.next is None` first:

```python
while current.next.next is not None:
    current = current.next
```

If the list has only one node, `current.next` is `None`, and `current.next.next` tries to access `.next` on `None` — this crashes with a null pointer error (`AttributeError: 'NoneType' object has no attribute 'next'` in Python).

Always handle the single-node list **before** the lookahead loop.

## Mistake 2 — Wrong Stopping Condition

A very tempting but incorrect condition:

```python
while current.next is not None:
    current = current.next
```

This stops when `current` **is** the last node, not the second-to-last node. That's **one node too late** — by the time you stop, you no longer have access to the node before the last one, and you cannot cut the link anymore.

The correct condition checks **one node ahead**:

```python
while current.next.next is not None:
    current = current.next
```

## Mistake 3 — Not Handling the Empty List

Calling `.next` on a `None` head immediately crashes:

```python
head.next   # AttributeError if head is None
```

Always check `head is None` first, before anything else.

## Mistake 4 — Doing Two Passes When One Is Enough

Counting the length first and then traversing again works, but it's unnecessary extra work. The single-pass lookahead approach achieves the same `O(n)` traversal without a separate counting pass.

## Mistake 5 — Returning `current` Instead of `head`

```python
return current   # WRONG — this returns the second-to-last node, not the head
```

Always return the original `head` reference (unless the list became empty, in which case return `None`).

# 14. Visual Cheat Sheet

## General Case (2+ nodes)

```text
Before:

10 -> 20 -> 30 -> 40 -> NULL
             ^      ^
             |      |
         current   last

Operation:

current.next = None

After:

10 -> 20 -> 30 -> NULL
```

## Single Node

```text
Before:

head
 |
 v
5 -> NULL

Operation:

return None

After:

head = None   (empty list)
```

## Empty List

```text
Before:

head = None

Operation:

return None (nothing to do)

After:

head = None
```

# 15. Interview Explanation in 30 Seconds

A strong interview explanation would be:

> Since this is a singly linked list, I can't move backward from the last node, so I need to walk forward until I reach the second-to-last node — the one whose `next` pointer must become `None`. I do this in a single pass by checking `current.next.next`: when that's `None`, `current` is exactly the node I need. I handle two special cases upfront — an empty list, which I return as-is, and a single-node list, which becomes empty after deletion. The traversal takes `O(n)` time and `O(1)` extra space.

# 16. Interviewer Follow-Up Questions

## Q1. How would maintaining a tail pointer change this? Would it make it O(1)?

Surprisingly — **no**, not for a singly linked list.

Even with a `tail` pointer, you'd still need to find the **second-to-last** node to update its `next` to `None` and reassign `tail`. A `tail` pointer alone doesn't give you backward access.

```text
tail -> last_node

To delete last_node, we still need: second_last.next = None
tail pointer alone does not know who "second_last" is.
```

However, for a **doubly linked list** with a `tail` pointer, it *is* `O(1)`, because `tail.prev` directly gives you the second-to-last node:

```text
new_tail = tail.prev
new_tail.next = None
tail = new_tail
```

## Q2. How does having `prev` pointers make this trivial in a doubly linked list?

Because every node already stores a reference to the node before it. Deleting the last node becomes:

```python
def deleteLast(self, tail):
    if tail is None:
        return None
    new_tail = tail.prev
    if new_tail is not None:
        new_tail.next = None
    return new_tail
```

No traversal needed at all — just pointer reassignment, `O(1)` time.

## Q3. Can you write a recursive version?

Yes:

```python
class Solution:

    def deleteLast(self, head):

        # Empty list — nothing to delete.
        if head is None:
            return None

        # Single node left — recursion base case, list becomes empty.
        if head.next is None:
            return None

        # If the next node is the last node, cut the link here.
        if head.next.next is None:
            head.next = None
            return head

        # Otherwise, recurse further into the list.
        head.next = self.deleteLast(head.next)
        return head
```

This uses `O(n)` call stack space in addition to `O(n)` time, so the iterative version is usually preferred unless recursion is explicitly requested.

## Q4. Does not knowing the list's length in advance matter here?

Not really — the single-pass lookahead approach doesn't need to know the length beforehand. It discovers "I'm at the second-to-last node" naturally as it traverses, using the `current.next.next is None` check. This is strictly better than the two-pass "count then traverse" approach, which does need the length computed first.

## Q5. What if you were given a pointer to a node that you know is *not* the tail — can you delete it in O(1)?

That's a different, well-known trick: copy the next node's data into the current node, then delete the next node instead. It works for any non-tail node with a known next node, but does **not** apply when deleting the actual last node, since there is no node after it to copy from.

# 17. Important Comparison — Array vs Singly vs Doubly Linked List

| Structure | Delete Last Element |
|---|---:|
| Array | `O(1)` amortized (`pop()`) |
| Singly Linked List | `O(n)` (must traverse to second-to-last node) |
| Doubly Linked List (with tail pointer) | `O(1)` (`tail.prev` gives direct access) |

This is a great interview talking point:

> Arrays are efficient at removing from the end because they support direct indexing. Singly linked lists are efficient at removing from the **front** but not the end, because there's no backward reference. Doubly linked lists get the best of both worlds for end-deletion, at the cost of extra memory per node for the `prev` pointer.

# 18. Pattern Recognition

The general insight from this problem:

> **Singly linked lists are bad at "last element" operations unless you maintain extra bookkeeping.**

A `tail` pointer helps with **insertion** at the end (`O(1)` — just attach the new node and update `tail`), but it does **not** help with **deletion** at the end, because deletion needs the node *before* the tail, which a plain `tail` pointer cannot give you in a singly linked structure.

This asymmetry — insertion at the end being cheap, deletion at the end being expensive — is a recurring theme in linked-list design discussions, and it's exactly why doubly linked lists exist: the `prev` pointer closes this gap.

Whenever you see a linked-list problem involving "the last node" or "the N-th from the end," ask yourself:

```text
"Do I have a way to reach the node before this one?"
```

If not, a full traversal is unavoidable in a singly linked list.

# 19. Final Solution

```python
class Solution:

    # This function deletes the last node of the linked list.
    def deleteLast(self, head):

        # If the linked list is empty, there is nothing to delete.
        if head is None:

            # Return the empty list itself.
            return None

        # Special case: only one node in the list.
        if head.next is None:

            # Deleting the only node makes the list empty.
            return None

        # Start traversal from the head node.
        current = head

        # Move current forward while it is not yet the second-to-last node.
        while current.next.next is not None:

            # Advance current one step forward.
            current = current.next

        # current is now the second-to-last node — cut the link to the last node.
        current.next = None

        # Return the unchanged head of the modified list.
        return head
```

# 20. Interview Takeaways

Remember these points:

```text
1. Deleting the head is O(1); deleting the last node is O(n) — the opposite of arrays.

2. A singly linked list has no backward pointer, so reaching the
   second-to-last node requires a full forward traversal.

3. The lookahead check "current.next.next is None" finds the
   second-to-last node in a single pass — no length counting needed.

4. Always handle the empty list and single-node list as special cases
   BEFORE the main loop, or you risk a null pointer crash.

5. A tail pointer alone does NOT make this O(1) for a singly linked list —
   only a doubly linked list's "prev" pointer does.

6. Time complexity  = O(n)
7. Space complexity = O(1)
```

The key sentence to remember is:

> **In a singly linked list, deleting the last node is fundamentally a search problem — you must walk to the second-to-last node before you can perform the one pointer change that actually deletes anything.**

## Related Problems to Practice

After this problem, practice these linked-list patterns:

1. Delete node at the head of a linked list.
2. Linked List Delete at Position.
3. Remove N-th node from the end.
4. Delete middle node of a linked list.
5. Reverse a linked list.
6. Find the middle of a linked list.
7. Detect a cycle in a linked list.
8. Merge two sorted linked lists.
9. Remove duplicates from a sorted linked list.
10. Convert a singly linked list to a doubly linked list.

These problems build directly on the same traversal and pointer-manipulation fundamentals.
