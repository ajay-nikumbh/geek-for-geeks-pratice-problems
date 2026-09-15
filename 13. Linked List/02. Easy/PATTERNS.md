# Linked List — Easy: Patterns

These are the core recurring patterns seen across the 43 Easy-level Linked List problems. Most problems boil down to a handful of pointer-manipulation techniques — traversal, two-pointer scanning, in-place reversal, insertion/deletion at a position, and merging/comparing two lists — applied to singly, doubly, or circular variants.

## Pattern 1: Traversal, Search & Counting

The most basic technique — walk the list once (or twice) with a single pointer, examining or accumulating data along the way (counting nodes, checking a value's frequency, converting to decimal, checking sortedness, comparing two lists node-by-node). No pointer rewiring is needed, just careful iteration and bookkeeping.

| # | Problem | Link |
|---|---|---|
| 1 | [Frequency in a Linked List](https://www.geeksforgeeks.org/problems/occurence-of-an-integer-in-a-linked-list/1) | [`19. Frequency in a Linked List/`](19.%20Frequency%20in%20a%20Linked%20List/) |
| 2 | [Decimal Equivalent of Binary Linked List](https://www.geeksforgeeks.org/problems/decimal-equivalent-of-binary-linked-list/1) | [`20. Decimal Equivalent of Binary Linked List/`](20.%20Decimal%20Equivalent%20of%20Binary%20Linked%20List/) |
| 3 | [Is Linked List Sorted](https://www.geeksforgeeks.org/problems/is-linked-list-sorted/1) | [`28. Is Linked List Sorted/`](28.%20Is%20Linked%20List%20Sorted/) |
| 4 | [Compare two linked lists](https://www.geeksforgeeks.org/problems/compare-two-linked-lists/1) | [`33. Compare two linked lists/`](33.%20Compare%20two%20linked%20lists/) |
| 5 | [Size of Doubly Linked List](https://www.geeksforgeeks.org/problems/size-of-doubly-linked-list--114556/1) | [`43. Size of Doubly Linked List/`](43.%20Size%20of%20Doubly%20Linked%20List/) |
| 6 | [Check Linked list of Words a Palindrome](https://www.geeksforgeeks.org/problems/linked-list-of-strings-forms-a-palindrome/1) | [`26. Check Linked list of Words a Palindrome/`](26.%20Check%20Linked%20list%20of%20Words%20a%20Palindrome/) |

## Pattern 2: Indexed Access (Kth Node / Position Lookup)

Locating a node by its position — from the front, from the end, or by a ratio/fraction — using a single counting pass or an offset pass. The key idea is translating an index into a pointer walk.

| # | Problem | Link |
|---|---|---|
| 1 | [Kth from End of Linked List](https://www.geeksforgeeks.org/problems/nth-node-from-end-of-linked-list/1) | [`01. Kth from End of Linked List/`](01.%20Kth%20from%20End%20of%20Linked%20List/) |
| 2 | [Node at Given Index](https://www.geeksforgeeks.org/problems/node-at-a-given-index-in-linked-list/1) | [`14. Node at Given Index/`](14.%20Node%20at%20Given%20Index/) |
| 3 | [Sum of Last n Nodes of a Linked List](https://www.geeksforgeeks.org/problems/find-the-sum-of-last-n-nodes-of-the-linked-list/1) | [`23. Sum of Last n Nodes of a Linked List/`](23.%20Sum%20of%20Last%20n%20Nodes%20of%20a%20Linked%20List/) |
| 4 | [Find n/k th in Linked list](https://www.geeksforgeeks.org/problems/find-nk-th-node-in-linked-list/1) | [`25. Find nk th in Linked list/`](25.%20Find%20nk%20th%20in%20Linked%20list/) |

## Pattern 3: Fast-Slow Pointer (Middle Finding)

Two pointers move through the list at different speeds (slow advances one step, fast advances two) so that when fast reaches the end, slow sits at the middle. Used for locating or acting on the middle node.

| # | Problem | Link |
|---|---|---|
| 1 | [Middle of a Linked List](https://www.geeksforgeeks.org/problems/finding-middle-element-in-a-linked-list/1) | [`02. Middle of a Linked List/`](02.%20Middle%20of%20a%20Linked%20List/) |
| 2 | [Delete Middle of Linked List](https://www.geeksforgeeks.org/problems/delete-middle-of-linked-list/1) | [`10. Delete Middle of Linked List/`](10.%20Delete%20Middle%20of%20Linked%20List/) |
| 3 | [Split a Linked List Into Halves](https://www.geeksforgeeks.org/problems/split-a-circular-linked-list-into-two-halves/1) | [`22. Split a Linked List Into Halves/`](22.%20Split%20a%20Linked%20List%20Into%20Halves/) |

## Pattern 4: In-Place Reversal

Rewiring `next` pointers (using prev/curr/next trackers) to reverse the direction of all or part of a list, without allocating new nodes.

| # | Problem | Link |
|---|---|---|
| 1 | [Reverse a Linked List](https://www.geeksforgeeks.org/problems/reverse-a-linked-list/1) | [`03. Reverse a Linked List/`](03.%20Reverse%20a%20Linked%20List/) |
| 2 | [Reverse Two Parts of Linked List](https://www.geeksforgeeks.org/problems/reverse-both-parts--170647/1) | [`37. Reverse Two Parts of Linked List/`](37.%20Reverse%20Two%20Parts%20of%20Linked%20List/) |

## Pattern 5: Insertion (Beginning / Position / Sorted / Circular)

Creating a new node and relinking a constant number of pointers to insert it at the head, a given index, in sorted order, or into a circular list.

| # | Problem | Link |
|---|---|---|
| 1 | [Insert in a Sorted List](https://www.geeksforgeeks.org/problems/insert-in-a-sorted-list/1) | [`11. Insert in a Sorted List/`](11.%20Insert%20in%20a%20Sorted%20List/) |
| 2 | [Linked List Insertion At Beginning](https://www.geeksforgeeks.org/problems/linked-list-insertion-at-beginning/1) | [`32. Linked List Insertion At Beginning/`](32.%20Linked%20List%20Insertion%20At%20Beginning/) |
| 3 | [Insert in a Singly Linked List](https://www.geeksforgeeks.org/problems/insertion-at-a-given-position-in-a-linked-list/1) | [`36. Insert in a Singly Linked List/`](36.%20Insert%20in%20a%20Singly%20Linked%20List/) |
| 4 | [Insertion at Position in Circular Linked List](https://www.geeksforgeeks.org/problems/insertion-at-specific-position-in-circular-linked-list/1) | [`42. Insertion at Position in Circular Linked List/`](42.%20Insertion%20at%20Position%20in%20Circular%20Linked%20List/) |

## Pattern 6: Deletion (Position / Head / Tail / Pattern-Based)

Unlinking one or more nodes by adjusting the previous node's `next` pointer — whether removing a node at a specific position, the head, the tail, every kth node, alternate nodes, or nodes matching a value-based rule (e.g. greater element on the right, m-then-n grouping).

| # | Problem | Link |
|---|---|---|
| 1 | [Linked List Delete at Position](https://www.geeksforgeeks.org/problems/delete-a-node-in-single-linked-list/1) | [`06. Linked List Delete at Position/`](06.%20Linked%20List%20Delete%20at%20Position/) |
| 2 | [Delete Nodes with Greater on Right](https://www.geeksforgeeks.org/problems/delete-nodes-having-greater-value-on-right/1) | [`08. Delete Nodes with Greater on Right/`](08.%20Delete%20Nodes%20with%20Greater%20on%20Right/) |
| 3 | [Remove Every k'th in Linked List](https://www.geeksforgeeks.org/problems/remove-every-kth-node/1) | [`15. Remove Every k'th in Linked List/`](15.%20Remove%20Every%20k'th%20in%20Linked%20List/) |
| 4 | [Delete Alternate Nodes](https://www.geeksforgeeks.org/problems/delete-alternate-nodes/1) | [`18. Delete Alternate Nodes/`](18.%20Delete%20Alternate%20Nodes/) |
| 5 | [Delete N After Every M in Linked List](https://www.geeksforgeeks.org/problems/delete-n-nodes-after-m-nodes-of-a-linked-list/1) | [`24. Delete N After Every M in Linked List/`](24.%20Delete%20N%20After%20Every%20M%20in%20Linked%20List/) |
| 6 | [Delete Head of Linked List](https://www.geeksforgeeks.org/problems/delete-head-of-linked-list/1) | [`34. Delete Head of Linked List/`](34.%20Delete%20Head%20of%20Linked%20List/) |
| 7 | [Deletion at the end of a Linked List](https://www.geeksforgeeks.org/problems/deletion-at-the-end-of-a-linked-list/1) | [`39. Deletion at the end of a Linked List/`](39.%20Deletion%20at%20the%20end%20of%20a%20Linked%20List/) |

## Pattern 7: Duplicate Removal

Scanning a list (sorted or unsorted, singly or doubly linked) and unlinking nodes whose value has already been seen — using adjacent-node comparison when sorted, or a hash set when unsorted.

| # | Problem | Link |
|---|---|---|
| 1 | [Remove Duplicates in Sorted Linked List](https://www.geeksforgeeks.org/problems/remove-duplicate-element-from-sorted-linked-list/1) | [`04. Remove Duplicates in Sorted Linked List/`](04.%20Remove%20Duplicates%20in%20Sorted%20Linked%20List/) |
| 2 | [Remove Duplicates from Linked List](https://www.geeksforgeeks.org/problems/remove-duplicates-from-an-unsorted-linked-list/1) | [`05. Remove Duplicates from Linked List/`](05.%20Remove%20Duplicates%20from%20Linked%20List/) |
| 3 | [Remove duplicates from a sorted DLL](https://www.geeksforgeeks.org/problems/remove-duplicates-from-a-sorted-doubly-linked-list/1) | [`17. Remove duplicates from a sorted DLL/`](17.%20Remove%20duplicates%20from%20a%20sorted%20DLL/) |

## Pattern 8: Merge / Join / Intersection of Two Lists

Combining two separate lists into one (by concatenation, alternating merge, or sorted merge), or finding their common elements/nodes — problems that operate on two list pointers simultaneously.

| # | Problem | Link |
|---|---|---|
| 1 | [Intersection Sorted Linked Lists](https://www.geeksforgeeks.org/problems/intersection-of-two-sorted-linked-lists/1) | [`12. Intersection Sorted Linked Lists/`](12.%20Intersection%20Sorted%20Linked%20Lists/) |
| 2 | [Pair Sum Count in Two Linked Lists](https://www.geeksforgeeks.org/problems/count-pairs-whose-sum-is-equal-to-x/1) | [`13. Pair Sum Count in Two Linked Lists/`](13.%20Pair%20Sum%20Count%20in%20Two%20Linked%20Lists/) |
| 3 | [Intersection of Two Linked Lists](https://www.geeksforgeeks.org/problems/intersection-of-two-linked-list/1) | [`21. Intersection of Two Linked Lists/`](21.%20Intersection%20of%20Two%20Linked%20Lists/) |
| 4 | [Join Two Linked Lists](https://www.geeksforgeeks.org/problems/join-two-linked-lists/1) | [`40. Join Two Linked Lists/`](40.%20Join%20Two%20Linked%20Lists/) |
| 5 | [Merge Lists Alternatingly](https://www.geeksforgeeks.org/problems/merge-list-alternatingly/1) | [`41. Merge Lists Alternatingly/`](41.%20Merge%20Lists%20Alternatingly/) |

## Pattern 9: Rearrangement / Splitting / Grouping

Reordering nodes in place based on a structural or value-based rule — swapping pairs, moving an element to front, splitting into alternating sub-lists, or partitioning by value (zeros to front) — done through pointer relinking rather than reversal.

| # | Problem | Link |
|---|---|---|
| 1 | [Pairwise Swap in Linked List](https://www.geeksforgeeks.org/problems/pairwise-swap-elements-of-a-linked-list-by-swapping-data/1) | [`09. Pairwise Swap in Linked List/`](09.%20Pairwise%20Swap%20in%20Linked%20List/) |
| 2 | [Move Last to Front of a Linked List](https://www.geeksforgeeks.org/problems/move-last-element-to-front-of-a-linked-list/1) | [`27. Move Last to Front of a Linked List/`](27.%20Move%20Last%20to%20Front%20of%20a%20Linked%20List/) |
| 3 | [Split Linked List Alternatingly](https://www.geeksforgeeks.org/problems/split-singly-linked-list-alternatingly/1) | [`29. Split Linked List Alternatingly/`](29.%20Split%20Linked%20List%20Alternatingly/) |
| 4 | [Move all zeros to the front of the linked list](https://www.geeksforgeeks.org/problems/move-all-zeros-to-the-front-of-the-linked-list/1) | [`38. Move all zeros to the front of the linked list/`](38.%20Move%20all%20zeros%20to%20the%20front%20of%20the%20linked%20list/) |

## Pattern 10: Circular Linked List Operations

Problems specific to the circular variant — detecting circularity (tail points back to head) and rotating the list by shifting the point where it "starts".

| # | Problem | Link |
|---|---|---|
| 1 | [Check If Circular Linked List](https://www.geeksforgeeks.org/problems/circular-linked-list/1) | [`07. Check If Circular Linked List/`](07.%20Check%20If%20Circular%20Linked%20List/) |
| 2 | [Rotate Doubly Linked List](https://www.geeksforgeeks.org/problems/rotate-doubly-linked-list-by-p-nodes/1) | [`31. Rotate Doubly Linked List/`](31.%20Rotate%20Doubly%20Linked%20List/) |

## Pattern 11: Array ↔ Linked List Conversion & Alternate Representations

Building a linked list structure from another data source (an array, or a 2D grid), rather than transforming an existing list.

| # | Problem | Link |
|---|---|---|
| 1 | [Array to Linked List](https://www.geeksforgeeks.org/problems/introduction-to-linked-list/1) | [`16. Array to Linked List/`](16.%20Array%20to%20Linked%20List/) |
| 2 | [Linked List Representation of Matrix](https://www.geeksforgeeks.org/problems/linked-list-matrix/1) | [`30. Linked List Representation of Matrix/`](30.%20Linked%20List%20Representation%20of%20Matrix/) |

## Pattern 12: Linked List as an Auxiliary Structure (Hashing)

Using a linked list not as the primary data structure but as a building block inside another structure — e.g. chaining for collision resolution in a hash table.

| # | Problem | Link |
|---|---|---|
| 1 | [Separate Chaining in Hashing](https://www.geeksforgeeks.org/problems/separate-chaining-in-hashing-1587115621/1) | [`35. Separate Chaining in Hashing/`](35.%20Separate%20Chaining%20in%20Hashing/) |
