# Linked List — Delete at Position

> **Topic:** Linked List  
> **Difficulty:** Easy  
> **Submissions:** 262,233  
> **Accuracy:** 39.85%  
> **Companies:** Samsung, Adobe  
> **Related Tags:** Linked List  
> **Problem Link:** https://www.geeksforgeeks.org/problems/delete-a-node-in-single-linked-list/1

---

## Problem Statement

Given the head of a **singly linked list** and an integer `x`, delete the node present at the **x-th position** of the linked list.

The position is **1-indexed**:

- `x = 1` means delete the head.
- `x = 2` means delete the second node.
- and so on.

Return the head of the modified linked list.

---

# 1. Interview Intuition

Deleting a node from a singly linked list sounds simple, but there is one important restriction:

> In a singly linked list, every node only knows about the **next** node.

A node does **not** know about its previous node.

Suppose we have:

```text
10 -> 20 -> 30 -> 40 -> 50 -> NULL
```

and we want to delete position `3`.

The node to delete is:

```text
30
```

We cannot move backward from `30` to `20`.

Therefore, instead of directly reaching the node we want to delete, we should reach the node **just before it**.

```text
10 -> 20 -> 30 -> 40 -> 50 -> NULL
      ^
      |
   previous
```

Then we change one pointer:

```text
previous.next = previous.next.next
```

So:

```text
20.next = 40
```

and the list becomes:

```text
10 -> 20 -> 40 -> 50 -> NULL
```

That single pointer update removes `30` from the chain.

---

# 2. Core Linked List Idea

Consider three nodes:

```text
A -> B -> C
```

Suppose we want to delete `B`.

Initially:

```text
A.next = B
B.next = C
```

To delete `B`, make:

```text
A.next = C
```

Visual transformation:

```text
Before:

A --------> B --------> C



After:

A --------------------> C

B is no longer reachable from the linked list.
```

This is the fundamental operation behind deleting a node from a singly linked list.

---

# 3. Most Important Edge Case — Deleting the Head

Suppose:

```text
10 -> 20 -> 30 -> NULL
```

and:

```text
x = 1
```

The node to delete is the head itself.

There is no previous node before the head.

Therefore:

```text
head = head.next
```

Visual:

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
10    20 -> 30 -> NULL
```

The new head becomes `20`.

So the first position must usually be handled separately.

---

# 4. Approach 1 — Brute Force Thinking

A brute-force approach could be:

1. Traverse the linked list.
2. Store every value in an array.
3. Remove the value at position `x`.
4. Build a completely new linked list from the remaining values.

Example:

```text
Linked List:

10 -> 20 -> 30 -> 40

Convert to array:

[10, 20, 30, 40]

Delete position 3:

[10, 20, 40]

Rebuild:

10 -> 20 -> 40
```

### Complexity

If there are `n` nodes:

```text
Time  = O(n)
Space = O(n)
```

Although the time is still linear, the additional array and reconstruction are unnecessary.

For an interview, the interviewer expects an **in-place pointer solution**.

---

# 5. Optimal Approach — Reach the Previous Node

To delete the node at position `x`, we need to reach position:

```text
x - 1
```

because that is the node whose `next` pointer must be changed.

Example:

```text
10 -> 20 -> 30 -> 40 -> 50
```

Delete:

```text
x = 4
```

Target node:

```text
40
```

Previous node:

```text
30
```

So:

```text
30.next = 40.next
```

which means:

```text
30.next = 50
```

Result:

```text
10 -> 20 -> 30 -> 50
```

---

# 6. Pointer Movement

Suppose:

```text
x = 4
```

and:

```text
10 -> 20 -> 30 -> 40 -> 50 -> NULL
```

Start:

```text
current
   |
   v
  10 -> 20 -> 30 -> 40 -> 50
```

We want `current` to stop at position:

```text
x - 1 = 3
```

After one move:

```text
      current
         |
         v
10 ->   20 -> 30 -> 40 -> 50
```

After two moves:

```text
            current
               |
               v
