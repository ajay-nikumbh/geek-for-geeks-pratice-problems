# Sorting — Hard: Patterns

Hard-level Sorting problems (2) count relationships across positions: smaller elements to the right via merge sort (or a Fenwick tree), and subarrays with a given median via a +1/-1 balance and a prefix-count map.

## Pattern 1: Merge-Based Processing (Merge / Inversions / Multi-Array Scan)

The merge step of merge sort is a pattern of its own. On two or three sorted arrays it produces a merged order, a union, or an intersection, and on three arrays it finds the triplet with the smallest spread by advancing the minimum. Inside merge sort, every time an element from the right half is placed before remaining left-half elements, those pairs are inversions. Recording this per index gives the count of smaller elements on the right. A sorted array transformed by a quadratic is merged from both ends, and a prefix-sorted array only needs its suffix sorted and merged.

| # | Problem | Link |
|---|---|---|
| 1 | [Count Smaller on Right](https://www.geeksforgeeks.org/problems/count-smaller-elements2214/1) | [`01. Count Smaller on Right/`](01.%20Count%20Smaller%20on%20Right/) |

## Pattern 2: Frequency Map / Rank Compression

Some sorting problems only need to know which values are equal or how they rank. Two strings are anagrams if their character counts match. Ranks come from sorting the distinct values once and storing value → rank in a map. Pairs with zero XOR are pairs of equal values, so each group of size c gives `c*(c-1)/2`. Distinct frequencies are checked by putting the counts in a set. Counting subarrays with median m maps each value to +1, -1, or 0 relative to m and counts prefix balances with a hash map.

| # | Problem | Link |
|---|---|---|
| 1 | [Count Subarrays with Given Median](https://www.geeksforgeeks.org/problems/median-of-the-subarrays--170647/1) | [`02. Count Subarrays with Given Median/`](02.%20Count%20Subarrays%20with%20Given%20Median/) |
