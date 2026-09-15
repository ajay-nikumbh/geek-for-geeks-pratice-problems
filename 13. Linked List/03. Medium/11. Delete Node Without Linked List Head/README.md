# Delete Node Without Linked List Head

| Field | Value |
|---|---|
| Topic | Linked List |
| Difficulty | Medium |
| Submissions | 228,637 |
| Accuracy | 78.57% |
| Companies | Amazon, Microsoft, Samsung, Visa, Goldman Sachs, Kritikal Solutions |
| Related Tags | Linked List |
| Problem Link | [https://www.geeksforgeeks.org/problems/delete-without-head-pointer/1](https://www.geeksforgeeks.org/problems/delete-without-head-pointer/1) |

## Problem Statement

You are given a **pointer to a node** that needs to be deleted from a **singly linked list**.

You do **not** have access to the **head** of the linked list.

You must delete the given node from the list. It is **guaranteed** that the node to be deleted is **not the last node** of the list.

You do not need to return anything — the node's identity in the list must simply cease to exist by the time your function finishes.

### Example 1

```text
List:            A -> B -> C -> D -> NULL

Given pointer:   pointer to B (not head, no access to A)
```

After "deleting" `B`, the list should behave as:

```text
A -> C -> D -> NULL
```

### Example 2

```text
List:            10 -> 20 -> 30 -> 40 -> NULL

Given pointer:   pointer to 20
```

After deletion:

```text
10 -> 30 -> 40 -> NULL
```

---

# 1. Interview Intuition

This is one of the most famous "trick" questions in linked-list interviews, and it is worth slowing down on.

Normally, to delete a node from a singly linked list, we do this:

```text
previous.next = current.next
```

That single line requires **one thing**: a pointer to the node **before** the one we want to delete.

But here is the catch in this problem:

> We are not given the head. We are not given any way to walk backward. We are only given a pointer to the node itself.

```text
A -> B -> C -> D -> NULL
     ^
     |
   given pointer (node to delete)
```

In a **singly** linked list, a node only knows about what comes **after** it via `node.next`. It has **no** `previous` pointer. So from `B`, we can reach `C` and `D`, but we can **never** reach `A`.

If we cannot reach `A`, we cannot execute:

```text
A.next = C
```

because we simply do not have a variable that refers to `A`. This looks like a dead end.

### The trick

Since we cannot **remove** the given node from the chain (because we can't touch the link pointing into it), we do something completely different:

> We don't delete the node we were given. Instead, we overwrite its data with the next node's data, and then delete the **next** node instead — which we *do* have a pointer to.

In other words, `B` "impersonates" `C`. Once `B` holds `C`'s value and points to whatever `C` used to point to, nobody outside can tell the difference between "we deleted B" and "we deleted C and renamed B to C."

```text
Before:
A -> B(20) -> C(30) -> D(40) -> NULL

Step 1 — copy C's data into B:
A -> B(30) -> C(30) -> D(40) -> NULL

Step 2 — bypass C:
A -> B(30) --------> D(40) -> NULL

Viewed from A, the list now reads:
A -> 30 -> 40 -> NULL
```

The node object that used to be called `C` is thrown away instead of `B`. But since we never had a way to distinguish "the object called B" from "the value 20" from the outside, nobody can tell the difference — the **sequence of values** is exactly what we wanted.

This is the entire trick. It converts an "impossible without head" problem into an `O(1)` pointer operation.

---

# 2. Core Linked List Idea

Let's visualize this precisely with four nodes:

```text
A -> B -> C -> D -> NULL
```

We are given a pointer to `B`. We do not have `A`.

### Step 1 — Copy `C`'s value into `B`

```text
Before:

A --> [B: 20] --> [C: 30] --> [D: 40] --> NULL


Copy C.data into B.data:

A --> [B: 30] --> [C: 30] --> [D: 40] --> NULL

(B now holds C's value, but the pointers haven't changed yet)
```

### Step 2 — Bypass `C` by relinking `B.next`

```text
B.next = C.next

A --> [B: 30] -------------> [D: 40] --> NULL

                [C: 30]   <-- orphaned, no longer reachable
```

### Result

From `A`'s perspective — and from anyone traversing the list from the head — the list now reads:

```text
A -> 30 -> 40 -> NULL
```

which is functionally identical to `A -> C -> D`. The node object we physically removed was `C`, but the **value** that disappeared from the sequence was `B`'s original value (`20`). That's exactly the deletion we were asked to perform.

---

# 3. Most Important Edge Case — The Node to Delete Is the Last Node

This trick has exactly one fatal weakness: it requires a **next node** to copy from.

```text
A -> B -> C -> NULL
              ^
              |
     given pointer (last node)
```

Here, `C.next` is `None`. There is no node after `C` whose value we can copy in. We cannot do:

```text
node.data = node.next.data   # crashes: node.next is None
```

**The problem statement explicitly guarantees this case will never occur** — "the node to be deleted is not the last node." That guarantee is not a minor detail; it is what makes this problem solvable at all.

### Why is it truly impossible in general?

If you are given *only* a pointer to the last node, and *no* head, there is **no way** to delete it:

- You cannot reach the second-to-last node (no backward pointers).
- You cannot copy data from the next node (there isn't one).
- Setting `node = None` only reassigns your **local variable** — the actual second-to-last node's `.next` still points to the original node object, so the list is unchanged.

This is a classic interviewer follow-up: *"What if it's the last node?"* The honest answer is:

> Without a reference to the previous node or the head, deleting the true last node is **impossible** using only a pointer to that node. That's precisely why the problem guarantees it won't happen.

---

# 4. Approach 1 — "Brute Force" Thinking

Normally, a brute-force section explores an inefficient-but-workable alternative. Here, that section looks unusually short, and that's the whole point of teaching this problem.

**If you had the head**, the "obvious" (if unoptimized) approach would be:

1. Start `previous = head`.
2. Traverse forward, comparing each node to the target node (by reference or by value), until `previous.next == target`.
3. Once found: `previous.next = target.next`.

```text
head -> A -> B -> C -> D -> NULL
                  ^
                  |
               target

Traverse: head, A, B ... until previous.next is C
previous = B
previous.next = target.next = D

Result: A -> B -> D
```

That approach costs `O(n)` time because you must **search** for the previous node.

**But in this problem, you don't have `head` at all.** There is no list to traverse, no starting point to search from, and no way to "look for" the previous node — it is fundamentally unreachable. There is no array-copy trick, no two-pointer trick, no recursion trick that can conjure a reference to `A` out of nothing.

> In the traditional sense, there is **no brute force** for this problem. Either you know the copy-and-bypass trick, or the problem is unsolvable with the given information.

This absence of a fallback is exactly why this question separates candidates who have seen the trick from those who haven't — there's no partial credit for "traversing slowly."

---

# 5. Optimal Approach — Copy-and-Bypass Trick

Since there is only one viable technique, let's state it with full precision.

Given `node` (the node to delete, guaranteed to have a valid `node.next`):

```python
node.data = node.next.data
node.next = node.next.next
```

That's it — two lines, no traversal, no head required.

### Why this works

- Line 1 makes `node` **look like** its successor from a value standpoint.
- Line 2 removes the actual successor node from the chain, since we *do* have a direct reference to it via `node.next`.
- The node we truly deallocate (the former `node.next`) is one we can always reach — we never needed `head` for it in the first place.

---

# 6. Pointer Movement

Two distinct micro-steps happen — let's separate them completely.

### Step A — The Copy (data only, pointers untouched)

```text
Before:

... -> [node: 20] -> [next: 30] -> [next.next: 40] -> ...


node.data = node.next.data


After copy:

... -> [node: 30] -> [next: 30] -> [next.next: 40] -> ...

(two nodes now hold the same value "30" — nothing has been
 unlinked yet, this step ONLY changes a data field)
```

### Step B — The Bypass (pointer only, no more data changes)

```text
node.next = node.next.next


Before:

[node: 30] --> [next: 30] --> [next.next: 40]


After:

[node: 30] ---------------->  [next.next: 40]

              [next: 30]   <-- unreachable, garbage collected
```

Combining both steps, the net visible effect on the list is that the value `20` (originally in `node`) has vanished from the sequence, exactly as if `node` itself had been unlinked.

---

# 7. Algorithm

### Step 1

Confirm (per problem guarantee) that `node.next` is not `None` — i.e., `node` is not the last node.

### Step 2

Copy the value from the next node into the current node:

```text
node.data = node.next.data
```

### Step 3

Bypass the next node by relinking `node.next` to skip over it:

```text
node.next = node.next.next
```

### Step 4

Done. No return value is needed — the mutation is in place and visible to anyone still holding the head.

---

# 8. Optimal Python Solution

```python
class Solution:

    # This function deletes the given node from the linked list.
    # We are NOT given the head, only a pointer to this node.
    # It is guaranteed that this node is not the last node.
    def deleteNode(self, node):

        # We cannot reach the previous node, so we cannot unlink
        # this node directly. Instead, we copy the next node's
        # value into this node, making this node "become" its successor.
        node.data = node.next.data

        # Now that this node holds the next node's value, we bypass
        # the actual next node by pointing directly to what it pointed to.
        # This removes the (now duplicate) next node from the chain.
        node.next = node.next.next

        # No return is required — the list is mutated in place,
        # and the change is visible from the original head reference.
```

---

# 9. Complete Dry Run

Consider:

```text
A(10) -> B(20) -> C(30) -> D(40) -> NULL
```

We are given a pointer to node `B`, holding value `20`. We do **not** have access to `A`.

### Initial State

```text
A(10) -> B(20) -> C(30) -> D(40) -> NULL
          ^
          |
    given pointer "node"
```

### Step 1 — Copy `node.next.data` into `node.data`

```text
node.next.data = C.data = 30

node.data = 30
```

State after Step 1:

```text
A(10) -> B(30) -> C(30) -> D(40) -> NULL
```

`B` now holds the value `30`. Both `B` and `C` currently store `30` — this is a transient state, not the final answer.

### Step 2 — Bypass `node.next`

```text
node.next = node.next.next
          = C.next
          = D
```

State after Step 2:

```text
A(10) -> B(30) -------------> D(40) -> NULL

                  C(30)   <-- unreachable
```

### Final List (as seen from `A`, which we never touched)

```text
10 -> 30 -> 40 -> NULL
```

This is exactly what we wanted: the value `20` is gone, and the sequence reads as if `B` had been truly deleted.

---

# 10. Complexity Analysis

Let:

```text
n = number of nodes in the list
```

We perform:

```text
node.data = node.next.data     # O(1)
node.next = node.next.next     # O(1)
```

No traversal happens at all — not even a single step.

```text
Time Complexity  = O(1)
Space Complexity = O(1)
```

### Final Complexity

| Metric | Complexity |
|---|---|
| Time | `O(1)` |
| Extra Space | `O(1)` |

---

# 11. Why This Is Optimal

Here is the paradox that makes this problem famous:

> Having **less** information (no head) still lets us solve this in `O(1)` — which is actually **better** than the `O(n)` you'd need if you *did* have the head and had to find the previous node by searching.

If you had the head and wanted to delete a node by reference, you would normally need to:

1. Traverse from `head`.
2. Compare each node against the target (by reference).
3. Stop at the node right before it.
4. Relink.

That is `O(n)` in the worst case, because "finding the previous node" is inherently a search problem in a singly linked list.

But in this problem, we sidestep the search entirely. We don't need the previous node — we only need the **next** node, which is always one hop away regardless of list size. That's why the "obvious" `O(n)` approach isn't just suboptimal here, it isn't even *available* (no head to start from) — and the trick that replaces it happens to be **strictly faster**, at `O(1)`.

This is a rare case in interviews where removing information (the head) doesn't make the problem harder — it forces a different technique that turns out to be more efficient.

---

# 12. Common Mistakes

## Mistake 1 — Writing `node = node.next`

This is the single most common wrong instinct, and it deserves a full explanation.

```python
def deleteNode(self, node):
    node = node.next   # WRONG — does nothing useful
```

### Why this fails

In Python (and Java, and most languages), `node` is a **local variable** that holds a *reference* to a node object. When you write `node = node.next`, you are only changing **what the local variable points to** — you are not changing any node's `.next` field.

```text
Before the call:

A --------> [node: 20] --------> [next: 30] --------> [next.next: 40]
                 ^
                 |
      the caller's node reference AND our local
      parameter "node" both point to this same object


Inside the function: node = node.next


After the assignment:

A --------> [node: 20] --------> [next: 30] --------> [next.next: 40]
                 ^                     ^
                 |                     |
       caller's reference       our LOCAL "node" now
       still points HERE        points here instead

(Nothing about the actual linked list changed. A.next
 still points to the original 20-node. Our reassignment
 was invisible outside this function.)
```

The key insight: **the caller's reference to the original node object is untouched.** `A.next` never stopped pointing at the object holding `20`. We just made our own local variable "look away" from it — the list itself is exactly as it was before the function was called. When the function returns, the local variable is discarded, and the list still contains the node we were "trying" to delete.

This is the classic pitfall of **reference semantics**: reassigning a variable never mutates the object it used to point to, and never affects other variables (or fields) that still hold the old reference.

The correct trick instead **mutates the object itself** (`node.data = ...`, `node.next = ...`), which every reference to that same object will observe — including `A.next`.

## Mistake 2 — Assuming this works for the last node

```python
node.data = node.next.data   # crashes if node.next is None
```

If `node` is the last node, `node.next` is `None`, and `node.next.data` raises an `AttributeError`. Always remember: this trick is only valid because the problem guarantees the node is not the last one.

## Mistake 3 — Trying to also update `head` or return something

There is no `head` in scope, and typically this function is not expected to return anything (`void`/`None`). Don't add unnecessary return statements or try to "reconstruct" the head — the mutation happens in place and is visible to whoever holds the actual head reference.

## Mistake 4 — Copying only the value but forgetting to relink `next`

```python
node.data = node.next.data
# forgot: node.next = node.next.next
```

If you stop here, the old "next" node is still in the list — you've just created a **duplicate value**, not removed a node. Both steps are mandatory.

---

# 13. Visual Cheat Sheet

## The Trick, End to End

```text
Before:

... -> [node: X] -> [succ: Y] -> [rest...]


Copy:  node.data = succ.data

... -> [node: Y] -> [succ: Y] -> [rest...]


Bypass:  node.next = succ.next

... -> [node: Y] ----------------> [rest...]

                    [succ: Y]  <-- discarded
```

## Why `node = node.next` Fails

```text
Caller's list:  A -> [node] -> [next] -> ...

Wrong: node = node.next
       (only rebinds the LOCAL variable, A.next unchanged)

Caller's list is UNCHANGED:  A -> [node] -> [next] -> ...
```

## The Forbidden Move (No Head)

```text
A -> [node] -> [next] -> ...

We want:  A.next = next     <-- IMPOSSIBLE, we have no reference to A
```

---

# 14. Interview Explanation in 30 Seconds

A strong interview explanation would be:

> Since I don't have the head, I can't reach the node before the one I need to delete, so I can't relink its `next` pointer directly. Instead, I copy the value from the next node into the given node, and then set the given node's `next` to skip over that next node. Effectively, the given node "becomes" its successor, and I delete the successor instead, which I *can* reach. This runs in `O(1)` time and space, and it only works because the problem guarantees the node isn't the last one — if it were, there'd be no next node to copy from, and the problem would be unsolvable with just this pointer.

---

# 15. Interviewer Follow-Up Questions

## Q1. Why can't you just do `node = node.next`?

Because that only reassigns the **local variable** `node` to point to a different object. It does not modify any `.next` field in the actual list, so the node the caller is holding a reference to (via `A.next`, or however they reached it) is completely unaffected. Mutation, not reassignment, is required — see Mistake 1 above.

## Q2. What if the node to delete is the last node — can this be solved at all?

No — not with only a pointer to that node. There is no next node to copy from, and no way to reach the previous node. The only way to genuinely support this case is to be given the head (or a previous pointer, or use a doubly linked list). That's precisely why the problem guarantees the node given is never the last one.

## Q3. Does this work for a doubly linked list?

You wouldn't need this trick at all in a doubly linked list — you'd have direct access to `node.prev`, so you could simply do `node.prev.next = node.next` and `node.next.prev = node.prev` (with edge handling for the ends). The whole reason this trick exists is the *singly* linked list's lack of a backward pointer.

## Q4. What if there are other references to this node elsewhere in the program relying on its identity?

This is the sharpest follow-up. The trick changes the **identity** of the object that ends up "representing" the deleted value's old neighbor slot — it does not preserve object identity, only value sequence. If some other part of the program was holding a separate reference to the *original* `node` object expecting it to keep behaving as "the node after X," that reference now sees updated data (belonging to the former next node) rather than being genuinely removed. Similarly, any external reference to the old *next* node object becomes stale/dangling from the list's perspective, even though that object still exists in memory until garbage collected. In short: the trick is safe for value-based traversal, but it breaks any code that depends on **node identity** rather than node **position/value**.

## Q5. Is this technique used anywhere else, like in tree deletion?

Yes — this is the same underlying idea used in **BST (Binary Search Tree) deletion** when removing a node with two children: instead of trying to detach the node directly (which would require re-wiring several subtrees), you copy the value of the **in-order successor** (or predecessor) into the node, and then delete that successor node instead, which is structurally easier to remove (it has at most one child). It's the same principle: *"When you can't easily unlink a node directly, copy the next thing's value into it and delete that other, easier-to-remove node instead."*

---

# 16. Comparison Table

| Scenario | Requires Head? | Time | Space | Notes |
|---|---|---|---|---|
| Normal deletion (has head, has previous pointer) | Yes | `O(n)` | `O(1)` | Must traverse to find the previous node |
| Delete without head (copy-and-bypass trick) | No | `O(1)` | `O(1)` | Works only if the node has a valid `next` |
| Delete without head, node is the last node | No | Impossible | — | No next node to copy from; unsolvable with only this pointer |
| Doubly linked list, any node, no head | No | `O(1)` | `O(1)` | Trivial via `node.prev` / `node.next`, no trick needed |

The crucial caveat under the second row: **the trick only works when there is a next node**. Without that guarantee, the elegant `O(1)` solution simply does not exist.

---

# 17. Pattern Recognition

This problem is a specific instance of a much broader and very common interview pattern:

> **Value-copy deletion**: when you cannot cleanly unlink a node/element directly (because you lack a needed reference or the relinking is structurally awkward), copy the *identity/value* of an adjacent, easier-to-remove element into the current one, and delete that adjacent element instead.

You'll see this exact idea resurface in:

- **BST deletion** (two-children case): copy the in-order successor's value into the node, then delete the successor.
- **Deleting a node from a singly linked list without head access** (this problem).
- Certain **union-find / linked structure compaction** tricks, where a "placeholder" absorbs a neighbor's identity to avoid re-pointing many external references.

Whenever you find yourself unable to reach the "owner" of the pointer you need to change, ask:

```text
"Can I instead copy the NEXT thing's value into the CURRENT slot,
 and delete the next thing, which I CAN reach?"
```

If yes, you've found an `O(1)` trick instead of a traversal.

---

# 18. Final Solution

```python
class Solution:

    # This function deletes the given node from the linked list.
    # We are NOT given the head, only a pointer to this node.
    # It is guaranteed that this node is not the last node.
    def deleteNode(self, node):

        # We cannot reach the previous node, so we cannot unlink
        # this node directly. Instead, we copy the next node's
        # value into this node, making this node "become" its successor.
        node.data = node.next.data

        # Now that this node holds the next node's value, we bypass
        # the actual next node by pointing directly to what it pointed to.
        # This removes the (now duplicate) next node from the chain.
        node.next = node.next.next

        # No return is required — the list is mutated in place,
        # and the change is visible from the original head reference.
```

---

# 19. Interview Takeaways

Remember these points:

```text
1. Without head access, you cannot relink the previous node's pointer.

2. The only viable technique: copy the NEXT node's data into the
   current node, then bypass the next node.

   node.data = node.next.data
   node.next = node.next.next

3. This trick REQUIRES a valid next node — it fails for the last node,
   which is why the problem guarantees that case never occurs.

4. Never write "node = node.next" expecting it to delete anything —
   that only rebinds a local variable, it does not mutate the list.

5. This runs in O(1) time and O(1) space — faster than the O(n)
   traversal you'd need even WITH head access.

6. The same "copy value, delete the easier node" idea appears in
   BST deletion (copying the in-order successor).
```

The key sentence to remember is:

> **When you can't unlink the node you have, make it become the node you can reach — then delete that one instead.**

---

## Related Problems to Practice

After this problem, practice these linked-list and tree-deletion patterns:

1. Delete a node at a given position (with head access).
2. Delete the head node of a linked list.
3. Remove the N-th node from the end of a linked list.
4. Delete the middle node of a linked list.
5. Delete a node in a doubly linked list.
6. Delete a node in a Binary Search Tree (two-children case).
7. Reverse a linked list.
8. Detect and remove a cycle in a linked list.
9. Merge two sorted linked lists.
10. Remove duplicates from a sorted linked list.

These problems reinforce the same core lesson: in linked structures, deletion is really about deciding **which pointer must change**, and sometimes the cleverest answer is to change a different node than the one you were asked to remove.
