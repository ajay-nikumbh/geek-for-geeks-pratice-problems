# Delete Head of Linked List

> **Topic:** Linked List  
> **Difficulty:** Easy  
> **Submissions:** 25,017  
> **Accuracy:** 70.33%  
> **Companies:** —  
> **Related Tags:** Linked List  
> **Problem Link:** https://www.geeksforgeeks.org/problems/delete-head-of-linked-list/1  

---

## Problem Statement

Given the head of a **singly linked list**, delete the **head node** of the list and return the new head.

If the list has only one node, the list becomes **empty** after deletion.

If the list is already empty, there is nothing to delete.

### Example 1

```text
Input:
10 -> 20 -> 30 -> NULL

Delete head (10).

Output:
20 -> 30 -> NULL
```

### Example 2

```text
Input:
5 -> NULL

Delete head (5).

Output:
NULL   (empty list)
```

---

# 1. Interview Intuition

Most linked-list deletion problems force you to solve a smaller sub-problem first:

> "Find the node **just before** the one I want to delete."

That is why deleting an arbitrary position or an arbitrary value normally costs `O(n)` — you have to walk the list to find the previous node, because a singly linked list cannot move backward.

Deleting the **head** is the one case where that sub-problem does not exist at all.

```text
head
 |
 v
10 -> 20 -> 30 -> NULL
```

You are not searching for the head — you already have a direct reference to it in the `head` variable. There is no "previous" node before the head, because the head is the very start of the list.

So the question "which node's `next` pointer must I change?" has a trivial answer here:

> None. There is nothing before the head to update. You only need to move the `head` reference itself, one step forward.

```text
head = head.next
```

That is the entire algorithm. No traversal, no loop, no searching — just one pointer reassignment. This is what makes deleting the head the **fastest possible mutation** you can perform on a linked list.

---

# 2. Core Linked List Idea

Consider:

```text
10 -> 20 -> 30 -> NULL
```

The `head` pointer is simply a variable that stores the address of the first node. To "delete" the head, we do not touch node `10` at all — we just point `head` somewhere else.

```text
Before:

head
 |
 v
10 -> 20 -> 30 -> NULL


After:

        head
         |
         v
10      20 -> 30 -> NULL
```

Node `10` still physically exists for an instant, but nothing in the list points to it anymore, and no variable references it. It becomes unreachable and is garbage collected. The list, as far as anyone can observe, now starts at `20`.

---

# 3. Most Important Edge Case

## Case A — Empty List

```text
head = None
```

There is nothing to delete. Attempting `head.next` here would crash with a null-pointer/attribute error.

```text
if head is None:
    return None
```

## Case B — Single-Node List

```text
5 -> NULL
```

After deleting the head:

```text
head = head.next
head = None
```

The list becomes completely empty. This is a valid and expected outcome, not an error — "deleting the head" of a one-element list simply empties the list.

## Case C — General List

```text
10 -> 20 -> 30 -> NULL
```

`head.next` is guaranteed to exist, so the move is always safe once the empty-list case is handled.

The only real edge case to guard against is the empty list. Everything else falls out naturally from `head = head.next`.

---

# 4. Approach 1 — Brute Force Thinking

It is worth asking: is there even a "slower" way to do this, and why would it be worse?

A brute-force mindset might do:

1. Traverse the entire list and copy every value into an array.
2. Drop the first element of the array.
3. Rebuild a brand-new linked list from the remaining values.
4. Return the new list's head.

```text
Linked List:
10 -> 20 -> 30 -> NULL

Convert to array:
[10, 20, 30]

Drop first element:
[20, 30]

Rebuild:
20 -> 30 -> NULL
```

### Why this is a bad idea here

This approach touches **every single node** just to remove the first one:

```text
Time  = O(n)   — traverse + rebuild
Space = O(n)   — new array + new nodes
```

Compare that to the optimal approach, which needs:

```text
Time  = O(1)
Space = O(1)
```

There is no partial credit for this in an interview — rebuilding the whole list to drop one element from the front is a clear signal that the candidate has not recognized that they already hold a direct reference to the node being removed. Unlike "delete at position `x`," there is no search step to justify any traversal at all.

---

# 5. Optimal Approach — Direct Pointer Move

Since `head` already refers to the exact node we want to remove, deletion is a single reassignment:

```python
head = head.next
```

## Why no other node needs to change

In a singly linked list, links only point **forward**:

```text
10 -> 20 -> 30
```

Node `20` does not know that `10` points to it. No node anywhere in the list holds a backward reference to the head. So when we move `head` to point at `20` instead of `10`, **no other node's `next` pointer needs to be touched** — none of them were pointing at `10` in the first place except the `head` variable itself.

This is fundamentally different from deleting a middle or last node, where some node `X` has `X.next` pointing at the target, and `X.next` must be rewritten to skip over it. For the head, the only "pointer" that ever referenced it was `head`, and that is exactly the one we update.