10 -> 20 ->   30 -> 40 -> 50
```

Now:

```text
current      = 30
current.next = 40
```

Delete `40` by performing:

```text
current.next = current.next.next
```

Therefore:

```text
30.next = 50
```

Final list:

```text
10 -> 20 -> 30 -> 50 -> NULL
```

---

# 7. Why Do We Move `x - 2` Times?

This is a common interview confusion.

We begin at position `1`.

```text
current = head
```

If we want to reach position:

```text
x - 1
```

then the number of moves required is:

```text
(x - 1) - 1
```

which becomes:

```text
x - 2
```

Example:

```text
x = 4
```

We need to reach position `3`.

Start at position `1`.

Moves:

```text
1 -> 2    move 1
2 -> 3    move 2
```

Total:

```text
2 = x - 2
```

---

# 8. Algorithm

### Step 1

If the linked list is empty:

```text
head == None
```

return `None`.

### Step 2

If:

```text
x == 1
```

delete the head:

```text
head = head.next
```

and return the new head.

### Step 3

Otherwise, start from the head:

```text
current = head
```

### Step 4

Move until `current` reaches the node immediately before the node that must be deleted.

That means moving:

```text
x - 2
```

times.

### Step 5

Bypass the target node:

```text
current.next = current.next.next
```

### Step 6

Return `head`.

---

# 9. Optimal Python Solution

```python
class Solution:

    # This function deletes the node present at the x-th position.
    def deleteNode(self, head, x):

        # If the linked list is empty, there is nothing to delete.
        if head is None:

            # Return the empty list.
            return None

        # If the first node has to be deleted.
        if x == 1:

            # Move the head pointer to the second node.
            head = head.next

            # Return the new head.
            return head

        # Start traversal from the head node.
        current = head

        # We need to stop at the node just before position x.
        for _ in range(x - 2):

            # Move current one node forward.
            current = current.next

        # Store the node that will be deleted.
        node_to_delete = current.next

        # Make the previous node skip the target node.
        current.next = node_to_delete.next

        # Return the unchanged head of the modified linked list.
        return head
```

---

# 10. Cleaner Interview Version

If the input guarantees that `x` is always a valid position, we can write:

```python
class Solution:

    # Delete the node present at position x.
    def deleteNode(self, head, x):

        # Handle deletion of the head separately.
        if x == 1:

            # Return the second node as the new head.
            return head.next

        # Start at the head.
        current = head

        # Move to the node immediately before the target node.
        for _ in range(x - 2):

            # Advance one node.
            current = current.next

        # Skip the node at position x.
        current.next = current.next.next

        # Return the original head.
        return head
```

This is usually the best version when the platform guarantees valid input.

---

# 11. Defensive Version for Invalid Position

In a real production system, the position may not always be valid.

For example:

```text
10 -> 20 -> 30
```

but:

```text
x = 8
```

Trying to repeatedly access:

```python
current.next
```

would eventually cause an error.

A safer implementation is:

```python
class Solution:

    # Delete a node safely even if the requested position is invalid.
    def deleteNode(self, head, x):

        # If the list is empty, nothing can be deleted.
        if head is None:

            # Return the empty list.
            return None

        # A linked-list position must be positive.
        if x <= 0:

            # Leave the list unchanged.
            return head

        # Handle deletion of the first node.
        if x == 1:

            # Return the next node as the new head.
            return head.next

        # Start traversal from the head.
        current = head

        # Start current at position one.
        current_position = 1

        # Continue until we reach the node before x.
        while current is not None and current_position < x - 1:

            # Move to the next node.
            current = current.next

            # Update the current position.
            current_position += 1

        # If the previous node does not exist, x is outside the list.
        if current is None:

            # Return the original list.
            return head

        # If there is no node after current, x is outside the list.
        if current.next is None:

            # Return the original list.
            return head

        # Skip the target node.
        current.next = current.next.next

        # Return the modified list.
        return head
```

For coding platforms, this extra defensive logic is often unnecessary unless the problem explicitly allows invalid positions.

---

# 12. Complete Dry Run

Consider:

```text
head = 5 -> 8 -> 12 -> 20 -> 25 -> NULL
x = 3
```

We want to delete:

```text
12
```

## Initial State

```text
Position:    1      2      3       4       5

             5 ---> 8 ---> 12 ---> 20 ---> 25 ---> NULL
             ^
             |
          current
```

Since:

```text
x = 3
```

we need to move:

```text
x - 2 = 1
```

time.

After one move:

```text
Position:    1      2      3       4       5

             5 ---> 8 ---> 12 ---> 20 ---> 25 ---> NULL
                    ^
                    |
                 current
```

Now:

```text
current      = 8
current.next = 12
```

We perform:

```python
current.next = current.next.next
```

Since:

```text
current.next.next = 20
```

the pointer becomes:

```text
8.next = 20
```

Final result:

```text
5 -> 8 -> 20 -> 25 -> NULL
```

---

# 13. Dry Run — Delete Head

Input:

```text
7 -> 14 -> 21 -> NULL
```

Position:

```text
x = 1
```

Before:

```text
head
 |
 v
7 -> 14 -> 21 -> NULL
```

Perform:

```python
head = head.next
```

After:

```text
     head
      |
      v
