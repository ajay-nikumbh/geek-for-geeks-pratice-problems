# Sorting — Basics: Patterns

Basics-level Sorting problems (5) use a library sort plus one simple step: drop the top elements, interleave from both ends, merge two arrays, count characters, or check the first valid triangle from the largest side.

## Pattern 1: Sort + Greedy Pairing / Assignment

Many optimisation problems become a single pass once the data is sorted. To maximise a sum of products, pair large with large. To minimise it, pair large with small. To satisfy as many requests as possible, match the smallest item that still fits. To fill limited capacity, take the most valuable units first. Digit problems sort the digits and then build the number greedily (alternate digits into two numbers, put the smallest even digit last). Each variant needs a short exchange argument: swapping any out-of-order pair cannot improve the answer.

| # | Problem | Link |
|---|---|---|
| 1 | [Maximum Perimeter of Triangle from Array](https://www.geeksforgeeks.org/problems/maximum-perimeter-of-triangle-from-array4322/1) | [`05. Maximum Perimeter of Triangle from Array/`](05.%20Maximum%20Perimeter%20of%20Triangle%20from%20Array/) |

## Pattern 2: Split, Sort Segments, Reassemble (Alternate / Wave / Parity)

The output order is not one global sort but a combination of sorted groups. Alternative sorting takes from both ends of a sorted array in turn. Wave arrays swap adjacent pairs of a sorted array. Odd-first or even-first orders sort each class and concatenate. Case-specific sorting sorts the upper- and lower-case letters separately and refills each original slot with the next letter of its own case. Other variants sort only a subarray, every element except one, or each matrix diagonal on its own.

| # | Problem | Link |
|---|---|---|
| 1 | [Alternative Sorting](https://www.geeksforgeeks.org/problems/alternative-sorting1311/1) | [`03. Alternative Sorting/`](03.%20Alternative%20Sorting/) |

## Pattern 3: Merge-Based Processing (Merge / Inversions / Multi-Array Scan)

The merge step of merge sort is a pattern of its own. On two or three sorted arrays it produces a merged order, a union, or an intersection, and on three arrays it finds the triplet with the smallest spread by advancing the minimum. Inside merge sort, every time an element from the right half is placed before remaining left-half elements, those pairs are inversions. Recording this per index gives the count of smaller elements on the right. A sorted array transformed by a quadratic is merged from both ends, and a prefix-sorted array only needs its suffix sorted and merged.

| # | Problem | Link |
|---|---|---|
| 1 | [Merge and Sort](https://www.geeksforgeeks.org/problems/merge-and-sort5821/1) | [`04. Merge and Sort/`](04.%20Merge%20and%20Sort/) |

## Pattern 4: Order Statistics: Kth / Top-K / Heap

Only a few positions of the sorted order matter. A max-heap of size k keeps the k smallest elements, and its top is the kth smallest. Quickselect partitions around a pivot and recurses into one side only. A k-sorted array is fixed by sliding a min-heap of size k+1 across it. Simpler cases just sort and index: the median survives alternate max-min removal, all but the top two are the answer, or the product of the k smallest values is taken modulo a prime. Repeatedly combining the two smallest values uses a min-heap.

| # | Problem | Link |
|---|---|---|
| 1 | [At least Two Greater](https://www.geeksforgeeks.org/problems/at-least-two-greater-elements4625/1) | [`01. At least Two Greater/`](01.%20At%20least%20Two%20Greater/) |

## Pattern 5: Non-Comparison Sorts (Counting / Radix / Index Placement)

When values are small integers or characters, skip comparisons. Counting sort counts each value and rewrites them in order, using prefix sums for stable placement. Radix sort runs a stable counting sort per digit, starting from the least significant one. Numbers in `[0, n^2)` are two digits in base n. A permutation of 1..n is sorted in place by swapping each value to index `value - 1` (cyclic sort). Strings over 26 letters are sorted with a 26-slot count array.

| # | Problem | Link |
|---|---|---|
| 1 | [Sort a String](https://www.geeksforgeeks.org/problems/sort-a-string2943/1) | [`02. Sort a String/`](02.%20Sort%20a%20String/) |
