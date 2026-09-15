# Arrays — Easy: Patterns

This file groups all 135 "Arrays > Easy" problems into the core recurring patterns/techniques they draw on. Each problem is listed under the single pattern that best captures its dominant solving technique, so you can revise by pattern instead of by problem name.

## Pattern 1: Two Pointers / In-place Partitioning

Problems where two indices (often from opposite ends, or a slow/fast pair) scan the array once to partition, segregate, reverse, or rearrange elements in place without extra space. Common for "move X to one side", "reverse", "segregate 0s/1s", "zig-zag".

| # | Problem | Link |
|---|---|---|
| 1 | [Move All Zeroes to End](https://www.geeksforgeeks.org/problems/move-all-zeroes-to-end-of-array0751/1) | [`04. Move All Zeroes to End/`](04.%20Move%20All%20Zeroes%20to%20End/) |
| 2 | [Reverse Array](https://www.geeksforgeeks.org/problems/reverse-an-array/1) | [`05. Reverse Array/`](05.%20Reverse%20Array/) |
| 3 | [Array of alternate +ve and -ve nos](https://www.geeksforgeeks.org/problems/array-of-alternate-ve-and-ve-nos1401/1) | [`06. Alternate Positive Negative/`](06.%20Alternate%20Positive%20Negative/) |
| 4 | [Move all negative elements to end](https://www.geeksforgeeks.org/problems/move-all-negative-elements-to-end1813/1) | [`07. Move all negative elements to end/`](07.%20Move%20all%20negative%20elements%20to%20end/) |
| 5 | [Segregate 0s and 1s](https://www.geeksforgeeks.org/problems/segregate-0s-and-1s5106/1) | [`12. Segregate 0s and 1s/`](12.%20Segregate%200s%20and%201s/) |
| 6 | [Convert Array into Zig-Zag Fashion](https://www.geeksforgeeks.org/problems/convert-array-into-zig-zag-fashion1638/1) | [`13. Convert To Zig-Zag/`](13.%20Convert%20To%20Zig-Zag/) |
| 7 | [Need Some Change (Swap Adjacent in Array)](https://www.geeksforgeeks.org/problems/need-some-change/1) | [`20. Swap Adjacent in Array/`](20.%20Swap%20Adjacent%20in%20Array/) |
| 8 | [Print an array in Pendulum Arrangement](https://www.geeksforgeeks.org/problems/print-an-array-in-pendulum-arrangement4004/1) | [`47. Array in Pendulum Arrangement/`](47.%20Array%20in%20Pendulum%20Arrangement/) |
| 9 | [Even and Odd (Even at Even Index and Odd at Odd)](https://www.geeksforgeeks.org/problems/even-and-odd/1) | [`52. Even at Even Index and Odd at Odd/`](52.%20Even%20at%20Even%20Index%20and%20Odd%20at%20Odd/) |
| 10 | [Even and odd elements at even and odd positions](https://www.geeksforgeeks.org/problems/even-and-odd-elements-at-even-and-odd-positions1342/1) | [`68. Position According to Parity/`](68.%20Position%20According%20to%20Parity/) |
| 11 | [Need Some Change (Java) — Swap All with Next of Next](https://www.geeksforgeeks.org/problems/need-some-change-java/1) | [`65. Swap All with Next of Next/`](65.%20Swap%20All%20with%20Next%20of%20Next/) |
| 12 | [Two Swaps (Sorted in Two Swaps)](https://www.geeksforgeeks.org/problems/two-swaps--155623/1) | [`37. Sorted in Two Swaps/`](37.%20Sorted%20in%20Two%20Swaps/) |
| 13 | [Rearrange an array such that arr[i] = i](https://www.geeksforgeeks.org/problems/rearrange-an-array-such-that-arri-i3618/1) | [`30. Rearrange to Make arr[i] = i/`](30.%20Rearrange%20to%20Make%20arr%5Bi%5D%20%3D%20i/) |
| 14 | [Left or Right Positioned Array](https://www.geeksforgeeks.org/problems/left-or-right-positioned-array5757/1) | [`121. Left or Right Positioned Array/`](121.%20Left%20or%20Right%20Positioned%20Array/) |

## Pattern 2: Sorting-based

Problems whose cleanest solution is to sort the array (or a copy) first, then read off the answer directly from the sorted order — kth element, closest value, forming largest/smallest number, checking distinctness, etc.

| # | Problem | Link |
|---|---|---|
| 1 | [Third Largest Element](https://www.geeksforgeeks.org/problems/third-largest-element/1) | [`09. Third Largest/`](09.%20Third%20Largest/) |
| 2 | [Find the smallest and second smallest element](https://www.geeksforgeeks.org/problems/find-the-smallest-and-second-smallest-element-in-an-array3226/1) | [`11. First and Second Smallests/`](11.%20First%20and%20Second%20Smallests/) |
| 3 | [Professor and Parties (all elements distinct)](https://www.geeksforgeeks.org/problems/professor-and-parties2000/1) | [`51. Check if all array elements are distinct/`](51.%20Check%20if%20all%20array%20elements%20are%20distinct/) |
| 4 | [Form Largest Number from Digits](https://www.geeksforgeeks.org/problems/form-largest-number-from-digits5430/1) | [`55. Largest from Digits/`](55.%20Largest%20from%20Digits/) |
| 5 | [Maximum Gap](https://www.geeksforgeeks.org/problems/maximum-gap3845/1) | [`67. Maximum Gap/`](67.%20Maximum%20Gap/) |
| 6 | [Length of Unsorted Subarray](https://www.geeksforgeeks.org/problems/length-unsorted-subarray3022/1) | [`49. Sort Unsorted Subarray/`](49.%20Sort%20Unsorted%20Subarray/) |
| 7 | [Minimum Product Pair](https://www.geeksforgeeks.org/problems/minimum-product-pair3608/1) | [`78. Minimum Product Pair/`](78.%20Minimum%20Product%20Pair/) |
| 8 | [Pair with Greatest Product in Array](https://www.geeksforgeeks.org/problems/pair-with-greatest-product-in-array3342/1) | [`81. Max Product of other Two in an Array/`](81.%20Max%20Product%20of%20other%20Two%20in%20an%20Array/) |
| 9 | [Chocolate Station](https://www.geeksforgeeks.org/problems/chocolate-station2951/1) | [`84. Chocolate Station/`](84.%20Chocolate%20Station/) |
| 10 | [Maximum Difference Indexes](https://www.geeksforgeeks.org/problems/maximum-difference-10429/1) | [`89. Maximum difference Indexes/`](89.%20Maximum%20difference%20Indexes/) |
| 11 | [Reading Books](https://www.geeksforgeeks.org/problems/reading-books3803/1) | [`90. Reading Books/`](90.%20Reading%20Books/) |
| 12 | [Number of Pairs with Maximum Sum](https://www.geeksforgeeks.org/problems/number-of-pairs-with-maximum-sum2924/1) | [`97. Count Pairs With Maximum Sum/`](97.%20Count%20Pairs%20With%20Maximum%20Sum/) |
| 13 | [Maximum Weight Difference (choosing K numbers)](https://www.geeksforgeeks.org/problems/maximum-weight-difference5036/1) | [`99. Maximum Difference by Choosing K Numbers/`](99.%20Maximum%20Difference%20by%20Choosing%20K%20Numbers/) |
| 14 | [Pair the Minimum (Minimize Max Pair Sum)](https://www.geeksforgeeks.org/problems/pair-the-minimum5535/1) | [`104. Minimize Max Pair Sum/`](104.%20Minimize%20Max%20Pair%20Sum/) |
| 15 | [Form a Triangle (triplet check)](https://www.geeksforgeeks.org/problems/form-a-triangle5935/1) | [`109. Check if Any Triplet  can Form a Triangle/`](109.%20Check%20if%20Any%20Triplet%20%20can%20Form%20a%20Triangle/) |
| 16 | [Count the Pairs with Maximum Difference](https://www.geeksforgeeks.org/problems/count-the-pairs-with-maximum-difference4807/1) | [`114. Count Pairs with Max Diff/`](114.%20Count%20Pairs%20with%20Max%20Diff/) |
| 17 | [Maximum Value K (k larger elements)](https://www.geeksforgeeks.org/problems/maximum-value-k2745/1) | [`120. Maximum k with k Larger Elements/`](120.%20Maximum%20k%20with%20k%20Larger%20Elements/) |

## Pattern 3: Binary Search on Sorted Array

Problems directly asking for lower/upper bound, floor/ceil, closest element, kth missing, or an index/value search on a sorted array — solved in O(log n) with binary search variants.

| # | Problem | Link |
|---|---|---|
| 1 | [Ceil the Floor (Floor and Ceil in Unsorted)](https://www.geeksforgeeks.org/problems/ceil-the-floor2802/1) | [`10. Floor and Ceil in Unsorted/`](10.%20Floor%20and%20Ceil%20in%20Unsorted/) |
| 2 | [Implement Lower Bound](https://www.geeksforgeeks.org/problems/implement-lower-bound/1) | [`17. Implement Lower Bound/`](17.%20Implement%20Lower%20Bound/) |
| 3 | [Find Index (First and Last in Unsorted)](https://www.geeksforgeeks.org/problems/find-index4752/1) | [`19. First and Last in Unosrted/`](19.%20First%20and%20Last%20in%20Unosrted/) |
| 4 | [Find the Closest Number](https://www.geeksforgeeks.org/problems/find-the-closest-number5513/1) | [`21. Closest in Sorted Array/`](21.%20Closest%20in%20Sorted%20Array/) |
| 5 | [Implement Upper Bound](https://www.geeksforgeeks.org/problems/implement-upper-bound/1) | [`26. Implement Upper Bound/`](26.%20Implement%20Upper%20Bound/) |
| 6 | [K-th Missing Element (sorted)](https://www.geeksforgeeks.org/problems/k-th-missing-element3635/1) | [`39. K-th Missing in Sorted/`](39.%20K-th%20Missing%20in%20Sorted/) |
| 7 | [Magical Number (Same Value as Index in Sorted)](https://www.geeksforgeeks.org/problems/magical-number-1587115620/1) | [`60. Same Value as Index in Sorted/`](60.%20Same%20Value%20as%20Index%20in%20Sorted/) |
| 8 | [Missing Number in Sorted Array of Natural Numbers](https://www.geeksforgeeks.org/problems/missing-number-in-sorted-array-of-natural-numbers/1) | [`88. Missing Number in Sorted Array of Natural Numbers/`](88.%20Missing%20Number%20in%20Sorted%20Array%20of%20Natural%20Numbers/) |
| 9 | [Find K-th Missing Element (a[] missing from b[])](https://www.geeksforgeeks.org/problems/find-k-th-missing-element2556/1) | [`91. K-th in a[] Missing from b[]/`](91.%20K-th%20in%20a%5B%5D%20Missing%20from%20b%5B%5D/) |
| 10 | [Partition Point in the Array](https://www.geeksforgeeks.org/problems/partition-point-in-the-array0004/1) | [`92. Partition Point in Array/`](92.%20Partition%20Point%20in%20Array/) |
| 11 | [Equal Point in Sorted Array](https://www.geeksforgeeks.org/problems/equal-point-in-sorted-array0040/1) | [`106. Equal Point in Sorted Array/`](106.%20Equal%20Point%20in%20Sorted%20Array/) |
| 12 | [Minimum Element whose N-th Power is Greater than Product](https://www.geeksforgeeks.org/problems/minimum-element-whose-n-th-power-is-greater-than-product-of-an-array4640/1) | [`116. Minimum N-th Power More Than Array Product/`](116.%20Minimum%20N-th%20Power%20More%20Than%20Array%20Product/) |

## Pattern 4: Hashing / Frequency Counting

Problems that use a hash set/map (or a count array) to track seen elements, frequencies, or duplicates in O(n) — finding duplicates, distinct counts, unique pairs, unions.

| # | Problem | Link |
|---|---|---|
| 1 | [Find Duplicates in an Array (Limited Range)](https://www.geeksforgeeks.org/problems/find-duplicates-in-an-array/1) | [`02. Duplicates in a Limited Range Array/`](02.%20Duplicates%20in%20a%20Limited%20Range%20Array/) |
| 2 | [Find Distinct Elements](https://www.geeksforgeeks.org/problems/find-distinct-elements--130928/1) | [`45. Count Distinct in an Array/`](45.%20Count%20Distinct%20in%20an%20Array/) |
| 3 | [Union of Two Sorted Arrays with Distinct Elements](https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays-with-distinct-elements/1) | [`54. Union of Two Sorted with Distinct/`](54.%20Union%20of%20Two%20Sorted%20with%20Distinct/) |
| 4 | [Count the Specials (n/k times occurring)](https://www.geeksforgeeks.org/problems/count-the-specials/1) | [`57. Count nk Times Occurring/`](57.%20Count%20nk%20Times%20Occurring/) |
| 5 | [Find Duplicates Under Given Constraints (Majority in Sorted)](https://www.geeksforgeeks.org/problems/find-duplicates-under-given-constraints0856/1) | [`66. Majority in a Sorted Array/`](66.%20Majority%20in%20a%20Sorted%20Array/) |
| 6 | [Find Unique Pair in an Array with Pairs of Numbers](https://www.geeksforgeeks.org/problems/find-unique-pair-in-an-array-with-pairs-of-numbers2425/1) | [`103. Unique Pair in Array/`](103.%20Unique%20Pair%20in%20Array/) |
| 7 | [Absolute Distinct Count](https://www.geeksforgeeks.org/problems/absolute-distinct-count5118/1) | [`108. Positive Distinct Count/`](108.%20Positive%20Distinct%20Count/) |
| 8 | [Union of Two Arrays with Distinct Elements](https://www.geeksforgeeks.org/problems/union-of-two-arrays-with-distinct-elements/1) | [`129. Union of Two Arrays with Distinct Elements/`](129.%20Union%20of%20Two%20Arrays%20with%20Distinct%20Elements/) |
| 9 | [Count Subsets having Distinct Even Numbers](https://www.geeksforgeeks.org/problems/count-subsets-having-distinct-even-numbers5726/1) | [`119. Subsets with Distinct and Even Numbers/`](119.%20Subsets%20with%20Distinct%20and%20Even%20Numbers/) |

## Pattern 5: Prefix/Suffix Arrays

Problems solved by precomputing running sums, max/min-so-far, or counts from the left and/or right in one or two linear passes, then answering per-index in O(1) — leaders, greater-on-right, product-except-self style, sunlight-blocked buildings.

| # | Problem | Link |
|---|---|---|
| 1 | [Leaders in an Array](https://www.geeksforgeeks.org/problems/leaders-in-an-array-1587115620/1) | [`01. Array Leaders/`](01.%20Array%20Leaders/) |
| 2 | [Product of Array Except Self](https://www.geeksforgeeks.org/problems/product-of-array-element/1) | [`15. Product of Array/`](15.%20Product%20of%20Array/) |
| 3 | [Buildings Receiving Sunlight](https://www.geeksforgeeks.org/problems/buildings-receiving-sunlight3032/1) | [`16. Buildings with Sunlight/`](16.%20Buildings%20with%20Sunlight/) |
| 4 | [Unsorted Array (Left Smaller Right Greater)](https://www.geeksforgeeks.org/problems/unsorted-array4925/1) | [`14. Left Smaller Right Greater/`](14.%20Left%20Smaller%20Right%20Greater/) |
| 5 | [Greater on Right Side](https://www.geeksforgeeks.org/problems/greater-on-right-side4305/1) | [`33. Greatest on Right Side/`](33.%20Greatest%20on%20Right%20Side/) |
| 6 | [Sum of Submatrix Elements](https://www.geeksforgeeks.org/problems/addition-of-submatrix5835/1) | [`71. Sum of Submatrix Elements/`](71.%20Sum%20of%20Submatrix%20Elements/) |
| 7 | [Bird and Maximum Fruit Gathering](https://www.geeksforgeeks.org/problems/bird-and-maximum-fruit-gathering--170645/1) | [`76. Bird and Max Fruit Gathering/`](76.%20Bird%20and%20Max%20Fruit%20Gathering/) |
| 8 | [Balance with Respect to an Array](https://www.geeksforgeeks.org/problems/balance-with-respect-to-an-array5443/1) | [`96. Balanced Floor and Ceil Distance/`](96.%20Balanced%20Floor%20and%20Ceil%20Distance/) |
| 9 | [Max Sum Submatrix Queries](https://www.geeksforgeeks.org/problems/max-sum-submatrix2725/1) | [`118. Max Sum Submatrix Queries/`](118.%20Max%20Sum%20Submatrix%20Queries/) |
| 10 | [Total Distance Travelled in a Permutation of 1..n](https://www.geeksforgeeks.org/problems/total-distance-travelled-in-an-array3628/1) | [`98. Distance Travelled in a Permutation of 1 to n/`](98.%20Distance%20Travelled%20in%20a%20Permutation%20of%201%20to%20n/) |

## Pattern 6: Sliding Window / Subarray Scan

Problems that scan a contiguous window (fixed or variable size) across the array to track a running property — max average subarray, longest increasing run, consecutive ones, subarrays with equal min/max, non-overlapping subarray lengths.

| # | Problem | Link |
|---|---|---|
| 1 | [Max Consecutive Ones](https://www.geeksforgeeks.org/problems/max-consecutive-one/1) | [`32. Max Consecutive Bit/`](32.%20Max%20Consecutive%20Bit/) |
| 2 | [Number of Subarrays of 0s](https://www.geeksforgeeks.org/problems/number-of-subarrays-of-0s--170647/1) | [`56. Coount Subarrays with 0's Only/`](56.%20Coount%20Subarrays%20with%200%27s%20Only/) |
| 3 | [Maximum Average Subarray](https://www.geeksforgeeks.org/problems/maximum-average-subarray5859/1) | [`62. Maximum Average Subarray/`](62.%20Maximum%20Average%20Subarray/) |
| 4 | [Longest Increasing Subarray](https://www.geeksforgeeks.org/problems/longest-increasing-subarray3811/1) | [`64. Longest Increasing Subarray/`](64.%20Longest%20Increasing%20Subarray/) |
| 5 | [Sum of Lengths of Non-Overlapping Subarrays](https://www.geeksforgeeks.org/problems/sum-of-lengths-of-non-overlapping-subarrays2237/1) | [`75. Sum of Lengths of Non-Overlapping SubArrays/`](75.%20Sum%20of%20Lengths%20of%20Non-Overlapping%20SubArrays/) |
| 6 | [Find Maximum Sum Strictly Increasing Subarray](https://www.geeksforgeeks.org/problems/find-maximum-sum-strictly-increasing-subarray4443/1) | [`105. Max Sum Strictly Increasing Subarray/`](105.%20Max%20Sum%20Strictly%20Increasing%20Subarray/) |
| 7 | [Number of Subarrays whose Minimum and Maximum are Same](https://www.geeksforgeeks.org/problems/number-of-subarrays-whose-minimum-and-maximum-are-same5259/1) | [`123. Subarrays with Same Min and Max/`](123.%20Subarrays%20with%20Same%20Min%20and%20Max/) |
| 8 | [Maximum Size of Consecutives (with K Additions)](https://www.geeksforgeeks.org/problems/maximum-size-of-consecutives3154/1) | [`132. Maximum Consecutives Subset with K Additions/`](132.%20Maximum%20Consecutives%20Subset%20with%20K%20Additions/) |
| 9 | [Consecutive Array Elements](https://www.geeksforgeeks.org/problems/consecutive-array-elements2711/1) | [`86. Consecutive Array Elements/`](86.%20Consecutive%20Array%20Elements/) |
| 10 | [Equal Sum and Product Subarrays](https://www.geeksforgeeks.org/problems/equal-sum-and-product2057/1) | [`93. Equal Sum and Product Subarrays/`](93.%20Equal%20Sum%20and%20Product%20Subarrays/) |
| 11 | [Pairs of Adjacent Elements (count consecutive)](https://www.geeksforgeeks.org/problems/pairs-of-adjacent-elements4814/1) | [`117. Count Consecutive Adjacent Pairs/`](117.%20Count%20Consecutive%20Adjacent%20Pairs/) |

## Pattern 7: Two-Pointer Pair Search (Sorted Array)

Problems that find pairs satisfying a sum/difference condition by walking two pointers across a sorted array (or sorting first), rather than brute-force checking all pairs.

| # | Problem | Link |
|---|---|---|
| 1 | [Pairs With Difference K](https://www.geeksforgeeks.org/problems/pairs-with-difference-k1713/1) | [`28. All Pairs with Diff k/`](28.%20All%20Pairs%20with%20Diff%20k/) |
| 2 | [Pairs with Difference Less than K](https://www.geeksforgeeks.org/problems/pairs-with-difference-less-than-k1348/1) | [`61. Pairs with Less Than K Diff/`](61.%20Pairs%20with%20Less%20Than%20K%20Diff/) |
| 3 | [Nth Item Through Sum (Kth in Two Arrays Sums)](https://www.geeksforgeeks.org/problems/nth-item-through-sum3544/1) | [`69. Kth in Two Arrays Sums/`](69.%20Kth%20in%20Two%20Arrays%20Sums/) |
| 4 | [Pair with Largest Sum Which is Less Than K](https://www.geeksforgeeks.org/problems/pair-with-largest-sum-which-is-less-than-k-in-the-array/1) | [`107. Max Pair Sum Less Than K/`](107.%20Max%20Pair%20Sum%20Less%20Than%20K/) |
| 5 | [Finding Pairs (Search Pairs in a String)](https://www.geeksforgeeks.org/problems/finding-pairs2835/1) | [`115. Search Pairs in a String/`](115.%20Search%20Pairs%20in%20a%20String/) |

## Pattern 8: Greedy

Problems solvable by making the locally optimal choice at each step (often after sorting) to reach a global optimum — negating smallest values, flipping bulbs, equalizing with minimum operations, distributing gifts/skills.

| # | Problem | Link |
|---|---|---|
| 1 | [Maximize Sum After K Negations](https://www.geeksforgeeks.org/problems/maximize-sum-after-k-negations1149/1) | [`22. Maximize Sum After k Negations/`](22.%20Maximize%20Sum%20After%20k%20Negations/) |
| 2 | [Compete the Skills](https://www.geeksforgeeks.org/problems/compete-the-skills5807/1) | [`44. Compete the Skills/`](44.%20Compete%20the%20Skills/) |
| 3 | [Minimum Steps to Make Product Equal to One](https://www.geeksforgeeks.org/problems/minimum-steps-to-make-product-equal-to-one/1) | [`58. Minimum Steps for Product One/`](58.%20Minimum%20Steps%20for%20Product%20One/) |
| 4 | [Make Array Elements Equal](https://www.geeksforgeeks.org/problems/make-array-elements-equal--170647/1) | [`42. Make Array Elements Equal/`](42.%20Make%20Array%20Elements%20Equal/) |
| 5 | [Array Operations (Make Array 0 with Subarray Ops)](https://www.geeksforgeeks.org/problems/array-operations--170648/1) | [`43. Make Array 0 with Subarray Operations/`](43.%20Make%20Array%200%20with%20Subarray%20Operations/) |
| 6 | [Minimum Increment by K Operations to Make All Equal](https://www.geeksforgeeks.org/problems/minimum-increment-by-k-operations-to-make-all-equal/1) | [`101. Minimum Increment by k to Make Equal/`](101.%20Minimum%20Increment%20by%20k%20to%20Make%20Equal/) |
| 7 | [Faulty Wiring and Bulbs](https://www.geeksforgeeks.org/problems/faulty-wiring-and-bulbs2939/1) | [`102. Minimum Right Flips to Turn On All Bulbs/`](102.%20Minimum%20Right%20Flips%20to%20Turn%20On%20All%20Bulbs/) |
| 8 | [Equalization of an Array](https://www.geeksforgeeks.org/problems/equalization-of-an-array1656/1) | [`112. Minimum Operations to Equalize Array/`](112.%20Minimum%20Operations%20to%20Equalize%20Array/) |
| 9 | [Gifts Gifts Gifts (Distribution According to Preference)](https://www.geeksforgeeks.org/problems/gifts-gifts-gifts1524/1) | [`126. Gift Distribution According to Preference/`](126.%20Gift%20Distribution%20According%20to%20Preference/) |
| 10 | [Minimum Value Product (Replace All with Min Value)](https://www.geeksforgeeks.org/problems/minimum-value-product1814/1) | [`127. Replace All with Min Value and Greater Product/`](127.%20Replace%20All%20with%20Min%20Value%20and%20Greater%20Product/) |
| 11 | [Cross the Hurdles - the Game](https://www.geeksforgeeks.org/problems/cross-the-hurdles-the-game4734/1) | [`128. Energy After Crossing All Hurdles/`](128.%20Energy%20After%20Crossing%20All%20Hurdles/) |
| 12 | [Minimum Energy (Minimum Initial Energy to Cross)](https://www.geeksforgeeks.org/problems/minimum-energy1107/1) | [`80. Minimum Initial Energy to Cross/`](80.%20Minimum%20Initial%20Energy%20to%20Cross/) |
| 13 | [Decreasing Sequence with K Subtraction](https://www.geeksforgeeks.org/problems/decreasing-sequence2722/1) | [`122. Make Decreasing Sequence with K Subtraction/`](122.%20Make%20Decreasing%20Sequence%20with%20K%20Subtraction/) |
| 14 | [Stuffs Division (Distribution with i Allocated to arr[i])](https://www.geeksforgeeks.org/problems/stuffs-division5735/1) | [`100. Distribution with i Allocated to arr[i]/`](100.%20Distribution%20with%20i%20Allocated%20to%20arr%5Bi%5D/) |
| 15 | [Left Out Candies](https://www.geeksforgeeks.org/problems/left-out-candies5652/1) | [`87. Left Out Candies/`](87.%20Left%20Out%20Candies/) |
| 16 | [Drive the Car](https://www.geeksforgeeks.org/problems/drive-the-car2541/1) | [`74. Drive the car/`](74.%20Drive%20the%20car/) |
| 17 | [Split Array Elements into Bounded Parts](https://www.geeksforgeeks.org/problems/total-count2415/1) | [`29. Split Array Elements into Bounded Parts/`](29.%20Split%20Array%20Elements%20into%20Bounded%20Parts/) |
| 18 | [Frogs and Jumps](https://www.geeksforgeeks.org/problems/frogs-and-jumps--170647/1) | [`24. Frogs and Jumps/`](24.%20Frogs%20and%20Jumps/) |
| 19 | [Jumping Caterpillars](https://www.geeksforgeeks.org/problems/jumping-caterpillars4412/1) | [`63. Jumping Caterpillars/`](63.%20Jumping%20Caterpillars/) |
| 20 | [Possible to Form a Regular Polygon](https://www.geeksforgeeks.org/problems/regular-polygon-12611/1) | [`130. Possible to Form a Regular Polygon/`](130.%20Possible%20to%20Form%20a%20Regular%20Polygon/) |

## Pattern 9: Simple Linear Scan / Min-Max Tracking

Straightforward single-pass problems that just track a running min, max, sum, or count as they iterate — no auxiliary structure or two-pointer technique needed beyond basic bookkeeping.

| # | Problem | Link |
|---|---|---|
| 1 | [Minimum Distance Between Two Numbers](https://www.geeksforgeeks.org/problems/minimum-distance-between-two-numbers/1) | [`08. Minimum distance in an Array/`](08.%20Minimum%20distance%20in%20an%20Array/) |
| 2 | [Maximum in Struct Array (Max Pairwise Computed Value)](https://www.geeksforgeeks.org/problems/maximum-in-struct-array/1) | [`36. Maximum Pairwise Computed Value/`](36.%20Maximum%20Pairwise%20Computed%20Value/) |
| 3 | [K-Sorted Array (Check k Sorted)](https://www.geeksforgeeks.org/problems/k-sorted-array1610/1) | [`40. Check k Sorted/`](40.%20Check%20k%20Sorted/) |
| 4 | [Minimum Absolute Difference Between Adjacent Elements (Circular)](https://www.geeksforgeeks.org/problems/minimum-absloute-difference-between-adjacent-elements-in-a-circular-array-1587115620/1) | [`41. Minimum adjacent difference in a circular array/`](41.%20Minimum%20adjacent%20difference%20in%20a%20circular%20array/) |
| 5 | [Find Number of Numbers (Count a Digit in Array)](https://www.geeksforgeeks.org/problems/find-number-of-numbers/1) | [`46. Count a Digit in Array/`](46.%20Count%20a%20Digit%20in%20Array/) |
| 6 | [Play with an Array](https://www.geeksforgeeks.org/problems/play-with-an-array/1) | [`48. Play with an array/`](48.%20Play%20with%20an%20array/) |
| 7 | [Maximum Number of Zeroes](https://www.geeksforgeeks.org/problems/maximum-number-of-zeroes4048/1) | [`50. Maximum number of zeroes/`](50.%20Maximum%20number%20of%20zeroes/) |
| 8 | [Minimum Number](https://www.geeksforgeeks.org/problems/minimum-number--170647/1) | [`53. Minimum Number/`](53.%20Minimum%20Number/) |
| 9 | [Java ArrayList Operation](https://www.geeksforgeeks.org/problems/arraylist-operation/1) | [`59. Java ArrayList Operation/`](59.%20Java%20ArrayList%20Operation/) |
| 10 | [Minimum Integer](https://www.geeksforgeeks.org/problems/minimum-integer--170647/1) | [`27. Minimum Integer/`](27.%20Minimum%20Integer/) |
| 11 | [Max Value](https://www.geeksforgeeks.org/problems/max-value1205/1) | [`70. Max value/`](70.%20Max%20value/) |
| 12 | [Missing Ranges of Numbers](https://www.geeksforgeeks.org/problems/missing-ranges-of-numbers1019/1) | [`72. Missing Intervals in an Array/`](72.%20Missing%20Intervals%20in%20an%20Array/) |
| 13 | [Digits in a Set (Count the Numbers)](https://www.geeksforgeeks.org/problems/count-the-numbers2359/1) | [`79. Digits in a Set/`](79.%20Digits%20in%20a%20Set/) |
| 14 | [Sum of Distinct Elements (1 to n)](https://www.geeksforgeeks.org/problems/sum-of-distinct-elements-15115/1) | [`83. Distinct Sum in Array of 1 to n/`](83.%20Distinct%20Sum%20in%20Array%20of%201%20to%20n/) |
| 15 | [K-Modulus Array Element (Values with Equal Remainders)](https://www.geeksforgeeks.org/problems/k-modulus-array-element0255/1) | [`85. Values with Equal Array Remainders/`](85.%20Values%20with%20Equal%20Array%20Remainders/) |
| 16 | [Tracks (Check for Specific Order Around Mid)](https://www.geeksforgeeks.org/problems/tracks0436/1) | [`94. Check for Specific Order Around Mid/`](94.%20Check%20for%20Specific%20Order%20Around%20Mid/) |
| 17 | [The Inverting Factor](https://www.geeksforgeeks.org/problems/the-inverting-factor3932/1) | [`95. The Inverting Factor/`](95.%20The%20Inverting%20Factor/) |
| 18 | [Almost Prime Numbers](https://www.geeksforgeeks.org/problems/almost-prime-numbers/1) | [`111. Almost Prime Numbers/`](111.%20Almost%20Prime%20Numbers/) |
| 19 | [Powers Game (Count Digit Occurrences in Powers)](https://www.geeksforgeeks.org/problems/powers-game3701/1) | [`113. Count Digit Occurrences in Powers/`](113.%20Count%20Digit%20Occurrences%20in%20Powers/) |
| 20 | [Number of Matches](https://www.geeksforgeeks.org/problems/number-of-matches1120/1) | [`131. Number of Matches/`](131.%20Number%20of%20Matches/) |
| 21 | [Sum of a Numpy Array](https://www.geeksforgeeks.org/problems/find-the-sum-of-all-elements-in-a-numpy-array/1) | [`124. Sum of a Numpy Array/`](124.%20Sum%20of%20a%20Numpy%20Array/) |
| 22 | [Flatten a 3D Array into a 1D Array](https://www.geeksforgeeks.org/problems/flatten-a-3d-array-into-a-1d-array/1) | [`133. Flatten a 3D Array into a 1D Array/`](133.%20Flatten%20a%203D%20Array%20into%20a%201D%20Array/) |
| 23 | [Linear Algebra - Solve Linear System](https://www.geeksforgeeks.org/problems/linear-algebra-solve-linear-system/1) | [`134. Linear Algebra - Solve Linear System/`](134.%20Linear%20Algebra%20-%20Solve%20Linear%20System/) |

## Pattern 10: Math / Digit / Number-Theory on Arrays

Problems that lean on arithmetic or number-theory reasoning applied over the array — divisibility by 3, big-number addition/increment represented as arrays, XOR tricks, modulo transformations.

| # | Problem | Link |
|---|---|---|
| 1 | [Adding One to Array](https://www.geeksforgeeks.org/problems/adding-one2529/1) | [`18. Adding One to Array/`](18.%20Adding%20One%20to%20Array/) |
| 2 | [Form a Number Divisible by 3 Using Array Digits](https://www.geeksforgeeks.org/problems/form-a-number-divisible-by-3-using-array-digits0717/1) | [`23. Array Permutation Divisible by 3/`](23.%20Array%20Permutation%20Divisible%20by%203/) |
| 3 | [Replace with XOR of Adjacent](https://www.geeksforgeeks.org/problems/replace-with-xor-of-adjacent/1) | [`25. Replace with XOR of Adjacent/`](25.%20Replace%20with%20XOR%20of%20Adjacent/) |
| 4 | [Adding Ones](https://www.geeksforgeeks.org/problems/adding-ones3628/1) | [`34. Adding Ones/`](34.%20Adding%20Ones/) |
| 5 | [Sum of Two Numbers Represented as Arrays](https://www.geeksforgeeks.org/problems/sum-of-two-numbers-represented-as-arrays3110/1) | [`35. Sum of Two Represented as Arrays/`](35.%20Sum%20of%20Two%20Represented%20as%20Arrays/) |
| 6 | [Replace with Adjacent Multiplication](https://www.geeksforgeeks.org/problems/replace-with-adjacent-multiplication/1) | [`125. Replace with Adjacent Multiplication/`](125.%20Replace%20with%20Adjacent%20Multiplication/) |
| 7 | [Array Transformation with Repeated Steps and Modulo Operation](https://www.geeksforgeeks.org/problems/array-transformation-with-repeated-steps-and-modulo-operation/1) | [`135. Array Transformation with Repeated Steps and Modulo Operation/`](135.%20Array%20Transformation%20with%20Repeated%20Steps%20and%20Modulo%20Operation/) |

## Pattern 11: Cyclic Sort / Index-Value Mapping

Problems on arrays containing values in a bounded range (like 1..n) where placing each value at its "correct" index (value == index) in one pass reveals missing/repeating/duplicate elements or builds an inverse mapping.

| # | Problem | Link |
|---|---|---|
| 1 | [Find Missing and Repeating](https://www.geeksforgeeks.org/problems/find-missing-and-repeating2512/1) | [`03. Missing And Repeating/`](03.%20Missing%20And%20Repeating/) |
| 2 | [Inverse Permutation](https://www.geeksforgeeks.org/problems/inverse-permutation0344/1) | [`73. Inverse Permutation/`](73.%20Inverse%20Permutation/) |
| 3 | [Any Duplicate Within K Distance](https://www.geeksforgeeks.org/problems/kth-distance3757/1) | [`31. Any Duplicate Within K Distance/`](31.%20Any%20Duplicate%20Within%20K%20Distance/) |

## Pattern 12: Reconstruction / Simulation

Problems that reconstruct an original array from derived data (like a pair-sum array), or simulate a described process/game step by step to compute the final outcome.

| # | Problem | Link |
|---|---|---|
| 1 | [Construct an Array from its Pair-Sum Array](https://www.geeksforgeeks.org/problems/construct-an-array-from-its-pair-sum-array/1) | [`77. Construct an array from its pair-sum array/`](77.%20Construct%20an%20array%20from%20its%20pair-sum%20array/) |
| 2 | [Equal Sums (Equal Sum with Insertion)](https://www.geeksforgeeks.org/problems/equal-sums4801/1) | [`110. Equal Sum with Insertion/`](110.%20Equal%20Sum%20with%20Insertion/) |
| 3 | [Matrix Interchange](https://www.geeksforgeeks.org/problems/matrix-interchange/1) | [`38. Matrix Interchange/`](38.%20Matrix%20Interchange/) |

## Pattern 13: Brute-Force Enumeration / Generation

Problems whose natural/expected solution enumerates all subarrays, pairs, or combinations directly (often O(n²) or worse) because the problem asks to generate or examine every such structure.

| # | Problem | Link |
|---|---|---|
| 1 | [Generating All Subarrays](https://www.geeksforgeeks.org/problems/generating-all-subarrays/1) | [`82. Generating All Subarrays/`](82.%20Generating%20All%20Subarrays/) |

Total problems covered: **135**