7    14 -> 21 -> NULL
```

Returned list:

```text
14 -> 21 -> NULL
```

---

# 14. Dry Run — Delete Last Node

Input:

```text
10 -> 20 -> 30 -> 40 -> NULL
```

Delete:

```text
x = 4
```

We stop at:

```text
30
```

```text
10 -> 20 -> 30 -> 40 -> NULL
            ^      ^
            |      |
         current  target
```

Perform:

```python
current.next = current.next.next
```

Because:

```text
40.next = None
```

we get:

```text
30.next = None
```

Final list:

```text
10 -> 20 -> 30 -> NULL
```

The same pointer logic naturally handles deletion of the last node.

---

# 15. Complexity Analysis

Let:

```text
n = number of nodes
```

and the deleted position be:

```text
x
```

We traverse at most:

```text
x - 1
```

nodes.

Therefore:

```text
Time Complexity = O(x)
```

Since:

```text
x <= n
```

the worst case is:

```text
O(n)
```

Only a few pointer variables are used.

```text
Space Complexity = O(1)
```

### Final Complexity

| Metric | Complexity |
|---|---|
| Time | `O(n)` worst case |
| Extra Space | `O(1)` |

---

# 16. Why This Is Optimal

Could we do better than `O(n)`?

For an arbitrary position in a singly linked list, generally **no**.

Why?

Because linked lists do not support direct indexing.

An array allows:

```text
arr[100]
```

in approximately:

```text
O(1)
```

But a linked list requires:

```text
head -> node2 -> node3 -> ... -> node100
```

Therefore, reaching a node near the end requires traversing the nodes before it.

So:

```text
O(n)
```

is optimal for arbitrary-position deletion in a singly linked list.

---

# 17. Common Mistakes

## Mistake 1 — Moving to the Target Instead of Its Previous Node

Wrong idea:

```python
for _ in range(x - 1):
    current = current.next
```

Now `current` points to the node we want to delete.

But in a singly linked list, we need the **previous node** to change its `next` pointer.

Correct target:

```text
position x - 1
```

---

## Mistake 2 — Forgetting the Head Case

This does not work when:

```text
x = 1
```

because there is no previous node.

Always think:

```text
Deleting head = change head itself.
```

---

## Mistake 3 — Off-by-One Error

If:

```text
x = 4
```

we need to stop at position:

```text
3
```

Starting from position `1`, that requires:

```text
2 moves
```

Therefore:

```python
range(x - 2)
```

---

## Mistake 4 — Returning `current`

The problem asks for the head of the modified linked list.

Wrong:

```python
return current
```

Correct:

```python
return head
```

---

## Mistake 5 — Creating an Unnecessary New Linked List

Deletion can be done by changing a single pointer.

Do not rebuild the list unless specifically required.

---

# 18. Visual Cheat Sheet

## Delete Middle Node

```text
Before:

prev
 |
 v
20 --------> 30 --------> 40
              target


Operation:

prev.next = prev.next.next


After:

20 ---------------------> 40
```

---

## Delete Head

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

---

## Delete Last Node

```text
Before:

20 -> 30 -> 40 -> NULL
      ^
      |
     prev


Operation:

prev.next = prev.next.next


After:

