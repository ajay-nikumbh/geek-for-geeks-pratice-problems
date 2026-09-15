# Linked List — Hard: Patterns

These are the core recurring patterns across Hard-level linked list problems. At this difficulty, problems typically combine multiple pointer techniques (reversal, multi-pointer traversal, divide and conquer) or require simulating arithmetic/graph-like structures on top of a linked list.

## Pattern 1: Segment/Group Reversal

This pattern reverses a bounded window of nodes in place — either a fixed-size group (repeated across the whole list) or an arbitrary sublist between two positions. The core technique is iterative pointer reversal (prev/curr/next) applied within careful boundary bookkeeping, so the nodes before and after the reversed segment are correctly reconnected. Recursion is often used to chain groups together.

| # | Problem | Link |
|---|---|---|
| 1 | [Reverse a linked list in groups of given size](https://www.geeksforgeeks.org/problems/reverse-a-linked-list-in-groups-of-given-size/1) | [`01. Linked List Group Reverse/`](01.%20Linked%20List%20Group%20Reverse/) |
| 2 | [Reverse a sublist of a linked list](https://www.geeksforgeeks.org/problems/reverse-a-sublist-of-a-linked-list/1) | [`07. Reverse Sublist of Linked List/`](07.%20Reverse%20Sublist%20of%20Linked%20List/) |

## Pattern 2: Advanced Node Manipulation with Extra Pointers (Random Pointer Clone)

This pattern deals with nodes that carry an additional pointer beyond `next` (here, a `random` pointer), requiring a deep copy that preserves both pointer structures. The classic technique interleaves cloned nodes into the original list (or uses a hash map) so random pointers can be resolved in O(1) before the two lists are split apart again.

| # | Problem | Link |
|---|---|---|
| 1 | [Clone a linked list with next and random pointer](https://www.geeksforgeeks.org/problems/clone-a-linked-list-with-next-and-random-pointer/1) | [`02. Clone List with Next and Random/`](02.%20Clone%20List%20with%20Next%20and%20Random/) |

## Pattern 3: Arithmetic on Linked List Numbers

This pattern represents large numbers as digit-per-node linked lists and performs arithmetic (multiplication, subtraction) without converting to native integer types. It relies on simulating manual arithmetic — carrying/borrowing digit by digit — often after reversing the lists so the least-significant digit is processed first, then building the result list (with leading-zero cleanup).

| # | Problem | Link |
|---|---|---|
| 1 | [Multiply two linked lists](https://www.geeksforgeeks.org/problems/multiply-two-linked-lists/1) | [`03. Multiply Two Linked Lists/`](03.%20Multiply%20Two%20Linked%20Lists/) |
| 2 | [Subtraction in linked list](https://www.geeksforgeeks.org/problems/subtraction-in-linked-list/1) | [`04. Subtraction in Linked List/`](04.%20Subtraction%20in%20Linked%20List/) |

## Pattern 4: Reordering via Middle-Find + Reverse + Merge

This pattern rearranges a list's node order (e.g., interleaving front and back halves) by composing three simpler techniques: locate the middle with slow/fast pointers, reverse the second half in place, then merge the two halves by alternating nodes. It's a good example of how Hard problems chain multiple Medium-level building blocks together.

| # | Problem | Link |
|---|---|---|
| 1 | [Reorder List](https://www.geeksforgeeks.org/problems/reorder-list/1) | [`05. Reorder List/`](05.%20Reorder%20List/) |

## Pattern 5: Divide and Conquer Sorting (Merge Sort on Linked List)

This pattern applies merge sort's divide-and-conquer strategy directly to linked list structures rather than arrays. The list is recursively split at its midpoint (via slow/fast pointers) down to single nodes, then merged back in sorted order; on a doubly linked list this additionally requires maintaining correct `prev` links during the merge step.

| # | Problem | Link |
|---|---|---|
| 1 | [Merge Sort on Doubly Linked List](https://www.geeksforgeeks.org/problems/merge-sort-on-doubly-linked-list/1) | [`06. Merge Sort on Doubly Linked List/`](06.%20Merge%20Sort%20on%20Doubly%20Linked%20List/) |
