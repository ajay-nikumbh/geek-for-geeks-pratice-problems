# Sorting — Easy: Patterns

These are the recurring patterns across the 55 Easy-level Sorting problems. Most sort first and then either scan neighbours or a fixed window, or make a greedy pairing choice. The rest implement the basic sorts (bubble, selection, insertion, counting), write custom comparators, merge sorted arrays, or handle intervals.

## Pattern 1: Sort + Greedy Pairing / Assignment

Many optimisation problems become a single pass once the data is sorted. To maximise a sum of products, pair large with large. To minimise it, pair large with small. To satisfy as many requests as possible, match the smallest item that still fits. To fill limited capacity, take the most valuable units first. Digit problems sort the digits and then build the number greedily (alternate digits into two numbers, put the smallest even digit last). Each variant needs a short exchange argument: swapping any out-of-order pair cannot improve the answer.

| # | Problem | Link |
|---|---|---|
| 1 | [Max Value Permutation](https://www.geeksforgeeks.org/problems/maximize-arrii-of-an-array0026/1) | [`06. Max Value Permutation/`](06.%20Max%20Value%20Permutation/) |
| 2 | [Permute Arrays for Sum Threshold](https://www.geeksforgeeks.org/problems/permutations-in-array1747/1) | [`22. Permute Arrays for Sum Threshold/`](22.%20Permute%20Arrays%20for%20Sum%20Threshold/) |
| 3 | [Bus Conductor](https://www.geeksforgeeks.org/problems/bus-conductor--170647/1) | [`23. Bus Conductor/`](23.%20Bus%20Conductor/) |
| 4 | [Fitting an Array into Another](https://www.geeksforgeeks.org/problems/fitting-the-array1514/1) | [`24. Fitting an Array into Another/`](24.%20Fitting%20an%20Array%20into%20Another/) |
| 5 | [Tywin's War Strategy](https://www.geeksforgeeks.org/problems/tywins-war-strategy0527/1) | [`28. Tywin's War Strategy/`](28.%20Tywin's%20War%20Strategy/) |
| 6 | [Assign Cookies](https://www.geeksforgeeks.org/problems/assign-cookies/1) | [`30. Assign Cookies/`](30.%20Assign%20Cookies/) |
| 7 | [Max Sum of Products from Two Arrays](https://www.geeksforgeeks.org/problems/maximum-possible-sum-of-products3637/1) | [`39. Max Sum of Products from Two Arrays/`](39.%20Max%20Sum%20of%20Products%20from%20Two%20Arrays/) |
| 8 | [Next Greater Even Number](https://www.geeksforgeeks.org/problems/next-greater-even-number0828/1) | [`43. Next Greater Even Number/`](43.%20Next%20Greater%20Even%20Number/) |
| 9 | [Rearrange for Largest Even Number](https://www.geeksforgeeks.org/problems/largest-even-number3821/1) | [`44. Rearrange for Largest Even Number/`](44.%20Rearrange%20for%20Largest%20Even%20Number/) |

## Pattern 2: Sort Then Linear Scan (Adjacent Gaps / Fixed Window / Runs)

Sorting puts close values next to each other. The minimum difference of any pair is then the minimum adjacent gap. The smallest spread among k chosen values is the best window `a[i+k-1] - a[i]`. The number of consecutive-number groups is one plus the number of gaps larger than 1. Other scans count distinct values, compute an H-index (`a[i] >= n - i`), or track a prefix maximum to find split points. Circular data, such as clock times, also compares the last element with the first plus one full cycle.

| # | Problem | Link |
|---|---|---|
| 1 | [Check Sorted Array](https://www.geeksforgeeks.org/problems/check-if-an-array-is-sorted0701/1) | [`03. Check Sorted Array/`](03.%20Check%20Sorted%20Array/) |
| 2 | [Chocolate Distribution Problem](https://www.geeksforgeeks.org/problems/chocolate-distribution-problem3825/1) | [`08. Chocolate Distribution Problem/`](08.%20Chocolate%20Distribution%20Problem/) |
| 3 | [Minimum Distance between Two Words](https://www.geeksforgeeks.org/problems/closest-strings0611/1) | [`17. Minimum Distance between Two Words/`](17.%20Minimum%20Distance%20between%20Two%20Words/) |
| 4 | [Min Diff Pair](https://www.geeksforgeeks.org/problems/minimum-difference-pair5444/1) | [`21. Min Diff Pair/`](21.%20Min%20Diff%20Pair/) |
| 5 | [Minimize Difference in Task Priorities](https://www.geeksforgeeks.org/problems/minimum-difference-among-k5805/1) | [`31. Minimize Difference in Task Priorities/`](31.%20Minimize%20Difference%20in%20Task%20Priorities/) |
| 6 | [Minimum Difference in an Array](https://www.geeksforgeeks.org/problems/minimum-difference-in-an-array/1) | [`32. Minimum Difference in an Array/`](32.%20Minimum%20Difference%20in%20an%20Array/) |
| 7 | [Min Subsets with Consecutive Numbers](https://www.geeksforgeeks.org/problems/min-subsets-with-consecutive-numbers0601/1) | [`35. Min Subsets with Consecutive Numbers/`](35.%20Min%20Subsets%20with%20Consecutive%20Numbers/) |
| 8 | [Rope Cutting](https://www.geeksforgeeks.org/problems/rope-cutting3334/1) | [`45. Rope Cutting/`](45.%20Rope%20Cutting/) |
| 9 | [Maximum Partitions to Make a Permutation Sorted](https://www.geeksforgeeks.org/problems/maximum-number-of-partitions-that-can-be-sorted-individually-to-make-sorted2926/1) | [`50. Maximum Partitions to Make a Permutation Sorted/`](50.%20Maximum%20Partitions%20to%20Make%20a%20Permutation%20Sorted/) |
| 10 | [Minimum Add/Subtract to Equalize Array](https://www.geeksforgeeks.org/problems/equalize-an-array3405/1) | [`51. Minimum AddSubtract to Equalize Array/`](51.%20Minimum%20AddSubtract%20to%20Equalize%20Array/) |

## Pattern 3: Split, Sort Segments, Reassemble (Alternate / Wave / Parity)

The output order is not one global sort but a combination of sorted groups. Alternative sorting takes from both ends of a sorted array in turn. Wave arrays swap adjacent pairs of a sorted array. Odd-first or even-first orders sort each class and concatenate. Case-specific sorting sorts the upper- and lower-case letters separately and refills each original slot with the next letter of its own case. Other variants sort only a subarray, every element except one, or each matrix diagonal on its own.

| # | Problem | Link |
|---|---|---|
| 1 | [Even Greater than Odd](https://www.geeksforgeeks.org/problems/rearrange-array-such-that-even-positioned-are-greater-than-odd4804/1) | [`34. Even Greater than Odd/`](34.%20Even%20Greater%20than%20Odd/) |
| 2 | [Sort a Subarray](https://www.geeksforgeeks.org/problems/part-sort2851/1) | [`40. Sort a Subarray/`](40.%20Sort%20a%20Subarray/) |
| 3 | [Bitonic Generator Sort](https://www.geeksforgeeks.org/problems/bitonic-generator-sort3343/1) | [`41. Bitonic Generator Sort/`](41.%20Bitonic%20Generator%20Sort/) |
| 4 | [Sorting All Except One](https://www.geeksforgeeks.org/problems/sorting-all-array-elements-except-one4653/1) | [`42. Sorting All Except One/`](42.%20Sorting%20All%20Except%20One/) |
| 5 | [Unusual String Sort](https://www.geeksforgeeks.org/problems/unusual-string-sort0405/1) | [`49. Unusual String Sort/`](49.%20Unusual%20String%20Sort/) |

## Pattern 4: Merge-Based Processing (Merge / Inversions / Multi-Array Scan)

The merge step of merge sort is a pattern of its own. On two or three sorted arrays it produces a merged order, a union, or an intersection, and on three arrays it finds the triplet with the smallest spread by advancing the minimum. Inside merge sort, every time an element from the right half is placed before remaining left-half elements, those pairs are inversions. Recording this per index gives the count of smaller elements on the right. A sorted array transformed by a quadratic is merged from both ends, and a prefix-sorted array only needs its suffix sorted and merged.

| # | Problem | Link |
|---|---|---|
| 1 | [Intersection of Two Sorted Arrays](https://www.geeksforgeeks.org/problems/intersection-of-two-sorted-array-1587115620/1) | [`13. Intersection of Two Sorted Arrays/`](13.%20Intersection%20of%20Two%20Sorted%20Arrays/) |
| 2 | [Intersection of Two Sorted Arrays](https://www.geeksforgeeks.org/problems/intersection-of-two-sorted-arrays-with-duplicate-elements/1) | [`26. Intersection of Two Sorted Arrays/`](26.%20Intersection%20of%20Two%20Sorted%20Arrays/) |
| 3 | [Merge two Unsorted Arrays](https://www.geeksforgeeks.org/problems/merging-two-unsorted-arrays-in-sorted-order1020/1) | [`33. Merge two Unsorted Arrays/`](33.%20Merge%20two%20Unsorted%20Arrays/) |

## Pattern 5: Order Statistics: Kth / Top-K / Heap

Only a few positions of the sorted order matter. A max-heap of size k keeps the k smallest elements, and its top is the kth smallest. Quickselect partitions around a pivot and recurses into one side only. A k-sorted array is fixed by sliding a min-heap of size k+1 across it. Simpler cases just sort and index: the median survives alternate max-min removal, all but the top two are the answer, or the product of the k smallest values is taken modulo a prime. Repeatedly combining the two smallest values uses a min-heap.

| # | Problem | Link |
|---|---|---|
| 1 | [Minimum Product of k Elements](https://www.geeksforgeeks.org/problems/minimum-product-of-k-integers2553/1) | [`19. Minimum Product of k Elements/`](19.%20Minimum%20Product%20of%20k%20Elements/) |
| 2 | [Last Remaining After Alternate Max-Min Removal](https://www.geeksforgeeks.org/problems/print-the-left-element2009/1) | [`20. Last Remaining After Alternate Max-Min Removal/`](20.%20Last%20Remaining%20After%20Alternate%20Max-Min%20Removal/) |
| 3 | [Minimize the sum](https://www.geeksforgeeks.org/problems/minimize-the-sum--170645/1) | [`29. Minimize the sum/`](29.%20Minimize%20the%20sum/) |
| 4 | [Indexes of Top K](https://www.geeksforgeeks.org/problems/toppers-of-class3826/1) | [`38. Indexes of Top K/`](38.%20Indexes%20of%20Top%20K/) |

## Pattern 6: Sort + Two Pointers (Pair / Triplet Counting)

Sorting gives the monotonic order that two-pointer moves need. For a pair with difference k, both pointers move left to right. For triangles, fix the largest side and count pairs on its left whose sum exceeds it: when `a[l] + a[r] > a[k]`, all of `l..r-1` work with `r`. Triplets with a sum in `[L, R]` are `count(<= R) - count(< L)`. Distinct absolute values merge from both ends while skipping duplicates.

| # | Problem | Link |
|---|---|---|
| 1 | [Pair With Difference](https://www.geeksforgeeks.org/problems/find-pair-given-difference1559/1) | [`05. Pair With Difference/`](05.%20Pair%20With%20Difference/) |
| 2 | [Distinct Absolutes in Array](https://www.geeksforgeeks.org/problems/distinct-absolute-array-elements4529/1) | [`37. Distinct Absolutes in Array/`](37.%20Distinct%20Absolutes%20in%20Array/) |
| 3 | [Good Pairs](https://www.geeksforgeeks.org/problems/good-pairs4519/1) | [`46. Good Pairs/`](46.%20Good%20Pairs/) |

## Pattern 7: Binary Search on Sorted Data

Once data is sorted, a value's position comes from a lower or upper bound. Floor and ceil are the two bounds. The smallest greater element for each value is an upper bound in a sorted copy. If each element is at most one place from its sorted position, compare `mid - 1`, `mid`, and `mid + 1` and then halve as usual. Counting pairs with `x^y > y^x` sorts one array and counts by bound, with special cases for 0 to 4. Maximising the minimum gap between k chosen points binary searches the gap and checks it greedily.

| # | Problem | Link |
|---|---|---|
| 1 | [Floor in a Sorted Array](https://www.geeksforgeeks.org/problems/floor-in-a-sorted-array-1587115620/1) | [`01. Floor in a Sorted Array/`](01.%20Floor%20in%20a%20Sorted%20Array/) |
| 2 | [Ceil in a Sorted Array](https://www.geeksforgeeks.org/problems/ceil-in-a-sorted-array/1) | [`14. Ceil in a Sorted Array/`](14.%20Ceil%20in%20a%20Sorted%20Array/) |
| 3 | [Smallest Greater in Whole Array](https://www.geeksforgeeks.org/problems/smallest-greater-elements-in-whole-array2751/1) | [`25. Smallest Greater in Whole Array/`](25.%20Smallest%20Greater%20in%20Whole%20Array/) |

## Pattern 8: Custom Comparator / Key-Based Sorting

The algorithm is a library sort. The work is the comparator. Sort by set-bit count, string length, distance from x, or frequency then value, and use a stable sort when ties must keep their input order. To form the largest number, put a before b when `a + b > b + a` as strings. To sort two arrays together, sort index pairs by the key array. The final position of one element after a stable sort is the number of smaller elements plus the equal elements before it.

| # | Problem | Link |
|---|---|---|
| 1 | [Sort by Set Bit Count](https://www.geeksforgeeks.org/problems/sort-by-set-bit-count1153/1) | [`15. Sort by Set Bit Count/`](15.%20Sort%20by%20Set%20Bit%20Count/) |
| 2 | [Sorting Two Arrays Together](https://www.geeksforgeeks.org/problems/sorting-employees5907/1) | [`36. Sorting Two Arrays Together/`](36.%20Sorting%20Two%20Arrays%20Together/) |
| 3 | [Stable Sort and Position](https://www.geeksforgeeks.org/problems/stable-sort-and-position1359/1) | [`48. Stable Sort and Position/`](48.%20Stable%20Sort%20and%20Position/) |

## Pattern 9: Implement a Sorting Algorithm

These problems test the algorithm, not its use. Bubble sort swaps adjacent out-of-order pairs, so after pass i the largest i values are in place. Selection sort moves the minimum of the unsorted suffix to its front. Insertion sort shifts the next element left into the sorted prefix. Merge sort splits in half, sorts each half recursively, and merges. Generic sorts take a comparator or template type. Know each algorithm's stability, best and worst case, and when it stops early.

| # | Problem | Link |
|---|---|---|
| 1 | [Bubble Sort](https://www.geeksforgeeks.org/problems/bubble-sort/1) | [`04. Bubble Sort/`](04.%20Bubble%20Sort/) |
| 2 | [Insertion Sort](https://www.geeksforgeeks.org/problems/insertion-sort/1) | [`07. Insertion Sort/`](07.%20Insertion%20Sort/) |
| 3 | [Selection Sort](https://www.geeksforgeeks.org/problems/selection-sort/1) | [`09. Selection Sort/`](09.%20Selection%20Sort/) |
| 4 | [Sort Array](https://www.geeksforgeeks.org/problems/sort-the-array0055/1) | [`11. Sort Array/`](11.%20Sort%20Array/) |

## Pattern 10: Non-Comparison Sorts (Counting / Radix / Index Placement)

When values are small integers or characters, skip comparisons. Counting sort counts each value and rewrites them in order, using prefix sums for stable placement. Radix sort runs a stable counting sort per digit, starting from the least significant one. Numbers in `[0, n^2)` are two digits in base n. A permutation of 1..n is sorted in place by swapping each value to index `value - 1` (cyclic sort). Strings over 26 letters are sorted with a 26-slot count array.

| # | Problem | Link |
|---|---|---|
| 1 | [Counting Sort](https://www.geeksforgeeks.org/problems/counting-sort/1) | [`16. Counting Sort/`](16.%20Counting%20Sort/) |
| 2 | [Sort an Array of 1 to n](https://www.geeksforgeeks.org/problems/sort-an-array-which-contains-1-to-n-values-using-mathematical-formula/1) | [`53. Sort an Array of 1 to n/`](53.%20Sort%20an%20Array%20of%201%20to%20n/) |
| 3 | [Smallest Rearrangement with No "cba" Subsequence](https://www.geeksforgeeks.org/problems/cba-subsequence--170645/1) | [`54. Smallest Rearrangement with No cba Subsequence/`](54.%20Smallest%20Rearrangement%20with%20No%20cba%20Subsequence/) |

## Pattern 11: Intervals & Sweep Line

Sort intervals by start to merge overlaps, or measure the gaps between merged blocks. Sort by end and pick greedily to keep the most non-overlapping intervals. To find the time with the most active intervals, split each interval into a start event (+1) and an end event (-1), sort the events, and keep a running sum. Count uncovered positions by subtracting the merged length from the total. Line-intersection problems map each line to the x-range where it meets a query and sweep those ranges.

| # | Problem | Link |
|---|---|---|
| 1 | [Overlapping Intervals](https://www.geeksforgeeks.org/problems/overlapping-intervals--174556/1) | [`47. Overlapping Intervals/`](47.%20Overlapping%20Intervals/) |
| 2 | [Count Uncovered Positions](https://www.geeksforgeeks.org/problems/race-in-fooland4522/1) | [`52. Count Uncovered Positions/`](52.%20Count%20Uncovered%20Positions/) |
| 3 | [Largest Gap in Intervals](https://www.geeksforgeeks.org/problems/largest-gap/1) | [`55. Largest Gap in Intervals/`](55.%20Largest%20Gap%20in%20Intervals/) |

## Pattern 12: Frequency Map / Rank Compression

Some sorting problems only need to know which values are equal or how they rank. Two strings are anagrams if their character counts match. Ranks come from sorting the distinct values once and storing value → rank in a map. Pairs with zero XOR are pairs of equal values, so each group of size c gives `c*(c-1)/2`. Distinct frequencies are checked by putting the counts in a set. Counting subarrays with median m maps each value to +1, -1, or 0 relative to m and counts prefix balances with a hash map.

| # | Problem | Link |
|---|---|---|
| 1 | [Anagram](https://www.geeksforgeeks.org/problems/anagram-1587115620/1) | [`02. Anagram/`](02.%20Anagram/) |
| 2 | [Replace Elements by Ranks](https://www.geeksforgeeks.org/problems/convert-an-array-to-reduced-form1101/1) | [`12. Replace Elements by Ranks/`](12.%20Replace%20Elements%20by%20Ranks/) |
| 3 | [Distinct Frequencies Check](https://www.geeksforgeeks.org/problems/unique-frequencies-of-not/1) | [`18. Distinct Frequencies Check/`](18.%20Distinct%20Frequencies%20Check/) |
| 4 | [Count Pairs with Zero XOR](https://www.geeksforgeeks.org/problems/counts-zeros-xor-pairs0349/1) | [`27. Count Pairs with Zero XOR/`](27.%20Count%20Pairs%20with%20Zero%20XOR/) |

## Pattern 13: Partition Schemes (Dutch Flag / Quick Sort)

Partitioning puts everything below a pivot to the left and everything above it to the right in one pass. The Dutch national flag keeps three regions with `low`, `mid`, and `high` pointers: a small value swaps to `low`, a large value swaps to `high`, and a middle value only advances `mid`. This sorts 0s, 1s and 2s, or splits around a range `[a, b]`. Quick sort applies Lomuto or Hoare partitioning recursively to both sides.

| # | Problem | Link |
|---|---|---|
| 1 | [Three way partitioning](https://www.geeksforgeeks.org/problems/three-way-partitioning/1) | [`10. Three way partitioning/`](10.%20Three%20way%20partitioning/) |
