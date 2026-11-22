# 8. Sorting

[← Back to root](../README.md) · [GfG topic problems](https://www.geeksforgeeks.org/explore?category%5B%5D=Sorting)

## Patterns (merged across all difficulty levels)

Same core technique shows up at every difficulty — this view merges those occurrences into one pattern, with problems ordered Basics → Easy → Medium → Hard. Logic/Time/Space are filled in as each problem's full article is written.

| # | Pattern | Logic | Typical Time | Typical Space | Total | Basics | Easy | Medium | Hard |
|---|---|---|---|---|---|---|---|---|---|
| 1 | [Sort + Greedy Pairing / Assignment](#sort--greedy-pairing--assignment-15) | Sort one or both inputs so the greedy choice becomes positional (largest with largest, smallest with largest, cheapest first), then take or pair elements in that order. | O(n log n) | O(1) to O(n) | 15 | 1 | 9 | 5 | 0 |
| 2 | [Sort Then Linear Scan (Adjacent Gaps / Fixed Window / Runs)](#sort-then-linear-scan-adjacent-gaps--fixed-window--runs-12) | After sorting, the answer depends only on neighbours or a window of k consecutive elements — scan once for min gap, min spread, run breaks, or a prefix condition. | O(n log n) | O(1) | 12 | 0 | 10 | 2 | 0 |
| 3 | [Split, Sort Segments, Reassemble (Alternate / Wave / Parity)](#split-sort-segments-reassemble-alternate--wave--parity-12) | Separate elements by position, parity, case, or range, sort each group (or only a subrange), then write them back interleaved or in a fixed group order. | O(n log n) | O(n) (O(1) for in-place wave/subarray) | 12 | 1 | 5 | 6 | 0 |
| 4 | [Merge-Based Processing (Merge / Inversions / Multi-Array Scan)](#merge-based-processing-merge--inversions--multi-array-scan-10) | Walk sorted sequences with one pointer each and always advance the smaller — merge, intersect, or, inside merge sort, count cross pairs (inversions, smaller-on-right). | O(n + m) merge / O(n log n) counting | O(n + m) | 10 | 1 | 3 | 5 | 1 |
| 5 | [Order Statistics: Kth / Top-K / Heap](#order-statistics-kth--top-k--heap-7) | Find the k smallest/largest elements or the element at a given rank via sorting, quickselect, or a size-k heap. | O(n log k) heap / O(n) avg quickselect | O(k) | 7 | 1 | 4 | 2 | 0 |
| 6 | [Sort + Two Pointers (Pair / Triplet Counting)](#sort--two-pointers-pair--triplet-counting-7) | Sort, then move two pointers (from both ends or both from the left) to find or count pairs and triplets that meet a sum, difference, or triangle condition. | O(n log n) pairs / O(n^2) triplets | O(1) | 7 | 0 | 3 | 4 | 0 |
| 7 | [Binary Search on Sorted Data](#binary-search-on-sorted-data-7) | Use sorted order for lower/upper bound lookups (floor, ceil, next greater), search with a small known disorder, or binary search on the answer. | O(log n) per query / O(n log range) | O(1) | 7 | 0 | 3 | 4 | 0 |
| 8 | [Custom Comparator / Key-Based Sorting](#custom-comparator--key-based-sorting-7) | Define the order with a key or comparator (set bits, length, frequency, distance to x, concatenation order) and use a stable sort when ties keep input order. | O(n log n · compare cost) | O(n) | 7 | 0 | 3 | 4 | 0 |
| 9 | [Implement a Sorting Algorithm](#implement-a-sorting-algorithm-6) | Write the algorithm itself — bubble, selection, insertion, merge sort, or a generic comparison sort — and respect its loop invariant. | O(n^2) simple sorts / O(n log n) merge sort | O(1) / O(n) merge sort | 6 | 0 | 4 | 2 | 0 |
| 10 | [Non-Comparison Sorts (Counting / Radix / Index Placement)](#non-comparison-sorts-counting--radix--index-placement-6) | Exploit a small value range: count occurrences, sort digit by digit with a stable counting pass, or place each value at its own index. | O(n + k) / O(d · (n + b)) | O(k) / O(n + b) | 6 | 1 | 3 | 2 | 0 |
| 11 | [Intervals & Sweep Line](#intervals--sweep-line-6) | Sort intervals by start (or end) or turn them into +1/-1 events, then sweep to merge, count overlaps, pick non-overlapping ones, or measure gaps. | O(n log n) | O(n) | 6 | 0 | 3 | 3 | 0 |
| 12 | [Frequency Map / Rank Compression](#frequency-map--rank-compression-5) | Replace sorting with counting where only equality or rank matters: compare character counts, map values to their sorted rank, or count equal groups and balanced prefixes. | O(n) to O(n log n) | O(n) | 5 | 0 | 4 | 0 | 1 |
| 13 | [Partition Schemes (Dutch Flag / Quick Sort)](#partition-schemes-dutch-flag--quick-sort-3) | Rearrange in place around a pivot or value range with low/mid/high pointers (Dutch national flag) or Lomuto/Hoare partitioning inside quick sort. | O(n) partition / O(n log n) avg quick sort | O(1) / O(log n) stack | 3 | 0 | 1 | 2 | 0 |
| | **Total (13 patterns)** | | | | **103** | **5** | **55** | **41** | **2** |

### Sort + Greedy Pairing / Assignment (15)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Maximum Perimeter of Triangle from Array](https://www.geeksforgeeks.org/problems/maximum-perimeter-of-triangle-from-array4322/1) | — | — | — | Basics | — | Arrays, Mathematics, Sorting | [`01. Basics/05. Maximum Perimeter of Triangle from Array/`](01.%20Basics/05.%20Maximum%20Perimeter%20of%20Triangle%20from%20Array/) |
| 2 | [Max Value Permutation](https://www.geeksforgeeks.org/problems/maximize-arrii-of-an-array0026/1) | — | — | — | Easy | SAP Labs | Arrays, Sorting | [`02. Easy/06. Max Value Permutation/`](02.%20Easy/06.%20Max%20Value%20Permutation/) |
| 3 | [Permute Arrays for Sum Threshold](https://www.geeksforgeeks.org/problems/permutations-in-array1747/1) | — | — | — | Easy | — | Arrays, Sorting | [`02. Easy/22. Permute Arrays for Sum Threshold/`](02.%20Easy/22.%20Permute%20Arrays%20for%20Sum%20Threshold/) |
| 4 | [Bus Conductor](https://www.geeksforgeeks.org/problems/bus-conductor--170647/1) | — | — | — | Easy | — | Arrays, Sorting | [`02. Easy/23. Bus Conductor/`](02.%20Easy/23.%20Bus%20Conductor/) |
| 5 | [Fitting an Array into Another](https://www.geeksforgeeks.org/problems/fitting-the-array1514/1) | — | — | — | Easy | — | Arrays, Sorting, logical-thinking | [`02. Easy/24. Fitting an Array into Another/`](02.%20Easy/24.%20Fitting%20an%20Array%20into%20Another/) |
| 6 | [Tywin's War Strategy](https://www.geeksforgeeks.org/problems/tywins-war-strategy0527/1) | — | — | — | Easy | NPCI | Arrays, Sorting | [`02. Easy/28. Tywin's War Strategy/`](02.%20Easy/28.%20Tywin's%20War%20Strategy/) |
| 7 | [Assign Cookies](https://www.geeksforgeeks.org/problems/assign-cookies/1) | — | — | — | Easy | — | Arrays, Sorting | [`02. Easy/30. Assign Cookies/`](02.%20Easy/30.%20Assign%20Cookies/) |
| 8 | [Max Sum of Products from Two Arrays](https://www.geeksforgeeks.org/problems/maximum-possible-sum-of-products3637/1) | — | — | — | Easy | Accolite, Amazon | Mathematics, Sorting | [`02. Easy/39. Max Sum of Products from Two Arrays/`](02.%20Easy/39.%20Max%20Sum%20of%20Products%20from%20Two%20Arrays/) |
| 9 | [Next Greater Even Number](https://www.geeksforgeeks.org/problems/next-greater-even-number0828/1) | — | — | — | Easy | Zoho, Amazon, FactSet, MakeMyTrip, Yahoo | Arrays, Strings, Sorting | [`02. Easy/43. Next Greater Even Number/`](02.%20Easy/43.%20Next%20Greater%20Even%20Number/) |
| 10 | [Rearrange for Largest Even Number](https://www.geeksforgeeks.org/problems/largest-even-number3821/1) | — | — | — | Easy | Snapdeal | Mathematics, Sorting | [`02. Easy/44. Rearrange for Largest Even Number/`](02.%20Easy/44.%20Rearrange%20for%20Largest%20Even%20Number/) |
| 11 | [Min Sum Pair using Digits](https://www.geeksforgeeks.org/problems/minimum-sum4058/1) | — | — | — | Medium | Google | Arrays, Sorting, Binary Search | [`03. Medium/07. Min Sum Pair using Digits/`](03.%20Medium/07.%20Min%20Sum%20Pair%20using%20Digits/) |
| 12 | [Max Profit from Two Machines](https://www.geeksforgeeks.org/problems/max-profit-from-two-machines/1) | — | — | — | Medium | Amazon, TCS | Arrays, Sorting | [`03. Medium/12. Max Profit from Two Machines/`](03.%20Medium/12.%20Max%20Profit%20from%20Two%20Machines/) |
| 13 | [Equalize All Prefix Sums](https://www.geeksforgeeks.org/problems/equalize-all-prefix-sums/1) | — | — | — | Medium | — | Arrays, Sorting | [`03. Medium/21. Equalize All Prefix Sums/`](03.%20Medium/21.%20Equalize%20All%20Prefix%20Sums/) |
| 14 | [Max Gold Coins from Limited Plates](https://www.geeksforgeeks.org/problems/help-a-thief5938/1) | — | — | — | Medium | — | Sorting | [`03. Medium/29. Max Gold Coins from Limited Plates/`](03.%20Medium/29.%20Max%20Gold%20Coins%20from%20Limited%20Plates/) |
| 15 | [Min Pair Product Sum  Rearrangement](https://www.geeksforgeeks.org/problems/minimize-sum-of-alternate-product2033/1) | — | — | — | Medium | — | Arrays, Sorting | [`03. Medium/33. Min Pair Product Sum Rearrangement/`](03.%20Medium/33.%20Min%20Pair%20Product%20Sum%20Rearrangement/) |

### Sort Then Linear Scan (Adjacent Gaps / Fixed Window / Runs) (12)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Check Sorted Array](https://www.geeksforgeeks.org/problems/check-if-an-array-is-sorted0701/1) | — | — | — | Easy | — | Arrays, Sorting | [`02. Easy/03. Check Sorted Array/`](02.%20Easy/03.%20Check%20Sorted%20Array/) |
| 2 | [Chocolate Distribution Problem](https://www.geeksforgeeks.org/problems/chocolate-distribution-problem3825/1) | — | — | — | Easy | Flipkart | Sorting | [`02. Easy/08. Chocolate Distribution Problem/`](02.%20Easy/08.%20Chocolate%20Distribution%20Problem/) |
| 3 | [Minimum Distance between Two Words](https://www.geeksforgeeks.org/problems/closest-strings0611/1) | — | — | — | Easy | Amazon, Linkedin | Strings, Sorting, Arrays | [`02. Easy/17. Minimum Distance between Two Words/`](02.%20Easy/17.%20Minimum%20Distance%20between%20Two%20Words/) |
| 4 | [Min Diff Pair](https://www.geeksforgeeks.org/problems/minimum-difference-pair5444/1) | — | — | — | Easy | Amazon | Sorting | [`02. Easy/21. Min Diff Pair/`](02.%20Easy/21.%20Min%20Diff%20Pair/) |
| 5 | [Minimize Difference in Task Priorities](https://www.geeksforgeeks.org/problems/minimum-difference-among-k5805/1) | — | — | — | Easy | Amazon | Arrays, Sorting | [`02. Easy/31. Minimize Difference in Task Priorities/`](02.%20Easy/31.%20Minimize%20Difference%20in%20Task%20Priorities/) |
| 6 | [Minimum Difference in an Array](https://www.geeksforgeeks.org/problems/minimum-difference-in-an-array/1) | — | — | — | Easy | — | Sorting | [`02. Easy/32. Minimum Difference in an Array/`](02.%20Easy/32.%20Minimum%20Difference%20in%20an%20Array/) |
| 7 | [Min Subsets with Consecutive Numbers](https://www.geeksforgeeks.org/problems/min-subsets-with-consecutive-numbers0601/1) | — | — | — | Easy | — | Arrays, Sorting | [`02. Easy/35. Min Subsets with Consecutive Numbers/`](02.%20Easy/35.%20Min%20Subsets%20with%20Consecutive%20Numbers/) |
| 8 | [Rope Cutting](https://www.geeksforgeeks.org/problems/rope-cutting3334/1) | — | — | — | Easy | — | Arrays, Sorting | [`02. Easy/45. Rope Cutting/`](02.%20Easy/45.%20Rope%20Cutting/) |
| 9 | [Maximum Partitions to Make a Permutation Sorted](https://www.geeksforgeeks.org/problems/maximum-number-of-partitions-that-can-be-sorted-individually-to-make-sorted2926/1) | — | — | — | Easy | — | Arrays, Sorting | [`02. Easy/50. Maximum Partitions to Make a Permutation Sorted/`](02.%20Easy/50.%20Maximum%20Partitions%20to%20Make%20a%20Permutation%20Sorted/) |
| 10 | [Minimum Add/Subtract to Equalize Array](https://www.geeksforgeeks.org/problems/equalize-an-array3405/1) | — | — | — | Easy | — | Mathematics, Sorting | [`02. Easy/51. Minimum AddSubtract to Equalize Array/`](02.%20Easy/51.%20Minimum%20AddSubtract%20to%20Equalize%20Array/) |
| 11 | [Find H-Index](https://www.geeksforgeeks.org/problems/find-h-index--165609/1) | — | — | — | Medium | NPCI | Sorting, Arrays | [`03. Medium/14. Find H-Index/`](03.%20Medium/14.%20Find%20H-Index/) |
| 12 | [Difference Check](https://www.geeksforgeeks.org/problems/difference-check/1) | — | — | — | Medium | — | Strings, Sorting | [`03. Medium/30. Difference Check/`](03.%20Medium/30.%20Difference%20Check/) |

### Split, Sort Segments, Reassemble (Alternate / Wave / Parity) (12)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Alternative Sorting](https://www.geeksforgeeks.org/problems/alternative-sorting1311/1) | — | — | — | Basics | Zoho | Arrays, Sorting | [`01. Basics/03. Alternative Sorting/`](01.%20Basics/03.%20Alternative%20Sorting/) |
| 2 | [Even Greater than Odd](https://www.geeksforgeeks.org/problems/rearrange-array-such-that-even-positioned-are-greater-than-odd4804/1) | — | — | — | Easy | — | Arrays, Sorting | [`02. Easy/34. Even Greater than Odd/`](02.%20Easy/34.%20Even%20Greater%20than%20Odd/) |
| 3 | [Sort a Subarray](https://www.geeksforgeeks.org/problems/part-sort2851/1) | — | — | — | Easy | — | Sorting | [`02. Easy/40. Sort a Subarray/`](02.%20Easy/40.%20Sort%20a%20Subarray/) |
| 4 | [Bitonic Generator Sort](https://www.geeksforgeeks.org/problems/bitonic-generator-sort3343/1) | — | — | — | Easy | Zoho | Arrays, Sorting, STL | [`02. Easy/41. Bitonic Generator Sort/`](02.%20Easy/41.%20Bitonic%20Generator%20Sort/) |
| 5 | [Sorting All Except One](https://www.geeksforgeeks.org/problems/sorting-all-array-elements-except-one4653/1) | — | — | — | Easy | — | Arrays, Sorting | [`02. Easy/42. Sorting All Except One/`](02.%20Easy/42.%20Sorting%20All%20Except%20One/) |
| 6 | [Unusual String Sort](https://www.geeksforgeeks.org/problems/unusual-string-sort0405/1) | — | — | — | Easy | — | Strings, Sorting | [`02. Easy/49. Unusual String Sort/`](02.%20Easy/49.%20Unusual%20String%20Sort/) |
| 7 | [Wave Array](https://www.geeksforgeeks.org/problems/wave-array-1587115621/1) | — | — | — | Medium | Paytm, Flipkart, Amazon, Microsoft, FactSet, Goldman Sachs, Google | Arrays, Sorting | [`03. Medium/05. Wave Array/`](03.%20Medium/05.%20Wave%20Array/) |
| 8 | [Case-specific Sorting of Strings](https://www.geeksforgeeks.org/problems/case-specific-sorting-of-strings4845/1) | — | — | — | Medium | — | Strings, Sorting | [`03. Medium/13. Case-specific Sorting of Strings/`](03.%20Medium/13.%20Case-specific%20Sorting%20of%20Strings/) |
| 9 | [Sort in specific order](https://www.geeksforgeeks.org/problems/sort-in-specific-order2422/1) | — | — | — | Medium | Zoho, Microsoft | Arrays, Sorting, Numbers | [`03. Medium/17. Sort in specific order/`](03.%20Medium/17.%20Sort%20in%20specific%20order/) |
| 10 | [Largest Array Formation with Same Parity Swaps](https://www.geeksforgeeks.org/problems/even-swap/1) | — | — | — | Medium | — | Arrays, Sorting | [`03. Medium/26. Largest Array Formation with Same Parity Swaps/`](03.%20Medium/26.%20Largest%20Array%20Formation%20with%20Same%20Parity%20Swaps/) |
| 11 | [Rearrange to Maximize Alternate Addition Subtraction](https://www.geeksforgeeks.org/problems/reaching-the-heights1921/1) | — | — | — | Medium | — | Arrays, Sorting, Misc | [`03. Medium/31. Rearrange to Maximize Alternate Addition Subtraction/`](03.%20Medium/31.%20Rearrange%20to%20Maximize%20Alternate%20Addition%20Subtraction/) |
| 12 | [Sort Matrix Diagonally](https://www.geeksforgeeks.org/problems/diagonal-morning-assembly0028/1) | — | — | — | Medium | Microsoft | Sorting, Matrix | [`03. Medium/34. Sort Matrix Diagonally/`](03.%20Medium/34.%20Sort%20Matrix%20Diagonally/) |

### Merge-Based Processing (Merge / Inversions / Multi-Array Scan) (10)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Merge and Sort](https://www.geeksforgeeks.org/problems/merge-and-sort5821/1) | — | — | — | Basics | — | Arrays, Sorting, Merge Sort | [`01. Basics/04. Merge and Sort/`](01.%20Basics/04.%20Merge%20and%20Sort/) |
| 2 | [Intersection of Two Sorted Arrays](https://www.geeksforgeeks.org/problems/intersection-of-two-sorted-array-1587115620/1) | — | — | — | Easy | — | Arrays, Sorting | [`02. Easy/13. Intersection of Two Sorted Arrays/`](02.%20Easy/13.%20Intersection%20of%20Two%20Sorted%20Arrays/) |
| 3 | [Intersection of Two Sorted Arrays](https://www.geeksforgeeks.org/problems/intersection-of-two-sorted-arrays-with-duplicate-elements/1) | — | — | — | Easy | — | Sorting, Arrays | [`02. Easy/26. Intersection of Two Sorted Arrays/`](02.%20Easy/26.%20Intersection%20of%20Two%20Sorted%20Arrays/) |
| 4 | [Merge two Unsorted Arrays](https://www.geeksforgeeks.org/problems/merging-two-unsorted-arrays-in-sorted-order1020/1) | — | — | — | Easy | Flipkart, Amazon, Amdocs | Arrays, Sorting | [`02. Easy/33. Merge two Unsorted Arrays/`](02.%20Easy/33.%20Merge%20two%20Unsorted%20Arrays/) |
| 5 | [Count Inversions](https://www.geeksforgeeks.org/problems/inversion-of-array-1587115620/1) | — | — | — | Medium | Flipkart, Amazon, Microsoft, MakeMyTrip, Adobe, BankBazaar, Myntra | Arrays, Divide and Conquer, Sorting | [`03. Medium/03. Count Inversions/`](03.%20Medium/03.%20Count%20Inversions/) |
| 6 | [Sort the given array after applying the given equation](https://www.geeksforgeeks.org/problems/sort-the-given-array-after-applying-the-given-equation0304/1) | — | — | — | Medium | Adobe | Mathematics, Sorting | [`03. Medium/19. Sort the given array after applying the given equation/`](03.%20Medium/19.%20Sort%20the%20given%20array%20after%20applying%20the%20given%20equation/) |
| 7 | [Merge three sorted arrays](https://www.geeksforgeeks.org/problems/merge-three-sorted-arrays-1587115620/1) | — | — | — | Medium | — | Arrays, Sorting | [`03. Medium/22. Merge three sorted arrays/`](03.%20Medium/22.%20Merge%20three%20sorted%20arrays/) |
| 8 | [Smallest Diff Triplet in Three Arrays](https://www.geeksforgeeks.org/problems/happiest-triplet2921/1) | — | — | — | Medium | — | Arrays, Searching, Sorting | [`03. Medium/27. Smallest Diff Triplet in Three Arrays/`](03.%20Medium/27.%20Smallest%20Diff%20Triplet%20in%20Three%20Arrays/) |
| 9 | [Sort a Prefix Sorted Array](https://www.geeksforgeeks.org/problems/sort-last-m-elements--155156/1) | — | — | — | Medium | Microsoft | Sorting, Merge Sort | [`03. Medium/40. Sort a Prefix Sorted Array/`](03.%20Medium/40.%20Sort%20a%20Prefix%20Sorted%20Array/) |
| 10 | [Count Smaller on Right](https://www.geeksforgeeks.org/problems/count-smaller-elements2214/1) | — | — | — | Hard | Google, Codenation | Arrays, Sorting, Binary Search | [`04. Hard/01. Count Smaller on Right/`](04.%20Hard/01.%20Count%20Smaller%20on%20Right/) |

### Order Statistics: Kth / Top-K / Heap (7)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [At least Two Greater](https://www.geeksforgeeks.org/problems/at-least-two-greater-elements4625/1) | — | — | — | Basics | Amazon | Arrays, Sorting | [`01. Basics/01. At least Two Greater/`](01.%20Basics/01.%20At%20least%20Two%20Greater/) |
| 2 | [Minimum Product of k Elements](https://www.geeksforgeeks.org/problems/minimum-product-of-k-integers2553/1) | — | — | — | Easy | — | Arrays, Sorting, Modular Arithmetic | [`02. Easy/19. Minimum Product of k Elements/`](02.%20Easy/19.%20Minimum%20Product%20of%20k%20Elements/) |
| 3 | [Last Remaining After Alternate Max-Min Removal](https://www.geeksforgeeks.org/problems/print-the-left-element2009/1) | — | — | — | Easy | — | Arrays, Sorting | [`02. Easy/20. Last Remaining After Alternate Max-Min Removal/`](02.%20Easy/20.%20Last%20Remaining%20After%20Alternate%20Max-Min%20Removal/) |
| 4 | [Minimize the sum](https://www.geeksforgeeks.org/problems/minimize-the-sum--170645/1) | — | — | — | Easy | Swiggy | Arrays, Sorting, Priority Queue | [`02. Easy/29. Minimize the sum/`](02.%20Easy/29.%20Minimize%20the%20sum/) |
| 5 | [Indexes of Top K](https://www.geeksforgeeks.org/problems/toppers-of-class3826/1) | — | — | — | Easy | D-E-Shaw | Arrays, Sorting | [`02. Easy/38. Indexes of Top K/`](02.%20Easy/38.%20Indexes%20of%20Top%20K/) |
| 6 | [Kth Smallest](https://www.geeksforgeeks.org/problems/kth-smallest-element5635/1) | — | — | — | Medium | VMWare, Accolite, Amazon, Microsoft, Snapdeal, Hike, Adobe, Google, ABCO, Cisco | Arrays, Searching, Sorting | [`03. Medium/02. Kth Smallest/`](03.%20Medium/02.%20Kth%20Smallest/) |
| 7 | [Nearly sorted](https://www.geeksforgeeks.org/problems/nearly-sorted-1587115620/1) | — | — | — | Medium | Google | Sorting, Arrays, Priority Queue | [`03. Medium/11. Nearly sorted/`](03.%20Medium/11.%20Nearly%20sorted/) |

### Sort + Two Pointers (Pair / Triplet Counting) (7)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Pair With Difference](https://www.geeksforgeeks.org/problems/find-pair-given-difference1559/1) | — | — | — | Easy | Amazon, Visa | Sorting, Binary Search | [`02. Easy/05. Pair With Difference/`](02.%20Easy/05.%20Pair%20With%20Difference/) |
| 2 | [Distinct Absolutes in Array](https://www.geeksforgeeks.org/problems/distinct-absolute-array-elements4529/1) | — | — | — | Easy | — | Arrays, Sorting | [`02. Easy/37. Distinct Absolutes in Array/`](02.%20Easy/37.%20Distinct%20Absolutes%20in%20Array/) |
| 3 | [Good Pairs](https://www.geeksforgeeks.org/problems/good-pairs4519/1) | — | — | — | Easy | — | Searching, Sorting | [`02. Easy/46. Good Pairs/`](02.%20Easy/46.%20Good%20Pairs/) |
| 4 | [Count the Number of Possible Triangles](https://www.geeksforgeeks.org/problems/count-possible-triangles-1587115620/1) | — | — | — | Medium | Amazon, Microsoft | Arrays, Sorting | [`03. Medium/09. Count the Number of Possible Triangles/`](03.%20Medium/09.%20Count%20the%20Number%20of%20Possible%20Triangles/) |
| 5 | [Triplet Family](https://www.geeksforgeeks.org/problems/triplet-family/1) | — | — | — | Medium | Arcesium | Arrays, Sorting | [`03. Medium/16. Triplet Family/`](03.%20Medium/16.%20Triplet%20Family/) |
| 6 | [Triplets with Sum in Range](https://www.geeksforgeeks.org/problems/triplets-with-sum-with-given-range/1) | — | — | — | Medium | Microsoft | Sorting | [`03. Medium/18. Triplets with Sum in Range/`](03.%20Medium/18.%20Triplets%20with%20Sum%20in%20Range/) |
| 7 | [Count the number of possible triangles](https://www.geeksforgeeks.org/problems/count-possible-triangles-1587115620--094125/1) | — | — | — | Medium | Amazon, Microsoft | Arrays, Sorting | [`03. Medium/41. Count the number of possible triangles/`](03.%20Medium/41.%20Count%20the%20number%20of%20possible%20triangles/) |

### Binary Search on Sorted Data (7)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Floor in a Sorted Array](https://www.geeksforgeeks.org/problems/floor-in-a-sorted-array-1587115620/1) | — | — | — | Easy | Amazon | Searching, Sorting | [`02. Easy/01. Floor in a Sorted Array/`](02.%20Easy/01.%20Floor%20in%20a%20Sorted%20Array/) |
| 2 | [Ceil in a Sorted Array](https://www.geeksforgeeks.org/problems/ceil-in-a-sorted-array/1) | — | — | — | Easy | Amazon | Binary Search, Sorting, Searching | [`02. Easy/14. Ceil in a Sorted Array/`](02.%20Easy/14.%20Ceil%20in%20a%20Sorted%20Array/) |
| 3 | [Smallest Greater in Whole Array](https://www.geeksforgeeks.org/problems/smallest-greater-elements-in-whole-array2751/1) | — | — | — | Easy | Zoho | Arrays, Searching, Sorting, CPP, STL | [`02. Easy/25. Smallest Greater in Whole Array/`](02.%20Easy/25.%20Smallest%20Greater%20in%20Whole%20Array/) |
| 4 | [Count Power Pairs from Two Arrays](https://www.geeksforgeeks.org/problems/number-of-pairs3422/1) | — | — | — | Medium | FactSet | Arrays, Sorting | [`03. Medium/10. Count Power Pairs from Two Arrays/`](03.%20Medium/10.%20Count%20Power%20Pairs%20from%20Two%20Arrays/) |
| 5 | [Search in an almost Sorted Array](https://www.geeksforgeeks.org/problems/search-in-an-almost-sorted-array/1) | — | — | — | Medium | — | Binary Search, Sorting, Arrays | [`03. Medium/20. Search in an almost Sorted Array/`](03.%20Medium/20.%20Search%20in%20an%20almost%20Sorted%20Array/) |
| 6 | [Closer to sort](https://www.geeksforgeeks.org/problems/closer-to-sort-1587115620/1) | — | — | — | Medium | — | Searching, Sorting, Binary Search | [`03. Medium/24. Closer to sort/`](03.%20Medium/24.%20Closer%20to%20sort/) |
| 7 | [Maximize the minimum difference between k elements](https://www.geeksforgeeks.org/problems/maximize-the-minimum-difference-between-k-elements/1) | — | — | — | Medium | NPCI | Binary Search, Sorting, Arrays | [`03. Medium/32. Maximize the minimum difference between k elements/`](03.%20Medium/32.%20Maximize%20the%20minimum%20difference%20between%20k%20elements/) |

### Custom Comparator / Key-Based Sorting (7)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Sort by Set Bit Count](https://www.geeksforgeeks.org/problems/sort-by-set-bit-count1153/1) | — | — | — | Easy | — | Arrays, Sorting | [`02. Easy/15. Sort by Set Bit Count/`](02.%20Easy/15.%20Sort%20by%20Set%20Bit%20Count/) |
| 2 | [Sorting Two Arrays Together](https://www.geeksforgeeks.org/problems/sorting-employees5907/1) | — | — | — | Easy | Oracle | Arrays, Strings, Sorting | [`02. Easy/36. Sorting Two Arrays Together/`](02.%20Easy/36.%20Sorting%20Two%20Arrays%20Together/) |
| 3 | [Stable Sort and Position](https://www.geeksforgeeks.org/problems/stable-sort-and-position1359/1) | — | — | — | Easy | — | Arrays, Sorting | [`02. Easy/48. Stable Sort and Position/`](02.%20Easy/48.%20Stable%20Sort%20and%20Position/) |
| 4 | [Form the Largest Number](https://www.geeksforgeeks.org/problems/largest-number-formed-from-an-array1117/1) | — | — | — | Medium | Paytm, Zoho, Amazon, Microsoft, MakeMyTrip | Arrays, Sorting | [`03. Medium/08. Form the Largest Number/`](03.%20Medium/08.%20Form%20the%20Largest%20Number/) |
| 5 | [Sort by Absolute Difference](https://www.geeksforgeeks.org/problems/sort-by-absolute-difference-1587115621/1) | — | — | — | Medium | NPCI | Arrays, Sorting | [`03. Medium/15. Sort by Absolute Difference/`](03.%20Medium/15.%20Sort%20by%20Absolute%20Difference/) |
| 6 | [Sort by Frequency](https://www.geeksforgeeks.org/problems/sort-string-according-to-increasing-frequency/1) | — | — | — | Medium | — | Strings, Sorting | [`03. Medium/38. Sort by Frequency/`](03.%20Medium/38.%20Sort%20by%20Frequency/) |
| 7 | [Sort an array of strings according to string lengths](https://www.geeksforgeeks.org/problems/sort-an-array-of-strings-according-to-string-lengths/1) | — | — | — | Medium | — | Strings, Sorting, Arrays | [`03. Medium/39. Sort an array of strings according to string lengths/`](03.%20Medium/39.%20Sort%20an%20array%20of%20strings%20according%20to%20string%20lengths/) |

### Implement a Sorting Algorithm (6)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Bubble Sort](https://www.geeksforgeeks.org/problems/bubble-sort/1) | — | — | — | Easy | Microsoft, Wipro, SAP Labs, Cisco, Nagarro, redBus, Accenture, Huawei | Sorting | [`02. Easy/04. Bubble Sort/`](02.%20Easy/04.%20Bubble%20Sort/) |
| 2 | [Insertion Sort](https://www.geeksforgeeks.org/problems/insertion-sort/1) | — | — | — | Easy | Microsoft, MAQ Software, Juniper Networks, Cisco, Accenture, Dell, Veritas, Grofers | Sorting | [`02. Easy/07. Insertion Sort/`](02.%20Easy/07.%20Insertion%20Sort/) |
| 3 | [Selection Sort](https://www.geeksforgeeks.org/problems/selection-sort/1) | — | — | — | Easy | Microsoft, Medlife | Sorting | [`02. Easy/09. Selection Sort/`](02.%20Easy/09.%20Selection%20Sort/) |
| 4 | [Sort Array](https://www.geeksforgeeks.org/problems/sort-the-array0055/1) | — | — | — | Easy | Cisco | Sorting | [`02. Easy/11. Sort Array/`](02.%20Easy/11.%20Sort%20Array/) |
| 5 | [Merge Sort](https://www.geeksforgeeks.org/problems/merge-sort/1) | — | — | — | Medium | Paytm, Amazon, Microsoft, Snapdeal, Oracle, Goldman Sachs, Wipro, Qualcomm, Boomerang Commerce, Grofers, Target Corporation, Medlife | Divide and Conquer, Sorting | [`03. Medium/06. Merge Sort/`](03.%20Medium/06.%20Merge%20Sort/) |
| 6 | [C++ Generic sort](https://www.geeksforgeeks.org/problems/c-generic-sort/1) | — | — | — | Medium | — | Sorting, Misc, CPP | [`03. Medium/28. C++ Generic sort/`](03.%20Medium/28.%20C++%20Generic%20sort/) |

### Non-Comparison Sorts (Counting / Radix / Index Placement) (6)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Sort a String](https://www.geeksforgeeks.org/problems/sort-a-string2943/1) | — | — | — | Basics | — | Strings, Sorting | [`01. Basics/02. Sort a String/`](01.%20Basics/02.%20Sort%20a%20String/) |
| 2 | [Counting Sort](https://www.geeksforgeeks.org/problems/counting-sort/1) | — | — | — | Easy | Microsoft, Goldman Sachs, Cisco | Sorting | [`02. Easy/16. Counting Sort/`](02.%20Easy/16.%20Counting%20Sort/) |
| 3 | [Sort an Array of 1 to n](https://www.geeksforgeeks.org/problems/sort-an-array-which-contains-1-to-n-values-using-mathematical-formula/1) | — | — | — | Easy | — | Sorting, Arrays | [`02. Easy/53. Sort an Array of 1 to n/`](02.%20Easy/53.%20Sort%20an%20Array%20of%201%20to%20n/) |
| 4 | [Smallest Rearrangement with No "cba" Subsequence](https://www.geeksforgeeks.org/problems/cba-subsequence--170645/1) | — | — | — | Easy | — | Strings, Sorting | [`02. Easy/54. Smallest Rearrangement with No cba Subsequence/`](02.%20Easy/54.%20Smallest%20Rearrangement%20with%20No%20cba%20Subsequence/) |
| 5 | [Radix Sort](https://www.geeksforgeeks.org/problems/radix-sort/1) | — | — | — | Medium | — | Sorting | [`03. Medium/35. Radix Sort/`](03.%20Medium/35.%20Radix%20Sort/) |
| 6 | [Sort Numbers in Limited Range](https://www.geeksforgeeks.org/problems/efficiently-sorting-number-from-0-to-n2-15444/1) | — | — | — | Medium | — | Sorting, Sqrt Decomposition, radix sort | [`03. Medium/36. Sort Numbers in Limited Range/`](03.%20Medium/36.%20Sort%20Numbers%20in%20Limited%20Range/) |

### Intervals & Sweep Line (6)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Overlapping Intervals](https://www.geeksforgeeks.org/problems/overlapping-intervals--174556/1) | — | — | — | Easy | — | Sorting | [`02. Easy/47. Overlapping Intervals/`](02.%20Easy/47.%20Overlapping%20Intervals/) |
| 2 | [Count Uncovered Positions](https://www.geeksforgeeks.org/problems/race-in-fooland4522/1) | — | — | — | Easy | — | Arrays, Sorting, STL | [`02. Easy/52. Count Uncovered Positions/`](02.%20Easy/52.%20Count%20Uncovered%20Positions/) |
| 3 | [Largest Gap in Intervals](https://www.geeksforgeeks.org/problems/largest-gap/1) | — | — | — | Easy | Flipkart | Arrays, Sorting | [`02. Easy/55. Largest Gap in Intervals/`](02.%20Easy/55.%20Largest%20Gap%20in%20Intervals/) |
| 4 | [Maximum Intersecting Lines](https://www.geeksforgeeks.org/problems/maximum-intersecting-lines--170647/1) | — | — | — | Medium | Swiggy | Mathematics, Sorting, Geometric | [`03. Medium/23. Maximum Intersecting Lines/`](03.%20Medium/23.%20Maximum%20Intersecting%20Lines/) |
| 5 | [Maximum Intervals Overlap](https://www.geeksforgeeks.org/problems/maximum-intervals-overlap5708/1) | — | — | — | Medium | Flipkart, Accolite, Amazon, Visa, Directi | Sorting | [`03. Medium/25. Maximum Intervals Overlap/`](03.%20Medium/25.%20Maximum%20Intervals%20Overlap/) |
| 6 | [Max Non Overlapping Intervals](https://www.geeksforgeeks.org/problems/maximum-selections--170637/1) | — | — | — | Medium | — | Sorting | [`03. Medium/37. Max Non Overlapping Intervals/`](03.%20Medium/37.%20Max%20Non%20Overlapping%20Intervals/) |

### Frequency Map / Rank Compression (5)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Anagram](https://www.geeksforgeeks.org/problems/anagram-1587115620/1) | — | — | — | Easy | Flipkart, Directi, Adobe, Google, Nagarro, Media.net | Strings, Sorting | [`02. Easy/02. Anagram/`](02.%20Easy/02.%20Anagram/) |
| 2 | [Replace Elements by Ranks](https://www.geeksforgeeks.org/problems/convert-an-array-to-reduced-form1101/1) | — | — | — | Easy | — | Arrays, Sorting | [`02. Easy/12. Replace Elements by Ranks/`](02.%20Easy/12.%20Replace%20Elements%20by%20Ranks/) |
| 3 | [Distinct Frequencies Check](https://www.geeksforgeeks.org/problems/unique-frequencies-of-not/1) | — | — | — | Easy | PayPal, Bloomberg, Adobe, Google, Amazon, Apple | Set, Sorting, Map | [`02. Easy/18. Distinct Frequencies Check/`](02.%20Easy/18.%20Distinct%20Frequencies%20Check/) |
| 4 | [Count Pairs with Zero XOR](https://www.geeksforgeeks.org/problems/counts-zeros-xor-pairs0349/1) | — | — | — | Easy | — | Arrays, Bit Magic, Sorting | [`02. Easy/27. Count Pairs with Zero XOR/`](02.%20Easy/27.%20Count%20Pairs%20with%20Zero%20XOR/) |
| 5 | [Count Subarrays with Given Median](https://www.geeksforgeeks.org/problems/median-of-the-subarrays--170647/1) | — | — | — | Hard | Sprinklr | Sorting, Map | [`04. Hard/02. Count Subarrays with Given Median/`](04.%20Hard/02.%20Count%20Subarrays%20with%20Given%20Median/) |

### Partition Schemes (Dutch Flag / Quick Sort) (3)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Three way partitioning](https://www.geeksforgeeks.org/problems/three-way-partitioning/1) | — | — | — | Easy | Yahoo | Arrays, Sorting | [`02. Easy/10. Three way partitioning/`](02.%20Easy/10.%20Three%20way%20partitioning/) |
| 2 | [Sort 0s, 1s and 2s](https://www.geeksforgeeks.org/problems/sort-an-array-of-0s-1s-and-2s4231/1) | — | — | — | Medium | Paytm, Flipkart, Morgan Stanley, Amazon, Microsoft, OYO Rooms, Samsung, Snapdeal, Hike, MakeMyTrip, Ola Cabs, Walmart, MAQ Software, Adobe, Yatra.com, SAP Labs, Qualcomm | Arrays, Sorting | [`03. Medium/01. Sort 0s, 1s and 2s/`](03.%20Medium/01.%20Sort%200s,%201s%20and%202s/) |
| 3 | [Quick Sort](https://www.geeksforgeeks.org/problems/quick-sort/1) | — | — | — | Medium | VMWare, Amazon, Microsoft, Samsung, Hike, Ola Cabs, Goldman Sachs, Adobe, SAP Labs, Qualcomm, HSBC, Grofers, Target Corporation | Divide and Conquer, Sorting | [`03. Medium/04. Quick Sort/`](03.%20Medium/04.%20Quick%20Sort/) |
