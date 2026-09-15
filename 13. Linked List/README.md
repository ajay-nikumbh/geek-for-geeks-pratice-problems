# 13. Linked List

[← Back to root](../README.md) · [GfG topic problems](https://www.geeksforgeeks.org/explore?category%5B%5D=Linked%20List)

## Patterns (merged across all difficulty levels)

Same core technique shows up at every difficulty — this view merges those occurrences into one pattern, with problems ordered Basics → Easy → Medium → Hard. Logic/Time/Space are filled in as each problem's full article is written.

| # | Pattern | Logic | Typical Time | Typical Space | Total | Basics | Easy | Medium | Hard |
|---|---|---|---|---|---|---|---|---|---|
| 1 | [Deletion](#deletion-10) | Unlink one or more nodes by adjusting the previous node's next pointer — by position, head, tail, kth, alternate, or a value-based rule. | O(n) | O(1) | 10 | 0 | 7 | 3 | 0 |
| 2 | [Merge / Intersection of Two Lists](#merge-intersection-of-two-lists-10) | Combine two lists (concatenation, alternating, or sorted merge) or find their common node/elements by walking two list pointers together. | O(n + m) | O(1) merge / O(n) intersection with hashing | 10 | 0 | 5 | 5 | 0 |
| 3 | [Rearrangement / Positional Reordering](#rearrangement-positional-reordering-9) | Reorder nodes in place per a structural rule — swap pairs, zig-zag, split alternating, partition by value — via pointer relinking, not full reversal. | O(n) | O(1) | 9 | 0 | 4 | 4 | 1 |
| 4 | [Traversal / Display](#traversal-display-8) | Walk the list once from head to NULL (or back to head for circular lists), printing or accumulating data along the way — no pointer rewiring needed. | O(n) | O(1) | 8 | 2 | 6 | 0 | 0 |
| 5 | [Insertion](#insertion-7) | Create a new node and relink a constant number of pointers to insert it at the head, a given index, in sorted order, or into a circular list. | O(n) to locate + O(1) to insert | O(1) | 7 | 3 | 4 | 0 | 0 |
| 6 | [Search / Comparison](#search-comparison-7) | Traverse one or two lists checking a condition per node — searching for a value, comparing lists for equality, or locating a node by index/ratio. | O(n) | O(1) | 7 | 3 | 4 | 0 | 0 |
| 7 | [Sorting Algorithms on Linked List](#sorting-algorithms-on-linked-list-7) | Adapt classical sorting (merge sort, quick sort, insertion sort) to the linked-list pointer model instead of index-based arrays. | O(n log n) merge/quick sort, O(n^2) insertion sort | O(log n) recursion / O(1) iterative | 7 | 0 | 0 | 6 | 1 |
| 8 | [Circular / Doubly Linked List Operations](#circular-doubly-linked-list-operations-6) | Problems specific to the circular or doubly linked structure — adjusting loop/termination conditions and maintaining prev/next links correctly. | O(n) | O(1) | 6 | 1 | 2 | 3 | 0 |
| 9 | [Reversal (Full / Partial / K-Group)](#reversal-full-partial-k-group-6) | Rewire next pointers (prev/curr/next trackers) to reverse the whole list, a sublist, or fixed-size K-groups in place, no new nodes allocated. | O(n) | O(1) | 6 | 0 | 2 | 2 | 2 |
| 10 | [Fast-Slow Pointer (Two Pointer)](#fast-slow-pointer-two-pointer-5) | Two pointers advance at different speeds (slow +1, fast +2) so when fast reaches the end, slow sits at the middle — used for middle-finding, offsets, splitting. | O(n) | O(1) | 5 | 0 | 3 | 2 | 0 |
| 11 | [Arithmetic on Linked List Numbers](#arithmetic-on-linked-list-numbers-5) | Treat the list as digits (or polynomial terms) and perform arithmetic digit-by-digit, typically via reversal, propagating carries/borrows. | O(n) | O(1) to O(n) with reversal | 5 | 0 | 0 | 3 | 2 |
| 12 | [Cycle Detection (Floyd's Algorithm)](#cycle-detection-floyds-algorithm-4) | Slow/fast (tortoise-and-hare) pointers detect, measure, or locate a cycle; if they meet, a cycle exists, and resetting one pointer to head finds the loop start. | O(n) | O(1) | 4 | 0 | 0 | 4 | 0 |
| 13 | [Segregation / Partitioning by Value](#segregation-partitioning-by-value-4) | Rearrange nodes into groups by a value predicate (even/odd, 0/1/2, less/greater than pivot) using separate sub-chains stitched back together. | O(n) | O(1) | 4 | 0 | 0 | 4 | 0 |
| 14 | [Duplicate Removal](#duplicate-removal-3) | Scan a list (sorted or unsorted) unlinking nodes whose value has already been seen, via adjacent comparison (sorted) or a hash set (unsorted). | O(n) | O(1) sorted / O(n) unsorted | 3 | 0 | 3 | 0 | 0 |
| 15 | [Value-Based Filtering / Transformation](#value-based-filtering-transformation-3) | Scan the list transforming or filtering nodes based on a computed property of their value (primality, absolute value, a modification rule). | O(n) to O(n sqrt(max val)) | O(1) to O(n) | 3 | 0 | 0 | 3 | 0 |
| 16 | [String / Multi-Node Pattern Matching](#string-multi-node-pattern-matching-3) | Treat sequences of node values as strings or groups to find sub-structure — palindromic sub-lists, anagram groups, triplets summing to a target. | O(n) to O(n^2) | O(n) | 3 | 0 | 0 | 3 | 0 |
| 17 | [Length / Counting](#length-counting-2) | Traverse the list incrementing a counter to derive length or a length-based property — a building block used inside many other patterns. | O(n) | O(1) | 2 | 2 | 0 | 0 | 0 |
| 18 | [Array <-> Linked List Conversion](#array---linked-list-conversion-2) | Build a linked list from another data source (array, matrix), or represent one structure in terms of the other. | O(n) | O(n) | 2 | 0 | 2 | 0 | 0 |
| 19 | [Set Operations / Multi-Level Structures](#set-operations-multi-level-structures-2) | Flatten a multi-level list (each node with an extra down pointer) via repeated merging, or compute union/intersection of two lists. | O(n log n) flatten, O(n + m) union | O(1) to O(n) | 2 | 0 | 0 | 2 | 0 |
| 20 | [Linked List as Auxiliary Structure](#linked-list-as-auxiliary-structure-1) | Use a linked list as a building block inside another structure — e.g. chaining for collision resolution in a hash table. | O(1) amortized per op | O(n) | 1 | 0 | 1 | 0 | 0 |
| 21 | [Advanced Node Manipulation (Extra Pointers)](#advanced-node-manipulation-extra-pointers-1) | Nodes carry an extra pointer (e.g. random) requiring a deep copy that preserves both structures — interleave cloned nodes or use a hash map. | O(n) | O(1) interleaving / O(n) hash map | 1 | 0 | 0 | 0 | 1 |
| | **Total (21 patterns)** | | | | **105** | **11** | **43** | **44** | **7** |

### Deletion (10)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Linked List Delete at Position](https://www.geeksforgeeks.org/problems/delete-a-node-in-single-linked-list/1) | — | — | — | Easy | Samsung, Adobe | Linked List | [`02. Easy/06. Linked List Delete at Position/`](02.%20Easy/06.%20Linked%20List%20Delete%20at%20Position/) |
| 2 | [Delete Nodes with Greater on Right](https://www.geeksforgeeks.org/problems/delete-nodes-having-greater-value-on-right/1) | — | — | — | Easy | Amazon | Linked List | [`02. Easy/08. Delete Nodes with Greater on Right/`](02.%20Easy/08.%20Delete%20Nodes%20with%20Greater%20on%20Right/) |
| 3 | [Remove Every k'th in Linked List](https://www.geeksforgeeks.org/problems/remove-every-kth-node/1) | — | — | — | Easy | — | Linked List | [`02. Easy/15. Remove Every k'th in Linked List/`](02.%20Easy/15.%20Remove%20Every%20k'th%20in%20Linked%20List/) |
| 4 | [Delete Alternate Nodes](https://www.geeksforgeeks.org/problems/delete-alternate-nodes/1) | — | — | — | Easy | Morgan Stanley | Linked List | [`02. Easy/18. Delete Alternate Nodes/`](02.%20Easy/18.%20Delete%20Alternate%20Nodes/) |
| 5 | [Delete N After Every M in Linked List](https://www.geeksforgeeks.org/problems/delete-n-nodes-after-m-nodes-of-a-linked-list/1) | — | — | — | Easy | Amazon, Microsoft | Linked List | [`02. Easy/24. Delete N After Every M in Linked List/`](02.%20Easy/24.%20Delete%20N%20After%20Every%20M%20in%20Linked%20List/) |
| 6 | [Delete Head of Linked List](https://www.geeksforgeeks.org/problems/delete-head-of-linked-list/1) | — | — | — | Easy | — | Linked List | [`02. Easy/34. Delete Head of Linked List/`](02.%20Easy/34.%20Delete%20Head%20of%20Linked%20List/) |
| 7 | [Deletion at the end of a Linked List](https://www.geeksforgeeks.org/problems/deletion-at-the-end-of-a-linked-list/1) | — | — | — | Easy | — | Linked List | [`02. Easy/39. Deletion at the end of a Linked List/`](02.%20Easy/39.%20Deletion%20at%20the%20end%20of%20a%20Linked%20List/) |
| 8 | [Delete Node Without Linked List Head](https://www.geeksforgeeks.org/problems/delete-without-head-pointer/1) | — | — | — | Medium | Amazon, Microsoft, Samsung, Visa, Goldman Sachs, Kritikal Solutions | Linked List | [`03. Medium/11. Delete Node Without Linked List Head/`](03.%20Medium/11.%20Delete%20Node%20Without%20Linked%20List%20Head/) |
| 9 | [Remove All  Duplicates in a Linked List](https://www.geeksforgeeks.org/problems/remove-all-occurences-of-duplicates-in-a-linked-list/1) | — | — | — | Medium | Microsoft | Linked List | [`03. Medium/25. Remove All Duplicates in a Linked List/`](03.%20Medium/25.%20Remove%20All%20Duplicates%20in%20a%20Linked%20List/) |
| 10 | [Delete All Occurrences in a Linked list](https://www.geeksforgeeks.org/problems/delete-keys-in-a-linked-list/1) | — | — | — | Medium | — | Linked List | [`03. Medium/30. Delete All Occurrences in a Linked list/`](03.%20Medium/30.%20Delete%20All%20Occurrences%20in%20a%20Linked%20list/) |

### Merge / Intersection of Two Lists (10)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Intersection Sorted Linked Lists](https://www.geeksforgeeks.org/problems/intersection-of-two-sorted-linked-lists/1) | — | — | — | Easy | Amazon, Microsoft, D-E-Shaw, Zopper | Linked List, Sorting | [`02. Easy/12. Intersection Sorted Linked Lists/`](02.%20Easy/12.%20Intersection%20Sorted%20Linked%20Lists/) |
| 2 | [Pair Sum Count in Two Linked Lists](https://www.geeksforgeeks.org/problems/count-pairs-whose-sum-is-equal-to-x/1) | — | — | — | Easy | Amazon | Linked List | [`02. Easy/13. Pair Sum Count in Two Linked Lists/`](02.%20Easy/13.%20Pair%20Sum%20Count%20in%20Two%20Linked%20Lists/) |
| 3 | [Intersection of Two Linked Lists](https://www.geeksforgeeks.org/problems/intersection-of-two-linked-list/1) | — | — | — | Easy | VMWare, Flipkart, Accolite, Amazon, Microsoft, 24*7 Innovation Labs, D-E-Shaw, Walmart, Komli Media, Taxi4Sure | Linked List, Hash, Sorting | [`02. Easy/21. Intersection of Two Linked Lists/`](02.%20Easy/21.%20Intersection%20of%20Two%20Linked%20Lists/) |
| 4 | [Join Two Linked Lists](https://www.geeksforgeeks.org/problems/join-two-linked-lists/1) | — | — | — | Easy | — | Linked List | [`02. Easy/40. Join Two Linked Lists/`](02.%20Easy/40.%20Join%20Two%20Linked%20Lists/) |
| 5 | [Merge Lists Alternatingly](https://www.geeksforgeeks.org/problems/merge-list-alternatingly/1) | — | — | — | Easy | Amazon | Linked List | [`02. Easy/41. Merge Lists Alternatingly/`](02.%20Easy/41.%20Merge%20Lists%20Alternatingly/) |
| 6 | [Intersection in Y Shaped Lists](https://www.geeksforgeeks.org/problems/intersection-point-in-y-shapped-linked-lists/1) | — | — | — | Medium | VMWare, Flipkart, Accolite, Amazon, Microsoft, Snapdeal, D-E-Shaw, FactSet, MakeMyTrip, Visa, Goldman Sachs, MAQ Software, Adobe, Qualcomm | Linked List | [`03. Medium/06. Intersection in Y Shaped Lists/`](03.%20Medium/06.%20Intersection%20in%20Y%20Shaped%20Lists/) |
| 7 | [Intersection Point in Y Shaped Linked Lists](https://www.geeksforgeeks.org/problems/intersection-point-in-y-shaped-linked-lists--170645/1) | — | — | — | Medium | VMWare, Flipkart, Accolite, Amazon, Microsoft, Snapdeal, D-E-Shaw, FactSet, MakeMyTrip, Visa, Goldman Sachs, MAQ Software, Adobe, Qualcomm | Linked List | [`03. Medium/31. Intersection Point in Y Shaped Linked Lists/`](03.%20Medium/31.%20Intersection%20Point%20in%20Y%20Shaped%20Linked%20Lists/) |
| 8 | [Merge two sorted linked lists](https://www.geeksforgeeks.org/problems/merge-two-sorted-linked-lists/1) | — | — | — | Medium | Zoho, Flipkart, Accolite, Amazon, Microsoft, Samsung, FactSet, MakeMyTrip, Oracle, Brocade, Synopsys, OATS Systems, Belzabar, NPCI | Linked List | [`03. Medium/12. Merge two sorted linked lists/`](03.%20Medium/12.%20Merge%20two%20sorted%20linked%20lists/) |
| 9 | [Merge 2 Sorted Linked Lists in Reverse Order](https://www.geeksforgeeks.org/problems/merge-2-sorted-linked-list-in-reverse-order/1) | — | — | — | Medium | Microsoft | Linked List, Merge Sort | [`03. Medium/20. Merge 2 Sorted Linked Lists in Reverse Order/`](03.%20Medium/20.%20Merge%202%20Sorted%20Linked%20Lists%20in%20Reverse%20Order/) |
| 10 | [Sort Alternate Sorted Linked List](https://www.geeksforgeeks.org/problems/linked-list-that-is-sorted-alternatingly/1) | — | — | — | Medium | Amazon | Linked List, Sorting | [`03. Medium/21. Sort Alternate Sorted Linked List/`](03.%20Medium/21.%20Sort%20Alternate%20Sorted%20Linked%20List/) |

### Rearrangement / Positional Reordering (9)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Pairwise Swap in Linked List](https://www.geeksforgeeks.org/problems/pairwise-swap-elements-of-a-linked-list-by-swapping-data/1) | — | — | — | Easy | Moonfrog Labs, Amazon, Microsoft, Intuit | Linked List | [`02. Easy/09. Pairwise Swap in Linked List/`](02.%20Easy/09.%20Pairwise%20Swap%20in%20Linked%20List/) |
| 2 | [Move Last to Front of a Linked List](https://www.geeksforgeeks.org/problems/move-last-element-to-front-of-a-linked-list/1) | — | — | — | Easy | — | Linked List | [`02. Easy/27. Move Last to Front of a Linked List/`](02.%20Easy/27.%20Move%20Last%20to%20Front%20of%20a%20Linked%20List/) |
| 3 | [Split Linked List Alternatingly](https://www.geeksforgeeks.org/problems/split-singly-linked-list-alternatingly/1) | — | — | — | Easy | — | Linked List | [`02. Easy/29. Split Linked List Alternatingly/`](02.%20Easy/29.%20Split%20Linked%20List%20Alternatingly/) |
| 4 | [Move all zeros to the front of the linked list](https://www.geeksforgeeks.org/problems/move-all-zeros-to-the-front-of-the-linked-list/1) | — | — | — | Easy | — | Linked List | [`02. Easy/38. Move all zeros to the front of the linked list/`](02.%20Easy/38.%20Move%20all%20zeros%20to%20the%20front%20of%20the%20linked%20list/) |
| 5 | [Swap Kth nodes from ends](https://www.geeksforgeeks.org/problems/swap-kth-node-from-beginning-and-kth-node-from-end-in-a-singly-linked-list/1) | — | — | — | Medium | Morgan Stanley, Amazon, NPCI | Linked List | [`03. Medium/17. Swap Kth nodes from ends/`](03.%20Medium/17.%20Swap%20Kth%20nodes%20from%20ends/) |
| 6 | [Rearrange a linked list](https://www.geeksforgeeks.org/problems/rearrange-a-linked-list/1) | — | — | — | Medium | Amazon, Microsoft | Linked List | [`03. Medium/23. Rearrange a linked list/`](03.%20Medium/23.%20Rearrange%20a%20linked%20list/) |
| 7 | [Linked List in Zig-Zag fashion](https://www.geeksforgeeks.org/problems/linked-list-in-zig-zag-fashion/1) | — | — | — | Medium | Amazon, OYO Rooms | Linked List | [`03. Medium/37. Linked List in Zig-Zag fashion/`](03.%20Medium/37.%20Linked%20List%20in%20Zig-Zag%20fashion/) |
| 8 | [Rearrange linked list in-place](https://www.geeksforgeeks.org/problems/rearrange-linked-list-in-place/1) | — | — | — | Medium | — | Linked List | [`03. Medium/42. Rearrange linked list in-place/`](03.%20Medium/42.%20Rearrange%20linked%20list%20in-place/) |
| 9 | [Reorder List](https://www.geeksforgeeks.org/problems/reorder-list/1) | — | — | — | Hard | Amazon, Microsoft, OYO Rooms, Intuit | Linked List | [`04. Hard/05. Reorder List/`](04.%20Hard/05.%20Reorder%20List/) |

### Traversal / Display (8)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Print Linked List](https://www.geeksforgeeks.org/problems/print-linked-list-elements/1) | — | — | — | Basics | — | Linked List | [`01. Basics/04. Print Linked List/`](01.%20Basics/04.%20Print%20Linked%20List/) |
| 2 | [Doubly Linked List Traversal](https://www.geeksforgeeks.org/problems/display-doubly-linked-list--154650/1) | — | — | — | Basics | — | Doubly Linked List, Linked List | [`01. Basics/09. Doubly Linked List Traversal/`](01.%20Basics/09.%20Doubly%20Linked%20List%20Traversal/) |
| 3 | [Frequency in a Linked List](https://www.geeksforgeeks.org/problems/occurence-of-an-integer-in-a-linked-list/1) | — | — | — | Easy | — | Linked List | [`02. Easy/19. Frequency in a Linked List/`](02.%20Easy/19.%20Frequency%20in%20a%20Linked%20List/) |
| 4 | [Decimal Equivalent of Binary Linked List](https://www.geeksforgeeks.org/problems/decimal-equivalent-of-binary-linked-list/1) | — | — | — | Easy | Juniper Networks | Linked List | [`02. Easy/20. Decimal Equivalent of Binary Linked List/`](02.%20Easy/20.%20Decimal%20Equivalent%20of%20Binary%20Linked%20List/) |
| 5 | [Is Linked List Sorted](https://www.geeksforgeeks.org/problems/is-linked-list-sorted/1) | — | — | — | Easy | — | Linked List | [`02. Easy/28. Is Linked List Sorted/`](02.%20Easy/28.%20Is%20Linked%20List%20Sorted/) |
| 6 | [Compare two linked lists](https://www.geeksforgeeks.org/problems/compare-two-linked-lists/1) | — | — | — | Easy | — | Linked List | [`02. Easy/33. Compare two linked lists/`](02.%20Easy/33.%20Compare%20two%20linked%20lists/) |
| 7 | [Size of Doubly Linked List](https://www.geeksforgeeks.org/problems/size-of-doubly-linked-list--114556/1) | — | — | — | Easy | — | Linked List | [`02. Easy/43. Size of Doubly Linked List/`](02.%20Easy/43.%20Size%20of%20Doubly%20Linked%20List/) |
| 8 | [Check Linked list of Words a Palindrome](https://www.geeksforgeeks.org/problems/linked-list-of-strings-forms-a-palindrome/1) | — | — | — | Easy | — | Linked List, palindrome | [`02. Easy/26. Check Linked list of Words a Palindrome/`](02.%20Easy/26.%20Check%20Linked%20list%20of%20Words%20a%20Palindrome/) |

### Insertion (7)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Linked List End Insertion](https://www.geeksforgeeks.org/problems/linked-list-insertion-1587115620/1) | — | — | — | Basics | Hike, Wipro, TCS | Linked List | [`01. Basics/01. Linked List End Insertion/`](01.%20Basics/01.%20Linked%20List%20End%20Insertion/) |
| 2 | [Insert at Middle of Linked List](https://www.geeksforgeeks.org/problems/insert-in-middle-of-linked-list/1) | — | — | — | Basics | — | Linked List | [`01. Basics/06. Insert at Middle of Linked List/`](01.%20Basics/06.%20Insert%20at%20Middle%20of%20Linked%20List/) |
| 3 | [Insertion in Empty Circular List](https://www.geeksforgeeks.org/problems/insertion-in-an-empty-circular-linked-list/1) | — | — | — | Basics | — | Linked List | [`01. Basics/11. Insertion in Empty Circular List/`](01.%20Basics/11.%20Insertion%20in%20Empty%20Circular%20List/) |
| 4 | [Insert in a Sorted List](https://www.geeksforgeeks.org/problems/insert-in-a-sorted-list/1) | — | — | — | Easy | Amazon, Wipro, SAP Labs | Linked List | [`02. Easy/11. Insert in a Sorted List/`](02.%20Easy/11.%20Insert%20in%20a%20Sorted%20List/) |
| 5 | [Linked List Insertion At Beginning](https://www.geeksforgeeks.org/problems/linked-list-insertion-at-beginning/1) | — | — | — | Easy | — | Linked List | [`02. Easy/32. Linked List Insertion At Beginning/`](02.%20Easy/32.%20Linked%20List%20Insertion%20At%20Beginning/) |
| 6 | [Insert in a Singly Linked List](https://www.geeksforgeeks.org/problems/insertion-at-a-given-position-in-a-linked-list/1) | — | — | — | Easy | — | Linked List | [`02. Easy/36. Insert in a Singly Linked List/`](02.%20Easy/36.%20Insert%20in%20a%20Singly%20Linked%20List/) |
| 7 | [Insertion at Position in Circular Linked List](https://www.geeksforgeeks.org/problems/insertion-at-specific-position-in-circular-linked-list/1) | — | — | — | Easy | — | Linked List | [`02. Easy/42. Insertion at Position in Circular Linked List/`](02.%20Easy/42.%20Insertion%20at%20Position%20in%20Circular%20Linked%20List/) |

### Search / Comparison (7)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Search in Linked List](https://www.geeksforgeeks.org/problems/search-in-linked-list-1664434326/1) | — | — | — | Basics | — | Linked List | [`01. Basics/05. Search in Linked List/`](01.%20Basics/05.%20Search%20in%20Linked%20List/) |
| 2 | [Identical Linked Lists](https://www.geeksforgeeks.org/problems/identical-linked-lists/1) | — | — | — | Basics | — | Linked List | [`01. Basics/03. Identical Linked Lists/`](01.%20Basics/03.%20Identical%20Linked%20Lists/) |
| 3 | [Modular Node in Linked List](https://www.geeksforgeeks.org/problems/modular-node/1) | — | — | — | Basics | — | Linked List, Modular Arithmetic | [`01. Basics/08. Modular Node in Linked List/`](01.%20Basics/08.%20Modular%20Node%20in%20Linked%20List/) |
| 4 | [Kth from End of Linked List](https://www.geeksforgeeks.org/problems/nth-node-from-end-of-linked-list/1) | — | — | — | Easy | Flipkart, Morgan Stanley, Accolite, Amazon, OYO Rooms, Samsung, Snapdeal, FactSet, Hike, MAQ Software, Adobe, Qualcomm, Epic Systems, Citicorp, Monotype Solutions | Linked List | [`02. Easy/01. Kth from End of Linked List/`](02.%20Easy/01.%20Kth%20from%20End%20of%20Linked%20List/) |
| 5 | [Node at Given Index](https://www.geeksforgeeks.org/problems/node-at-a-given-index-in-linked-list/1) | — | — | — | Easy | — | Linked List | [`02. Easy/14. Node at Given Index/`](02.%20Easy/14.%20Node%20at%20Given%20Index/) |
| 6 | [Sum of Last n Nodes of a Linked List](https://www.geeksforgeeks.org/problems/find-the-sum-of-last-n-nodes-of-the-linked-list/1) | — | — | — | Easy | — | Linked List | [`02. Easy/23. Sum of Last n Nodes of a Linked List/`](02.%20Easy/23.%20Sum%20of%20Last%20n%20Nodes%20of%20a%20Linked%20List/) |
| 7 | [Find n/k th in Linked list](https://www.geeksforgeeks.org/problems/find-nk-th-node-in-linked-list/1) | — | — | — | Easy | Hike, SAP Labs | Linked List | [`02. Easy/25. Find nk th in Linked list/`](02.%20Easy/25.%20Find%20nk%20th%20in%20Linked%20list/) |

### Sorting Algorithms on Linked List (7)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Merge Sort for Linked List](https://www.geeksforgeeks.org/problems/sort-a-linked-list/1) | — | — | — | Medium | Paytm, Accolite, Amazon, Microsoft, MAQ Software, Adobe, Veritas, NPCI | Linked List, Sorting, Merge Sort | [`03. Medium/16. Merge Sort for Linked List/`](03.%20Medium/16.%20Merge%20Sort%20for%20Linked%20List/) |
| 2 | [Quick Sort on Linked List](https://www.geeksforgeeks.org/problems/quick-sort-on-linked-list/1) | — | — | — | Medium | Paytm | Linked List | [`03. Medium/26. Quick Sort on Linked List/`](03.%20Medium/26.%20Quick%20Sort%20on%20Linked%20List/) |
| 3 | [Sort Singly Linked List](https://www.geeksforgeeks.org/problems/insertion-sort-for-singly-linked-list/1) | — | — | — | Medium | Microsoft | Linked List | [`03. Medium/28. Sort Singly Linked List/`](03.%20Medium/28.%20Sort%20Singly%20Linked%20List/) |
| 4 | [Sort k Sorted DLL](https://www.geeksforgeeks.org/problems/sort-a-k-sorted-doubly-linked-list/1) | — | — | — | Medium | — | Linked List | [`03. Medium/34. Sort k Sorted DLL/`](03.%20Medium/34.%20Sort%20k%20Sorted%20DLL/) |
| 5 | [QuickSort on Doubly Linked List](https://www.geeksforgeeks.org/problems/quicksort-on-doubly-linked-list/1) | — | — | — | Medium | HSBC | Doubly Linked List, Linked List | [`03. Medium/40. QuickSort on Doubly Linked List/`](03.%20Medium/40.%20QuickSort%20on%20Doubly%20Linked%20List/) |
| 6 | [Insertion Sort Linked List](https://www.geeksforgeeks.org/problems/insertion-sort-list/1) | — | — | — | Medium | Google | Linked List | [`03. Medium/44. Insertion Sort Linked List/`](03.%20Medium/44.%20Insertion%20Sort%20Linked%20List/) |
| 7 | [Merge Sort on Doubly Linked List](https://www.geeksforgeeks.org/problems/merge-sort-on-doubly-linked-list/1) | — | — | — | Hard | — | Doubly Linked List, Linked List, Sorting, Merge Sort | [`04. Hard/06. Merge Sort on Doubly Linked List/`](04.%20Hard/06.%20Merge%20Sort%20on%20Doubly%20Linked%20List/) |

### Circular / Doubly Linked List Operations (6)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Length of Circular Linked List](https://www.geeksforgeeks.org/problems/length-of-circular-linked-list/1) | — | — | — | Basics | — | Linked List | [`01. Basics/10. Length of Circular Linked List/`](01.%20Basics/10.%20Length%20of%20Circular%20Linked%20List/) |
| 2 | [Check If Circular Linked List](https://www.geeksforgeeks.org/problems/circular-linked-list/1) | — | — | — | Easy | Microsoft, MAQ Software, SAP Labs | Circular Linked List, Linked List | [`02. Easy/07. Check If Circular Linked List/`](02.%20Easy/07.%20Check%20If%20Circular%20Linked%20List/) |
| 3 | [Rotate Doubly Linked List](https://www.geeksforgeeks.org/problems/rotate-doubly-linked-list-by-p-nodes/1) | — | — | — | Easy | — | Doubly Linked List, Linked List | [`02. Easy/31. Rotate Doubly Linked List/`](02.%20Easy/31.%20Rotate%20Doubly%20Linked%20List/) |
| 4 | [Insert in Sorted Circular Linked List](https://www.geeksforgeeks.org/problems/sorted-insert-for-circular-linked-list/1) | — | — | — | Medium | Zoho, Amazon, Microsoft | Circular Linked List, Linked List | [`03. Medium/13. Insert in Sorted Circular Linked List/`](03.%20Medium/13.%20Insert%20in%20Sorted%20Circular%20Linked%20List/) |
| 5 | [Sorted Insert in DLL](https://www.geeksforgeeks.org/problems/insert-in-sorted-way-in-a-sorted-dll/1) | — | — | — | Medium | — | Doubly Linked List, Linked List | [`03. Medium/18. Sorted Insert in DLL/`](03.%20Medium/18.%20Sorted%20Insert%20in%20DLL/) |
| 6 | [Insertion at the beginning of Circular Linked List](https://www.geeksforgeeks.org/problems/insertion-at-the-beginning-of-circular-linked-list/1) | — | — | — | Medium | — | Linked List | [`03. Medium/43. Insertion at the beginning of Circular Linked List/`](03.%20Medium/43.%20Insertion%20at%20the%20beginning%20of%20Circular%20Linked%20List/) |

### Reversal (Full / Partial / K-Group) (6)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Reverse a Linked List](https://www.geeksforgeeks.org/problems/reverse-a-linked-list/1) | — | — | — | Easy | Paytm, VMWare, Zoho, Accolite, Amazon, Microsoft, Samsung, Snapdeal, D-E-Shaw, MakeMyTrip, Teradata, Walmart, Goldman Sachs, Intuit, Adobe, SAP Labs, Tejas Network, Cisco, Qualcomm, Cognizant, Mahindra Comviva, IgniteWorld | Linked List | [`02. Easy/03. Reverse a Linked List/`](02.%20Easy/03.%20Reverse%20a%20Linked%20List/) |
| 2 | [Reverse Two Parts of Linked List](https://www.geeksforgeeks.org/problems/reverse-both-parts--170647/1) | — | — | — | Easy | — | Linked List | [`02. Easy/37. Reverse Two Parts of Linked List/`](02.%20Easy/37.%20Reverse%20Two%20Parts%20of%20Linked%20List/) |
| 3 | [Reverse Alternate in Link List](https://www.geeksforgeeks.org/problems/given-a-linked-list-reverse-alternate-nodes-and-append-at-the-end/1) | — | — | — | Medium | Amazon, Walmart | Linked List | [`03. Medium/22. Reverse Alternate in Link List/`](03.%20Medium/22.%20Reverse%20Alternate%20in%20Link%20List/) |
| 4 | [Reverse Alternate K in Linked List](https://www.geeksforgeeks.org/problems/xor-linked-list/1) | — | — | — | Medium | — | Linked List | [`03. Medium/32. Reverse Alternate K in Linked List/`](03.%20Medium/32.%20Reverse%20Alternate%20K%20in%20Linked%20List/) |
| 5 | [Linked List Group Reverse](https://www.geeksforgeeks.org/problems/reverse-a-linked-list-in-groups-of-given-size/1) | — | — | — | Hard | Paytm, VMWare, Accolite, Amazon, Microsoft, Snapdeal, Hike, MakeMyTrip, Walmart, Goldman Sachs, Adobe, SAP Labs | Linked List, two-pointer-algorithm | [`04. Hard/01. Linked List Group Reverse/`](04.%20Hard/01.%20Linked%20List%20Group%20Reverse/) |
| 6 | [Reverse Sublist of Linked List](https://www.geeksforgeeks.org/problems/reverse-a-sublist-of-a-linked-list/1) | — | — | — | Hard | Microsoft | Linked List | [`04. Hard/07. Reverse Sublist of Linked List/`](04.%20Hard/07.%20Reverse%20Sublist%20of%20Linked%20List/) |

### Fast-Slow Pointer (Two Pointer) (5)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Middle of a Linked List](https://www.geeksforgeeks.org/problems/finding-middle-element-in-a-linked-list/1) | — | — | — | Easy | VMWare, Zoho, Flipkart, Morgan Stanley, Amazon, Microsoft, Samsung, Hike, Payu, MAQ Software, Adobe, Wipro, SAP Labs, Qualcomm, Nagarro, GE, Veritas, IgniteWorld, Netskope, NPCI | Linked List, two-pointer-algorithm | [`02. Easy/02. Middle of a Linked List/`](02.%20Easy/02.%20Middle%20of%20a%20Linked%20List/) |
| 2 | [Delete Middle of Linked List](https://www.geeksforgeeks.org/problems/delete-middle-of-linked-list/1) | — | — | — | Easy | Flipkart, Amazon, Microsoft | Linked List, two-pointer-algorithm | [`02. Easy/10. Delete Middle of Linked List/`](02.%20Easy/10.%20Delete%20Middle%20of%20Linked%20List/) |
| 3 | [Split a Linked List Into Halves](https://www.geeksforgeeks.org/problems/split-a-circular-linked-list-into-two-halves/1) | — | — | — | Easy | Yahoo | Circular Linked List, Linked List | [`02. Easy/22. Split a Linked List Into Halves/`](02.%20Easy/22.%20Split%20a%20Linked%20List%20Into%20Halves/) |
| 4 | [Palindrome Linked List](https://www.geeksforgeeks.org/problems/check-if-linked-list-is-pallindrome/1) | — | — | — | Medium | Accolite, Amazon, Microsoft, Snapdeal, MakeMyTrip, Adobe, Yodlee Infotech, KLA Tencor, Kritikal Solutions, NPCI | Linked List, palindrome | [`03. Medium/03. Palindrome Linked List/`](03.%20Medium/03.%20Palindrome%20Linked%20List/) |
| 5 | [Rotate a Linked List](https://www.geeksforgeeks.org/problems/rotate-a-linked-list/1) | — | — | — | Medium | Accolite, Amazon, Microsoft, MakeMyTrip | Linked List | [`03. Medium/08. Rotate a Linked List/`](03.%20Medium/08.%20Rotate%20a%20Linked%20List/) |

### Arithmetic on Linked List Numbers (5)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Add Number Linked Lists](https://www.geeksforgeeks.org/problems/add-two-numbers-represented-by-linked-lists/1) | — | — | — | Medium | Flipkart, Morgan Stanley, Accolite, Amazon, Microsoft, Snapdeal, MakeMyTrip, Qualcomm | Linked List, two-pointer-algorithm | [`03. Medium/04. Add Number Linked Lists/`](03.%20Medium/04.%20Add%20Number%20Linked%20Lists/) |
| 2 | [Add 1 to a Linked List Number](https://www.geeksforgeeks.org/problems/add-1-to-a-number-represented-as-linked-list/1) | — | — | — | Medium | Amazon | Linked List | [`03. Medium/05. Add 1 to a Linked List Number/`](03.%20Medium/05.%20Add%201%20to%20a%20Linked%20List%20Number/) |
| 3 | [Polynomial Addition](https://www.geeksforgeeks.org/problems/polynomial-addition/1) | — | — | — | Medium | Amazon | Linked List, Mathematics | [`03. Medium/33. Polynomial Addition/`](03.%20Medium/33.%20Polynomial%20Addition/) |
| 4 | [Multiply Two Linked Lists](https://www.geeksforgeeks.org/problems/multiply-two-linked-lists/1) | — | — | — | Hard | Amazon | Linked List, Modular Arithmetic | [`04. Hard/03. Multiply Two Linked Lists/`](04.%20Hard/03.%20Multiply%20Two%20Linked%20Lists/) |
| 5 | [Subtraction in Linked List](https://www.geeksforgeeks.org/problems/subtraction-in-linked-list/1) | — | — | — | Hard | Amazon | Linked List, Recursion | [`04. Hard/04. Subtraction in Linked List/`](04.%20Hard/04.%20Subtraction%20in%20Linked%20List/) |

### Cycle Detection (Floyd's Algorithm) (4)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Remove Cycle in Linked List](https://www.geeksforgeeks.org/problems/remove-loop-in-linked-list/1) | — | — | — | Medium | VMWare, Morgan Stanley, Amazon, Microsoft, Snapdeal, MakeMyTrip, Oracle, Walmart, Goldman Sachs, Adobe, Qualcomm, Kuliza, Netskope | Linked List, two-pointer-algorithm | [`03. Medium/01. Remove Cycle in Linked List/`](03.%20Medium/01.%20Remove%20Cycle%20in%20Linked%20List/) |
| 2 | [Detect Loop in linked list](https://www.geeksforgeeks.org/problems/detect-loop-in-linked-list/1) | — | — | — | Medium | Paytm, VMWare, Accolite, Amazon, OYO Rooms, Samsung, Snapdeal, D-E-Shaw, Hike, MakeMyTrip, Walmart, MAQ Software, Adobe, SAP Labs, Qualcomm, Veritas, Mahindra Comviva, Lybrate | Linked List, two-pointer-algorithm | [`03. Medium/02. Detect Loop in linked list/`](03.%20Medium/02.%20Detect%20Loop%20in%20linked%20list/) |
| 3 | [Cycle Length in Linked List](https://www.geeksforgeeks.org/problems/find-length-of-loop/1) | — | — | — | Medium | Amazon, Adobe, Qualcomm | Linked List | [`03. Medium/07. Cycle Length in Linked List/`](03.%20Medium/07.%20Cycle%20Length%20in%20Linked%20List/) |
| 4 | [First Node of Loop in Linked List](https://www.geeksforgeeks.org/problems/find-the-first-node-of-loop-in-linked-list--170645/1) | — | — | — | Medium | — | Linked List, two-pointer-algorithm | [`03. Medium/14. First Node of Loop in Linked List/`](03.%20Medium/14.%20First%20Node%20of%20Loop%20in%20Linked%20List/) |

### Segregation / Partitioning by Value (4)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Sort a linked list of 0s, 1s and 2s](https://www.geeksforgeeks.org/problems/given-a-linked-list-of-0s-1s-and-2s-sort-it/1) | — | — | — | Medium | Amazon, Microsoft, MakeMyTrip, NPCI | Linked List | [`03. Medium/09. Sort a linked list of 0s, 1s and 2s/`](03.%20Medium/09.%20Sort%20a%20linked%20list%20of%200s,%201s%20and%202s/) |
| 2 | [Segregate Evens and Odds in a Linked List](https://www.geeksforgeeks.org/problems/segregate-even-and-odd-nodes-in-a-linked-list5035/1) | — | — | — | Medium | — | Linked List | [`03. Medium/15. Segregate Evens and Odds in a Linked List/`](03.%20Medium/15.%20Segregate%20Evens%20and%20Odds%20in%20a%20Linked%20List/) |
| 3 | [Separate Consonants and Vowels in Linked List](https://www.geeksforgeeks.org/problems/arrange-consonants-and-vowels/1) | — | — | — | Medium | Amazon | Linked List | [`03. Medium/27. Separate Consonants and Vowels in Linked List/`](03.%20Medium/27.%20Separate%20Consonants%20and%20Vowels%20in%20Linked%20List/) |
| 4 | [Partition a Linked List around a given value](https://www.geeksforgeeks.org/problems/partition-a-linked-list-around-a-given-value/1) | — | — | — | Medium | Microsoft | Linked List | [`03. Medium/36. Partition a Linked List around a given value/`](03.%20Medium/36.%20Partition%20a%20Linked%20List%20around%20a%20given%20value/) |

### Duplicate Removal (3)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Remove Duplicates in Sorted Linked List](https://www.geeksforgeeks.org/problems/remove-duplicate-element-from-sorted-linked-list/1) | — | — | — | Easy | Microsoft, OYO Rooms, Oracle, Visa, Adobe, Myntra | Linked List | [`02. Easy/04. Remove Duplicates in Sorted Linked List/`](02.%20Easy/04.%20Remove%20Duplicates%20in%20Sorted%20Linked%20List/) |
| 2 | [Remove Duplicates from Linked List](https://www.geeksforgeeks.org/problems/remove-duplicates-from-an-unsorted-linked-list/1) | — | — | — | Easy | Amazon, Intuit | Linked List | [`02. Easy/05. Remove Duplicates from Linked List/`](02.%20Easy/05.%20Remove%20Duplicates%20from%20Linked%20List/) |
| 3 | [Remove duplicates from a sorted DLL](https://www.geeksforgeeks.org/problems/remove-duplicates-from-a-sorted-doubly-linked-list/1) | — | — | — | Easy | — | Linked List | [`02. Easy/17. Remove duplicates from a sorted DLL/`](02.%20Easy/17.%20Remove%20duplicates%20from%20a%20sorted%20DLL/) |

### Value-Based Filtering / Transformation (3)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Prime List](https://www.geeksforgeeks.org/problems/prime-list--170646/1) | — | — | — | Medium | — | Linked List, Mathematics, Prime Number | [`03. Medium/24. Prime List/`](03.%20Medium/24.%20Prime%20List/) |
| 2 | [Absolute List Sorting](https://www.geeksforgeeks.org/problems/absolute-list-sorting/1) | — | — | — | Medium | Amazon, OYO Rooms | Linked List | [`03. Medium/29. Absolute List Sorting/`](03.%20Medium/29.%20Absolute%20List%20Sorting/) |
| 3 | [Modify Linked List](https://www.geeksforgeeks.org/problems/modify-linked-list-1-0546/1) | — | — | — | Medium | Amazon | Linked List | [`03. Medium/35. Modify Linked List/`](03.%20Medium/35.%20Modify%20Linked%20List/) |

### String / Multi-Node Pattern Matching (3)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Longest Palindrome in Linked List](https://www.geeksforgeeks.org/problems/length-of-longest-palindrome-in-linked-list/1) | — | — | — | Medium | Accolite, Microsoft | Linked List, palindrome | [`03. Medium/38. Longest Palindrome in Linked List/`](03.%20Medium/38.%20Longest%20Palindrome%20in%20Linked%20List/) |
| 2 | [Anagrams in Linked List](https://www.geeksforgeeks.org/problems/find-anagrams-in-linked-list--170647/1) | — | — | — | Medium | — | Linked List, sliding-window | [`03. Medium/39. Anagrams in Linked List/`](03.%20Medium/39.%20Anagrams%20in%20Linked%20List/) |
| 3 | [Triplets in Sorted Linked List](https://www.geeksforgeeks.org/problems/count-triplets--141631/1) | — | — | — | Medium | — | Linked List, Mathematics | [`03. Medium/41. Triplets in Sorted Linked List/`](03.%20Medium/41.%20Triplets%20in%20Sorted%20Linked%20List/) |

### Length / Counting (2)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Length of Linked List](https://www.geeksforgeeks.org/problems/count-nodes-of-linked-list/1) | — | — | — | Basics | — | Linked List | [`01. Basics/02. Length of Linked List/`](01.%20Basics/02.%20Length%20of%20Linked%20List/) |
| 2 | [Is Linked List Length Even](https://www.geeksforgeeks.org/problems/linked-list-length-even-or-odd/1) | — | — | — | Basics | — | Linked List | [`01. Basics/07. Is Linked List Length Even/`](01.%20Basics/07.%20Is%20Linked%20List%20Length%20Even/) |

### Array <-> Linked List Conversion (2)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Array to Linked List](https://www.geeksforgeeks.org/problems/introduction-to-linked-list/1) | — | — | — | Easy | — | Linked List | [`02. Easy/16. Array to Linked List/`](02.%20Easy/16.%20Array%20to%20Linked%20List/) |
| 2 | [Linked List Representation of Matrix](https://www.geeksforgeeks.org/problems/linked-list-matrix/1) | — | — | — | Easy | FactSet | Linked List | [`02. Easy/30. Linked List Representation of Matrix/`](02.%20Easy/30.%20Linked%20List%20Representation%20of%20Matrix/) |

### Set Operations / Multi-Level Structures (2)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Flattening a Linked List](https://www.geeksforgeeks.org/problems/flattening-a-linked-list/1) | — | — | — | Medium | Paytm, Flipkart, Amazon, Microsoft, Snapdeal, 24*7 Innovation Labs, Payu, Visa, Goldman Sachs, Qualcomm, Drishti-Soft | Linked List | [`03. Medium/10. Flattening a Linked List/`](03.%20Medium/10.%20Flattening%20a%20Linked%20List/) |
| 2 | [Union of Two Linked Lists](https://www.geeksforgeeks.org/problems/union-of-two-linked-list/1) | — | — | — | Medium | Flipkart, Amazon, Microsoft, 24*7 Innovation Labs, Komli Media, Taxi4Sure | Linked List, Hash, Sorting | [`03. Medium/19. Union of Two Linked Lists/`](03.%20Medium/19.%20Union%20of%20Two%20Linked%20Lists/) |

### Linked List as Auxiliary Structure (1)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Separate Chaining in Hashing](https://www.geeksforgeeks.org/problems/separate-chaining-in-hashing-1587115621/1) | — | — | — | Easy | — | Hash, Linked List, Arrays | [`02. Easy/35. Separate Chaining in Hashing/`](02.%20Easy/35.%20Separate%20Chaining%20in%20Hashing/) |

### Advanced Node Manipulation (Extra Pointers) (1)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Clone List with Next and Random](https://www.geeksforgeeks.org/problems/clone-a-linked-list-with-next-and-random-pointer/1) | — | — | — | Hard | Flipkart, Morgan Stanley, Amazon, Microsoft, OYO Rooms, Snapdeal, D-E-Shaw, MakeMyTrip, Ola Cabs, Walmart, Adobe, BankBazaar | Linked List | [`04. Hard/02. Clone List with Next and Random/`](04.%20Hard/02.%20Clone%20List%20with%20Next%20and%20Random/) |
