# Two Pointers — Easy: Patterns

These are the recurring patterns across the 24 Easy-level Two Pointers problems. Most are pair search on a sorted array, with merge-style scans of two sorted inputs and in-place read/write compaction as the other main families.

## Pattern 1: Opposite-Ends Pair Search (Sorted Input)

The classic two-pointer move: on a sorted sequence, place `left` at the start and `right` at the end. If `a[left] + a[right]` is too small, move `left` right; if too large, move `right` left. Each step discards one candidate for good, so the whole search is linear. Variants count all pairs below a limit (add `right - left` in one go), track the closest sum, handle duplicates when counting, or run the same idea on a doubly linked list or a rotated array (start at the pivot and wrap with modulo).

| # | Problem | Link |
|---|---|---|
| 1 | [Pairs with 0 Sum](https://www.geeksforgeeks.org/problems/count-pairs-with-given-sum5022/1) | [`01. Pairs with 0 Sum/`](01.%20Pairs%20with%200%20Sum/) |
| 2 | [Pair Sum in Sorted Doubly Linked List](https://www.geeksforgeeks.org/problems/find-pairs-with-given-sum-in-doubly-linked-list/1) | [`05. Pair Sum in Sorted Doubly Linked List/`](05.%20Pair%20Sum%20in%20Sorted%20Doubly%20Linked%20List/) |
| 3 | [Count Sum Pairs in Sorted](https://www.geeksforgeeks.org/problems/pair-with-given-sum-in-a-sorted-array4940/1) | [`06. Count Sum Pairs in Sorted/`](06.%20Count%20Sum%20Pairs%20in%20Sorted/) |
| 4 | [Closest Pair Sum](https://www.geeksforgeeks.org/problems/pair-in-array-whose-sum-is-closest-to-x1124/1) | [`07. Closest Pair Sum/`](07.%20Closest%20Pair%20Sum/) |
| 5 | [Pairs with Limited Sum](https://www.geeksforgeeks.org/problems/count-pairs-whose-sum-is-less-than-target/1) | [`11. Pairs with Limited Sum/`](11.%20Pairs%20with%20Limited%20Sum/) |
| 6 | [Dominant Pairs](https://www.geeksforgeeks.org/problems/dominant-pairs/1) | [`12. Dominant Pairs/`](12.%20Dominant%20Pairs/) |
| 7 | [Largest Pair Sum](https://www.geeksforgeeks.org/problems/pair-sum--120604/1) | [`13. Largest Pair Sum/`](13.%20Largest%20Pair%20Sum/) |
| 8 | [Two Sum in Sorted Array](https://www.geeksforgeeks.org/problems/two-sum-in-sorted-array/1) | [`18. Two Sum in Sorted Array/`](18.%20Two%20Sum%20in%20Sorted%20Array/) |
| 9 | [2 Sum - Find a pair with given sum](https://www.geeksforgeeks.org/problems/2-sum-find-a-pair-with-given-sum/1) | [`20. 2 Sum - Find a pair with given sum/`](20.%202%20Sum%20-%20Find%20a%20pair%20with%20given%20sum/) |
| 10 | [Count Pairs in a sorted array whose sum is less than target](https://www.geeksforgeeks.org/problems/count-pairs-in-a-sorted-array-whose-sum-is-less-than-target/1) | [`23. Count Pairs in a sorted array whose sum is less than target/`](23.%20Count%20Pairs%20in%20a%20sorted%20array%20whose%20sum%20is%20less%20than%20target/) |

## Pattern 2: Fix One + Pair Search (3-Sum / 4-Sum / k-Sum)

k-Sum problems reduce to pair search. Sort the array, loop over the first element (and the second for 4-Sum), and solve the remaining 2-Sum with opposite-ends pointers on the suffix. Skip equal neighbours to emit only distinct tuples. The same frame handles counting triplets below a target, finding the closest triplet sum, or checking if one element is the sum of the other two (fix the largest, search the pair on its left).

| # | Problem | Link |
|---|---|---|
| 1 | [Triplets Where One is Sum of Other Two](https://www.geeksforgeeks.org/problems/count-the-triplets4615/1) | [`04. Triplets Where One is Sum of Other Two/`](04.%20Triplets%20Where%20One%20is%20Sum%20of%20Other%20Two/) |
| 2 | [Check for 4 Sum](https://www.geeksforgeeks.org/problems/four-elements2452/1) | [`08. Check for 4 Sum/`](08.%20Check%20for%204%20Sum/) |
| 3 | [Distinct Triplets with Given Sum](https://www.geeksforgeeks.org/problems/find-all-distinct-triplets-with-given-sum/1) | [`22. Distinct Triplets with Given Sum/`](22.%20Distinct%20Triplets%20with%20Given%20Sum/) |

## Pattern 3: Merge-Style Scan of Sorted Sequences

When two (or three) sequences are each sorted, keep one index per sequence and repeatedly advance the one pointing at the smaller element. This is the merge step of merge sort, and it also yields union, intersection (with or without duplicates), and the minimum spread across three arrays. Interval versions advance the interval that ends first. The in-place variant (merge without extra space) uses the gap method or swaps from the boundary.

| # | Problem | Link |
|---|---|---|
| 1 | [Intersection of Arrays with Distinct](https://www.geeksforgeeks.org/problems/intersection-of-two-arrays2404/1) | [`03. Intersection of Arrays with Distinct/`](03.%20Intersection%20of%20Arrays%20with%20Distinct/) |
| 2 | [Intersection of Two arrays with Duplicate Elements](https://www.geeksforgeeks.org/problems/intersection-of-two-arrays-with-duplicate-elements/1) | [`10. Intersection of Two arrays with Duplicate Elements/`](10.%20Intersection%20of%20Two%20arrays%20with%20Duplicate%20Elements/) |
| 3 | [Sort Two Parts  Sorted](https://www.geeksforgeeks.org/problems/sort-the-half-sorted2157/1) | [`19. Sort Two Parts Sorted/`](19.%20Sort%20Two%20Parts%20Sorted/) |
| 4 | [Closest Triplet Diff in Three Arrays](https://www.geeksforgeeks.org/problems/closest-triplet3807/1) | [`24. Closest Triplet Diff in Three Arrays/`](24.%20Closest%20Triplet%20Diff%20in%20Three%20Arrays/) |

## Pattern 4: Palindrome / Reverse from Both Ends (Strings)

String problems where the answer depends on mirrored positions. Compare `s[left]` and `s[right]` for palindromes, or swap them to reverse. The twist in each variant is which characters to skip: spaces stay in place, non-letters are ignored, or reversal happens only among selected characters.

| # | Problem | Link |
|---|---|---|
| 1 | [Palindrome Sentence](https://www.geeksforgeeks.org/problems/string-palindromic-ignoring-spaces4723/1) | [`09. Palindrome Sentence/`](09.%20Palindrome%20Sentence/) |
| 2 | [Special String Reversal](https://www.geeksforgeeks.org/problems/special-array-reversal2328/1) | [`15. Special String Reversal/`](15.%20Special%20String%20Reversal/) |

## Pattern 5: Container / Greedy Shrink from Both Ends

Objective has the form `(j - i) * min(a[i], a[j])` or `j - i` subject to a value condition. Start at the widest pair. Moving the taller side can never help because width shrinks and the minimum cannot grow, so always move the shorter side. Maximum Index uses the same idea with prefix-min and suffix-max arrays scanned by two pointers.

| # | Problem | Link |
|---|---|---|
| 1 | [Max of Index Diff and Min Value Product](https://www.geeksforgeeks.org/problems/find-maximum-value/1) | [`21. Max of Index Diff and Min Value Product/`](21.%20Max%20of%20Index%20Diff%20and%20Min%20Value%20Product/) |

## Pattern 6: Read-Write / Slow-Fast Pointers (In-Place)

Two pointers move in the same direction at different rates. In-place compaction (remove duplicates from a sorted array, sort a binary array) keeps a `write` index that advances only when an element is kept. For a repeated value in `1..n-1`, treat values as next-pointers and use Floyd's slow/fast cycle detection, or a sum/XOR trick.

| # | Problem | Link |
|---|---|---|
| 1 | [Remove Duplicates Sorted Array](https://www.geeksforgeeks.org/problems/remove-duplicate-elements-from-sorted-array/1) | [`02. Remove Duplicates Sorted Array/`](02.%20Remove%20Duplicates%20Sorted%20Array/) |
| 2 | [Find Only Repetitive Element from 1 to n-1](https://www.geeksforgeeks.org/problems/find-repetitive-element-from-1-to-n-1/1) | [`14. Find Only Repetitive Element from 1 to n-1/`](14.%20Find%20Only%20Repetitive%20Element%20from%201%20to%20n-1/) |

## Pattern 7: Linear Scan with Start/End Markers

One index scans the input while a second index (or a counter) remembers where the current segment began. When the segment ends, emit it or update the answer. Examples: extract the integers from a string, find the matching closing bracket by counting depth, and find the longest run of non-negative values.

| # | Problem | Link |
|---|---|---|
| 1 | [Length of longest subarray](https://www.geeksforgeeks.org/problems/length-of-longest-subarray0440/1) | [`16. Length of longest subarray/`](16.%20Length%20of%20longest%20subarray/) |
| 2 | [Closing Bracket Index](https://www.geeksforgeeks.org/problems/closing-bracket-index5900/1) | [`17. Closing Bracket Index/`](17.%20Closing%20Bracket%20Index/) |
