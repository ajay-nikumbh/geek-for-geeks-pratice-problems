# Two Pointers — Medium: Patterns

Medium-level Two Pointers problems (20) extend the Easy patterns: pair search grows into 3-Sum and 4-Sum, merge scans move to intervals, and same-direction pointers become sliding windows with a frequency map.

## Pattern 1: Opposite-Ends Pair Search (Sorted Input)

The classic two-pointer move: on a sorted sequence, place `left` at the start and `right` at the end. If `a[left] + a[right]` is too small, move `left` right; if too large, move `right` left. Each step discards one candidate for good, so the whole search is linear. Variants count all pairs below a limit (add `right - left` in one go), track the closest sum, handle duplicates when counting, or run the same idea on a doubly linked list or a rotated array (start at the pivot and wrap with modulo).

| # | Problem | Link |
|---|---|---|
| 1 | [Count Pairs with Sum](https://www.geeksforgeeks.org/problems/count-pairs-with-given-sum--150253/1) | [`12. Count Pairs with Sum/`](12.%20Count%20Pairs%20with%20Sum/) |
| 2 | [Pair Sum in a Sorted and Rotated Array](https://www.geeksforgeeks.org/problems/pair-sum-in-a-sorted-and-rotated-array/1) | [`17. Pair Sum in a Sorted and Rotated Array/`](17.%20Pair%20Sum%20in%20a%20Sorted%20and%20Rotated%20Array/) |

## Pattern 2: Fix One + Pair Search (3-Sum / 4-Sum / k-Sum)

k-Sum problems reduce to pair search. Sort the array, loop over the first element (and the second for 4-Sum), and solve the remaining 2-Sum with opposite-ends pointers on the suffix. Skip equal neighbours to emit only distinct tuples. The same frame handles counting triplets below a target, finding the closest triplet sum, or checking if one element is the sum of the other two (fix the largest, search the pair on its left).

| # | Problem | Link |
|---|---|---|
| 1 | [Triplet Sum in Array](https://www.geeksforgeeks.org/problems/triplet-sum-in-array-1587115621/1) | [`02. Triplet Sum in Array/`](02.%20Triplet%20Sum%20in%20Array/) |
| 2 | [Find triplets with zero sum](https://www.geeksforgeeks.org/problems/find-triplets-with-zero-sum/1) | [`04. Find triplets with zero sum/`](04.%20Find%20triplets%20with%20zero%20sum/) |
| 3 | [4 Sum - All Quadruples](https://www.geeksforgeeks.org/problems/find-all-four-sum-numbers1732/1) | [`07. 4 Sum - All Quadruples/`](07.%204%20Sum%20-%20All%20Quadruples/) |
| 4 | [Triplets with Smaller Sum](https://www.geeksforgeeks.org/problems/count-triplets-with-sum-smaller-than-x5549/1) | [`09. Triplets with Smaller Sum/`](09.%20Triplets%20with%20Smaller%20Sum/) |
| 5 | [Closest Three Sum](https://www.geeksforgeeks.org/problems/three-sum-closest/1) | [`11. Closest Three Sum/`](11.%20Closest%20Three%20Sum/) |
| 6 | [Count all triplets with given sum in sorted array](https://www.geeksforgeeks.org/problems/count-all-triplets-with-given-sum-in-sorted-array/1) | [`13. Count all triplets with given sum in sorted array/`](13.%20Count%20all%20triplets%20with%20given%20sum%20in%20sorted%20array/) |

## Pattern 3: Merge-Style Scan of Sorted Sequences

When two (or three) sequences are each sorted, keep one index per sequence and repeatedly advance the one pointing at the smaller element. This is the merge step of merge sort, and it also yields union, intersection (with or without duplicates), and the minimum spread across three arrays. Interval versions advance the interval that ends first. The in-place variant (merge without extra space) uses the gap method or swaps from the boundary.

| # | Problem | Link |
|---|---|---|
| 1 | [Union of 2 Sorted Arrays](https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays-1587115621/1) | [`01. Union of 2 Sorted Arrays/`](01.%20Union%20of%202%20Sorted%20Arrays/) |
| 2 | [Merge Without Extra Space](https://www.geeksforgeeks.org/problems/merge-two-sorted-arrays-1587115620/1) | [`05. Merge Without Extra Space/`](05.%20Merge%20Without%20Extra%20Space/) |
| 3 | [Earliest Common Slot](https://www.geeksforgeeks.org/problems/earliest-common-slot/1) | [`19. Earliest Common Slot/`](19.%20Earliest%20Common%20Slot/) |
| 4 | [Interval List Intersections](https://www.geeksforgeeks.org/problems/interval-list-intersections/1) | [`20. Interval List Intersections/`](20.%20Interval%20List%20Intersections/) |

## Pattern 4: Palindrome / Reverse from Both Ends (Strings)

String problems where the answer depends on mirrored positions. Compare `s[left]` and `s[right]` for palindromes, or swap them to reverse. The twist in each variant is which characters to skip: spaces stay in place, non-letters are ignored, or reversal happens only among selected characters.

| # | Problem | Link |
|---|---|---|
| 1 | [Remove and Reverse](https://www.geeksforgeeks.org/problems/remove-and-reverse--170634/1) | [`15. Remove and Reverse/`](15.%20Remove%20and%20Reverse/) |

## Pattern 5: Container / Greedy Shrink from Both Ends

Objective has the form `(j - i) * min(a[i], a[j])` or `j - i` subject to a value condition. Start at the widest pair. Moving the taller side can never help because width shrinks and the minimum cannot grow, so always move the shorter side. Maximum Index uses the same idea with prefix-min and suffix-max arrays scanned by two pointers.

| # | Problem | Link |
|---|---|---|
| 1 | [Maximum Index](https://www.geeksforgeeks.org/problems/maximum-index-1587115620/1) | [`03. Maximum Index/`](03.%20Maximum%20Index/) |
| 2 | [Container With Most Water](https://www.geeksforgeeks.org/problems/container-with-most-water0535/1) | [`10. Container With Most Water/`](10.%20Container%20With%20Most%20Water/) |
| 3 | [Maximum Area Between Bars](https://www.geeksforgeeks.org/problems/maximum-area-between-bars/1) | [`16. Maximum Area Between Bars/`](16.%20Maximum%20Area%20Between%20Bars/) |

## Pattern 6: Variable-Size Sliding Window

A same-direction two-pointer: `right` grows the window one step at a time, and `left` moves forward only while the window is invalid. A frequency map tracks the window contents. Use it for longest substring with at most K distinct characters, longest run after K replacements (`window - maxFreq <= k`), or counting substrings that contain all required characters (add `left` positions once valid).

| # | Problem | Link |
|---|---|---|
| 1 | [Longest Substring with K Uniques](https://www.geeksforgeeks.org/problems/longest-k-unique-characters-substring0853/1) | [`06. Longest Substring with K Uniques/`](06.%20Longest%20Substring%20with%20K%20Uniques/) |
| 2 | [Longest Repeating Character Replacement](https://www.geeksforgeeks.org/problems/longest-repeating-character-replacement/1) | [`14. Longest Repeating Character Replacement/`](14.%20Longest%20Repeating%20Character%20Replacement/) |
| 3 | [Count Substrings with a, b and c](https://www.geeksforgeeks.org/problems/count-substring/1) | [`18. Count Substrings with a, b and c/`](18.%20Count%20Substrings%20with%20a,%20b%20and%20c/) |

## Pattern 7: Read-Write / Slow-Fast Pointers (In-Place)

Two pointers move in the same direction at different rates. In-place compaction (remove duplicates from a sorted array, sort a binary array) keeps a `write` index that advances only when an element is kept. For a repeated value in `1..n-1`, treat values as next-pointers and use Floyd's slow/fast cycle detection, or a sum/XOR trick.

| # | Problem | Link |
|---|---|---|
| 1 | [Binary Array Sorting](https://www.geeksforgeeks.org/problems/binary-array-sorting-1587115620/1) | [`08. Binary Array Sorting/`](08.%20Binary%20Array%20Sorting/) |
