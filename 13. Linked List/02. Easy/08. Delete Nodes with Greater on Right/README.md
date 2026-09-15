# Delete Nodes with Greater on Right

> **Topic:** Linked List  
> **Difficulty:** Easy  
> **Submissions:** 163,868  
> **Accuracy:** 35.51%  
> **Companies:** Amazon  
> **Related Tags:** Linked List  
> **Problem Link:** https://www.geeksforgeeks.org/problems/delete-nodes-having-greater-value-on-right/1  

---

## Problem Statement

Given the head of a **singly linked list**, delete every node which has **some node with a greater value anywhere to its right**.

In other words, keep a node only if it is **greater than or equal to every node that comes after it**. Return the head of the modified linked list.

### Example 1

```text
Input:  12 -> 15 -> 10 -> 11 -> 5 -> 6 -> 2 -> 3 -> NULL

Output: 15 -> 11 -> 6 -> 3 -> NULL
```

Explanation:

- `12` has `15` to its right → delete.
- `15` has nothing bigger to its right → keep.
- `10` has `11` to its right → delete.
- `11` has nothing bigger to its right → keep.
- `5` has `6` to its right → delete.
- `6` has nothing bigger to its right → keep.
- `2` has `3` to its right → delete.
- `3` is the last node → keep.

### Example 2

```text
Input:  1 -> 2 -> 3 -> 4 -> NULL

Output: 4 -> NULL
```

Explanation: The list is strictly increasing, so every node except the last one has something bigger to its right. Only the final node, `4`, survives.

---

# 1. Interview Intuition

The problem statement sounds like "look ahead" logic:

> For every node, check whether anything bigger exists further down the list.

In an array this would be trivial — index forward and peek at later indices. But this is a **singly linked list**, and we already know the golden rule:

> A node only knows about the node **after** it through `next`. It has no way to look at "everything to its right" without walking through it.

If we tried to solve this the direct way, for every node we would need to walk the *rest* of the list to check whether a bigger value shows up. That works, but it is expensive.

The key realization is this:

> "Is there anything bigger to my right?" said **before** reversing the list becomes "Have I already seen anything bigger?" said **after** reversing the list and walking left to right.

Reversing a singly linked list flips the direction of traversal without needing random access. Once the list is reversed:

```text
Original: 12 -> 15 -> 10 -> 11 -> 5 -> 6 -> 2 -> 3
Reversed:  3 -> 2  -> 6  -> 5  -> 11 -> 10 -> 15 -> 12
```

Now walking the reversed list from left to right is exactly the same as walking the original list from **right to left**. At every step we can maintain a running maximum of everything we've seen so far (which, in original-list terms, is everything to the current node's right, including itself).

> **Core trick:** if a node's value is strictly less than the running maximum (built from the right side), it must be deleted, because that running maximum represents a bigger value that appears to its right in the original list.

This single trick converts an `O(n^2)` look-ahead problem into two linear passes: reverse, then filter using a running max (and reverse back if the original orientation must be preserved).

---

# 2. Core Linked List Idea

Visualize the transformation in three stages.

### Stage 1 — Original List

```text
12 -> 15 -> 10 -> 11 -> 5 -> 6 -> 2 -> 3 -> NULL
```

### Stage 2 — Reverse It

```text
3 -> 2 -> 6 -> 5 -> 11 -> 10 -> 15 -> 12 -> NULL
```

Now the *rightmost* elements of the original list are at the *front*.

### Stage 3 — Sweep Left to Right, Track Running Max

```text
node:      3    2    6    5    11    10    15    12
maxSoFar:  3    3    6    6    11    11    15    15
keep?      Y    N    Y    N    Y     N     Y     N
```

A node is kept only if its value is `>= maxSoFar` *before* updating `maxSoFar` with it (equivalently: it becomes the new maximum, so `value >= maxSoFar`).

Filtered reversed list:

```text
3 -> 6 -> 11 -> 15 -> NULL
```

### Stage 4 — Reverse Back to Restore Original Order

```text
15 -> 11 -> 6 -> 3 -> NULL
```

This matches the expected output exactly.