20 -> 30 -> NULL
```

---

# 19. Interview Explanation in 30 Seconds

A strong interview explanation would be:

> Because this is a singly linked list, I cannot move backward from the node being deleted. Therefore, except when deleting the head, I traverse to the node immediately before position `x`. Once I reach it, I bypass the target using `current.next = current.next.next`. If `x == 1`, I simply return `head.next`. The traversal takes `O(n)` time in the worst case and uses `O(1)` extra space.

---

# 20. Interviewer Follow-Up Questions

## Q1. Why do you stop at `x - 1` instead of `x`?

Because deleting a node requires modifying the `next` pointer of its previous node.

```text
prev -> target -> next
```

We perform:

```text
prev.next = next
```

---

## Q2. Why is deleting the head special?

The head has no previous node.

Therefore, we cannot bypass it using another node.

We must update the head itself:

```python
head = head.next
```

---

## Q3. What happens when deleting the last node?

Nothing special is required.

For:

```text
A -> B -> C -> NULL
```

deleting `C` performs:

```text
B.next = C.next
```

Since:

```text
C.next = None
```

we get:

```text
B.next = None
```

---

## Q4. Can deletion be done in `O(1)` time?

If we are only given the **head and position**, no.

We first need to reach the appropriate node, requiring traversal.

However, if we are directly given a pointer to a non-tail node, there is a famous trick that can delete it in `O(1)` by copying data from the next node.

That is a different problem.

---

## Q5. What if the position is invalid?

There are two possibilities:

1. The problem guarantees valid positions — no extra handling is needed.
2. The problem does not guarantee them — validate during traversal and leave the list unchanged or return an error depending on the specification.

---

## Q6. Why is the space complexity `O(1)`?

Because the algorithm only stores a fixed number of references such as:

```text
head
current
node_to_delete
```

The number of variables does not grow with the input size.

---

# 21. Important Comparison — Array vs Linked List

| Operation | Array | Singly Linked List |
|---|---:|---:|
| Access by index | `O(1)` | `O(n)` |
| Delete after reaching location | `O(n)` due to shifting | `O(1)` pointer change |
| Find arbitrary position | `O(1)` | `O(n)` |
| Delete arbitrary position overall | `O(n)` | `O(n)` |

An important interview insight is:

> Linked-list deletion itself is cheap; **finding the location** is what costs time.

---

# 22. Alternative Technique — Dummy Node

A dummy node can remove the special-case logic for deleting the head.

Concept:

```text
dummy -> 10 -> 20 -> 30
```

If we want to delete position `1`, the previous node becomes the dummy node.

```text
dummy -> 10 -> 20 -> 30
^
|
previous
```

Then we can use the same operation:

```python
previous.next = previous.next.next
```

This produces:

```text
dummy -> 20 -> 30
```

and we return:

```python
dummy.next
```

### Dummy-Node Version

```python
class Solution:

    # Delete the node at position x using a dummy node.
    def deleteNode(self, head, x):

        # Create a dummy node before the real head.
        dummy = Node(0)

        # Connect the dummy node to the original list.
        dummy.next = head

        # Start previous from the dummy node.
        previous = dummy

        # Move previous until it reaches the node before position x.
        for _ in range(x - 1):

            # Move previous one node forward.
            previous = previous.next

        # Skip the node at position x.
        previous.next = previous.next.next

        # Return the actual head after deletion.
        return dummy.next
```

### Why Interviewers Like Dummy Nodes

Dummy nodes are extremely useful because they reduce special-case branching for operations involving the head.

You will see them repeatedly in problems such as:

- delete nodes
- merge linked lists
- remove duplicates
- partition lists
- reverse sublists
- add two numbers
- remove N-th node from end

---

# 23. Head-Case vs Dummy-Node Comparison

## Without Dummy Node

```text
if x == 1:
    handle separately

otherwise:
    find previous node
    delete target
```

## With Dummy Node

```text
dummy -> head -> ...

find previous node starting from dummy

delete target using the same logic for every position
```

The dummy-node technique can make linked-list code more uniform and less error-prone.

---

# 24. Pattern Recognition

Whenever a linked-list problem asks you to:

- delete a node,
- insert before a node,
- remove the N-th node,
- reconnect part of a list,

ask yourself:

```text
"Which node's next pointer must change?"
```

That question often immediately reveals the solution.

For this problem:

```text
node at position x - 1
```

owns the pointer that must change.

---

# 25. Final Optimal Strategy

```text
                    Delete node at position x
                              |
              +---------------+---------------+
              |                               |
            x == 1                          x > 1
              |                               |
              v                               v
      head = head.next            Move to position x - 1
                                              |
                                              v
                              current.next = current.next.next
                                              |
                                              v
                                         return head
```

---

# 26. Final Solution

```python
class Solution:

    # Delete the node at the x-th position of the linked list.
    def deleteNode(self, head, x):

        # If the first node must be deleted, return the second node.
        if x == 1:

            # The second node becomes the new head.
            return head.next

        # Start traversal from the head.
        current = head

        # Move to the node immediately before the node to delete.
        for _ in range(x - 2):

            # Advance current by one node.
            current = current.next

        # Bypass the node at position x.
        current.next = current.next.next

        # Return the head of the modified linked list.
        return head
```

---

# 27. Interview Takeaways

Remember these points:

```text
1. Singly linked lists only move forward.

2. To delete node x, usually reach node x - 1.

3. Change one pointer:

   prev.next = prev.next.next

4. Deleting the head requires changing head itself.

5. A dummy node can eliminate the special head case.

6. Traversal dominates the complexity.

7. Worst-case time  = O(n)

8. Extra space      = O(1)
```

The key sentence to remember is:

> **In a singly linked list, deletion is fundamentally about changing the `next` pointer of the node immediately before the target.**

---

## Related Problems to Practice

After this problem, practice these linked-list patterns:

1. Delete a node without head pointer.
2. Remove N-th node from end.
3. Delete middle node.
4. Reverse a linked list.
5. Find middle of linked list.
6. Detect a cycle.
7. Merge two sorted linked lists.
8. Remove duplicates from sorted linked list.
9. Intersection of two linked lists.
10. Reverse nodes in groups of `k`.

These problems build directly on the same pointer-manipulation fundamentals.