## Why this is O(1)

- No traversal — the node is already known.
- No searching for a "previous" node — none exists to update.
- A single reference reassignment — constant work regardless of list size, whether the list has 3 nodes or 3 million.

---

# 6. Pointer Movement

```text
Before:

head
 |
 v
10 -> 20 -> 30 -> NULL


Operation:

head = head.next


After:

       head
        |
        v
10     20 -> 30 -> NULL
```

Only the `head` reference moved. Every other pointer in the list (`20.next -> 30`, `30.next -> NULL`) is untouched.

---

# 7. Algorithm

### Step 1

If the list is empty (`head is None`), return `None` — there is nothing to delete.

### Step 2

Otherwise, move the head pointer forward by one node:

```text
head = head.next
```

### Step 3

Return the new `head`.

---

# 8. Optimal Python Solution

```python
class Solution:

    # This function deletes the head node of the linked list.
    def deleteHead(self, head):

        # If the linked list is empty, there is no head to delete.
        if head is None:

            # Return None since the list stays empty.
            return None

        # Move the head pointer to the second node,
        # which disconnects the original head from the list.
        head = head.next

        # Return the new head of the list.
        return head
```

---

# 9. Complete Dry Run

Input:

```text
10 -> 20 -> 30 -> NULL
```

## Before

```text
head
 |
 v
10 -> 20 -> 30 -> NULL
```

`head` is not `None`, so we proceed.

```python
head = head.next
```

`head.next` is node `20`, so:

```text
head = 20
```

## After

```text
      head
       |
       v
10    20 -> 30 -> NULL
```

Returned list:

```text
20 -> 30 -> NULL
```

Node `10` is no longer reachable from anywhere and is discarded.

---

# 10. Dry Run — Single-Node List

Input:

```text
5 -> NULL
```

## Before

```text
head
 |
 v
5 -> NULL
```

`head` is not `None`, so we proceed.

```python
head = head.next
```

Since `5.next = None`:

```text
head = None
```

## After

```text
head = None
```

Returned list:

```text
NULL   (empty list)
```

The list correctly becomes empty — there is no special-case branch needed for this; `head.next` on the last node is naturally `None`.

---

# 11. Complexity Analysis

```text
Time Complexity  = O(1)
Space Complexity = O(1)
```

There is no loop, no recursion, and no auxiliary data structure. Exactly one pointer read (`head.next`) and one pointer write (`head = ...`) happen, regardless of whether the list has 1 node or 10 million nodes.

This is the **fastest possible operation** you can perform on a linked list — it is the baseline against which every other linked-list mutation (which usually requires at least some traversal) is compared.

---

# 12. Why This Is Optimal

You cannot do better than `O(1)` here, because:

- The node to be removed (`head`) is already known — no search is required.
- Only one reference needs updating (`head` itself) — there is no "previous node" whose pointer must be rewritten, since nothing in the list points backward to the head.
- Any correct solution must at least read and write the `head` reference once, so `O(1)` is also the theoretical lower bound.

Contrast this with deleting the **last** node of a singly linked list, which requires walking all the way to the second-to-last node just to update its `next` pointer — an unavoidable `O(n)` because that node's location isn't known in advance.

---

# 13. Common Mistakes

## Mistake 1 — Not Checking for an Empty List

```python
def deleteHead(self, head):
    return head.next
```

If `head` is `None`, then `head.next` crashes with an `AttributeError`. Always guard against the empty list first.

---

## Mistake 2 — Returning the Old Head

```python
def deleteHead(self, head):
    if head is None:
        return None
    new_head = head.next
    return head   # wrong — this returns the node we just deleted
```

The whole point of the operation is to return the **new** head, not the one that was removed.

---

## Mistake 3 — Unnecessarily Traversing the List

```python
def deleteHead(self, head):
    current = head
    while current.next is not None:
        current = current.next
    return head.next
```

This walks the entire list for no reason before doing the same one-line operation. Deleting the head needs zero traversal — resist the instinct to "find" something that is already given to you.

---

## Mistake 4 — Manually Clearing the Old Head's `next`

```python
def deleteHead(self, head):
    if head is None:
        return None
    old_head = head
    head = head.next
    old_head.next = None   # unnecessary
    return head
```

There is no need to null out the old head's `next` pointer. Once nothing references `old_head`, it is unreachable and will be cleaned up regardless of what its `next` still points to.

---

# 14. Visual Cheat Sheet

## Delete Head — General List

```text
Before:

head
 |
 v
10 -> 20 -> 30

Operation:

head = head.next

After:

      head
       |
       v
      20 -> 30
```

## Delete Head — Single Node

```text
Before:

head
 |
 v
5 -> NULL

Operation:

head = head.next

After:

head = None   (empty list)
```

## Delete Head — Empty List

```text
Before:

head = None

Operation:

(nothing to do)

After:

head = None
```

---