---

# 3. Most Important Edge Case — Strictly Increasing List

Consider:

```text
1 -> 2 -> 3 -> 4 -> NULL
```

Every node except the last has something bigger to its right (its immediate successor, in fact). So they all get deleted.

```text
Reversed: 4 -> 3 -> 2 -> 1

maxSoFar tracking:
node:      4    3    2    1
maxSoFar:  4    4    4    4
keep?      Y    N    N    N

Filtered reversed: 4

Reverse back: 4
```

> **Key insight:** the **rightmost (last) node always survives**, no matter what, because there is nothing to its right that could be bigger. Everything else is a candidate for deletion.

The opposite edge case — a strictly **decreasing** list, e.g. `9 -> 7 -> 5 -> 3` — results in **nothing being deleted**, since every node is already bigger than everything to its right. This is the sanity check that confirms the algorithm: when the list is already "non-increasing," the running-max sweep keeps every single node.

---

# 4. Approach 1 — Brute Force Thinking

The most direct translation of the problem statement:

1. For every node, scan all nodes strictly to its right.
2. If any of them has a greater value, mark the current node for deletion.
3. After scanning the whole list, remove all marked nodes in a second pass.

```text
List: 12 -> 15 -> 10 -> 11 -> 5 -> 6 -> 2 -> 3

For 12: scan [15, 10, 11, 5, 6, 2, 3] -> found 15 > 12 -> mark delete
For 15: scan [10, 11, 5, 6, 2, 3]     -> nothing bigger -> keep
For 10: scan [11, 5, 6, 2, 3]          -> found 11 > 10 -> mark delete
For 11: scan [5, 6, 2, 3]              -> nothing bigger -> keep
For 5:  scan [6, 2, 3]                 -> found 6 > 5 -> mark delete
For 6:  scan [2, 3]                    -> nothing bigger -> keep
For 2:  scan [3]                       -> found 3 > 2 -> mark delete
For 3:  scan []                        -> nothing bigger -> keep
```

### Brute Force Code

```python
class Solution:

    # Brute force: for every node, look ahead at every later node.
    def compute(self, head):

        # If the list is empty, there is nothing to do.
        if head is None:

            # Return the empty list unchanged.
            return None

        # Use a dummy node so head deletion is handled uniformly.
        dummy = Node(0)

        # Connect the dummy node to the original head.
        dummy.next = head

        # 'previous' will always trail just behind 'current'.
        previous = dummy

        # 'current' is the node we are currently deciding to keep or delete.
        current = head

        # Walk through every node in the list.
        while current is not None:

            # Assume, until proven otherwise, that nothing bigger exists to the right.
            found_greater = False

            # Look at every node strictly after 'current'.
            scanner = current.next

            # Scan the remainder of the list.
            while scanner is not None:

                # If we find a strictly greater value, mark this node for deletion.
                if scanner.data > current.data:

                    # Record that a bigger value was found.
                    found_greater = True

                    # No need to scan further; one bigger value is enough.
                    break

                # Move the scanner forward.
                scanner = scanner.next

            # If a bigger value was found to the right, delete 'current'.
            if found_greater:

                # Bypass 'current' from the list.
                previous.next = current.next

                # Advance current, but previous stays the same.
                current = current.next

            else:

                # Keep 'current'; advance both pointers.
                previous = current

                # Move to the next node.
                current = current.next

        # Return the (possibly new) head after all deletions.
        return dummy.next
```

### Dry Run (Brief)

```text
12 -> 15 -> 10 -> 11 -> 5 -> 6 -> 2 -> 3

12 deleted (15 is bigger)
10 deleted (11 is bigger)
5  deleted (6 is bigger)
2  deleted (3 is bigger)

Result: 15 -> 11 -> 6 -> 3
```

### Complexity

```text
Time  = O(n^2)   (for every node, scan the rest of the list)
Space = O(1)     (only pointers, no extra data structure)
```

This is correct, but for large lists the quadratic scanning is wasteful — we are re-deriving "what's the max to the right" over and over for overlapping suffixes.

---

# 5. Optimal Approach — Reverse + Track Max

