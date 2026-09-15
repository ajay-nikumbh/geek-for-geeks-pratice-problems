# Linked List — Basics: Patterns

Basics-level linked list problems mostly test whether you can safely manipulate pointers: walking a list, counting it, inserting into it, comparing it against another, or handling the wrap-around edge case of circular lists. These core patterns recur across almost every linked list problem at higher difficulty too.

## Pattern 1: Traversal & Display

The foundation of every linked list problem — walking node by node from `head` until `NULL` (or back to `head` for circular/doubly lists), typically to print or collect values. Doubly linked list traversal additionally exercises following `prev`/`next` pointers correctly. Mastering this loop (`while (curr != NULL) { ...; curr = curr->next; }`) is a prerequisite for every other pattern below.

| # | Problem | Link |
|---|---|---|
| 1 | [Print Linked List](https://www.geeksforgeeks.org/problems/print-linked-list-elements/1) | [`04. Print Linked List/`](04.%20Print%20Linked%20List/) |
| 2 | [Doubly Linked List Traversal](https://www.geeksforgeeks.org/problems/display-doubly-linked-list--154650/1) | [`09. Doubly Linked List Traversal/`](09.%20Doubly%20Linked%20List%20Traversal/) |

## Pattern 2: Length / Counting

Counting nodes by traversing the list while incrementing a counter, then using that count for a derived property (e.g. checking even/odd length). This pattern is a simple extension of traversal but is called out separately because "compute length first" is a building block used inside many other linked list algorithms (finding the middle, the nth node, etc.).

| # | Problem | Link |
|---|---|---|
| 1 | [Length of Linked List](https://www.geeksforgeeks.org/problems/count-nodes-of-linked-list/1) | [`02. Length of Linked List/`](02.%20Length%20of%20Linked%20List/) |
| 2 | [Is Linked List Length Even](https://www.geeksforgeeks.org/problems/linked-list-length-even-or-odd/1) | [`07. Is Linked List Length Even/`](07.%20Is%20Linked%20List%20Length%20Even/) |

## Pattern 3: Insertion

Attaching a new node into a list at a specific location — the end, the middle, or as the first node of an empty (circular) list. Each variant requires correctly re-linking pointers (and for circular lists, making the new node point to itself) without losing the rest of the list, which is the core skill this pattern builds.

| # | Problem | Link |
|---|---|---|
| 1 | [Linked List End Insertion](https://www.geeksforgeeks.org/problems/linked-list-insertion-1587115620/1) | [`01. Linked List End Insertion/`](01.%20Linked%20List%20End%20Insertion/) |
| 2 | [Insert at Middle of Linked List](https://www.geeksforgeeks.org/problems/insert-in-middle-of-linked-list/1) | [`06. Insert at Middle of Linked List/`](06.%20Insert%20at%20Middle%20of%20Linked%20List/) |
| 3 | [Insertion in Empty Circular List](https://www.geeksforgeeks.org/problems/insertion-in-an-empty-circular-linked-list/1) | [`11. Insertion in Empty Circular List/`](11.%20Insertion%20in%20Empty%20Circular%20List/) |

## Pattern 4: Search, Comparison & Positional Access

Problems that traverse one or two lists while checking a condition at each step rather than just printing/counting — searching for a target value, comparing two lists node-by-node for equality, or picking out a node at a position determined by an index/modulus rule. These share the technique of pairing traversal with a per-node check or index calculation.

| # | Problem | Link |
|---|---|---|
| 1 | [Search in Linked List](https://www.geeksforgeeks.org/problems/search-in-linked-list-1664434326/1) | [`05. Search in Linked List/`](05.%20Search%20in%20Linked%20List/) |
| 2 | [Identical Linked Lists](https://www.geeksforgeeks.org/problems/identical-linked-lists/1) | [`03. Identical Linked Lists/`](03.%20Identical%20Linked%20Lists/) |
| 3 | [Modular Node in Linked List](https://www.geeksforgeeks.org/problems/modular-node/1) | [`08. Modular Node in Linked List/`](08.%20Modular%20Node%20in%20Linked%20List/) |

## Pattern 5: Circular Linked List Basics

Problems specific to the circular linked list structure, where the last node points back to `head` instead of `NULL`. The key adjustment from ordinary traversal is the loop/termination condition — you must stop when you come back to the starting node rather than hitting `NULL`, which affects both traversal (counting length) and insertion (self-pointing single node).

| # | Problem | Link |
|---|---|---|
| 1 | [Length of Circular Linked List](https://www.geeksforgeeks.org/problems/length-of-circular-linked-list/1) | [`10. Length of Circular Linked List/`](10.%20Length%20of%20Circular%20Linked%20List/) |
