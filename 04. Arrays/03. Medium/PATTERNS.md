# Arrays — Medium: Patterns

This file groups the 103 Medium-level array problems into the core recurring DSA patterns they draw on. Each problem is listed under the single pattern that best captures the dominant technique needed to solve it — many problems blend ideas, but the placement reflects the primary insight.

## Pattern 1: Binary Search on Answer / Monotonic Predicate

Problems where the answer space (a rate, capacity, divisor, or day count) is monotonic — feasibility increases or decreases as the candidate grows — so binary search is applied over the *answer* itself rather than over array indices, checking feasibility with a linear scan at each guess.

| # | Problem | Link |
|---|---|---|
| 1 | [Koko Eating Bananas](https://www.geeksforgeeks.org/problems/koko-eating-bananas/1) | [`28. Koko Eating Bananas/`](28.%20Koko%20Eating%20Bananas/) |
| 2 | [Minimum Days to Make m Bouquets](https://www.geeksforgeeks.org/problems/minimum-days-to-make-m-bouquets/1) | [`43. Minimum Days to Make m Bouquets/`](43.%20Minimum%20Days%20to%20Make%20m%20Bouquets/) |
| 3 | [Capacity To Ship Packages Within d Days](https://www.geeksforgeeks.org/problems/capacity-to-ship-packages-within-d-days/1) | [`44. Capacity To Ship Packages Within d Days/`](44.%20Capacity%20To%20Ship%20Packages%20Within%20d%20Days/) |
| 4 | [Smallest Divisor](https://www.geeksforgeeks.org/problems/smallest-divisor/1) | [`46. Smallest Divisor/`](46.%20Smallest%20Divisor/) |

## Pattern 2: Binary Search on Sorted / Rotated Arrays

Direct binary search (or its variants) applied over an array that is sorted, or sorted-then-rotated, to locate boundaries, counts, occurrences, or elements in logarithmic time.

| # | Problem | Link |
|---|---|---|
| 1 | [First and Last in Sorted](https://www.geeksforgeeks.org/problems/first-and-last-occurrences-of-x3116/1) | [`04. First and Last in Sorted/`](04.%20First%20and%20Last%20in%20Sorted/) |
| 2 | [K Closest in a Sorted Array](https://www.geeksforgeeks.org/problems/k-closest-elements3619/1) | [`16. K Closest in a Sorted Array/`](16.%20K%20Closest%20in%20a%20Sorted%20Array/) |
| 3 | [Kth Missing Positive Number in a Sorted Array](https://www.geeksforgeeks.org/problems/kth-missing-positive-number-in-a-sorted-array/1) | [`30. Kth Missing Positive Number in a Sorted Array/`](30.%20Kth%20Missing%20Positive%20Number%20in%20a%20Sorted%20Array/) |
| 4 | [Search in Rotated Array 2](https://www.geeksforgeeks.org/problems/search-in-rotated-array-2/1) | [`41. Search in Rotated Array 2/`](41.%20Search%20in%20Rotated%20Array%202/) |
| 5 | [Count X in Range of a Sorted Array](https://www.geeksforgeeks.org/problems/count-x-in-range-of-a-sorted-array/1) | [`70. Count X in Range of a Sorted Array/`](70.%20Count%20X%20in%20Range%20of%20a%20Sorted%20Array/) |
| 6 | [Count elements less than or equal to k in a sorted rotated array](https://www.geeksforgeeks.org/problems/count-elements-less-than-or-equal-to-k-in-a-sorted-rotated-array/1) | [`71. Count elements less than or equal to k in a sorted rotated array/`](71.%20Count%20elements%20less%20than%20or%20equal%20to%20k%20in%20a%20sorted%20rotated%20array/) |
| 7 | [Index Element After Rotations](https://www.geeksforgeeks.org/problems/find-the-element-at-given-index4630/1) | [`93. Index Element After Rotations/`](93.%20Index%20Element%20After%20Rotations/) |
| 8 | [Successful Binary Searches Irrespective of Pivot](https://www.geeksforgeeks.org/problems/count-always-found/1) | [`103. Successful Binary Searches Irrespective of Pivot/`](103.%20Successful%20Binary%20Searches%20Irrespective%20of%20Pivot/) |

## Pattern 3: K-th Element / Order Statistics via Merge or Partition

Finding the k-th smallest/largest element or a median-like quantity across one or two sorted arrays, typically via a merge-style walk, partitioning logic, or a min/max-heap of size k.

| # | Problem | Link |
|---|---|---|
| 1 | [K-th of Two Sorted Arrays](https://www.geeksforgeeks.org/problems/k-th-element-of-two-sorted-array1317/1) | [`02. K-th of Two Sorted Arrays/`](02.%20K-th%20of%20Two%20Sorted%20Arrays/) |
| 2 | [Sum of Middle of two sorted arrays](https://www.geeksforgeeks.org/problems/sum-of-middle-elements-of-two-sorted-arrays2305/1) | [`21. Sum of Middle of two sorted arrays/`](21.%20Sum%20of%20Middle%20of%20two%20sorted%20arrays/) |
| 3 | [Top k Frequent in Stream](https://www.geeksforgeeks.org/problems/top-k-numbers3425/1) | [`37. Top k Frequent in Stream/`](37.%20Top%20k%20Frequent%20in%20Stream/) |
| 4 | [K-th Largest Sum Contiguous Subarray](https://www.geeksforgeeks.org/problems/k-th-largest-sum-contiguous-subarray/1) | [`39. K-th Largest Sum Contiguous Subarray/`](39.%20K-th%20Largest%20Sum%20Contiguous%20Subarray/) |
| 5 | [Kth Smallest Pairwise Difference](https://www.geeksforgeeks.org/problems/smallest-absolute-difference4320/1) | [`67. Kth Smallest Pairwise Difference/`](67.%20Kth%20Smallest%20Pairwise%20Difference/) |
| 6 | [Max Product Subsequence of Size K](https://www.geeksforgeeks.org/problems/maximum-product4633/1) | [`68. Max Product Subsequence of Size K/`](68.%20Max%20Product%20Subsequence%20of%20Size%20K/) |

## Pattern 4: Prefix Sum / Cumulative Aggregate

Problems solved by precomputing running sums, counts, or frequency prefixes so range queries or subarray aggregates can be answered without re-scanning the array each time.

| # | Problem | Link |
|---|---|---|
| 1 | [Max Sum Subarray of Non-Negative](https://www.geeksforgeeks.org/problems/maximum-sub-array5443/1) | [`09. Max Sum Subarray of Non-Negative/`](09.%20Max%20Sum%20Subarray%20of%20Non-Negative/) |
| 2 | [Sum of Subarrays](https://www.geeksforgeeks.org/problems/sum-of-subarrays2229/1) | [`33. Sum of Subarrays/`](33.%20Sum%20of%20Subarrays/) |
| 3 | [Smaller Sum for All](https://www.geeksforgeeks.org/problems/smaller-sum--170647/1) | [`49. Smaller Sum for All/`](49.%20Smaller%20Sum%20for%20All/) |
| 4 | [Update Queries](https://www.geeksforgeeks.org/problems/update-queries--170647/1) | [`62. Update Queries/`](62.%20Update%20Queries/) |
| 5 | [Subarrays Having Even Sum](https://www.geeksforgeeks.org/problems/find-the-number-of-sub-arrays-having-even-sum1533/1) | [`82. Subarrays Having Even Sum/`](82.%20Subarrays%20Having%20Even%20Sum/) |
| 6 | [Maximum Bitonic Subarray Sum](https://www.geeksforgeeks.org/problems/maximum-bitonic-subarray-sum5616/1) | [`88. Maximum Bitonic Subarray Sum/`](88.%20Maximum%20Bitonic%20Subarray%20Sum/) |

## Pattern 5: XOR / Prefix-XOR Techniques

Problems that use XOR's self-cancelling property, often paired with prefix-XOR and hashing, to count subarrays, split arrays, or isolate unique elements.

| # | Problem | Link |
|---|---|---|
| 1 | [Count Subarrays with given XOR](https://www.geeksforgeeks.org/problems/count-subarray-with-given-xor/1) | [`14. Count Subarrays with given XOR/`](14.%20Count%20Subarrays%20with%20given%20XOR/) |
| 2 | [Unique Number III](https://www.geeksforgeeks.org/problems/find-element-occuring-once-when-all-other-are-present-thrice/1) | [`26. Unique Number III/`](26.%20Unique%20Number%20III/) |
| 3 | [Sum of XOR of all pairs](https://www.geeksforgeeks.org/problems/sum-of-xor-of-all-pairs0723/1) | [`29. Sum of XOR of all pairs/`](29.%20Sum%20of%20XOR%20of%20all%20pairs/) |
| 4 | [Construct List using XOR Queries](https://www.geeksforgeeks.org/problems/construct-list-using-given-q-xor-queries/1) | [`35. Construct List using XOR Queries/`](35.%20Construct%20List%20using%20XOR%20Queries/) |
| 5 | [Maximum Subset XOR](https://www.geeksforgeeks.org/problems/maximum-subset-xor/1) | [`40. Maximum Subset XOR/`](40.%20Maximum%20Subset%20XOR/) |
| 6 | [Minimum XOR with given set bits](https://www.geeksforgeeks.org/problems/minimum-x-xor-a--170645/1) | [`53. Minimum XOR with given set bits/`](53.%20Minimum%20XOR%20with%20given%20set%20bits/) |
| 7 | [Ways to Split into 2 with Same XOR](https://www.geeksforgeeks.org/problems/split-the-array0238/1) | [`57. Ways to Split into 2 with Same XOR/`](57.%20Ways%20to%20Split%20into%202%20with%20Same%20XOR/) |
| 8 | [Smallest Non-Zero Number](https://www.geeksforgeeks.org/problems/find-smallest-non-zero-number4510/1) | [`65. Smallest Non-Zero Number/`](65.%20Smallest%20Non-Zero%20Number/) |

## Pattern 6: Bit Manipulation (Non-XOR)

Problems reasoning bit-by-bit about set bits, flips, or pairwise bit comparisons, without XOR-prefix counting being the primary lever.

| # | Problem | Link |
|---|---|---|
| 1 | [Flip to Maximize 1s](https://www.geeksforgeeks.org/problems/flip-bits0240/1) | [`22. Flip to Maximize 1s/`](22.%20Flip%20to%20Maximize%201s/) |
| 2 | [Sum of Pairwise Bit Differences](https://www.geeksforgeeks.org/problems/sum-of-bit-differences2937/1) | [`25. Sum of Pairwise Bit Differences/`](25.%20Sum%20of%20Pairwise%20Bit%20Differences/) |
| 3 | [Total Hamming Distance](https://www.geeksforgeeks.org/problems/total-hamming-distance/1) | [`95. Total Hamming Distance/`](95.%20Total%20Hamming%20Distance/) |

## Pattern 7: Two Pointer / Sorted-Array Techniques

Problems where sorting the array first, then walking with two (or three) pointers from the ends or in tandem, finds pairs/triplets/subsequences meeting a condition in linear or near-linear time after the sort.

| # | Problem | Link |
|---|---|---|
| 1 | [Pythagorean Triplet](https://www.geeksforgeeks.org/problems/pythagorean-triplet3018/1) | [`06. Pythagorean Triplet/`](06.%20Pythagorean%20Triplet/) |
| 2 | [Product Pair](https://www.geeksforgeeks.org/problems/equal-to-product3836/1) | [`15. Product Pair/`](15.%20Product%20Pair/) |
| 3 | [Sorted Subsequence of Size 3](https://www.geeksforgeeks.org/problems/sorted-subsequence-of-size-3/1) | [`18. Sorted Subsequence of Size 3/`](18.%20Sorted%20Subsequence%20of%20Size%203/) |
| 4 | [Maximum Triplet product](https://www.geeksforgeeks.org/problems/maximum-triplet-product--170647/1) | [`24. Maximum Triplet product/`](24.%20Maximum%20Triplet%20product/) |
| 5 | [Count Sorted Subsequences of Size 3](https://www.geeksforgeeks.org/problems/magic-triplets4003/1) | [`55. Count Sorted Subsequences of Size 3/`](55.%20Count%20Sorted%20Subsequences%20of%20Size%203/) |
| 6 | [Pairs with Sum Less Than Product](https://www.geeksforgeeks.org/problems/pair-array-product-sum4912/1) | [`85. Pairs with Sum Less Than Product/`](85.%20Pairs%20with%20Sum%20Less%20Than%20Product/) |
| 7 | [4 Sum – Count Quadruplets with Sum](https://www.geeksforgeeks.org/problems/count-quadruplets-with-given-sum/1) | [`86. 4 Sum – Count Quadruplets with Sum/`](86.%204%20Sum%20%E2%80%93%20Count%20Quadruplets%20with%20Sum/) |
| 8 | [Max Product Sorted Subsequence of Size 3](https://www.geeksforgeeks.org/problems/maximum-product-of-increasing-subsequence-of-size-32027/1) | [`79. Max Product Sorted Subsequence of Size 3/`](79.%20Max%20Product%20Sorted%20Subsequence%20of%20Size%203/) |

## Pattern 8: Greedy Array Rearrangement / Scheduling

Problems solved by sorting (or otherwise ordering) elements and then making locally optimal choices — placement, matching, or scheduling — that provably yield the global optimum.

| # | Problem | Link |
|---|---|---|
| 1 | [Rearrange Array Alternately](https://www.geeksforgeeks.org/problems/-rearrange-array-alternately-1587115620/1) | [`05. Rearrange Array Alternately/`](05.%20Rearrange%20Array%20Alternately/) |
| 2 | [Max sum in the configuration](https://www.geeksforgeeks.org/problems/max-sum-in-the-configuration/1) | [`12. Max sum in the configuration/`](12.%20Max%20sum%20in%20the%20configuration/) |
| 3 | [Sum of 2 Primes](https://www.geeksforgeeks.org/problems/sum-of-prime4751/1) | [`23. Sum of 2 Primes/`](23.%20Sum%20of%202%20Primes/) |
| 4 | [Minimum to Add for Prime Array Sum](https://www.geeksforgeeks.org/problems/transform-to-prime4635/1) | [`34. Minimum to Add for Prime Array Sum/`](34.%20Minimum%20to%20Add%20for%20Prime%20Array%20Sum/) |
| 5 | [Buy Maximum Stocks](https://www.geeksforgeeks.org/problems/buy-maximum-stocks-if-i-stocks-can-be-bought-on-i-th-day/1) | [`36. Buy Maximum Stocks/`](36.%20Buy%20Maximum%20Stocks/) |
| 6 | [Min Swaps to Group 1s](https://www.geeksforgeeks.org/problems/minimum-swaps-required-to-group-all-1s-together2451/1) | [`47. Min Swaps to Group 1s/`](47.%20Min%20Swaps%20to%20Group%201s/) |
| 7 | [Equalize the Towers](https://www.geeksforgeeks.org/problems/equalize-the-towers2804/1) | [`54. Equalize the Towers/`](54.%20Equalize%20the%20Towers/) |
| 8 | [Make Arrays Equal with Min Operations](https://www.geeksforgeeks.org/problems/unequal-arrays--170647/1) | [`58. Make Arrays Equal with Min Operations/`](58.%20Make%20Arrays%20Equal%20with%20Min%20Operations/) |
| 9 | [Minimum Increment or Double Operations to Convert](https://www.geeksforgeeks.org/problems/minimum-steps-to-get-desired-array5519/1) | [`63. Minimum Increment or Double Operations to Convert/`](63.%20Minimum%20Increment%20or%20Double%20Operations%20to%20Convert/) |
| 10 | [Min Removals to Make Max <= 2*Min](https://www.geeksforgeeks.org/problems/remove-minimum-elements4612/1) | [`74. Min Removals to Make Max = 2Min/`](74.%20Min%20Removals%20to%20Make%20Max%20%3D%202Min/) |
| 11 | [Fill 1's With Changes to Adjacent](https://www.geeksforgeeks.org/problems/fill-array-by-1s0920/1) | [`75. Fill 1's With Changes to Adjacent/`](75.%20Fill%201%27s%20With%20Changes%20to%20Adjacent/) |
| 12 | [Minimum Picks for K Sock Pairs](https://www.geeksforgeeks.org/problems/number-of-minimum-picks-to-get-k-pairs-of-socks-from-a-drawer--141631/1) | [`78. Minimum Picks for K Sock Pairs/`](78.%20Minimum%20Picks%20for%20K%20Sock%20Pairs/) |
| 13 | [Minimum Operations to Make Array Sorted](https://www.geeksforgeeks.org/problems/minimum-incrementdecrement-to-make-array-non-increasing--170637/1) | [`80. Minimum Operations to Make Array Sorted/`](80.%20Minimum%20Operations%20to%20Make%20Array%20Sorted/) |
| 14 | [Distribute n Candies Among k People](https://www.geeksforgeeks.org/problems/distribute-n-candies/1) | [`83. Distribute n Candies Among k People/`](83.%20Distribute%20n%20Candies%20Among%20k%20People/) |
| 15 | [Minimum Platforms 2](https://www.geeksforgeeks.org/problems/minimum-platforms-2--170647/1) | [`99. Minimum Platforms 2/`](99.%20Minimum%20Platforms%202/) |

## Pattern 9: In-Place Array Transformation

Problems requiring the array to be permuted, rotated, or restructured using only O(1) extra space via clever index math, cyclic swaps, or encoding tricks.

| # | Problem | Link |
|---|---|---|
| 1 | [Rotate Array](https://www.geeksforgeeks.org/problems/rotate-array-by-n-elements-1587115621/1) | [`01. Rotate Array/`](01.%20Rotate%20Array/) |
| 2 | [Reverse Array in Groups](https://www.geeksforgeeks.org/problems/reverse-array-in-groups0255/1) | [`03. Reverse Array in Groups/`](03.%20Reverse%20Array%20in%20Groups/) |
| 3 | [Next Permutation](https://www.geeksforgeeks.org/problems/next-permutation5226/1) | [`07. Next Permutation/`](07.%20Next%20Permutation/) |
| 4 | [Transform Array In-Place](https://www.geeksforgeeks.org/problems/rearrange-an-array-with-o1-extra-space3142/1) | [`11. Transform Array In-Place/`](11.%20Transform%20Array%20In-Place/) |
| 5 | [Rotate and delete](https://www.geeksforgeeks.org/problems/rotate-and-delete-1587115621/1) | [`31. Rotate and delete/`](31.%20Rotate%20and%20delete/) |
| 6 | [Shuffle Integers](https://www.geeksforgeeks.org/problems/shuffle-integers2401/1) | [`32. Shuffle Integers/`](32.%20Shuffle%20Integers/) |

## Pattern 10: Stock Buy-Sell / Sequential Decision DP

Classic single-pass or DP-style array scans that track running best/worst values to decide optimal buy/sell or transaction points.

| # | Problem | Link |
|---|---|---|
| 1 | [Stock Buy and Sell – Multiple Transaction Allowed](https://www.geeksforgeeks.org/problems/stock-buy-and-sell2615/1) | [`08. Stock Buy and Sell – Multiple Transaction Allowed/`](08.%20Stock%20Buy%20and%20Sell%20%E2%80%93%20Multiple%20Transaction%20Allowed/) |
| 2 | [Max Sum Path in Two Arrays](https://www.geeksforgeeks.org/problems/max-sum-path-in-two-arrays/1) | [`20. Max Sum Path in Two Arrays/`](20.%20Max%20Sum%20Path%20in%20Two%20Arrays/) |
| 3 | [Longest Subsequence with Adjacent Diff as 1](https://www.geeksforgeeks.org/problems/longest-sub-sequence-such-that-difference-between-adjacents-is-one2558/1) | [`27. Longest Subsequence with Adjacent Diff as 1/`](27.%20Longest%20Subsequence%20with%20Adjacent%20Diff%20as%201/) |
| 4 | [Longest Geometric Progression](https://www.geeksforgeeks.org/problems/longest-geometric-progression0131/1) | [`98. Longest Geometric Progression/`](98.%20Longest%20Geometric%20Progression/) |

## Pattern 11: Monotonic Run / Bitonic Subarray Scan

Problems identifying the longest or extremal contiguous run of a monotonic, alternating-parity, or bitonic (increase-then-decrease) shape via a single directional scan.

| # | Problem | Link |
|---|---|---|
| 1 | [Longest Subarray of Evens and Odds](https://www.geeksforgeeks.org/problems/longest-subarray-of-evens-and-odds/1) | [`42. Longest Subarray of Evens and Odds/`](42.%20Longest%20Subarray%20of%20Evens%20and%20Odds/) |
| 2 | [Longest Bitonic Subarray](https://www.geeksforgeeks.org/problems/maximum-length-bitonic-subarray5730/1) | [`52. Longest Bitonic Subarray/`](52.%20Longest%20Bitonic%20Subarray/) |
| 3 | [Mountain Subarray Queries](https://www.geeksforgeeks.org/problems/mountain-subarray-problem/1) | [`59. Mountain Subarray Queries/`](59.%20Mountain%20Subarray%20Queries/) |
| 4 | [Local Min and Max Sequence Ordering](https://www.geeksforgeeks.org/problems/track-the-trail/1) | [`91. Local Min and Max Sequence Ordering/`](91.%20Local%20Min%20and%20Max%20Sequence%20Ordering/) |

## Pattern 12: Monotonic Stack / Nearest Greater-Smaller

Problems finding, for each element, the nearest smaller/larger element to its left or right, solved efficiently with a monotonic stack instead of brute-force nested scans.

| # | Problem | Link |
|---|---|---|
| 1 | [Farthest Smaller Right](https://www.geeksforgeeks.org/problems/farthest-smaller-right/1) | [`60. Farthest Smaller Right/`](60.%20Farthest%20Smaller%20Right/) |
| 2 | [Farthest Smaller on Right](https://www.geeksforgeeks.org/problems/farthest-number--170636/1) | [`73. Farthest Smaller on Right/`](73.%20Farthest%20Smaller%20on%20Right/) |
| 3 | [Subarray Inversions](https://www.geeksforgeeks.org/problems/subarray-inversions0512/1) | [`100. Subarray Inversions/`](100.%20Subarray%20Inversions/) |

## Pattern 13: Hashing / Frequency Counting

Problems whose core trick is counting occurrences, remainders, or distinct values via a hash map or frequency array to answer pair/subset/divisibility questions in linear time.

| # | Problem | Link |
|---|---|---|
| 1 | [Max Occured in n Ranges](https://www.geeksforgeeks.org/problems/maximum-occured-integer4602/1) | [`17. Max Occured in n Ranges/`](17.%20Max%20Occured%20in%20n%20Ranges/) |
| 2 | [Maximum Identical Bowls](https://www.geeksforgeeks.org/problems/maximum-identical-bowls--170647/1) | [`51. Maximum Identical Bowls/`](51.%20Maximum%20Identical%20Bowls/) |
| 3 | [Distinct Difference](https://www.geeksforgeeks.org/problems/distinct-difference--170647/1) | [`61. Distinct Difference/`](61.%20Distinct%20Difference/) |
| 4 | [Subsets Multiple of 3](https://www.geeksforgeeks.org/problems/possible-groups2013/1) | [`72. Subsets Multiple of 3/`](72.%20Subsets%20Multiple%20of%203/) |
| 5 | [Subset with Pair Sums Not Divisible by K](https://www.geeksforgeeks.org/problems/subset-with-no-pair-sum-divisible-by-k1105/1) | [`76. Subset with Pair Sums Not Divisible by K/`](76.%20Subset%20with%20Pair%20Sums%20Not%20Divisible%20by%20K/) |
| 6 | [Queries for Counts of Multiples](https://www.geeksforgeeks.org/problems/queries-for-counts-of-multiples-in-an-array4028/1) | [`81. Queries for Counts of Multiples/`](81.%20Queries%20for%20Counts%20of%20Multiples/) |
| 7 | [Pairs with Given Modulo Value](https://www.geeksforgeeks.org/problems/mr-modulo-and-pairs5610/1) | [`84. Pairs with Given Modulo Value/`](84.%20Pairs%20with%20Given%20Modulo%20Value/) |
| 8 | [Max Modulo Pair in an Array](https://www.geeksforgeeks.org/problems/mr-modulo-and-arrays2827/1) | [`92. Max Modulo Pair in an Array/`](92.%20Max%20Modulo%20Pair%20in%20an%20Array/) |
| 9 | [Values Present in At Least K Ranges](https://www.geeksforgeeks.org/problems/sick-pasha0323/1) | [`97. Values Present in At Least K Ranges/`](97.%20Values%20Present%20in%20At%20Least%20K%20Ranges/) |
| 10 | [Pairs from Distict Element Subarrays](https://www.geeksforgeeks.org/problems/sub-array-pairs5530/1) | [`101. Pairs from Distict Element Subarrays/`](101.%20Pairs%20from%20Distict%20Element%20Subarrays/) |

## Pattern 14: Subset / Combinatorial Selection

Problems requiring enumeration or DP over subsets — products, XORs, differences, or divisor counts of chosen elements — where the search space is combinatorial rather than a simple scan.

| # | Problem | Link |
|---|---|---|
| 1 | [Max Product Subset](https://www.geeksforgeeks.org/problems/maximum-product-subset-of-an-array/1) | [`13. Max Product Subset/`](13.%20Max%20Product%20Subset/) |
| 2 | [Not a Subset Sum](https://www.geeksforgeeks.org/problems/smallest-number-subset1220/1) | [`19. Not a Subset Sum/`](19.%20Not%20a%20Subset%20Sum/) |
| 3 | [Min Product Subset](https://www.geeksforgeeks.org/problems/max-and-min-products3347/1) | [`66. Min Product Subset/`](66.%20Min%20Product%20Subset/) |
| 4 | [Maximum GCD of K Partition Sums](https://www.geeksforgeeks.org/problems/gcd-array--170645/1) | [`69. Maximum GCD of K Partition Sums/`](69.%20Maximum%20GCD%20of%20K%20Partition%20Sums/) |
| 5 | [Count Divisors of Array Product](https://www.geeksforgeeks.org/problems/count-divisors-of-product-of-array-elements0244/1) | [`77. Count Divisors of Array Product/`](77.%20Count%20Divisors%20of%20Array%20Product/) |
| 6 | [Subsets with given Max Diff](https://www.geeksforgeeks.org/problems/count-number4832/1) | [`94. Subsets with given Max Diff/`](94.%20Subsets%20with%20given%20Max%20Diff/) |
| 7 | [Sum of subset differences](https://www.geeksforgeeks.org/problems/sum-of-subset-differences/1) | [`96. Sum of subset differences/`](96.%20Sum%20of%20subset%20differences/) |

## Pattern 15: Index-Value Difference / Max-Diff Tricks

Problems that reframe a max/min difference question in terms of index and value simultaneously, solved by tracking running extremes or transforming the comparison.

| # | Problem | Link |
|---|---|---|
| 1 | [Max Diff Elements and Indexes](https://www.geeksforgeeks.org/problems/maximum-value-of-difference-of-a-pair-of-elements-and-their-index/1) | [`56. Max Diff Elements and Indexes/`](56.%20Max%20Diff%20Elements%20and%20Indexes/) |
| 2 | [Array Elements Divisible by Any Others](https://www.geeksforgeeks.org/problems/count-special-numbers--170647/1) | [`38. Array Elements Divisible by Any Others/`](38.%20Array%20Elements%20Divisible%20by%20Any%20Others/) |

## Pattern 16: Math / Number-Theoretic Construction

Problems whose core challenge is number-theoretic or combinatorial construction — factorials, permutation sums, digit arrangement, or simulation — more than a classic array-scanning technique.

| # | Problem | Link |
|---|---|---|
| 1 | [Pascal Triangle](https://www.geeksforgeeks.org/problems/pascal-triangle0652/1) | [`10. Pascal Triangle/`](10.%20Pascal%20Triangle/) |
| 2 | [Factorial of Array under Modulo](https://www.geeksforgeeks.org/problems/large-factorial4721/1) | [`45. Factorial of Array under Modulo/`](45.%20Factorial%20of%20Array%20under%20Modulo/) |
| 3 | [Number to Words](https://www.geeksforgeeks.org/problems/number-to-words0335/1) | [`48. Number to Words/`](48.%20Number%20to%20Words/) |
| 4 | [Composite and  Prime Queries](https://www.geeksforgeeks.org/problems/composite-and-prime0359/1) | [`50. Composite and Prime Queries/`](50.%20Composite%20and%20Prime%20Queries/) |
| 5 | [Tic Tac Toe](https://www.geeksforgeeks.org/problems/tic-tac-toe2412/1) | [`64. Tic Tac Toe/`](64.%20Tic%20Tac%20Toe/) |
| 6 | [Sum of Permutations of Distinct Digits](https://www.geeksforgeeks.org/problems/sum-of-permutations/1) | [`87. Sum of Permutations of Distinct Digits/`](87.%20Sum%20of%20Permutations%20of%20Distinct%20Digits/) |
| 7 | [Smallest Number from Power Digits](https://www.geeksforgeeks.org/problems/the-tiny-miny2541/1) | [`89. Smallest Number from Power Digits/`](89.%20Smallest%20Number%20from%20Power%20Digits/) |
| 8 | [Leading Digit and Exponent of Factorial](https://www.geeksforgeeks.org/problems/large-factorials2539/1) | [`90. Leading Digit and Exponent of Factorial/`](90.%20Leading%20Digit%20and%20Exponent%20of%20Factorial/) |
| 9 | [Rubik's Cube](https://www.geeksforgeeks.org/problems/rubiks-cube4626/1) | [`102. Rubik's Cube/`](102.%20Rubik%27s%20Cube/) |
