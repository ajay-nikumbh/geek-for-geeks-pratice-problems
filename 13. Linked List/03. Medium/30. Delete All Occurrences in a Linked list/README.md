# Delete All Occurrences in a Linked list

| Topic | Difficulty | Submissions | Accuracy | Companies | Related Tags | Problem Link |
|---|---|---|---|---|---|---|
| Linked List | Medium | 33,461 | 48.44% | — | Linked List | [https://www.geeksforgeeks.org/problems/delete-keys-in-a-linked-list/1](https://www.geeksforgeeks.org/problems/delete-keys-in-a-linked-list/1) |

## Problem Statement

Given the head of a **singly linked list** and an integer `key`, delete **every node** in the list whose value equals `key`.

The list is **not necessarily sorted**, so matching nodes may appear:

- anywhere in the list,
- possibly at the **head** (even several leading nodes in a row),
- as **consecutive** duplicates,
- or scattered with non-matching nodes in between.

Return the head of the modified linked list.

### Example 1

```text
Input:  2 -> 3 -> 2 -> 5 -> 2 -> 7 -> NULL
key:    2

Output: 3 -> 5 -> 7 -> NULL
```

Here `2` appears three times, scattered at positions 1, 3, and 5 — none of them adjacent. All three must be removed, including the head.

### Example 2

```text
Input:  4 -> 4 -> 4 -> 6 -> 9 -> 4 -> NULL
key:    4

Output: 6 -> 9 -> NULL
```

Here `4` appears as a **run of three consecutive nodes at the head**, plus one more scattered occurrence near the tail. Both patterns — consecutive and scattered — must be handled by the same logic.

# 1. Interview Intuition

This problem looks like a close cousin of "remove all duplicate values from a **sorted** linked list," but there is one crucial difference that changes the entire approach:

> The list here is **not sorted**, so occurrences of `key` can appear **anywhere**, in **any pattern** — isolated, consecutive, or both.

In the sorted-duplicates problem, once you pass a run of equal values, you know that value will never appear again. You only need to look at **immediate neighbors**.

Here, that assumption is gone. Consider:

```text
2 -> 3 -> 2 -> 5 -> 2 -> 7 -> NULL
key = 2
```

The value `2` shows up at position 1, then again at position 3, then again at position 5 — with completely different values in between. There is no "run" to detect. The only reliable strategy is:

> Check **every single node**, one at a time, and decide independently whether it matches `key`.

This also means the **head is not special-cased away** the way it might be in other problems — if `head.value == key`, the head must be deleted, and if the next node *also* equals `key`, that one must be deleted too, and so on. Since deletion requires modifying the `next` pointer of the node **before** the one being removed, and the head has no "before" node, we need a clean way to handle a match right at the front.

The standard fix is a **dummy node**:

```text
dummy -> 2 -> 3 -> 2 -> 5 -> 2 -> 7 -> NULL
```

Now every node in the original list — including the head — has a predecessor. This turns "maybe the head matches, maybe several leading nodes match" into an ordinary case handled by the exact same loop as everything else.

# 2. Core Linked List Idea

Place a dummy node before the head, then walk two pointers — `previous` and `current` — down the list together, deciding at each `current` node whether it must be spliced out.

```text
dummy -> 2 -> 3 -> 2 -> 5 -> 2 -> 7 -> NULL
key = 2

Step 0:
previous
   |
   v
 dummy -> 2 -> 3 -> 2 -> 5 -> 2 -> 7
           ^
           |
        current

current.value == 2  -> MATCH -> delete it
previous.next = current.next   (dummy -> 3 -> 2 -> 5 -> 2 -> 7)
current advances alone (previous stays at dummy)

Step 1:
previous
   |
   v
 dummy -> 3 -> 2 -> 5 -> 2 -> 7
                ^
                |
             current

current.value == 3  -> no match -> advance BOTH

Step 2:
        previous
           |
           v
 dummy -> 3 -> 2 -> 5 -> 2 -> 7
                ^
                |
             current

current.value == 2  -> MATCH -> delete it
previous.next = current.next   (dummy -> 3 -> 5 -> 2 -> 7)
current advances alone (previous stays at 3)

Step 3:
        previous
           |
           v
 dummy -> 3 -> 5 -> 2 -> 7
                ^
                |
             current

current.value == 5  -> no match -> advance BOTH

Step 4:
               previous
                  |
                  v
 dummy -> 3 -> 5 -> 2 -> 7
                     ^
                     |
                  current

current.value == 2  -> MATCH -> delete it
previous.next = current.next   (dummy -> 3 -> 5 -> 7)
current advances alone (previous stays at 5)

Step 5:
               previous
                  |
                  v
 dummy -> 3 -> 5 -> 7 -> NULL
                     ^
                     |
                  current

current.value == 7  -> no match -> advance BOTH -> current becomes NULL -> loop ends
```

Final list:

```text
3 -> 5 -> 7 -> NULL
```

Every match — whether at the head, in the middle, isolated, or scattered — is handled with exactly the same rule.

# 3. Most Important Edge Case

There are four scenarios that a correct solution must handle without special-casing:

## Case A — Head (or several leading nodes) match the key

```text
Input: 2 -> 2 -> 2 -> 3 -> NULL
key = 2
```

Because of the dummy node, `previous` starts at `dummy`, not at `head`. So even if `head.value == key`, the very first comparison already has a valid `previous` to splice through. Multiple leading matches are handled automatically because `previous` simply never moves off the dummy until a non-matching node is found.

## Case B — All nodes match the key

```text
Input: 2 -> 2 -> 2 -> NULL
key = 2
```

Every node gets deleted. `previous` never advances past the dummy. At the end, `dummy.next` is `None`, and returning `dummy.next` correctly yields an empty list.

## Case C — No node matches the key

```text
Input: 3 -> 5 -> 7 -> NULL
key = 2
```

`previous` and `current` advance together at every step; nothing is ever spliced out. The list returned is identical to the input.

## Case D — Consecutive matches anywhere in the list

```text
Input: 2 -> 2 -> 2 -> 3 -> NULL
key = 2
```

After deleting the first `2`, `current` moves to the second `2` while `previous` stays put (still at `dummy`). The second `2` is deleted the same way, then the third. Only once `current` reaches `3` (a non-match) does `previous` finally move. This is the single most important behavior of the algorithm: **`previous` must never advance on a match**, or consecutive runs will be handled incorrectly.

# 4. Approach 1 — Brute Force Thinking

A brute-force approach avoids pointer surgery entirely:

1. Traverse the linked list and copy every node's value into a plain array/list.
2. Filter out every value equal to `key` using a list comprehension.
3. Rebuild a brand-new linked list from the filtered values.

```text
Linked List:

2 -> 3 -> 2 -> 5 -> 2 -> 7

Convert to array:

[2, 3, 2, 5, 2, 7]

Filter out key = 2:

[3, 5, 7]

Rebuild:

3 -> 5 -> 7
```

```python
class Solution:

    # Brute-force approach: rebuild the list after filtering out the key.
    def deleteAllOccurrences(self, head, key):

        # This list will hold the values we want to keep.
        values = []

        # Walk the original list once, collecting values.
        node = head

        # Continue until we fall off the end of the list.
        while node is not None:

            # Keep the value only if it does not match the key.
            if node.value != key:

                # Store the surviving value.
                values.append(node.value)

            # Move to the next node.
            node = node.next

        # Handle the case where nothing survives.
        if not values:

            # An empty list has no head.
            return None

        # Create the new head from the first surviving value.
        new_head = Node(values[0])

        # Keep a pointer to build the rest of the list.
        tail = new_head

        # Attach every remaining surviving value.
        for value in values[1:]:

            # Create the next node.
            tail.next = Node(value)

            # Advance the tail pointer.
            tail = tail.next

        # Return the freshly built list.
        return new_head
```

### Complexity

```text
Time  = O(n)
Space = O(n)
```

### Is This Acceptable in an Interview?

Interestingly, the **time complexity here already matches the optimal solution** — both are `O(n)`, since every node must be inspected at least once to know whether it matches `key`. So unlike many "brute force vs optimal" problems, the brute-force version here is not asymptotically worse in time.

What it *does* sacrifice is **space** — it allocates a new array and builds an entirely new list, using `O(n)` extra memory, and it also discards the original node objects. The optimal approach reuses the existing nodes and only rewires pointers, achieving `O(1)` extra space. In an interview, mentioning the brute-force version briefly is fine, but you should proceed to show the pointer-based technique to demonstrate you understand in-place linked-list manipulation.

# 5. Optimal Approach — Dummy Node + Previous/Current Scan

The optimal technique uses a **dummy node** placed before the head, plus two pointers, `previous` and `current`, that scan the list together — but advance according to different rules depending on whether a match is found.

```text
dummy = Node(0)
dummy.next = head

previous = dummy
current  = head
```

Then, while `current` is not `None`:

**Case 1 — `current.value == key` (match found)**

```python
previous.next = current.next
current = current.next
```

We splice `current` out of the list by linking `previous` directly to whatever comes after `current`. Critically, **`previous` does not move**. Only `current` advances, now pointing at the node that took the deleted node's place.

**Case 2 — `current.value != key` (no match)**

```python
previous = current
current = current.next
```

Both pointers advance together, exactly as in a normal traversal.

### Why `previous` Must NOT Advance on a Match

This is the crux of the entire algorithm. After deleting `current`, the node now sitting at `previous.next` (formerly `current.next`) has **never been checked yet**. If it also equals `key` — which happens constantly with consecutive duplicates like `2 -> 2 -> 2 -> 3` — it must be deleted using the *same* `previous` pointer, because `previous` is still the last known **surviving** node.

If we mistakenly advanced `previous` to the just-deleted node, we would be pointing `previous` at garbage that has already been unlinked from the list — and the next deletion would corrupt the list or silently do nothing, because we would be writing to `current.next` on a node that is already disconnected from the chain we care about.

So the rule is:

> `previous` only ever advances to a node we know is being **kept**. It jumps forward exactly once per surviving node, and stays frozen through any number of consecutive deletions.

# 6. Pointer Movement

Let's trace this precisely on a list containing **both** a consecutive run at the head **and** a later scattered match:

```text
dummy -> 2 -> 2 -> 3 -> 2 -> NULL
key = 2
```

```text
Start:
previous
   |
   v
 dummy -> 2 -> 2 -> 3 -> 2
           ^
           |
        current

current.value = 2  -> MATCH
previous.next = current.next     (dummy -> 2 -> 3 -> 2)
current = current.next           (current now at the SECOND original 2)
previous stays at dummy
```

```text
Next:
previous
   |
   v
 dummy -> 2 -> 3 -> 2
           ^
           |
        current

current.value = 2  -> MATCH (this is the second consecutive 2)
previous.next = current.next     (dummy -> 3 -> 2)
current = current.next           (current now at 3)
previous STILL stays at dummy — this is the key moment: two
deletions in a row happened without previous ever moving.
```

```text
Next:
previous
   |
   v
 dummy -> 3 -> 2
           ^
           |
        current

current.value = 3  -> no match
previous = current    (previous moves to 3, its first move so far)
current  = current.next   (current moves to the scattered 2)
```

```text
Next:
        previous
           |
           v
 dummy -> 3 -> 2
                ^
                |
             current

current.value = 2  -> MATCH (the scattered occurrence, far from the earlier run)
previous.next = current.next     (dummy -> 3 -> NULL)
current = current.next           (current becomes NULL)
previous stays at 3
```

```text
current is None -> loop ends
```

Final list:

```text
3 -> NULL
```

Notice that `previous` moved exactly **once** in the entire trace (from `dummy` to `3`), even though **three** deletions happened — two of them consecutive, one of them scattered far later in the list. This is exactly the behavior we want.

# 7. Algorithm

### Step 1

Create a dummy node and point it at the head:

```text
dummy.next = head
```

### Step 2

Initialize:

```text
previous = dummy
current  = head
```

### Step 3

While `current` is not `None`:

- If `current.value == key`:
  - `previous.next = current.next`
  - `current = current.next`
  - (do **not** move `previous`)
- Else:
  - `previous = current`
  - `current = current.next`

### Step 4

Return `dummy.next` as the new head.

# 8. Optimal Python Solution

```python
class Solution:

    # This function deletes every node whose value equals key.
    def deleteAllOccurrences(self, head, key):

        # Create a dummy node so the head can be treated like any other node.
        dummy = Node(0)

        # Connect the dummy node to the original list.
        dummy.next = head

        # previous always points to the last node known to survive.
        previous = dummy

        # current is the node currently being examined.
        current = head

        # Walk through the entire list, checking every node individually.
        while current is not None:

            # If the current node's value matches the key, it must be removed.
            if current.value == key:

                # Splice current out by linking previous directly past it.
                previous.next = current.next

                # Move current forward only; previous stays put so that
                # consecutive matches are handled correctly.
                current = current.next

            else:

                # current is not a match, so it becomes the new previous.
                previous = current

                # Advance current to continue scanning the list.
                current = current.next

        # Return the head of the modified list, skipping the dummy node.
        return dummy.next
```

# 9. Complete Dry Run

Consider:

```text
head = 2 -> 3 -> 2 -> 5 -> 2 -> 7 -> NULL
key  = 2
```

## Initial Setup

```text
dummy -> 2 -> 3 -> 2 -> 5 -> 2 -> 7 -> NULL

previous = dummy
current  = 2 (first node)
```

## Step 1

```text
current.value = 2  ==  key  -> MATCH

previous.next = current.next   (dummy -> 3 -> 2 -> 5 -> 2 -> 7)
current       = current.next   (current -> 3)
previous stays at dummy
```

```text
previous
   |
   v
 dummy -> 3 -> 2 -> 5 -> 2 -> 7
           ^
           |
        current
```

## Step 2

```text
current.value = 3  !=  key  -> no match

previous = current   (previous -> 3)
current  = current.next   (current -> 2)
```

```text
        previous
           |
           v
 dummy -> 3 -> 2 -> 5 -> 2 -> 7
                ^
                |
             current
```

## Step 3

```text
current.value = 2  ==  key  -> MATCH

previous.next = current.next   (dummy -> 3 -> 5 -> 2 -> 7)
current       = current.next   (current -> 5)
previous stays at 3
```

```text
        previous
           |
           v
 dummy -> 3 -> 5 -> 2 -> 7
                ^
                |
             current
```

## Step 4

```text
current.value = 5  !=  key  -> no match

previous = current   (previous -> 5)
current  = current.next   (current -> 2)
```

```text
               previous
                  |
                  v
 dummy -> 3 -> 5 -> 2 -> 7
                     ^
                     |
                  current
```

## Step 5

```text
current.value = 2  ==  key  -> MATCH

previous.next = current.next   (dummy -> 3 -> 5 -> 7)
current       = current.next   (current -> 7)
previous stays at 5
```

```text
               previous
                  |
                  v
 dummy -> 3 -> 5 -> 7 -> NULL
                     ^
                     |
                  current
```

## Step 6

```text
current.value = 7  !=  key  -> no match

previous = current   (previous -> 7)
current  = current.next   (current -> None)
```

```text
                       previous
                          |
                          v
 dummy -> 3 -> 5 -> 7 -> NULL
                          ^
                          |
                       current (None)
```

## Loop Ends

```text
current is None -> exit loop
return dummy.next
```

Final result:

```text
3 -> 5 -> 7 -> NULL
```

Every one of the three (non-adjacent) `2`s was removed correctly, and the head itself — which originally matched `key` — was replaced cleanly through the dummy node.

# 10. Dry Run — Consecutive Matches at the Head

Consider the edge case where the first three nodes all equal the key:

```text
head = 2 -> 2 -> 2 -> 3 -> NULL
key  = 2
```

## Initial Setup

```text
dummy -> 2 -> 2 -> 2 -> 3 -> NULL

previous = dummy
current  = 2 (1st node)
```

## Step 1

```text
current.value = 2  -> MATCH

previous.next = current.next   (dummy -> 2 -> 2 -> 3)
current       = current.next   (current -> 2, the 2nd node)
previous stays at dummy
```

## Step 2

```text
current.value = 2  -> MATCH  (previous is STILL dummy)

previous.next = current.next   (dummy -> 2 -> 3)
current       = current.next   (current -> 2, the 3rd node)
previous stays at dummy
```

## Step 3

```text
current.value = 2  -> MATCH  (previous is STILL dummy)

previous.next = current.next   (dummy -> 3)
current       = current.next   (current -> 3)
previous stays at dummy
```

## Step 4

```text
current.value = 3  -> no match

previous = current   (previous -> 3, first time previous moves)
current  = current.next   (current -> None)
```

## Loop Ends

```text
current is None -> exit loop
return dummy.next
```

Final result:

```text
3 -> NULL
```

Notice `previous` remained parked at `dummy` through **three consecutive deletions** and only moved once, right at the end, when a genuinely surviving node (`3`) was found. `dummy.next` correctly reflects the fully updated head — `3` — even though the *original* head (`2`) was deleted, and so were the two nodes after it.

# 11. Complexity Analysis

Let:

```text
n = number of nodes in the list
```

## Optimal Approach (Dummy Node + Pointer Scan)

Every node is visited **exactly once**. At each node we do a constant amount of work — one comparison, and either one or two pointer reassignments.

```text
Time Complexity  = O(n)
Space Complexity = O(1)
```

No auxiliary array, no recursion stack, no extra nodes beyond the single dummy node (which is a constant, not proportional to `n`).

## Brute Force Approach (Array Rebuild)

```text
Time Complexity  = O(n)
Space Complexity = O(n)
```

### Final Complexity Table

| Approach | Time | Space |
|---|---|---|
| Brute Force (array rebuild) | `O(n)` | `O(n)` |
| Optimal (dummy + previous/current) | `O(n)` | `O(1)` |

# 12. Why This Is Optimal

Could we ever do better than `O(n)` time?

No — and the reasoning is simple:

> To know whether a node's value equals `key`, you must look at that node. There is no way to determine this without inspecting every node at least once.

So `O(n)` time is a hard lower bound for this problem, regardless of approach.

What separates a good solution from a great one is **space**. The brute-force approach spends `O(n)` extra memory building a parallel array and a brand-new list. The optimal approach achieves the same `O(n)` time bound while using only `O(1)` extra space — a fixed number of pointers (`dummy`, `previous`, `current`) that never grow with input size. It reuses the existing nodes in place, doing pure pointer surgery instead of reconstruction.

This is the hallmark of an optimal linked-list solution: match the best possible time bound, and drive the extra space down to the theoretical minimum.

# 13. Common Mistakes

## Mistake 1 — Advancing `previous` Even on a Match

Wrong:

```python
if current.value == key:
    previous.next = current.next
    previous = current      # WRONG — previous now points to a deleted node
    current = current.next
```

If `previous` moves onto the node that was just deleted, it is now referencing a node that has been unlinked from the list. Any subsequent deletion that tries to use `previous.next = ...` would be modifying a disconnected node, silently failing to affect the actual list — or, in a run of consecutive matches, breaking the chain entirely.

Correct:

```python
if current.value == key:
    previous.next = current.next
    current = current.next   # previous does NOT move
```

## Mistake 2 — Forgetting the Dummy Node

Without a dummy node, you must special-case "what if `head` itself matches `key`," and worse, "what if the first several nodes all match `key`" — which requires a `while head is not None and head.value == key: head = head.next` loop *before* the main scan even starts, plus a separate check for the case where the entire list is consumed by that loop. The dummy node eliminates all of this by giving even the head node a `previous` to be deleted through, uniformly.

## Mistake 3 — Not Advancing `current` in the Match Branch

Wrong:

```python
if current.value == key:
    previous.next = current.next
    # forgot to update current
```

If `current` is never reassigned in the match branch, the loop keeps re-examining the same (now-detached) node forever, causing an **infinite loop**. Every branch of the `if`/`else` must advance `current`.

## Mistake 4 — Assuming Matches Are Adjacent (Confusing With the Sorted "Remove Duplicates" Problem)

A very common mistake is porting logic from the classic "remove duplicates from a **sorted** linked list" problem, which only ever compares `current` to `current.next` because duplicates are guaranteed to be neighbors. In this problem the list is **unsorted**, so a value can reappear far later in the list with completely different values in between. Comparing only to the immediate next node will miss scattered occurrences entirely. Every node must be checked against `key` independently — proximity to other matching nodes is irrelevant.

## Mistake 5 — Returning `head` Instead of `dummy.next`

Since the original `head` node might itself be deleted, returning the original `head` variable (which may now point to a removed node) is incorrect. Always return `dummy.next`, which reflects whatever the *current*, possibly updated, first surviving node is.

# 14. Visual Cheat Sheet

## Deleting a Node in the Middle (No Adjacent Match)

```text
Before:

previous
   |
   v
  A --------> B(key) --------> C

Operation:

previous.next = current.next    (current = B)
current = current.next          (current -> C)
previous stays at A

After:

previous
   |
   v
  A --------------------------> C
```

## Deleting Consecutive Matches

```text
Before:

previous
   |
   v
  A --------> B(key) --> C(key) --> D

Step 1: delete B
previous.next = C
current = C
previous stays at A

Step 2: delete C  (previous STILL at A)
previous.next = D
current = D
previous stays at A

After:

previous
   |
   v
  A --------------------------> D
```

## Deleting the Head via Dummy Node

```text
Before:

previous
   |
   v
dummy -> head(key) -> B -> C

Operation:

previous.next = current.next    (current = head)
current = current.next          (current -> B)
previous stays at dummy

After:

previous
   |
   v
dummy -----------> B -> C

return dummy.next   -->   B becomes the new head
```

# 15. Interview Explanation in 30 Seconds

A strong interview explanation would be:

> Since the list isn't sorted, matching values can appear anywhere — including consecutively or right at the head — so I can't rely on comparing only neighboring nodes. I use a dummy node before the head so that even the head is deletable through a `previous` pointer. Then I walk `current` through the list: whenever `current.value == key`, I splice it out with `previous.next = current.next` and move only `current` forward, leaving `previous` untouched so any following match — even a run of consecutive matches — gets deleted through the same surviving `previous`. If there's no match, I advance both pointers together. This is a single `O(n)` pass with `O(1)` extra space.

# 16. Interviewer Follow-Up Questions

## Q1. How is this different from the sorted "remove all duplicate values" problem?

In the sorted version, equal values are guaranteed to be **adjacent**, so the algorithm only ever compares `current` to `current.next` and skips forward through a run. Here the list is **unsorted**, so occurrences of `key` can be scattered anywhere with unrelated values between them. There is no "run" to detect — every single node must be independently compared against `key`, regardless of its neighbors.

## Q2. What if you need to delete multiple different keys, given as a list of keys?

Convert the list of keys into a **set** for O(1) average membership checks, then change the condition from `current.value == key` to `current.value in keys_set`. The rest of the algorithm — dummy node, previous/current scan, previous frozen on a match — stays identical. Time complexity remains `O(n)` (assuming a hash set for the keys), with `O(k)` extra space for the set of `k` keys.

## Q3. Can this be written recursively?

Yes:

```python
class Solution:

    def deleteAllOccurrences(self, head, key):

        # Base case: empty list has nothing to delete.
        if head is None:
            return None

        # Recursively process the rest of the list first.
        head.next = self.deleteAllOccurrences(head.next, key)

        # If the current node matches, skip it; otherwise keep it.
        return head.next if head.value == key else head
```

This naturally handles the head, scattered matches, and consecutive matches, because each recursive call independently decides whether its own node survives after the rest of the list has already been cleaned. The trade-off is `O(n)` recursion stack space, versus `O(1)` for the iterative dummy-node version — so the iterative approach is still preferred when space matters.

## Q4. What if this were a doubly linked list — does the dummy-node technique still work?

Yes, the same dummy-node + previous/current scan works, but deleting a node in a doubly linked list requires updating **one extra pointer**: the `prev` pointer of the node *after* the deleted one, so it points back to the correct surviving predecessor instead of the removed node.

```python
if current.value == key:
    previous.next = current.next
    if current.next is not None:
        current.next.prev = previous     # extra bookkeeping
    current = current.next
else:
    previous = current
    current = current.next
```

Everything else — freezing `previous` during consecutive deletions, using a dummy node to cover head matches — remains exactly the same.

# 17. Important Comparison — This Problem vs Sorted "Remove All Duplicates"

| Aspect | This Problem (Unsorted, Delete-by-Key) | Sorted "Remove All Duplicates" |
|---|---|---|
| List ordering assumption | None — arbitrary order | Sorted, so duplicates are adjacent |
| What triggers deletion | `current.value == key` | `current.value == current.next.value` |
| Where matches can appear | Anywhere: head, middle, tail, scattered | Only in contiguous runs |
| Does `previous` ever advance on a match? | No — stays frozen through the whole match/run | No — similarly frozen through a duplicate run |
| Does `previous` ever advance on a non-match? | Yes — every time | Yes — every time |
| Can matches be non-adjacent? | Yes — key can reappear far later | No — sortedness guarantees adjacency |
| Requires comparing to `current.next`? | No — only `current.value == key` | Yes — inherently a neighbor comparison |
| Handles head matching specially? | Dummy node covers it uniformly | Dummy node (or head-loop) covers it uniformly |
| Time complexity | `O(n)` | `O(n)` |
| Space complexity (optimal) | `O(1)` | `O(1)` |

The core similarity is the **"freeze `previous` on a match"** rule — both problems need it to correctly handle runs of consecutive deletions. The core difference is **what decides a match**: a fixed external `key` here, versus a relationship between neighboring nodes there. That difference is exactly why this problem cannot assume adjacency and must check every node independently.

# 18. Pattern Recognition

This problem is an instance of a very general and reusable linked-list pattern:

> **Dummy Node + Conditional Previous-Advance**, for deleting every node that matches an arbitrary predicate.

Whenever a problem asks you to delete nodes based on a **condition** — rather than a single fixed position — ask:

```text
1. Does the head itself need a "previous" to be deleted through?
   -> If yes, use a dummy node.

2. When a node matches the condition, should previous move?
   -> No. Freeze previous so consecutive matches chain correctly.

3. When a node does NOT match, should previous move?
   -> Yes. previous always tracks the last known survivor.
```

This exact skeleton reappears in many linked-list problems:

- delete all nodes with a given value (this problem),
- delete all nodes less than / greater than a threshold,
- delete all even-valued or odd-valued nodes,
- remove all nodes matching any custom predicate function,
- remove duplicates (sorted or unsorted, with variations on the frozen-previous rule).

Once you recognize "arbitrary predicate deletion, possibly consecutive, possibly at the head," the dummy-node-plus-frozen-previous template should come to mind immediately.

# 19. Final Solution

```python
class Solution:

    # This function deletes every node whose value equals key.
    def deleteAllOccurrences(self, head, key):

        # Create a dummy node so the head can be treated like any other node.
        dummy = Node(0)

        # Connect the dummy node to the original list.
        dummy.next = head

        # previous always points to the last node known to survive.
        previous = dummy

        # current is the node currently being examined.
        current = head

        # Walk through the entire list, checking every node individually.
        while current is not None:

            # If the current node's value matches the key, it must be removed.
            if current.value == key:

                # Splice current out by linking previous directly past it.
                previous.next = current.next

                # Move current forward only; previous stays put so that
                # consecutive matches are handled correctly.
                current = current.next

            else:

                # current is not a match, so it becomes the new previous.
                previous = current

                # Advance current to continue scanning the list.
                current = current.next

        # Return the head of the modified list, skipping the dummy node.
        return dummy.next
```

# 20. Interview Takeaways

Remember these points:

```text
1. The list is unsorted, so matches can be scattered anywhere —
   not just adjacent to each other.

2. Every single node must be checked independently against the key.

3. A dummy node gives even the head a "previous" to delete through.

4. On a match:
       previous.next = current.next
       current = current.next
       (previous does NOT move)

5. On a non-match:
       previous = current
       current = current.next

6. Freezing previous during a match is what correctly handles
   consecutive deletions.

7. Time complexity  = O(n)  (every node inspected once — this is optimal)

8. Space complexity = O(1) for the pointer approach,
                       O(n) for the brute-force array-rebuild approach.
```

The key sentence to remember is:

> **When deletion depends on a condition rather than a position, use a dummy node plus a `previous` pointer that only advances past nodes you know are kept — never past nodes you just deleted.**

## Related Problems to Practice

After this problem, practice these linked-list patterns:

1. Remove duplicates from a sorted linked list.
2. Remove duplicates from an unsorted linked list.
3. Delete a node at a given position.
4. Delete the middle node of a linked list.
5. Remove N-th node from the end of a linked list.
6. Delete nodes greater than a given value on the right side (monotonic-stack style deletion).
7. Partition a linked list around a value.
8. Remove all zero-sum consecutive sublists.
9. Reverse a linked list.
10. Merge two sorted linked lists.

These problems build directly on the same dummy-node and pointer-manipulation fundamentals used here.