# 15. Interview Explanation in 30 Seconds

> Since I'm already given a direct reference to the head node, there's no node to search for and no "previous" node to update — the head has none. I just check whether the list is empty, and if not, move the head reference forward by one: `head = head.next`. This is `O(1)` time and `O(1)` space, the fastest possible mutation on a linked list.

---

# 16. Interviewer Follow-Up Questions

## Q1. Why is this `O(1)` but deleting the last node is `O(n)`?

Deleting the head requires updating only the `head` reference, which we already hold. Deleting the last node requires updating the `next` pointer of the **second-to-last** node, and the only way to reach it in a singly linked list is to traverse from the head — an unavoidable `O(n)` walk.

---

## Q2. How would a doubly linked list change this?

The operation is still `O(1)`, but there is slightly more to update:

```text
head = head.next
if head is not None:
    head.prev = None
```

You must also clear the new head's `prev` pointer, since it previously pointed backward to the deleted node. In a singly linked list this step doesn't exist because there is no `prev` pointer at all.

---

## Q3. What if you're given just a `Node` reference with no external `head` variable — how do you "delete" the head?

If you truly have no way to update the caller's head pointer (for example, the caller only passed the node by value and holds their own reference), you cannot delete it in the usual sense — you can only overwrite its contents by copying the next node's data into it and skipping over the next node:

```python
head.val = head.next.val
head.next = head.next.next
```

This is the classic "delete node given only that node" trick, and it fails only when the node given actually is the tail. In the standard version of this problem, though, we are given (and can reassign) the `head` variable itself, so the simple `head = head.next` suffices.

---

## Q4. How does this compare to an array's remove-first operation, which is `O(n)`?

In an array, removing the first element requires shifting every remaining element one position to the left to keep the array contiguous:

```text
[10, 20, 30, 40]   remove index 0
 ^
 shift everything left

[20, 30, 40]
```

That shift costs `O(n)`. A linked list has no contiguity constraint — nodes are connected purely by pointers, so moving the head reference forward touches nothing else. This is one of the classic reasons linked lists are preferred when frequent insertions/deletions at the front are required.

---

# 17. Important Comparison — Array vs Linked List

| Operation | Array (`pop(0)`) | Singly Linked List (`delete head`) |
|---|---:|---:|
| Remove first element | `O(n)` — shifts all remaining elements | `O(1)` — move one pointer |
| Extra space | `O(1)` | `O(1)` |
| Reason for cost | Contiguous memory must stay packed | Nodes connected by pointers, no packing needed |

This is one of the most quoted interview talking points in favor of linked lists:

> "If your workload does a lot of insert/delete at the front, a linked list beats an array — array removal-from-front is `O(n)` due to shifting, while linked-list head deletion is `O(1)`."

---

# 18. Pattern Recognition

The general principle behind this problem generalizes far beyond linked lists:

> If an operation only touches a node you **already have direct access to**, and does not require finding a "previous" or "neighboring" node first, it is `O(1)`.

Examples of this pattern:

- Deleting the head of a linked list — you already hold `head`.
- Pushing/popping from the top of a stack — you already hold the top pointer.
- Inserting right after a given node — you already have that node's reference.

The moment an operation requires "find the node before/after this one" in a structure that cannot be traversed backward, that search becomes the dominant cost — usually `O(n)`. Recognizing which category a problem falls into is often the fastest way to spot the correct time complexity before writing any code.

---

# 19. Final Solution

```python
class Solution:

    # This function deletes the head node of the linked list.
    def deleteHead(self, head):

        # If the linked list is empty, there is no head to delete.
        if head is None:

            # Return None since the list stays empty.
            return None

        # Move the head pointer to the second node,
        # which disconnects the original head from the list.
        head = head.next

        # Return the new head of the list.
        return head
```

---

# 20. Interview Takeaways

```text
1. Deleting the head needs no traversal at all.

2. There is no "previous" node before the head — that
   is exactly why it's O(1) instead of O(n).

3. The entire operation is one line:

   head = head.next

4. A single-node list correctly becomes None; no
   special-case branch is needed for it.

5. Always guard against an already-empty list before
   touching head.next.

6. Return the NEW head, never the old one.

7. Time  = O(1)
   Space = O(1)
```

The key sentence to remember is:

> **Deleting the head of a linked list requires no search, because you already hold the only reference that ever pointed to it — you simply move that reference forward.**

---

## Related Problems to Practice

After this problem, practice these linked-list patterns:

1. Delete at a given position in a linked list.
2. Delete the last node of a linked list.
3. Delete a node given only that node (no head access).
4. Remove N-th node from the end.
5. Delete middle node of a linked list.
6. Reverse a linked list.
7. Insert a node at the head (the inverse operation).
8. Remove duplicates from a sorted linked list.

These problems build directly on the same pointer-manipulation fundamentals — in particular, recognizing which node's pointer must change, and when no such search is needed at all.
