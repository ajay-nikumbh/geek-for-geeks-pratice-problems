# Arrays — Hard: Patterns

These are the core recurring patterns observed across the Hard-level array problems in this set. Recognizing which pattern a problem belongs to is usually the fastest route from problem statement to an efficient solution.

## Pattern 1: Binary Search on the Answer (Minimize the Maximum)

Instead of searching the array, you binary search over the *space of possible answers* (a distance, a sum, a capacity) and use a greedy/feasibility check (usually O(n) or O(n log n)) to test whether a candidate answer is achievable. Applies whenever the problem asks to "minimize the maximum" or "maximize the minimum" of some quantity resulting from partitioning or placing elements.

| # | Problem | Link |
|---|---|---|
| 1 | [Minimize Max Distance of Adjacent Gas Stations](https://www.geeksforgeeks.org/problems/minimize-max-distance-to-gas-station/1) | [`03. Minimize Max Distance of Adjacent Gas Stations/`](03.%20Minimize%20Max%20Distance%20of%20Adjacent%20Gas%20Stations/) |
| 2 | [Split Array Largest Sum](https://www.geeksforgeeks.org/problems/split-array-largest-sum--141634/1) | [`05. Split Array Largest Sum/`](05.%20Split%20Array%20Largest%20Sum/) |

## Pattern 2: Median / Order Statistics via Binary Search Partitioning

Finding the k-th smallest element (or median) across two sorted arrays without merging them, by binary searching a partition point on the smaller array and verifying the left/right partition boundary condition in O(log(min(n,m))). Same core idea regardless of whether array sizes are equal or different.

| # | Problem | Link |
|---|---|---|
| 1 | [Median of 2 Sorted Arrays of Different Sizes](https://www.geeksforgeeks.org/problems/median-of-2-sorted-arrays-of-different-sizes/1) | [`02. Median of 2 Sorted Arrays of Different Sizes/`](02.%20Median%20of%202%20Sorted%20Arrays%20of%20Different%20Sizes/) |
| 2 | [Median of 2 Sorted Arrays of Same Size](https://www.geeksforgeeks.org/problems/median-of-2-sorted-arrays-of-same-size/1) | [`10. Median of 2 Sorted Arrays of Same Size/`](10.%20Median%20of%202%20Sorted%20Arrays%20of%20Same%20Size/) |

## Pattern 3: Counting via Order Statistics / Hashing (Inversion-like Counting)

Counting the number of pairs, subarrays, or index-relationships satisfying a condition, where brute force is O(n^2) but a smarter pass using a hash map of running state (for equal-occurrence balance) or a modified merge-sort / BIT (for the i*arr[i] > j*arr[j] ordering condition) brings it down to near-linear or O(n log n). The common thread is transforming an O(n^2) pairwise counting problem into a single pass with auxiliary state.

| # | Problem | Link |
|---|---|---|
| 1 | [Count Pairs with i * arr[i] > j * arr[j]](https://www.geeksforgeeks.org/problems/count-pairs-in-an-array4145/1) | [`06. Count Pairs with i arr[i] j arr[j]/`](06.%20Count%20Pairs%20with%20i%20arr%5Bi%5D%20j%20arr%5Bj%5D/) |
| 2 | [Count Subarrays with Equal Occurrences of Two](https://www.geeksforgeeks.org/problems/sub-arrays-with-equal-number-of-occurences3901/1) | [`07. Count Subarrays with Equal Occurrences of Two/`](07.%20Count%20Subarrays%20with%20Equal%20Occurrences%20of%20Two/) |

## Pattern 4: Combinatorial Counting via Binary Search / Two Pointers on Sorted Data

Counting the number of subsets/sub-selections satisfying a product or arrangement constraint. After sorting, a two-pointer or binary-search-on-count technique lets you count qualifying subsets or arrangements without enumerating them, often combined with combinatorics (nCr-style counting) for the distribution problem.

| # | Problem | Link |
|---|---|---|
| 1 | [Cake Distribution Problem](https://www.geeksforgeeks.org/problems/cake-distribution-problem--170647/1) | [`08. Cake Distribution Problem/`](08.%20Cake%20Distribution%20Problem/) |
| 2 | [Subset Count with Product Less Than k](https://www.geeksforgeeks.org/problems/number-of-subsets-with-product-less-than-k/1) | [`09. Subset Count with Product Less Than k/`](09.%20Subset%20Count%20with%20Product%20Less%20Than%20k/) |

## Pattern 5: Circular Array Extension of Kadane's Algorithm

Extends the classic maximum subarray sum (Kadane's) idea to a circular array: the answer is either the standard Kadane max subarray, or total sum minus the minimum subarray sum (representing the best wrap-around segment). Requires reasoning about the complement of the minimum subarray rather than searching the circular array directly.

| # | Problem | Link |
|---|---|---|
| 1 | [Max Circular Subarray Sum](https://www.geeksforgeeks.org/problems/max-circular-subarray-sum-1587115620/1) | [`01. Max Circular Subarray Sum/`](01.%20Max%20Circular%20Subarray%20Sum/) |

## Pattern 6: Constructive Digit/Array Manipulation

Building the answer directly by manipulating array elements (digits) in place using two-pointer scanning from the ends toward the center, handling edge cases (carries, all-9s, single digit) explicitly rather than via search or DP. Common in "next X" construction problems.

| # | Problem | Link |
|---|---|---|
| 1 | [Next Smallest Palindrome](https://www.geeksforgeeks.org/problems/next-smallest-palindrome4740/1) | [`04. Next Smallest Palindrome/`](04.%20Next%20Smallest%20Palindrome/) |
