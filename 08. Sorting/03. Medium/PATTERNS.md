# Sorting — Medium: Patterns

Medium-level Sorting problems (41) add the classic algorithms (merge sort, quick sort, radix sort, Dutch flag) and their uses: counting inversions during merge, quickselect and heaps for the kth element, two-pointer triangle and triplet counting, binary search on the answer, and interval sweeps.

## Pattern 1: Sort + Greedy Pairing / Assignment

Many optimisation problems become a single pass once the data is sorted. To maximise a sum of products, pair large with large. To minimise it, pair large with small. To satisfy as many requests as possible, match the smallest item that still fits. To fill limited capacity, take the most valuable units first. Digit problems sort the digits and then build the number greedily (alternate digits into two numbers, put the smallest even digit last). Each variant needs a short exchange argument: swapping any out-of-order pair cannot improve the answer.

| # | Problem | Link |
|---|---|---|
| 1 | [Min Sum Pair using Digits](https://www.geeksforgeeks.org/problems/minimum-sum4058/1) | [`07. Min Sum Pair using Digits/`](07.%20Min%20Sum%20Pair%20using%20Digits/) |
| 2 | [Max Profit from Two Machines](https://www.geeksforgeeks.org/problems/max-profit-from-two-machines/1) | [`12. Max Profit from Two Machines/`](12.%20Max%20Profit%20from%20Two%20Machines/) |
| 3 | [Equalize All Prefix Sums](https://www.geeksforgeeks.org/problems/equalize-all-prefix-sums/1) | [`21. Equalize All Prefix Sums/`](21.%20Equalize%20All%20Prefix%20Sums/) |
| 4 | [Max Gold Coins from Limited Plates](https://www.geeksforgeeks.org/problems/help-a-thief5938/1) | [`29. Max Gold Coins from Limited Plates/`](29.%20Max%20Gold%20Coins%20from%20Limited%20Plates/) |
| 5 | [Min Pair Product Sum  Rearrangement](https://www.geeksforgeeks.org/problems/minimize-sum-of-alternate-product2033/1) | [`33. Min Pair Product Sum Rearrangement/`](33.%20Min%20Pair%20Product%20Sum%20Rearrangement/) |

## Pattern 2: Sort Then Linear Scan (Adjacent Gaps / Fixed Window / Runs)

Sorting puts close values next to each other. The minimum difference of any pair is then the minimum adjacent gap. The smallest spread among k chosen values is the best window `a[i+k-1] - a[i]`. The number of consecutive-number groups is one plus the number of gaps larger than 1. Other scans count distinct values, compute an H-index (`a[i] >= n - i`), or track a prefix maximum to find split points. Circular data, such as clock times, also compares the last element with the first plus one full cycle.

| # | Problem | Link |
|---|---|---|
| 1 | [Find H-Index](https://www.geeksforgeeks.org/problems/find-h-index--165609/1) | [`14. Find H-Index/`](14.%20Find%20H-Index/) |
| 2 | [Difference Check](https://www.geeksforgeeks.org/problems/difference-check/1) | [`30. Difference Check/`](30.%20Difference%20Check/) |

## Pattern 3: Split, Sort Segments, Reassemble (Alternate / Wave / Parity)

The output order is not one global sort but a combination of sorted groups. Alternative sorting takes from both ends of a sorted array in turn. Wave arrays swap adjacent pairs of a sorted array. Odd-first or even-first orders sort each class and concatenate. Case-specific sorting sorts the upper- and lower-case letters separately and refills each original slot with the next letter of its own case. Other variants sort only a subarray, every element except one, or each matrix diagonal on its own.

| # | Problem | Link |
|---|---|---|
| 1 | [Wave Array](https://www.geeksforgeeks.org/problems/wave-array-1587115621/1) | [`05. Wave Array/`](05.%20Wave%20Array/) |
| 2 | [Case-specific Sorting of Strings](https://www.geeksforgeeks.org/problems/case-specific-sorting-of-strings4845/1) | [`13. Case-specific Sorting of Strings/`](13.%20Case-specific%20Sorting%20of%20Strings/) |
| 3 | [Sort in specific order](https://www.geeksforgeeks.org/problems/sort-in-specific-order2422/1) | [`17. Sort in specific order/`](17.%20Sort%20in%20specific%20order/) |
| 4 | [Largest Array Formation with Same Parity Swaps](https://www.geeksforgeeks.org/problems/even-swap/1) | [`26. Largest Array Formation with Same Parity Swaps/`](26.%20Largest%20Array%20Formation%20with%20Same%20Parity%20Swaps/) |
| 5 | [Rearrange to Maximize Alternate Addition Subtraction](https://www.geeksforgeeks.org/problems/reaching-the-heights1921/1) | [`31. Rearrange to Maximize Alternate Addition Subtraction/`](31.%20Rearrange%20to%20Maximize%20Alternate%20Addition%20Subtraction/) |
| 6 | [Sort Matrix Diagonally](https://www.geeksforgeeks.org/problems/diagonal-morning-assembly0028/1) | [`34. Sort Matrix Diagonally/`](34.%20Sort%20Matrix%20Diagonally/) |

## Pattern 4: Merge-Based Processing (Merge / Inversions / Multi-Array Scan)

The merge step of merge sort is a pattern of its own. On two or three sorted arrays it produces a merged order, a union, or an intersection, and on three arrays it finds the triplet with the smallest spread by advancing the minimum. Inside merge sort, every time an element from the right half is placed before remaining left-half elements, those pairs are inversions. Recording this per index gives the count of smaller elements on the right. A sorted array transformed by a quadratic is merged from both ends, and a prefix-sorted array only needs its suffix sorted and merged.

| # | Problem | Link |
|---|---|---|
| 1 | [Count Inversions](https://www.geeksforgeeks.org/problems/inversion-of-array-1587115620/1) | [`03. Count Inversions/`](03.%20Count%20Inversions/) |
| 2 | [Sort the given array after applying the given equation](https://www.geeksforgeeks.org/problems/sort-the-given-array-after-applying-the-given-equation0304/1) | [`19. Sort the given array after applying the given equation/`](19.%20Sort%20the%20given%20array%20after%20applying%20the%20given%20equation/) |
| 3 | [Merge three sorted arrays](https://www.geeksforgeeks.org/problems/merge-three-sorted-arrays-1587115620/1) | [`22. Merge three sorted arrays/`](22.%20Merge%20three%20sorted%20arrays/) |
| 4 | [Smallest Diff Triplet in Three Arrays](https://www.geeksforgeeks.org/problems/happiest-triplet2921/1) | [`27. Smallest Diff Triplet in Three Arrays/`](27.%20Smallest%20Diff%20Triplet%20in%20Three%20Arrays/) |
| 5 | [Sort a Prefix Sorted Array](https://www.geeksforgeeks.org/problems/sort-last-m-elements--155156/1) | [`40. Sort a Prefix Sorted Array/`](40.%20Sort%20a%20Prefix%20Sorted%20Array/) |

## Pattern 5: Order Statistics: Kth / Top-K / Heap

Only a few positions of the sorted order matter. A max-heap of size k keeps the k smallest elements, and its top is the kth smallest. Quickselect partitions around a pivot and recurses into one side only. A k-sorted array is fixed by sliding a min-heap of size k+1 across it. Simpler cases just sort and index: the median survives alternate max-min removal, all but the top two are the answer, or the product of the k smallest values is taken modulo a prime. Repeatedly combining the two smallest values uses a min-heap.

| # | Problem | Link |
|---|---|---|
| 1 | [Kth Smallest](https://www.geeksforgeeks.org/problems/kth-smallest-element5635/1) | [`02. Kth Smallest/`](02.%20Kth%20Smallest/) |
| 2 | [Nearly sorted](https://www.geeksforgeeks.org/problems/nearly-sorted-1587115620/1) | [`11. Nearly sorted/`](11.%20Nearly%20sorted/) |

## Pattern 6: Sort + Two Pointers (Pair / Triplet Counting)

Sorting gives the monotonic order that two-pointer moves need. For a pair with difference k, both pointers move left to right. For triangles, fix the largest side and count pairs on its left whose sum exceeds it: when `a[l] + a[r] > a[k]`, all of `l..r-1` work with `r`. Triplets with a sum in `[L, R]` are `count(<= R) - count(< L)`. Distinct absolute values merge from both ends while skipping duplicates.

| # | Problem | Link |
|---|---|---|
| 1 | [Count the Number of Possible Triangles](https://www.geeksforgeeks.org/problems/count-possible-triangles-1587115620/1) | [`09. Count the Number of Possible Triangles/`](09.%20Count%20the%20Number%20of%20Possible%20Triangles/) |
| 2 | [Triplet Family](https://www.geeksforgeeks.org/problems/triplet-family/1) | [`16. Triplet Family/`](16.%20Triplet%20Family/) |
| 3 | [Triplets with Sum in Range](https://www.geeksforgeeks.org/problems/triplets-with-sum-with-given-range/1) | [`18. Triplets with Sum in Range/`](18.%20Triplets%20with%20Sum%20in%20Range/) |
| 4 | [Count the number of possible triangles](https://www.geeksforgeeks.org/problems/count-possible-triangles-1587115620--094125/1) | [`41. Count the number of possible triangles/`](41.%20Count%20the%20number%20of%20possible%20triangles/) |

## Pattern 7: Binary Search on Sorted Data

Once data is sorted, a value's position comes from a lower or upper bound. Floor and ceil are the two bounds. The smallest greater element for each value is an upper bound in a sorted copy. If each element is at most one place from its sorted position, compare `mid - 1`, `mid`, and `mid + 1` and then halve as usual. Counting pairs with `x^y > y^x` sorts one array and counts by bound, with special cases for 0 to 4. Maximising the minimum gap between k chosen points binary searches the gap and checks it greedily.

| # | Problem | Link |
|---|---|---|
| 1 | [Count Power Pairs from Two Arrays](https://www.geeksforgeeks.org/problems/number-of-pairs3422/1) | [`10. Count Power Pairs from Two Arrays/`](10.%20Count%20Power%20Pairs%20from%20Two%20Arrays/) |
| 2 | [Search in an almost Sorted Array](https://www.geeksforgeeks.org/problems/search-in-an-almost-sorted-array/1) | [`20. Search in an almost Sorted Array/`](20.%20Search%20in%20an%20almost%20Sorted%20Array/) |
| 3 | [Closer to sort](https://www.geeksforgeeks.org/problems/closer-to-sort-1587115620/1) | [`24. Closer to sort/`](24.%20Closer%20to%20sort/) |
| 4 | [Maximize the minimum difference between k elements](https://www.geeksforgeeks.org/problems/maximize-the-minimum-difference-between-k-elements/1) | [`32. Maximize the minimum difference between k elements/`](32.%20Maximize%20the%20minimum%20difference%20between%20k%20elements/) |

## Pattern 8: Custom Comparator / Key-Based Sorting

The algorithm is a library sort. The work is the comparator. Sort by set-bit count, string length, distance from x, or frequency then value, and use a stable sort when ties must keep their input order. To form the largest number, put a before b when `a + b > b + a` as strings. To sort two arrays together, sort index pairs by the key array. The final position of one element after a stable sort is the number of smaller elements plus the equal elements before it.

| # | Problem | Link |
|---|---|---|
| 1 | [Form the Largest Number](https://www.geeksforgeeks.org/problems/largest-number-formed-from-an-array1117/1) | [`08. Form the Largest Number/`](08.%20Form%20the%20Largest%20Number/) |
| 2 | [Sort by Absolute Difference](https://www.geeksforgeeks.org/problems/sort-by-absolute-difference-1587115621/1) | [`15. Sort by Absolute Difference/`](15.%20Sort%20by%20Absolute%20Difference/) |
| 3 | [Sort by Frequency](https://www.geeksforgeeks.org/problems/sort-string-according-to-increasing-frequency/1) | [`38. Sort by Frequency/`](38.%20Sort%20by%20Frequency/) |
| 4 | [Sort an array of strings according to string lengths](https://www.geeksforgeeks.org/problems/sort-an-array-of-strings-according-to-string-lengths/1) | [`39. Sort an array of strings according to string lengths/`](39.%20Sort%20an%20array%20of%20strings%20according%20to%20string%20lengths/) |

## Pattern 9: Implement a Sorting Algorithm

These problems test the algorithm, not its use. Bubble sort swaps adjacent out-of-order pairs, so after pass i the largest i values are in place. Selection sort moves the minimum of the unsorted suffix to its front. Insertion sort shifts the next element left into the sorted prefix. Merge sort splits in half, sorts each half recursively, and merges. Generic sorts take a comparator or template type. Know each algorithm's stability, best and worst case, and when it stops early.

| # | Problem | Link |
|---|---|---|
| 1 | [Merge Sort](https://www.geeksforgeeks.org/problems/merge-sort/1) | [`06. Merge Sort/`](06.%20Merge%20Sort/) |
| 2 | [C++ Generic sort](https://www.geeksforgeeks.org/problems/c-generic-sort/1) | [`28. C++ Generic sort/`](28.%20C++%20Generic%20sort/) |

## Pattern 10: Non-Comparison Sorts (Counting / Radix / Index Placement)

When values are small integers or characters, skip comparisons. Counting sort counts each value and rewrites them in order, using prefix sums for stable placement. Radix sort runs a stable counting sort per digit, starting from the least significant one. Numbers in `[0, n^2)` are two digits in base n. A permutation of 1..n is sorted in place by swapping each value to index `value - 1` (cyclic sort). Strings over 26 letters are sorted with a 26-slot count array.

| # | Problem | Link |
|---|---|---|
| 1 | [Radix Sort](https://www.geeksforgeeks.org/problems/radix-sort/1) | [`35. Radix Sort/`](35.%20Radix%20Sort/) |
| 2 | [Sort Numbers in Limited Range](https://www.geeksforgeeks.org/problems/efficiently-sorting-number-from-0-to-n2-15444/1) | [`36. Sort Numbers in Limited Range/`](36.%20Sort%20Numbers%20in%20Limited%20Range/) |

## Pattern 11: Intervals & Sweep Line

Sort intervals by start to merge overlaps, or measure the gaps between merged blocks. Sort by end and pick greedily to keep the most non-overlapping intervals. To find the time with the most active intervals, split each interval into a start event (+1) and an end event (-1), sort the events, and keep a running sum. Count uncovered positions by subtracting the merged length from the total. Line-intersection problems map each line to the x-range where it meets a query and sweep those ranges.

| # | Problem | Link |
|---|---|---|
| 1 | [Maximum Intersecting Lines](https://www.geeksforgeeks.org/problems/maximum-intersecting-lines--170647/1) | [`23. Maximum Intersecting Lines/`](23.%20Maximum%20Intersecting%20Lines/) |
| 2 | [Maximum Intervals Overlap](https://www.geeksforgeeks.org/problems/maximum-intervals-overlap5708/1) | [`25. Maximum Intervals Overlap/`](25.%20Maximum%20Intervals%20Overlap/) |
| 3 | [Max Non Overlapping Intervals](https://www.geeksforgeeks.org/problems/maximum-selections--170637/1) | [`37. Max Non Overlapping Intervals/`](37.%20Max%20Non%20Overlapping%20Intervals/) |

## Pattern 12: Partition Schemes (Dutch Flag / Quick Sort)

Partitioning puts everything below a pivot to the left and everything above it to the right in one pass. The Dutch national flag keeps three regions with `low`, `mid`, and `high` pointers: a small value swaps to `low`, a large value swaps to `high`, and a middle value only advances `mid`. This sorts 0s, 1s and 2s, or splits around a range `[a, b]`. Quick sort applies Lomuto or Hoare partitioning recursively to both sides.

| # | Problem | Link |
|---|---|---|
| 1 | [Sort 0s, 1s and 2s](https://www.geeksforgeeks.org/problems/sort-an-array-of-0s-1s-and-2s4231/1) | [`01. Sort 0s, 1s and 2s/`](01.%20Sort%200s,%201s%20and%202s/) |
| 2 | [Quick Sort](https://www.geeksforgeeks.org/problems/quick-sort/1) | [`04. Quick Sort/`](04.%20Quick%20Sort/) |