The whole inefficiency of the brute force comes from repeatedly asking "what's the max of everything to my right?" for every node, from scratch.

Instead, compute that information **once**, in the natural direction it is easy to compute: **right to left**. Since we can't walk right to left directly, we reverse the list so that right-to-left in the original becomes left-to-right in the reversed list.

### Steps

1. **Reverse** the linked list in place — O(n) time, O(1) space.
2. **Traverse the reversed list left to right**, maintaining `max_so_far`, initialized to negative infinity (or the first node's value).
3. For each node:
   - If `node.data >= max_so_far`, this node survives. Update `max_so_far = node.data` and keep the node linked into the result.
   - If `node.data < max_so_far`, this node must be deleted (skip it, do not link it into the result).
4. **Reverse the filtered list back** to restore the original left-to-right order.
5. Return the new head.

### Why This Works

> After reversing, walking left to right visits nodes in the exact reverse order of the original list. So "the maximum of everything seen so far" in the reversed walk is precisely "the maximum of everything to the right (inclusive)" in the original list.

A node in the original list should be deleted exactly when some node to its right is strictly greater than it — equivalently, when the running maximum built from the right (inclusive of nodes after it) exceeds its own value. This is captured perfectly by comparing each reversed-traversal node against `max_so_far` computed *before* including that node.

### Pointer Logic During the Filtering Pass

We build a brand-new filtered list on the reversed list rather than physically deleting from the reversed list, because it keeps the pointer bookkeeping simple:

```text
result_head = None
result_tail = None
max_so_far  = -infinity

for node in reversed_list:
    if node.data >= max_so_far:
        max_so_far = node.data
        append node to result list
    else:
        discard node (do not append)
```

Since the reversed list is processed destructively (we already own its `next` pointers from the reversal step), we simply relink the surviving nodes into a new chain and cut the `next` pointer of any survivor's successor node before reassigning it, avoiding stale links.

---

# 6. Pointer Movement

Let's trace the running-max sweep on the reversed list step by step for:

```text
Reversed list: 3 -> 2 -> 6 -> 5 -> 11 -> 10 -> 15 -> 12 -> NULL
```

### Step-by-step

```text
Start: max_so_far = -infinity, result = empty

node = 3
  3 >= -infinity?  yes -> keep, max_so_far = 3
  result: 3

node = 2
  2 >= 3?  no -> delete
  result: 3

node = 6
  6 >= 3?  yes -> keep, max_so_far = 6
  result: 3 -> 6

node = 5
  5 >= 6?  no -> delete
  result: 3 -> 6

node = 11
  11 >= 6?  yes -> keep, max_so_far = 11
  result: 3 -> 6 -> 11

node = 10
  10 >= 11?  no -> delete
  result: 3 -> 6 -> 11

node = 15
  15 >= 11?  yes -> keep, max_so_far = 15
  result: 3 -> 6 -> 11 -> 15

node = 12
  12 >= 15?  no -> delete
  result: 3 -> 6 -> 11 -> 15
```

Filtered reversed list:

```text
3 -> 6 -> 11 -> 15 -> NULL
```

### Reverse Back

```text
15 -> 11 -> 6 -> 3 -> NULL
```

This is the final answer.

---

# 7. Algorithm

### Step 1

If the list is empty or has a single node, return it unchanged — there is nothing to its right that could be bigger.

### Step 2

Reverse the linked list using the standard three-pointer reversal (`prev`, `current`, `next_node`).

### Step 3

Initialize:

```text
max_so_far = reversed_head.data
result_head = reversed_head
result_tail = reversed_head
current = reversed_head.next
```

### Step 4

Walk `current` through the rest of the reversed list:

- If `current.data >= max_so_far`, append it to the result chain and update `max_so_far`.
- Otherwise, skip it (do not attach it; move on).

### Step 5

Terminate the result chain properly by setting `result_tail.next = None` once the walk finishes.

### Step 6

Reverse the filtered result list again to restore the original left-to-right order.

### Step 7

Return the new head.

---

# 8. Optimal Python Solution

```python
class Solution:

    # Standard helper: reverses a singly linked list and returns its new head.
    def reverse(self, head):

        # 'previous' starts as None because the new tail's next must be None.
        previous = None

        # Start walking from the head of the list.
        current = head

        # Continue until we fall off the end of the list.
        while current is not None:

            # Remember the next node before we overwrite the pointer.
            next_node = current.next

            # Reverse the pointer: current now points backward.
            current.next = previous

            # Move 'previous' forward to the node we just processed.
            previous = current

            # Move 'current' forward to the node we saved earlier.
            current = next_node

        # 'previous' now points to the new head of the reversed list.
        return previous

    # Main function: delete every node that has a greater node to its right.
    def compute(self, head):

        # An empty list or single-node list has nothing to delete.
        if head is None or head.next is None:

            # Return it unchanged.
            return head

        # Step 1: reverse the list so "right side" becomes "already visited".
        reversed_head = self.reverse(head)

        # Track the maximum value seen so far while sweeping left to right.
        max_so_far = reversed_head.data

        # The first node of the reversed list is always kept (nothing seen yet).
        result_head = reversed_head

        # 'result_tail' tracks the last node appended to the surviving chain.
        result_tail = reversed_head

        # Start scanning from the second node of the reversed list.
        current = reversed_head.next

        # Walk through the rest of the reversed list.
        while current is not None:

            # Save the next node before we potentially cut 'current' loose.
            next_node = current.next

            # If this node is at least as large as everything seen so far, keep it.
            if current.data >= max_so_far:

                # Update the running maximum.
                max_so_far = current.data

                # Attach this node to the surviving chain.
                result_tail.next = current

                # Advance the tail pointer to this node.
                result_tail = current

            # Otherwise, this node has something bigger to its right in the
            # original list, so it is simply skipped (not linked anywhere).

            # Move on to the next node in the reversed list.
            current = next_node

        # Terminate the surviving chain to avoid dangling old pointers.
        result_tail.next = None

        # Step 2: reverse the filtered list back to the original order.
        final_head = self.reverse(result_head)

        # Return the head of the final, filtered, correctly-ordered list.
        return final_head
```

---

# 9. Complete Dry Run

Input:

```text
12 -> 15 -> 10 -> 11 -> 5 -> 6 -> 2 -> 3 -> NULL
```

### Phase 1 — Reverse

```text
3 -> 2 -> 6 -> 5 -> 11 -> 10 -> 15 -> 12 -> NULL
```

### Phase 2 — Running Max Sweep

```text
max_so_far starts at 3 (the first node's value)
result_head = result_tail = node(3)

current = 2
  2 >= 3? no -> skip

current = 6
  6 >= 3? yes -> keep, max_so_far = 6
  result: 3 -> 6

current = 5
  5 >= 6? no -> skip

current = 11
  11 >= 6? yes -> keep, max_so_far = 11
  result: 3 -> 6 -> 11

current = 10
  10 >= 11? no -> skip

current = 15
  15 >= 11? yes -> keep, max_so_far = 15
  result: 3 -> 6 -> 11 -> 15

current = 12
  12 >= 15? no -> skip

Terminate: result_tail.next = None
```

Filtered reversed list:

```text
3 -> 6 -> 11 -> 15 -> NULL
```

### Phase 3 — Reverse Back

```text
15 -> 11 -> 6 -> 3 -> NULL
```

This matches the expected output `[15, 11, 6, 3]`.

---

# 10. Complexity Analysis

Let:

```text
n = number of nodes
```

### Time Complexity

```text
Reverse (first pass)        = O(n)
Running max sweep           = O(n)
Reverse back (second pass)  = O(n)
-----------------------------------
Total                       = O(n)
```

### Space Complexity

```text
Reversal uses a constant number of pointers (previous, current, next_node) = O(1)
The sweep uses a constant number of pointers (max_so_far, result_head/tail) = O(1)
No new nodes are allocated; we only relink existing nodes.
-----------------------------------------------------------
Total extra space = O(1)
```

### Final Complexity

| Metric | Complexity |
|---|---|
| Time | `O(n)` (two reversals + one sweep, all linear) |
| Extra Space | `O(1)` (in-place pointer manipulation) |

This is a massive improvement over the brute force's `O(n^2)` time for the same `O(1)` space.

---

# 11. Why This Is Optimal

Every node in the list must be **inspected at least once** to determine whether a bigger value exists to its right — there is no way around examining each element, so `O(n)` is an unavoidable lower bound for time.

> We cannot do better than `O(n)` because even confirming that the *last* node should be kept requires having visited it, and in the worst case (a strictly increasing list) essentially the entire list must be examined to determine the correct answer for the first node.

The reversal trick lets us compute "the running maximum from the right" using only forward traversal — which is the only kind of traversal a singly linked list supports — without needing:

- Extra arrays (`O(n)` space), or
- Repeated look-ahead scans (`O(n^2)` time), or
- A stack to simulate right-to-left processing (`O(n)` space).

Because reversal itself is `O(n)` time and `O(1)` space, and the filtering sweep is also `O(n)` time and `O(1)` space, doing this twice (reverse, then reverse back) still keeps the overall complexity at the optimal `O(n)` time and `O(1)` extra space — matching the theoretical lower bound in both dimensions.

---

# 12. Common Mistakes

## Mistake 1 — Trying to "Look Ahead" Without Reversing

A tempting but flawed idea is to somehow peek forward from each node without extra space. In a **singly** linked list this is fundamentally impossible without either:

- re-scanning the tail repeatedly (`O(n^2)` time), or
- using an auxiliary structure like a stack or array (`O(n)` space).

The reversal technique is what allows an `O(1)`-space, `O(n)`-time solution.

## Mistake 2 — Forgetting That the Last Node Always Survives

```text
Wrong assumption: "the last node might get deleted too."
```

The last node has nothing to its right, so it can never be deleted. In the algorithm, this is naturally guaranteed because it becomes the **first** node of the reversed list, and the first node always initializes `max_so_far`, so it is always kept.

## Mistake 3 — Off-by-One: Using `>` Instead of `>=`

```python
if current.data >= max_so_far:   # correct
if current.data > max_so_far:    # WRONG
```

If we use strict `>`, then when consecutive equal values appear (e.g., `5 -> 5`), the later one (in reversed order) would be incorrectly discarded even though it is tied for the maximum and there is nothing strictly greater than it to its right. Using `>=` correctly keeps a node when it *ties* the running maximum, matching the problem's requirement of deleting only nodes with something **strictly greater** to their right.

## Mistake 4 — Forgetting to Terminate the Filtered List

After the sweep, `result_tail.next` may still point to a node that was later discarded during the reversed traversal (since we never explicitly cleared it). Forgetting:

```python
result_tail.next = None
```

can leave a dangling pointer to a deleted node, corrupting the list before the second reversal.

## Mistake 5 — Reversing Only Once

Reversing but forgetting to reverse back leaves the answer in **reverse order** relative to what the problem expects. The two reversals are symmetric and both required.

---

# 13. Visual Cheat Sheet

## The Whole Pipeline

```text
Original:        12 -> 15 -> 10 -> 11 -> 5 -> 6 -> 2 -> 3

Reverse:          3 -> 2  -> 6  -> 5  -> 11 -> 10 -> 15 -> 12

Running-max sweep (keep >= max_so_far):
                  3(keep) 2(drop) 6(keep) 5(drop) 11(keep) 10(drop) 15(keep) 12(drop)

Filtered:          3 -> 6 -> 11 -> 15

Reverse back:     15 -> 11 -> 6 -> 3
```

## Running Max Sweep in Isolation

```text
Before:

max_so_far = M
current node value = V

if V >= M:
    max_so_far = V
    keep node
else:
    drop node


After processing all nodes, only "record-breaking" values (from the right) remain.
```

---

# 14. Interview Explanation in 30 Seconds

> Since this is a singly linked list, I can't peek at values to a node's right directly. So I reverse the list first — that turns "is there something bigger to my right" into "have I already seen something bigger," which I can answer with a simple running maximum while walking left to right. Any node smaller than the running maximum gets dropped; anything that ties or beats it survives and becomes the new maximum. Once the sweep is done, I reverse the filtered list back to restore the original order. The whole thing is two reversals plus one linear sweep — `O(n)` time and `O(1)` extra space.

---

# 15. Interviewer Follow-Up Questions

## Q1. Can you do it without reversing twice?

Not while staying at `O(1)` extra space in a purely iterative style — you need the list back in its original order eventually. One alternative is to solve it **recursively**: recurse to the end of the list first (which implicitly uses the call stack, `O(n)` space), then unwind while tracking the maximum, deciding whether to keep each node as the recursion returns. This avoids explicit reversal but trades it for `O(n)` **implicit** stack space, so it is not actually cheaper — just structured differently.

```python
class Solution:
    def compute(self, head):
        self.max_so_far = float('-inf')
        return self._helper(head)

    def _helper(self, node):
        if node is None:
            return None
        # Recurse to the rightmost node first.
        node.next = self._helper(node.next)
        if node.data >= self.max_so_far:
            self.max_so_far = node.data
            return node
        return node.next
```

## Q2. What about a doubly linked list — is it easier?

Yes, dramatically. With a `prev` pointer available, you can start from the **tail** and walk backward directly, maintaining the running maximum without ever needing to reverse anything. That reduces the problem to a single `O(n)` backward pass with `O(1)` space — no reversal step needed at all.

## Q3. What if we want nodes with a greater value on the LEFT instead (delete if something bigger exists before it)?

This is actually the easier variant for a singly linked list, because "everything to the left" is exactly what you encounter naturally while walking forward. A single left-to-right pass with a running maximum solves it directly — no reversal needed:

```text
keep node if node.data >= max_so_far_from_left
```

This variant is a nice contrast to highlight in an interview: it shows you understand *why* reversal was necessary for the "greater on the right" version specifically.

## Q4. Why do we compare with `>=` and not `>`?

Because a node should only be deleted if something **strictly greater** exists to its right. If a later (further-right) node has an *equal* value, that does not disqualify the current node — ties do not count as "greater." Using `>=` when keeping nodes during the reversed sweep preserves this correctly.

## Q5. Is this the same idea as "Next Greater Element"?

Yes — conceptually. In arrays, "next greater element" is typically solved using a monotonic decreasing stack processed from right to left. Here, we don't have a stack-friendly structure without extra space, so reversing the linked list simulates that right-to-left processing order using only pointer manipulation.

## Q6. Can you solve it in a single pass without any reversal, using extra space?

Yes — push all node values onto a stack in one forward pass (`O(n)` space), then pop from the stack while tracking a running maximum, rebuilding the list from right to left. This achieves the same result with `O(n)` explicit space instead of the `O(1)`-space reversal trick, and is a reasonable thing to mention as an alternative if reversal feels awkward to implement live.

---

# 16. Comparison — This Problem vs "Next Greater Element" (Array)

| Aspect | Next Greater Element (Array) | Delete Nodes with Greater on Right (Linked List) |
|---|---|---|
| Data structure | Array (random access) | Singly linked list (forward-only access) |
| Classic technique | Monotonic stack, right to left | Reverse list, then running max, left to right |
| Extra space needed | `O(n)` (stack) | `O(1)` (in-place reversal) |
| Time complexity | `O(n)` | `O(n)` |
| Core question | "What is the next bigger value?" | "Should I delete this node?" |
| Underlying pattern | Suffix maximum / monotonic stack | Suffix maximum via reversal |

> Both problems boil down to computing a **suffix maximum** efficiently. Arrays get an `O(n)` solution using a monotonic stack directly; linked lists get there by reversing first, since a stack-like right-to-left walk isn't natively possible without one.

---

# 17. Pattern Recognition

This problem is the linked-list cousin of a well-known array pattern:

```text
Array version:        "Next Greater Element" / monotonic stack, scanned right to left.
Linked list version:  Same idea, but since we can't scan right to left directly,
                       we REVERSE the list to convert it into a left-to-right scan.
```

Whenever you see a linked-list problem that requires information "from the right" or "from the end," ask:

```text
"Can I get this by reversing the list and turning it into 
 information from the left / from the beginning instead?"
```

This single question resolves an entire family of problems:

- Delete nodes with a greater value on the right (this problem).
- Check if a linked list is a palindrome (reverse the second half, compare).
- Add two numbers represented as linked lists, least significant digit last (reverse, then simulate addition left to right).
- Reverse-related problems in general: whenever "backward-looking" information is needed and only forward pointers exist, reversal is the bridge.

---

# 18. Final Solution

```python
class Solution:

    # Reverses a singly linked list in place and returns the new head.
    def reverse(self, head):

        # Nothing before the first node yet.
        previous = None

        # Start from the given head.
        current = head

        # Walk until the end of the list.
        while current is not None:

            # Save the next node before breaking the forward link.
            next_node = current.next

            # Point this node backward instead of forward.
            current.next = previous

            # Shift 'previous' forward to this node.
            previous = current

            # Shift 'current' forward to the saved next node.
            current = next_node

        # 'previous' is the new head after a full reversal.
        return previous

    # Deletes every node that has a strictly greater value somewhere to its right.
    def compute(self, head):

        # An empty or single-node list needs no deletions.
        if head is None or head.next is None:

            # Nothing to its right can be bigger.
            return head

        # Reverse so a left-to-right scan mimics a right-to-left scan of the original.
        reversed_head = self.reverse(head)

        # The first node of the reversed list is always kept; it seeds the max.
        max_so_far = reversed_head.data

        # Track the head and tail of the surviving (filtered) chain.
        result_head = reversed_head
        result_tail = reversed_head

        # Start scanning from the second node onward.
        current = reversed_head.next

        # Sweep through the rest of the reversed list.
        while current is not None:

            # Preserve the next pointer before possibly discarding this node.
            next_node = current.next

            # Keep the node only if it ties or beats everything seen so far.
            if current.data >= max_so_far:

                # This node becomes the new running maximum.
                max_so_far = current.data

                # Link it into the surviving chain.
                result_tail.next = current

                # Advance the tail of the surviving chain.
                result_tail = current

            # Move to the next node in the reversed list regardless of outcome.
            current = next_node

        # Cut off any stale trailing pointer from a discarded node.
        result_tail.next = None

        # Reverse the filtered chain back to the original left-to-right order.
        final_head = self.reverse(result_head)

        # Return the head of the fully processed list.
        return final_head
```

---

# 19. Interview Takeaways

```text
1. A singly linked list only supports forward traversal.

2. "Something greater to the right" is naturally answered right-to-left,
   which a singly linked list cannot do directly.

3. Reversing the list converts "right-to-left" into "left-to-right,"
   which IS something we can do in O(n) time and O(1) space.

4. After reversing, a simple running maximum identifies every node
   that must be deleted (anything smaller than the max seen so far).

5. The last node of the original list ALWAYS survives — it becomes
   the first node of the reversed list and seeds the maximum.

6. Use >= (not >) when comparing against the running maximum, so
   that tied values are correctly kept.

7. Reverse the filtered list back to restore the original order.

8. Total complexity: O(n) time (two reversals + one sweep), O(1) space.
```

The key sentence to remember is:

> **When a linked-list problem needs information "from the right" but you can only move forward, reverse the list — it turns an impossible backward look into a simple forward scan.**

---

## Related Problems to Practice

After this problem, practice these linked-list patterns that build on reversal and suffix-style reasoning:

1. Reverse a linked list (iterative and recursive).
2. Reverse nodes in groups of `k`.
3. Check if a linked list is a palindrome.
4. Add two numbers represented as linked lists (digits in natural order).
5. Remove duplicates from an unsorted linked list.
6. Remove N-th node from the end of a linked list.
7. Find the middle of a linked list.
8. Next Greater Element (array version, using a monotonic stack).
9. Sort a linked list (merge sort on linked lists).
10. Partition a linked list around a value `x`.

These problems reinforce the same core idea: when forward-only traversal blocks you from getting information "from behind," either reverse the list or use an auxiliary stack to simulate the missing direction.
