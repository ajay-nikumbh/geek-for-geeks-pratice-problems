# Linked List — Medium: Patterns

These are the core recurring patterns observed across the 44 Medium-level Linked List problems. Most problems reduce to a small set of pointer-manipulation techniques — cycle detection, controlled reversal, merging, sorting adaptations, and value-based partitioning — applied with different framing.

## Pattern 1: Cycle Detection (Floyd's Algorithm)

Uses the classic slow/fast (tortoise-and-hare) pointer technique to detect, measure, locate, or remove a cycle in a linked list. The fast pointer moves two steps while the slow pointer moves one; if they meet, a cycle exists, and further pointer math (resetting one pointer to head) finds the loop's start node or length.

| # | Problem | Link |
|---|---|---|
| 1 | [Remove Cycle in Linked List](https://www.geeksforgeeks.org/problems/remove-loop-in-linked-list/1) | [`01. Remove Cycle in Linked List/`](01.%20Remove%20Cycle%20in%20Linked%20List/) |
| 2 | [Detect Loop in linked list](https://www.geeksforgeeks.org/problems/detect-loop-in-linked-list/1) | [`02. Detect Loop in linked list/`](02.%20Detect%20Loop%20in%20linked%20list/) |
| 3 | [Cycle Length in Linked List](https://www.geeksforgeeks.org/problems/find-length-of-loop/1) | [`07. Cycle Length in Linked List/`](07.%20Cycle%20Length%20in%20Linked%20List/) |
| 4 | [First Node of Loop in Linked List](https://www.geeksforgeeks.org/problems/find-the-first-node-of-loop-in-linked-list--170645/1) | [`14. First Node of Loop in Linked List/`](14.%20First%20Node%20of%20Loop%20in%20Linked%20List/) |

## Pattern 2: Two Pointer / Fast-Slow Traversal Utility

Applies the fast/slow pointer technique for structural tasks unrelated to cycles — finding the middle to split a list, or advancing a lead pointer to achieve an offset for rotation. The two-pointer gap is the enabling mechanism.

| # | Problem | Link |
|---|---|---|
| 1 | [Palindrome Linked List](https://www.geeksforgeeks.org/problems/check-if-linked-list-is-pallindrome/1) | [`03. Palindrome Linked List/`](03.%20Palindrome%20Linked%20List/) |
| 2 | [Rotate a Linked List](https://www.geeksforgeeks.org/problems/rotate-a-linked-list/1) | [`08. Rotate a Linked List/`](08.%20Rotate%20a%20Linked%20List/) |

## Pattern 3: Arithmetic on Linked List Numbers

Treats a linked list as a sequence of digits or polynomial terms and performs arithmetic (addition, incrementing by one) digit-by-digit, typically via reversal or a stack to align place values, then propagates carries.

| # | Problem | Link |
|---|---|---|
| 1 | [Add Number Linked Lists](https://www.geeksforgeeks.org/problems/add-two-numbers-represented-by-linked-lists/1) | [`04. Add Number Linked Lists/`](04.%20Add%20Number%20Linked%20Lists/) |
| 2 | [Add 1 to a Linked List Number](https://www.geeksforgeeks.org/problems/add-1-to-a-number-represented-as-linked-list/1) | [`05. Add 1 to a Linked List Number/`](05.%20Add%201%20to%20a%20Linked%20List%20Number/) |
| 3 | [Polynomial Addition](https://www.geeksforgeeks.org/problems/polynomial-addition/1) | [`33. Polynomial Addition/`](33.%20Polynomial%20Addition/) |

## Pattern 4: Intersection of Two Lists

Finds the common merge point of two singly linked lists (Y-shaped), typically by computing length differences or using the two-pointer switch-head trick so both pointers traverse equal total distance.

| # | Problem | Link |
|---|---|---|
| 1 | [Intersection in Y Shaped Lists](https://www.geeksforgeeks.org/problems/intersection-point-in-y-shapped-linked-lists/1) | [`06. Intersection in Y Shaped Lists/`](06.%20Intersection%20in%20Y%20Shaped%20Lists/) |
| 2 | [Intersection Point in Y Shaped Linked Lists](https://www.geeksforgeeks.org/problems/intersection-point-in-y-shaped-linked-lists--170645/1) | [`31. Intersection Point in Y Shaped Linked Lists/`](31.%20Intersection%20Point%20in%20Y%20Shaped%20Linked%20Lists/) |

## Pattern 5: Merging Sorted Lists

Merges two (or more) already-sorted linked lists into one, either preserving sort order or reversing it, or interleaving alternating sorted segments — all built on the same compare-and-splice merge step used in merge sort.

| # | Problem | Link |
|---|---|---|
| 1 | [Merge two sorted linked lists](https://www.geeksforgeeks.org/problems/merge-two-sorted-linked-lists/1) | [`12. Merge two sorted linked lists/`](12.%20Merge%20two%20sorted%20linked%20lists/) |
| 2 | [Merge 2 Sorted Linked Lists in Reverse Order](https://www.geeksforgeeks.org/problems/merge-2-sorted-linked-list-in-reverse-order/1) | [`20. Merge 2 Sorted Linked Lists in Reverse Order/`](20.%20Merge%202%20Sorted%20Linked%20Lists%20in%20Reverse%20Order/) |
| 3 | [Sort Alternate Sorted Linked List](https://www.geeksforgeeks.org/problems/linked-list-that-is-sorted-alternatingly/1) | [`21. Sort Alternate Sorted Linked List/`](21.%20Sort%20Alternate%20Sorted%20Linked%20List/) |

## Pattern 6: Sorting Algorithms on Linked List

Adapts classical array sorting algorithms (merge sort, quick sort, insertion sort) to the linked-list node/pointer model instead of index-based arrays, on both singly and doubly linked variants.

| # | Problem | Link |
|---|---|---|
| 1 | [Merge Sort for Linked List](https://www.geeksforgeeks.org/problems/sort-a-linked-list/1) | [`16. Merge Sort for Linked List/`](16.%20Merge%20Sort%20for%20Linked%20List/) |
| 2 | [Quick Sort on Linked List](https://www.geeksforgeeks.org/problems/quick-sort-on-linked-list/1) | [`26. Quick Sort on Linked List/`](26.%20Quick%20Sort%20on%20Linked%20List/) |
| 3 | [Sort Singly Linked List](https://www.geeksforgeeks.org/problems/insertion-sort-for-singly-linked-list/1) | [`28. Sort Singly Linked List/`](28.%20Sort%20Singly%20Linked%20List/) |
| 4 | [Sort k Sorted DLL](https://www.geeksforgeeks.org/problems/sort-a-k-sorted-doubly-linked-list/1) | [`34. Sort k Sorted DLL/`](34.%20Sort%20k%20Sorted%20DLL/) |
| 5 | [QuickSort on Doubly Linked List](https://www.geeksforgeeks.org/problems/quicksort-on-doubly-linked-list/1) | [`40. QuickSort on Doubly Linked List/`](40.%20QuickSort%20on%20Doubly%20Linked%20List/) |
| 6 | [Insertion Sort Linked List](https://www.geeksforgeeks.org/problems/insertion-sort-list/1) | [`44. Insertion Sort Linked List/`](44.%20Insertion%20Sort%20Linked%20List/) |

## Pattern 7: Segregation / Partitioning by Value

Rearranges nodes into groups based on a value predicate (even/odd, 0/1/2, consonant/vowel, less-than/greater-than a pivot) using separate sub-list chains that are stitched back together, without necessarily doing a full sort.

| # | Problem | Link |
|---|---|---|
| 1 | [Sort a linked list of 0s, 1s and 2s](https://www.geeksforgeeks.org/problems/given-a-linked-list-of-0s-1s-and-2s-sort-it/1) | [`09. Sort a linked list of 0s, 1s and 2s/`](09.%20Sort%20a%20linked%20list%20of%200s%2C%201s%20and%202s/) |
| 2 | [Segregate Evens and Odds in a Linked List](https://www.geeksforgeeks.org/problems/segregate-even-and-odd-nodes-in-a-linked-list5035/1) | [`15. Segregate Evens and Odds in a Linked List/`](15.%20Segregate%20Evens%20and%20Odds%20in%20a%20Linked%20List/) |
| 3 | [Separate Consonants and Vowels in Linked List](https://www.geeksforgeeks.org/problems/arrange-consonants-and-vowels/1) | [`27. Separate Consonants and Vowels in Linked List/`](27.%20Separate%20Consonants%20and%20Vowels%20in%20Linked%20List/) |
| 4 | [Partition a Linked List around a given value](https://www.geeksforgeeks.org/problems/partition-a-linked-list-around-a-given-value/1) | [`36. Partition a Linked List around a given value/`](36.%20Partition%20a%20Linked%20List%20around%20a%20given%20value/) |

## Pattern 8: Reversal (Alternate / K-Group Segments)

Reverses specific segments of a list rather than the whole — alternating groups of nodes, or groups of size K — requiring careful bookkeeping of segment boundaries and links back to the untouched parts.

| # | Problem | Link |
|---|---|---|
| 1 | [Reverse Alternate in Link List](https://www.geeksforgeeks.org/problems/given-a-linked-list-reverse-alternate-nodes-and-append-at-the-end/1) | [`22. Reverse Alternate in Link List/`](22.%20Reverse%20Alternate%20in%20Link%20List/) |
| 2 | [Reverse Alternate K in Linked List](https://www.geeksforgeeks.org/problems/xor-linked-list/1) | [`32. Reverse Alternate K in Linked List/`](32.%20Reverse%20Alternate%20K%20in%20Linked%20List/) |

## Pattern 9: Rearrangement / Zig-Zag / Positional Swap

Restructures node order according to a positional rule — interleaving first/last halves, zig-zag (alternating peak/valley) ordering, swapping the Kth node from each end, or general in-place reordering — usually combining middle-finding, reversal, and merging sub-steps.

| # | Problem | Link |
|---|---|---|
| 1 | [Swap Kth nodes from ends](https://www.geeksforgeeks.org/problems/swap-kth-node-from-beginning-and-kth-node-from-end-in-a-singly-linked-list/1) | [`17. Swap Kth nodes from ends/`](17.%20Swap%20Kth%20nodes%20from%20ends/) |
| 2 | [Rearrange a linked list](https://www.geeksforgeeks.org/problems/rearrange-a-linked-list/1) | [`23. Rearrange a linked list/`](23.%20Rearrange%20a%20linked%20list/) |
| 3 | [Linked List in Zig-Zag fashion](https://www.geeksforgeeks.org/problems/linked-list-in-zig-zag-fashion/1) | [`37. Linked List in Zig-Zag fashion/`](37.%20Linked%20List%20in%20Zig-Zag%20fashion/) |
| 4 | [Rearrange linked list in-place](https://www.geeksforgeeks.org/problems/rearrange-linked-list-in-place/1) | [`42. Rearrange linked list in-place/`](42.%20Rearrange%20linked%20list%20in-place/) |

## Pattern 10: Node Deletion Techniques (Duplicates, Keys, No-Head Access)

Removes nodes matching a criterion — duplicate values, a given set of keys, or a target node reachable without the head pointer — by relinking around them, sometimes using hashing to detect what to remove and sometimes the value-copy trick when head access is unavailable.

| # | Problem | Link |
|---|---|---|
| 1 | [Delete Node Without Linked List Head](https://www.geeksforgeeks.org/problems/delete-without-head-pointer/1) | [`11. Delete Node Without Linked List Head/`](11.%20Delete%20Node%20Without%20Linked%20List%20Head/) |
| 2 | [Remove All Duplicates in a Linked List](https://www.geeksforgeeks.org/problems/remove-all-occurences-of-duplicates-in-a-linked-list/1) | [`25. Remove All  Duplicates in a Linked List/`](25.%20Remove%20All%20%20Duplicates%20in%20a%20Linked%20List/) |
| 3 | [Delete All Occurrences in a Linked list](https://www.geeksforgeeks.org/problems/delete-keys-in-a-linked-list/1) | [`30. Delete All Occurrences in a Linked list/`](30.%20Delete%20All%20Occurrences%20in%20a%20Linked%20list/) |

## Pattern 11: Doubly / Circular Linked List Operations

Focuses on the mechanics specific to doubly linked and circular linked lists — maintaining `prev`/`next` links correctly and handling the wrap-around tail-to-head connection while inserting nodes in sorted or positional order.

| # | Problem | Link |
|---|---|---|
| 1 | [Insert in Sorted Circular Linked List](https://www.geeksforgeeks.org/problems/sorted-insert-for-circular-linked-list/1) | [`13. Insert in Sorted Circular Linked List/`](13.%20Insert%20in%20Sorted%20Circular%20Linked%20List/) |
| 2 | [Sorted Insert in DLL](https://www.geeksforgeeks.org/problems/insert-in-sorted-way-in-a-sorted-dll/1) | [`18. Sorted Insert in DLL/`](18.%20Sorted%20Insert%20in%20DLL/) |
| 3 | [Insertion at the beginning of Circular Linked List](https://www.geeksforgeeks.org/problems/insertion-at-the-beginning-of-circular-linked-list/1) | [`43. Insertion at the beginning of Circular Linked List/`](43.%20Insertion%20at%20the%20beginning%20of%20Circular%20Linked%20List/) |

## Pattern 12: Set Operations & Multi-Level Structures

Handles list-of-lists or set-style problems: flattening a multi-level linked list (each node with an extra "down" pointer to its own sorted sub-list) via repeated merging, and computing the union of two lists by combining and deduplicating elements.

| # | Problem | Link |
|---|---|---|
| 1 | [Flattening a Linked List](https://www.geeksforgeeks.org/problems/flattening-a-linked-list/1) | [`10. Flattening a Linked List/`](10.%20Flattening%20a%20Linked%20List/) |
| 2 | [Union of Two Linked Lists](https://www.geeksforgeeks.org/problems/union-of-two-linked-list/1) | [`19. Union of Two Linked Lists/`](19.%20Union%20of%20Two%20Linked%20Lists/) |

## Pattern 13: Value-Based Filtering & Transformation

Scans the list and transforms or filters nodes based on a computed property of their values — checking primality, converting values to their absolute-value-sorted equivalent, or applying a given modification rule to each node.

| # | Problem | Link |
|---|---|---|
| 1 | [Prime List](https://www.geeksforgeeks.org/problems/prime-list--170646/1) | [`24. Prime List/`](24.%20Prime%20List/) |
| 2 | [Absolute List Sorting](https://www.geeksforgeeks.org/problems/absolute-list-sorting/1) | [`29. Absolute List Sorting/`](29.%20Absolute%20List%20Sorting/) |
| 3 | [Modify Linked List](https://www.geeksforgeeks.org/problems/modify-linked-list-1-0546/1) | [`35. Modify Linked List/`](35.%20Modify%20Linked%20List/) |

## Pattern 14: String/Multi-Node Pattern Matching

Treats sequences of node values as strings or groups to find sub-structure — the longest palindromic sub-list, groups of anagram nodes, or triplets of nodes summing to a target — combining hashing/two-pointer ideas with list traversal.

| # | Problem | Link |
|---|---|---|
| 1 | [Longest Palindrome in Linked List](https://www.geeksforgeeks.org/problems/length-of-longest-palindrome-in-linked-list/1) | [`38. Longest Palindrome in Linked List/`](38.%20Longest%20Palindrome%20in%20Linked%20List/) |
| 2 | [Anagrams in Linked List](https://www.geeksforgeeks.org/problems/find-anagrams-in-linked-list--170647/1) | [`39. Anagrams in Linked List/`](39.%20Anagrams%20in%20Linked%20List/) |
| 3 | [Triplets in Sorted Linked List](https://www.geeksforgeeks.org/problems/count-triplets--141631/1) | [`41. Triplets in Sorted Linked List/`](41.%20Triplets%20in%20Sorted%20Linked%20List/) |
