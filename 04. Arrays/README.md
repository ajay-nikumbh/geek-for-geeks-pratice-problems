# 4. Arrays

[← Back to root](../README.md) · [GfG topic problems](https://www.geeksforgeeks.org/explore?category%5B%5D=Arrays)

## Patterns (merged across all difficulty levels)

Same core technique shows up at every difficulty — this view merges those occurrences into one pattern, with problems ordered Basics → Easy → Medium → Hard. Logic/Time/Space are filled in as each problem's full article is written.

| # | Pattern | Total | Basics | Easy | Medium | Hard |
|---|---|---|---|---|---|---|
| 1 | [Greedy](#greedy) | 35 | 0 | 20 | 15 | 0 |
| 2 | [Single Pass Linear Scan](#single-pass-linear-scan) | 34 | 11 | 23 | 0 | 0 |
| 3 | [Two Pointer](#two-pointer) | 34 | 5 | 19 | 8 | 2 |
| 4 | [Hashing / Frequency Counting](#hashing-frequency-counting) | 24 | 5 | 9 | 10 | 0 |
| 5 | [Sorting-based](#sorting-based) | 23 | 6 | 17 | 0 | 0 |
| 6 | [Prefix / Suffix Aggregate](#prefix-suffix-aggregate) | 22 | 6 | 10 | 6 | 0 |
| 7 | [Binary Search on Sorted Array](#binary-search-on-sorted-array) | 20 | 0 | 12 | 8 | 0 |
| 8 | [Math / Number-Theoretic Construction](#math-number-theoretic-construction) | 16 | 0 | 7 | 9 | 0 |
| 9 | [In-Place Rearrangement](#in-place-rearrangement) | 12 | 6 | 0 | 6 | 0 |
| 10 | [Sliding Window](#sliding-window) | 11 | 0 | 11 | 0 | 0 |
| 11 | [Array Modification / Insertion / Access](#array-modification-insertion-access) | 8 | 8 | 0 | 0 | 0 |
| 12 | [Digit / Bit Manipulation](#digit-bit-manipulation) | 8 | 4 | 0 | 3 | 1 |
| 13 | [Binary Search on Answer](#binary-search-on-answer) | 8 | 0 | 0 | 4 | 4 |
| 14 | [K-th Element / Order Statistics](#k-th-element-order-statistics) | 8 | 0 | 0 | 6 | 2 |
| 15 | [XOR / Prefix-XOR Techniques](#xor-prefix-xor-techniques) | 8 | 0 | 0 | 8 | 0 |
| 16 | [Subset / Combinatorial Selection](#subset-combinatorial-selection) | 7 | 0 | 0 | 7 | 0 |
| 17 | [Duplicate / Distinct Element Handling](#duplicate-distinct-element-handling) | 5 | 5 | 0 | 0 | 0 |
| 18 | [Stock Buy-Sell / Sequential Decision DP](#stock-buy-sell-sequential-decision-dp) | 4 | 0 | 0 | 4 | 0 |
| 19 | [Monotonic Run / Bitonic Subarray](#monotonic-run-bitonic-subarray) | 4 | 0 | 0 | 4 | 0 |
| 20 | [Cyclic Sort / Index-Value Mapping](#cyclic-sort-index-value-mapping) | 3 | 0 | 3 | 0 | 0 |
| 21 | [Reconstruction / Simulation](#reconstruction-simulation) | 3 | 0 | 3 | 0 | 0 |
| 22 | [Monotonic Stack](#monotonic-stack) | 3 | 0 | 0 | 3 | 0 |
| 23 | [Index-Value Difference / Max-Diff Tricks](#index-value-difference-max-diff-tricks) | 2 | 0 | 0 | 2 | 0 |
| 24 | [Brute-Force Enumeration / Generation](#brute-force-enumeration-generation) | 1 | 0 | 1 | 0 | 0 |
| 25 | [Circular Array / Kadane's Algorithm](#circular-array-kadane-s-algorithm) | 1 | 0 | 0 | 0 | 1 |

### Greedy (35)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Maximize Sum After k Negations](https://www.geeksforgeeks.org/problems/maximize-sum-after-k-negations1149/1) | — | — | — | Easy | — | Arrays, logical-thinking | [`02. Easy/22. Maximize Sum After k Negations/`](02.%20Easy/22.%20Maximize%20Sum%20After%20k%20Negations/) |
| 2 | [Compete the Skills](https://www.geeksforgeeks.org/problems/compete-the-skills5807/1) | — | — | — | Easy | — | Arrays | [`02. Easy/44. Compete the Skills/`](02.%20Easy/44.%20Compete%20the%20Skills/) |
| 3 | [Minimum Steps for Product One](https://www.geeksforgeeks.org/problems/minimum-steps-to-make-product-equal-to-one/1) | — | — | — | Easy | Amazon, Microsoft | Arrays, Mathematics | [`02. Easy/58. Minimum Steps for Product One/`](02.%20Easy/58.%20Minimum%20Steps%20for%20Product%20One/) |
| 4 | [Make Array Elements Equal](https://www.geeksforgeeks.org/problems/make-array-elements-equal--170647/1) | — | — | — | Easy | Expedia | Arrays | [`02. Easy/42. Make Array Elements Equal/`](02.%20Easy/42.%20Make%20Array%20Elements%20Equal/) |
| 5 | [Make Array 0 with Subarray Operations](https://www.geeksforgeeks.org/problems/array-operations--170648/1) | — | — | — | Easy | — | Arrays, Mathematics | [`02. Easy/43. Make Array 0 with Subarray Operations/`](02.%20Easy/43.%20Make%20Array%200%20with%20Subarray%20Operations/) |
| 6 | [Minimum Increment by k to Make Equal](https://www.geeksforgeeks.org/problems/minimum-increment-by-k-operations-to-make-all-equal/1) | — | — | — | Easy | — | Arrays | [`02. Easy/101. Minimum Increment by k to Make Equal/`](02.%20Easy/101.%20Minimum%20Increment%20by%20k%20to%20Make%20Equal/) |
| 7 | [Minimum Right Flips to Turn On All Bulbs](https://www.geeksforgeeks.org/problems/faulty-wiring-and-bulbs2939/1) | — | — | — | Easy | — | Arrays, Binary Representation | [`02. Easy/102. Minimum Right Flips to Turn On All Bulbs/`](02.%20Easy/102.%20Minimum%20Right%20Flips%20to%20Turn%20On%20All%20Bulbs/) |
| 8 | [Minimum Operations to Equalize Array](https://www.geeksforgeeks.org/problems/equalization-of-an-array1656/1) | — | — | — | Easy | — | Arrays | [`02. Easy/112. Minimum Operations to Equalize Array/`](02.%20Easy/112.%20Minimum%20Operations%20to%20Equalize%20Array/) |
| 9 | [Gift Distribution According to Preference](https://www.geeksforgeeks.org/problems/gifts-gifts-gifts1524/1) | — | — | — | Easy | — | Arrays | [`02. Easy/126. Gift Distribution According to Preference/`](02.%20Easy/126.%20Gift%20Distribution%20According%20to%20Preference/) |
| 10 | [Replace All with Min Value and Greater Product](https://www.geeksforgeeks.org/problems/minimum-value-product1814/1) | — | — | — | Easy | — | Arrays, Mathematics | [`02. Easy/127. Replace All with Min Value and Greater Product/`](02.%20Easy/127.%20Replace%20All%20with%20Min%20Value%20and%20Greater%20Product/) |
| 11 | [Energy After Crossing All Hurdles](https://www.geeksforgeeks.org/problems/cross-the-hurdles-the-game4734/1) | — | — | — | Easy | — | Arrays | [`02. Easy/128. Energy After Crossing All Hurdles/`](02.%20Easy/128.%20Energy%20After%20Crossing%20All%20Hurdles/) |
| 12 | [Minimum Initial Energy to Cross](https://www.geeksforgeeks.org/problems/minimum-energy1107/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/80. Minimum Initial Energy to Cross/`](02.%20Easy/80.%20Minimum%20Initial%20Energy%20to%20Cross/) |
| 13 | [Make Decreasing Sequence with K Subtraction](https://www.geeksforgeeks.org/problems/decreasing-sequence2722/1) | — | — | — | Easy | — | Arrays, Mathematics | [`02. Easy/122. Make Decreasing Sequence with K Subtraction/`](02.%20Easy/122.%20Make%20Decreasing%20Sequence%20with%20K%20Subtraction/) |
| 14 | [Distribution with i Allocated to arr[i]](https://www.geeksforgeeks.org/problems/stuffs-division5735/1) | — | — | — | Easy | — | Arrays, Mathematics | [`02. Easy/100. Distribution with i Allocated to arr[i]/`](02.%20Easy/100.%20Distribution%20with%20i%20Allocated%20to%20arr[i]/) |
| 15 | [Left Out Candies](https://www.geeksforgeeks.org/problems/left-out-candies5652/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/87. Left Out Candies/`](02.%20Easy/87.%20Left%20Out%20Candies/) |
| 16 | [Drive the car](https://www.geeksforgeeks.org/problems/drive-the-car2541/1) | — | — | — | Easy | — | Arrays | [`02. Easy/74. Drive the car/`](02.%20Easy/74.%20Drive%20the%20car/) |
| 17 | [Split Array Elements into Bounded Parts](https://www.geeksforgeeks.org/problems/total-count2415/1) | — | — | — | Easy | Zoho | Arrays, Division, Mathematics | [`02. Easy/29. Split Array Elements into Bounded Parts/`](02.%20Easy/29.%20Split%20Array%20Elements%20into%20Bounded%20Parts/) |
| 18 | [Frogs and Jumps](https://www.geeksforgeeks.org/problems/frogs-and-jumps--170647/1) | — | — | — | Easy | PayPal | Arrays, sieve | [`02. Easy/24. Frogs and Jumps/`](02.%20Easy/24.%20Frogs%20and%20Jumps/) |
| 19 | [Jumping Caterpillars](https://www.geeksforgeeks.org/problems/jumping-caterpillars4412/1) | — | — | — | Easy | Myntra | Arrays, Mathematics | [`02. Easy/63. Jumping Caterpillars/`](02.%20Easy/63.%20Jumping%20Caterpillars/) |
| 20 | [Possible to Form a Regular Polygon](https://www.geeksforgeeks.org/problems/regular-polygon-12611/1) | — | — | — | Easy | — | Arrays | [`02. Easy/130. Possible to Form a Regular Polygon/`](02.%20Easy/130.%20Possible%20to%20Form%20a%20Regular%20Polygon/) |
| 21 | [Rearrange Array Alternately](https://www.geeksforgeeks.org/problems/-rearrange-array-alternately-1587115620/1) | — | — | — | Medium | Zoho | Arrays | [`03. Medium/05. Rearrange Array Alternately/`](03.%20Medium/05.%20Rearrange%20Array%20Alternately/) |
| 22 | [Max sum in the configuration](https://www.geeksforgeeks.org/problems/max-sum-in-the-configuration/1) | — | — | — | Medium | Amazon | Arrays, Mathematics | [`03. Medium/12. Max sum in the configuration/`](03.%20Medium/12.%20Max%20sum%20in%20the%20configuration/) |
| 23 | [Sum of 2 Primes](https://www.geeksforgeeks.org/problems/sum-of-prime4751/1) | — | — | — | Medium | Zoho, Yahoo | Number Theory, constructive algo, Prime Number, Arrays | [`03. Medium/23. Sum of 2 Primes/`](03.%20Medium/23.%20Sum%20of%202%20Primes/) |
| 24 | [Minimum to Add for Prime Array Sum](https://www.geeksforgeeks.org/problems/transform-to-prime4635/1) | — | — | — | Medium | — | Arrays, Prime Number, sieve | [`03. Medium/34. Minimum to Add for Prime Array Sum/`](03.%20Medium/34.%20Minimum%20to%20Add%20for%20Prime%20Array%20Sum/) |
| 25 | [Buy Maximum Stocks](https://www.geeksforgeeks.org/problems/buy-maximum-stocks-if-i-stocks-can-be-bought-on-i-th-day/1) | — | — | — | Medium | — | Arrays | [`03. Medium/36. Buy Maximum Stocks/`](03.%20Medium/36.%20Buy%20Maximum%20Stocks/) |
| 26 | [Min Swaps to Group 1s](https://www.geeksforgeeks.org/problems/minimum-swaps-required-to-group-all-1s-together2451/1) | — | — | — | Medium | Adobe | Arrays | [`03. Medium/47. Min Swaps to Group 1s/`](03.%20Medium/47.%20Min%20Swaps%20to%20Group%201s/) |
| 27 | [Equalize the Towers](https://www.geeksforgeeks.org/problems/equalize-the-towers2804/1) | — | — | — | Medium | — | Arrays, Binary Search | [`03. Medium/54. Equalize the Towers/`](03.%20Medium/54.%20Equalize%20the%20Towers/) |
| 28 | [Make Arrays Equal with Min Operations](https://www.geeksforgeeks.org/problems/unequal-arrays--170647/1) | — | — | — | Medium | — | Arrays, logical-thinking | [`03. Medium/58. Make Arrays Equal with Min Operations/`](03.%20Medium/58.%20Make%20Arrays%20Equal%20with%20Min%20Operations/) |
| 29 | [Minimum Increment or Double Operations to Convert](https://www.geeksforgeeks.org/problems/minimum-steps-to-get-desired-array5519/1) | — | — | — | Medium | — | Arrays | [`03. Medium/63. Minimum Increment or Double Operations to Convert/`](03.%20Medium/63.%20Minimum%20Increment%20or%20Double%20Operations%20to%20Convert/) |
| 30 | [Min Removals to Make Max <= 2*Min](https://www.geeksforgeeks.org/problems/remove-minimum-elements4612/1) | — | — | — | Medium | Amazon | Arrays | [`03. Medium/74. Min Removals to Make Max = 2Min/`](03.%20Medium/74.%20Min%20Removals%20to%20Make%20Max%20=%202Min/) |
| 31 | [Fill 1's With Changes to Adjacent](https://www.geeksforgeeks.org/problems/fill-array-by-1s0920/1) | — | — | — | Medium | Amazon | Arrays, Mathematics | [`03. Medium/75. Fill 1's With Changes to Adjacent/`](03.%20Medium/75.%20Fill%201's%20With%20Changes%20to%20Adjacent/) |
| 32 | [Minimum Picks for K Sock Pairs](https://www.geeksforgeeks.org/problems/number-of-minimum-picks-to-get-k-pairs-of-socks-from-a-drawer--141631/1) | — | — | — | Medium | Amazon | Arrays | [`03. Medium/78. Minimum Picks for K Sock Pairs/`](03.%20Medium/78.%20Minimum%20Picks%20for%20K%20Sock%20Pairs/) |
| 33 | [Minimum Operations to Make Array Sorted](https://www.geeksforgeeks.org/problems/minimum-incrementdecrement-to-make-array-non-increasing--170637/1) | — | — | — | Medium | Amazon | Arrays, Priority Queue | [`03. Medium/80. Minimum Operations to Make Array Sorted/`](03.%20Medium/80.%20Minimum%20Operations%20to%20Make%20Array%20Sorted/) |
| 34 | [Distribute n Candies Among k People](https://www.geeksforgeeks.org/problems/distribute-n-candies/1) | — | — | — | Medium | Microsoft | Arrays, Mathematics, Binary Search | [`03. Medium/83. Distribute n Candies Among k People/`](03.%20Medium/83.%20Distribute%20n%20Candies%20Among%20k%20People/) |
| 35 | [Minimum Platforms 2](https://www.geeksforgeeks.org/problems/minimum-platforms-2--170647/1) | — | — | — | Medium | — | Arrays | [`03. Medium/99. Minimum Platforms 2/`](03.%20Medium/99.%20Minimum%20Platforms%202/) |

### Single Pass Linear Scan (34)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Largest in Array](https://www.geeksforgeeks.org/problems/largest-element-in-array4009/1) | — | — | — | Basics | Infosys, Oracle, Wipro, Morgan Stanley | Arrays | [`01. Basics/01. Largest in Array/`](01.%20Basics/01.%20Largest%20in%20Array/) |
| 2 | [Min and Max in Array](https://www.geeksforgeeks.org/problems/find-minimum-and-maximum-element-in-an-array4428/1) | — | — | — | Basics | NPCI | Arrays | [`01. Basics/02. Min and Max in Array/`](01.%20Basics/02.%20Min%20and%20Max%20in%20Array/) |
| 3 | [Sum of Array](https://www.geeksforgeeks.org/problems/sum-all-array-elements/1) | — | — | — | Basics | — | Arrays | [`01. Basics/04. Sum of Array/`](01.%20Basics/04.%20Sum%20of%20Array/) |
| 4 | [Count Odd and Even](https://www.geeksforgeeks.org/problems/count-odd-even/1) | — | — | — | Basics | — | Arrays | [`01. Basics/10. Count Odd and Even/`](01.%20Basics/10.%20Count%20Odd%20and%20Even/) |
| 5 | [Strongest Neighbour](https://www.geeksforgeeks.org/problems/strongest-neighbour/1) | — | — | — | Basics | — | Arrays | [`01. Basics/22. Strongest Neighbour/`](01.%20Basics/22.%20Strongest%20Neighbour/) |
| 6 | [Type of array](https://www.geeksforgeeks.org/problems/type-of-array4605/1) | — | — | — | Basics | Amazon | Arrays | [`01. Basics/29. Type of array/`](01.%20Basics/29.%20Type%20of%20array/) |
| 7 | [Two Max Adjacent in an Array](https://www.geeksforgeeks.org/problems/why-is-melody-so-chocolaty0446/1) | — | — | — | Basics | — | Arrays | [`01. Basics/46. Two Max Adjacent in an Array/`](01.%20Basics/46.%20Two%20Max%20Adjacent%20in%20an%20Array/) |
| 8 | [Different Adjacent Elements](https://www.geeksforgeeks.org/problems/distinct-adjacent-element2121/1) | — | — | — | Basics | — | Arrays | [`01. Basics/47. Different Adjacent Elements/`](01.%20Basics/47.%20Different%20Adjacent%20Elements/) |
| 9 | [Max Triplet Sum](https://www.geeksforgeeks.org/problems/maximum-triplet-sum-in-array0129/1) | — | — | — | Basics | — | Arrays | [`01. Basics/39. Max Triplet Sum/`](01.%20Basics/39.%20Max%20Triplet%20Sum/) |
| 10 | [Winner in Pairwise Army Battles](https://www.geeksforgeeks.org/problems/countries-at-war2936/1) | — | — | — | Basics | — | Arrays | [`01. Basics/38. Winner in Pairwise Army Battles/`](01.%20Basics/38.%20Winner%20in%20Pairwise%20Army%20Battles/) |
| 11 | [Occurrences of Consecutive 3 Numbers](https://www.geeksforgeeks.org/problems/special-integers/1) | — | — | — | Basics | — | Arrays, Map | [`01. Basics/56. Occurrences of Consecutive 3 Numbers/`](01.%20Basics/56.%20Occurrences%20of%20Consecutive%203%20Numbers/) |
| 12 | [Minimum distance in an Array](https://www.geeksforgeeks.org/problems/minimum-distance-between-two-numbers/1) | — | — | — | Easy | Paytm, Amazon | Arrays | [`02. Easy/08. Minimum distance in an Array/`](02.%20Easy/08.%20Minimum%20distance%20in%20an%20Array/) |
| 13 | [Maximum Pairwise Computed Value](https://www.geeksforgeeks.org/problems/maximum-in-struct-array/1) | — | — | — | Easy | Microsoft | Arrays | [`02. Easy/36. Maximum Pairwise Computed Value/`](02.%20Easy/36.%20Maximum%20Pairwise%20Computed%20Value/) |
| 14 | [Check k Sorted](https://www.geeksforgeeks.org/problems/k-sorted-array1610/1) | — | — | — | Easy | — | Arrays, Binary Search | [`02. Easy/40. Check k Sorted/`](02.%20Easy/40.%20Check%20k%20Sorted/) |
| 15 | [Minimum adjacent difference in a circular array](https://www.geeksforgeeks.org/problems/minimum-absloute-difference-between-adjacent-elements-in-a-circular-array-1587115620/1) | — | — | — | Easy | — | Arrays | [`02. Easy/41. Minimum adjacent difference in a circular array/`](02.%20Easy/41.%20Minimum%20adjacent%20difference%20in%20a%20circular%20array/) |
| 16 | [Count a Digit in Array](https://www.geeksforgeeks.org/problems/find-number-of-numbers/1) | — | — | — | Easy | — | Arrays | [`02. Easy/46. Count a Digit in Array/`](02.%20Easy/46.%20Count%20a%20Digit%20in%20Array/) |
| 17 | [Play with an array](https://www.geeksforgeeks.org/problems/play-with-an-array/1) | — | — | — | Easy | — | Arrays | [`02. Easy/48. Play with an array/`](02.%20Easy/48.%20Play%20with%20an%20array/) |
| 18 | [Maximum number of zeroes](https://www.geeksforgeeks.org/problems/maximum-number-of-zeroes4048/1) | — | — | — | Easy | Oracle | Arrays | [`02. Easy/50. Maximum number of zeroes/`](02.%20Easy/50.%20Maximum%20number%20of%20zeroes/) |
| 19 | [Minimum Number](https://www.geeksforgeeks.org/problems/minimum-number--170647/1) | — | — | — | Easy | — | Arrays, Number Theory | [`02. Easy/53. Minimum Number/`](02.%20Easy/53.%20Minimum%20Number/) |
| 20 | [Java ArrayList Operation](https://www.geeksforgeeks.org/problems/arraylist-operation/1) | — | — | — | Easy | — | Arrays | [`02. Easy/59. Java ArrayList Operation/`](02.%20Easy/59.%20Java%20ArrayList%20Operation/) |
| 21 | [Minimum Integer](https://www.geeksforgeeks.org/problems/minimum-integer--170647/1) | — | — | — | Easy | — | Mathematics, Arrays | [`02. Easy/27. Minimum Integer/`](02.%20Easy/27.%20Minimum%20Integer/) |
| 22 | [Max value](https://www.geeksforgeeks.org/problems/max-value1205/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/70. Max value/`](02.%20Easy/70.%20Max%20value/) |
| 23 | [Missing Intervals in an Array](https://www.geeksforgeeks.org/problems/missing-ranges-of-numbers1019/1) | — | — | — | Easy | Google | Arrays | [`02. Easy/72. Missing Intervals in an Array/`](02.%20Easy/72.%20Missing%20Intervals%20in%20an%20Array/) |
| 24 | [Digits in a Set](https://www.geeksforgeeks.org/problems/count-the-numbers2359/1) | — | — | — | Easy | Morgan Stanley | Arrays | [`02. Easy/79. Digits in a Set/`](02.%20Easy/79.%20Digits%20in%20a%20Set/) |
| 25 | [Distinct Sum in Array of 1 to n](https://www.geeksforgeeks.org/problems/sum-of-distinct-elements-15115/1) | — | — | — | Easy | — | Arrays | [`02. Easy/83. Distinct Sum in Array of 1 to n/`](02.%20Easy/83.%20Distinct%20Sum%20in%20Array%20of%201%20to%20n/) |
| 26 | [Values with Equal Array Remainders](https://www.geeksforgeeks.org/problems/k-modulus-array-element0255/1) | — | — | — | Easy | — | Arrays, Mathematics | [`02. Easy/85. Values with Equal Array Remainders/`](02.%20Easy/85.%20Values%20with%20Equal%20Array%20Remainders/) |
| 27 | [Check for Specific Order Around Mid](https://www.geeksforgeeks.org/problems/tracks0436/1) | — | — | — | Easy | — | Arrays, Mathematics | [`02. Easy/94. Check for Specific Order Around Mid/`](02.%20Easy/94.%20Check%20for%20Specific%20Order%20Around%20Mid/) |
| 28 | [The Inverting Factor](https://www.geeksforgeeks.org/problems/the-inverting-factor3932/1) | — | — | — | Easy | — | Arrays, Numbers, Reverse | [`02. Easy/95. The Inverting Factor/`](02.%20Easy/95.%20The%20Inverting%20Factor/) |
| 29 | [Almost Prime Numbers](https://www.geeksforgeeks.org/problems/almost-prime-numbers/1) | — | — | — | Easy | — | Arrays, Prime Number | [`02. Easy/111. Almost Prime Numbers/`](02.%20Easy/111.%20Almost%20Prime%20Numbers/) |
| 30 | [Count Digit Occurrences in Powers](https://www.geeksforgeeks.org/problems/powers-game3701/1) | — | — | — | Easy | — | Arrays, Modular Arithmetic, logical-thinking | [`02. Easy/113. Count Digit Occurrences in Powers/`](02.%20Easy/113.%20Count%20Digit%20Occurrences%20in%20Powers/) |
| 31 | [Number of Matches](https://www.geeksforgeeks.org/problems/number-of-matches1120/1) | — | — | — | Easy | — | Arrays | [`02. Easy/131. Number of Matches/`](02.%20Easy/131.%20Number%20of%20Matches/) |
| 32 | [Sum of a Numpy Array](https://www.geeksforgeeks.org/problems/find-the-sum-of-all-elements-in-a-numpy-array/1) | — | — | — | Easy | — | Arrays | [`02. Easy/124. Sum of a Numpy Array/`](02.%20Easy/124.%20Sum%20of%20a%20Numpy%20Array/) |
| 33 | [Flatten a 3D Array into a 1D Array](https://www.geeksforgeeks.org/problems/flatten-a-3d-array-into-a-1d-array/1) | — | — | — | Easy | — | Arrays | [`02. Easy/133. Flatten a 3D Array into a 1D Array/`](02.%20Easy/133.%20Flatten%20a%203D%20Array%20into%20a%201D%20Array/) |
| 34 | [Linear Algebra - Solve Linear System](https://www.geeksforgeeks.org/problems/linear-algebra-solve-linear-system/1) | — | — | — | Easy | — | Arrays | [`02. Easy/134. Linear Algebra - Solve Linear System/`](02.%20Easy/134.%20Linear%20Algebra%20-%20Solve%20Linear%20System/) |

### Two Pointer (34)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Array with All Palindromes](https://www.geeksforgeeks.org/problems/palindromic-array-1587115620/1) | — | — | — | Basics | — | Arrays | [`01. Basics/06. Array with All Palindromes/`](01.%20Basics/06.%20Array%20with%20All%20Palindromes/) |
| 2 | [Smaller and Larger in Sorted](https://www.geeksforgeeks.org/problems/smaller-and-larger4005/1) | — | — | — | Basics | — | Arrays | [`01. Basics/15. Smaller and Larger in Sorted/`](01.%20Basics/15.%20Smaller%20and%20Larger%20in%20Sorted/) |
| 3 | [Palindrome Array](https://www.geeksforgeeks.org/problems/perfect-arrays4645/1) | — | — | — | Basics | — | Arrays | [`01. Basics/16. Palindrome Array/`](01.%20Basics/16.%20Palindrome%20Array/) |
| 4 | [Shortest Unsorted Subarray](https://www.geeksforgeeks.org/problems/shortest-un-ordered-subarray3634/1) | — | — | — | Basics | Oracle | Arrays | [`01. Basics/48. Shortest Unsorted Subarray/`](01.%20Basics/48.%20Shortest%20Unsorted%20Subarray/) |
| 5 | [Check for Bitonic with Same Numbers](https://www.geeksforgeeks.org/problems/perfect-array2344/1) | — | — | — | Basics | — | Arrays | [`01. Basics/50. Check for Bitonic with Same Numbers/`](01.%20Basics/50.%20Check%20for%20Bitonic%20with%20Same%20Numbers/) |
| 6 | [Move All Zeroes to End](https://www.geeksforgeeks.org/problems/move-all-zeroes-to-end-of-array0751/1) | — | — | — | Easy | Paytm, Amazon, Microsoft, Samsung, SAP Labs, Linkedin, Bloomberg, NPCI | Arrays | [`02. Easy/04. Move All Zeroes to End/`](02.%20Easy/04.%20Move%20All%20Zeroes%20to%20End/) |
| 7 | [Reverse Array](https://www.geeksforgeeks.org/problems/reverse-an-array/1) | — | — | — | Easy | Bloomberg, Facebook, TCS, Adobe, Google, Infosys, Capgemini, Morgan Stanley, Amazon, Microsoft, Apple, Yahoo, PayPal, Uber | Arrays | [`02. Easy/05. Reverse Array/`](02.%20Easy/05.%20Reverse%20Array/) |
| 8 | [Alternate Positive Negative](https://www.geeksforgeeks.org/problems/array-of-alternate-ve-and-ve-nos1401/1) | — | — | — | Easy | Paytm, VMWare, Amazon, Microsoft, Intuit | Arrays | [`02. Easy/06. Alternate Positive Negative/`](02.%20Easy/06.%20Alternate%20Positive%20Negative/) |
| 9 | [Move all negative elements to end](https://www.geeksforgeeks.org/problems/move-all-negative-elements-to-end1813/1) | — | — | — | Easy | — | Arrays | [`02. Easy/07. Move all negative elements to end/`](02.%20Easy/07.%20Move%20all%20negative%20elements%20to%20end/) |
| 10 | [Segregate 0s and 1s](https://www.geeksforgeeks.org/problems/segregate-0s-and-1s5106/1) | — | — | — | Easy | Paytm, Goldman Sachs, Fab.com | Arrays | [`02. Easy/12. Segregate 0s and 1s/`](02.%20Easy/12.%20Segregate%200s%20and%201s/) |
| 11 | [Convert To Zig-Zag](https://www.geeksforgeeks.org/problems/convert-array-into-zig-zag-fashion1638/1) | — | — | — | Easy | Paytm, Amazon, Adobe | Arrays | [`02. Easy/13. Convert To Zig-Zag/`](02.%20Easy/13.%20Convert%20To%20Zig-Zag/) |
| 12 | [Swap Adjacent in Array](https://www.geeksforgeeks.org/problems/need-some-change/1) | — | — | — | Easy | — | Arrays | [`02. Easy/20. Swap Adjacent in Array/`](02.%20Easy/20.%20Swap%20Adjacent%20in%20Array/) |
| 13 | [Array in Pendulum Arrangement](https://www.geeksforgeeks.org/problems/print-an-array-in-pendulum-arrangement4004/1) | — | — | — | Easy | FactSet | Arrays | [`02. Easy/47. Array in Pendulum Arrangement/`](02.%20Easy/47.%20Array%20in%20Pendulum%20Arrangement/) |
| 14 | [Even at Even Index and Odd at Odd](https://www.geeksforgeeks.org/problems/even-and-odd/1) | — | — | — | Easy | Paytm, Amazon, Microsoft | Arrays | [`02. Easy/52. Even at Even Index and Odd at Odd/`](02.%20Easy/52.%20Even%20at%20Even%20Index%20and%20Odd%20at%20Odd/) |
| 15 | [Position According to Parity](https://www.geeksforgeeks.org/problems/even-and-odd-elements-at-even-and-odd-positions1342/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/68. Position According to Parity/`](02.%20Easy/68.%20Position%20According%20to%20Parity/) |
| 16 | [Swap All with Next of Next](https://www.geeksforgeeks.org/problems/need-some-change-java/1) | — | — | — | Easy | — | Arrays | [`02. Easy/65. Swap All with Next of Next/`](02.%20Easy/65.%20Swap%20All%20with%20Next%20of%20Next/) |
| 17 | [Sorted in Two Swaps](https://www.geeksforgeeks.org/problems/two-swaps--155623/1) | — | — | — | Easy | — | Arrays | [`02. Easy/37. Sorted in Two Swaps/`](02.%20Easy/37.%20Sorted%20in%20Two%20Swaps/) |
| 18 | [Rearrange to Make arr[i] = i](https://www.geeksforgeeks.org/problems/rearrange-an-array-such-that-arri-i3618/1) | — | — | — | Easy | — | Arrays | [`02. Easy/30. Rearrange to Make arr[i] = i/`](02.%20Easy/30.%20Rearrange%20to%20Make%20arr[i]%20=%20i/) |
| 19 | [Left or Right Positioned Array](https://www.geeksforgeeks.org/problems/left-or-right-positioned-array5757/1) | — | — | — | Easy | — | Arrays | [`02. Easy/121. Left or Right Positioned Array/`](02.%20Easy/121.%20Left%20or%20Right%20Positioned%20Array/) |
| 20 | [All Pairs with Diff k](https://www.geeksforgeeks.org/problems/pairs-with-difference-k1713/1) | — | — | — | Easy | Adobe | Arrays | [`02. Easy/28. All Pairs with Diff k/`](02.%20Easy/28.%20All%20Pairs%20with%20Diff%20k/) |
| 21 | [Pairs with Less Than K Diff](https://www.geeksforgeeks.org/problems/pairs-with-difference-less-than-k1348/1) | — | — | — | Easy | — | Arrays | [`02. Easy/61. Pairs with Less Than K Diff/`](02.%20Easy/61.%20Pairs%20with%20Less%20Than%20K%20Diff/) |
| 22 | [Kth in Two Arrays Sums](https://www.geeksforgeeks.org/problems/nth-item-through-sum3544/1) | — | — | — | Easy | Microsoft | Arrays, STL | [`02. Easy/69. Kth in Two Arrays Sums/`](02.%20Easy/69.%20Kth%20in%20Two%20Arrays%20Sums/) |
| 23 | [Max Pair Sum Less Than K](https://www.geeksforgeeks.org/problems/pair-with-largest-sum-which-is-less-than-k-in-the-array/1) | — | — | — | Easy | — | Arrays | [`02. Easy/107. Max Pair Sum Less Than K/`](02.%20Easy/107.%20Max%20Pair%20Sum%20Less%20Than%20K/) |
| 24 | [Search Pairs in a String](https://www.geeksforgeeks.org/problems/finding-pairs2835/1) | — | — | — | Easy | — | Arrays, STL | [`02. Easy/115. Search Pairs in a String/`](02.%20Easy/115.%20Search%20Pairs%20in%20a%20String/) |
| 25 | [Pythagorean Triplet](https://www.geeksforgeeks.org/problems/pythagorean-triplet3018/1) | — | — | — | Medium | Amazon, Adobe | Arrays | [`03. Medium/06. Pythagorean Triplet/`](03.%20Medium/06.%20Pythagorean%20Triplet/) |
| 26 | [Product Pair](https://www.geeksforgeeks.org/problems/equal-to-product3836/1) | — | — | — | Medium | Amazon, Visa | Arrays | [`03. Medium/15. Product Pair/`](03.%20Medium/15.%20Product%20Pair/) |
| 27 | [Sorted Subsequence of Size 3](https://www.geeksforgeeks.org/problems/sorted-subsequence-of-size-3/1) | — | — | — | Medium | Amazon, FactSet, Walmart | Arrays | [`03. Medium/18. Sorted Subsequence of Size 3/`](03.%20Medium/18.%20Sorted%20Subsequence%20of%20Size%203/) |
| 28 | [Maximum Triplet product](https://www.geeksforgeeks.org/problems/maximum-triplet-product--170647/1) | — | — | — | Medium | VMWare, Amazon, Snapdeal, Flipkart | Arrays, Mathematics | [`03. Medium/24. Maximum Triplet product/`](03.%20Medium/24.%20Maximum%20Triplet%20product/) |
| 29 | [Count Sorted Subsequences of Size 3](https://www.geeksforgeeks.org/problems/magic-triplets4003/1) | — | — | — | Medium | D-E-Shaw | Arrays | [`03. Medium/55. Count Sorted Subsequences of Size 3/`](03.%20Medium/55.%20Count%20Sorted%20Subsequences%20of%20Size%203/) |
| 30 | [Pairs with Sum Less Than Product](https://www.geeksforgeeks.org/problems/pair-array-product-sum4912/1) | — | — | — | Medium | — | Arrays | [`03. Medium/85. Pairs with Sum Less Than Product/`](03.%20Medium/85.%20Pairs%20with%20Sum%20Less%20Than%20Product/) |
| 31 | [4 Sum – Count Quadruplets with Sum](https://www.geeksforgeeks.org/problems/count-quadruplets-with-given-sum/1) | — | — | — | Medium | — | Arrays, Map | [`03. Medium/86. 4 Sum – Count Quadruplets with Sum/`](03.%20Medium/86.%204%20Sum%20–%20Count%20Quadruplets%20with%20Sum/) |
| 32 | [Max Product Sorted Subsequence of Size 3](https://www.geeksforgeeks.org/problems/maximum-product-of-increasing-subsequence-of-size-32027/1) | — | — | — | Medium | — | Set, Arrays | [`03. Medium/79. Max Product Sorted Subsequence of Size 3/`](03.%20Medium/79.%20Max%20Product%20Sorted%20Subsequence%20of%20Size%203/) |
| 33 | [Cake Distribution Problem](https://www.geeksforgeeks.org/problems/cake-distribution-problem--170647/1) | — | — | — | Hard | — | Binary Search, Arrays | [`04. Hard/08. Cake Distribution Problem/`](04.%20Hard/08.%20Cake%20Distribution%20Problem/) |
| 34 | [Subset Count with Product Less Than k](https://www.geeksforgeeks.org/problems/number-of-subsets-with-product-less-than-k/1) | — | — | — | Hard | Morgan Stanley, Amazon | Arrays, subset | [`04. Hard/09. Subset Count with Product Less Than k/`](04.%20Hard/09.%20Subset%20Count%20with%20Product%20Less%20Than%20k/) |

### Hashing / Frequency Counting (24)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Count Smaller in Array](https://www.geeksforgeeks.org/problems/count-of-smaller-elements5947/1) | — | — | — | Basics | — | Arrays | [`01. Basics/08. Count Smaller in Array/`](01.%20Basics/08.%20Count%20Smaller%20in%20Array/) |
| 2 | [Most Frequent of Two](https://www.geeksforgeeks.org/problems/who-has-the-majority/1) | — | — | — | Basics | — | Arrays | [`01. Basics/12. Most Frequent of Two/`](01.%20Basics/12.%20Most%20Frequent%20of%20Two/) |
| 3 | [Even Occurring Elements](https://www.geeksforgeeks.org/problems/even-occurring-elements4332/1) | — | — | — | Basics | — | Arrays, Bit Magic | [`01. Basics/45. Even Occurring Elements/`](01.%20Basics/45.%20Even%20Occurring%20Elements/) |
| 4 | [Average Count Array](https://www.geeksforgeeks.org/problems/average-count-array2215/1) | — | — | — | Basics | — | Arrays, Mathematics, logical-thinking | [`01. Basics/43. Average Count Array/`](01.%20Basics/43.%20Average%20Count%20Array/) |
| 5 | [Count Pairs Odd XOR](https://www.geeksforgeeks.org/problems/count-pairs-odd-xor0308/1) | — | — | — | Basics | — | Arrays, Mathematics | [`01. Basics/52. Count Pairs Odd XOR/`](01.%20Basics/52.%20Count%20Pairs%20Odd%20XOR/) |
| 6 | [Duplicates in a Limited Range Array](https://www.geeksforgeeks.org/problems/find-duplicates-in-an-array/1) | — | — | — | Easy | Paytm, Zoho, Flipkart, Amazon, D-E-Shaw, Qualcomm | Arrays | [`02. Easy/02. Duplicates in a Limited Range Array/`](02.%20Easy/02.%20Duplicates%20in%20a%20Limited%20Range%20Array/) |
| 7 | [Count Distinct in an Array](https://www.geeksforgeeks.org/problems/find-distinct-elements--130928/1) | — | — | — | Easy | — | Arrays | [`02. Easy/45. Count Distinct in an Array/`](02.%20Easy/45.%20Count%20Distinct%20in%20an%20Array/) |
| 8 | [Union of Two Sorted with Distinct](https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays-with-distinct-elements/1) | — | — | — | Easy | — | Arrays | [`02. Easy/54. Union of Two Sorted with Distinct/`](02.%20Easy/54.%20Union%20of%20Two%20Sorted%20with%20Distinct/) |
| 9 | [Count n/k Times Occurring](https://www.geeksforgeeks.org/problems/count-the-specials/1) | — | — | — | Easy | — | Arrays | [`02. Easy/57. Count nk Times Occurring/`](02.%20Easy/57.%20Count%20nk%20Times%20Occurring/) |
| 10 | [Majority in a Sorted Array](https://www.geeksforgeeks.org/problems/find-duplicates-under-given-constraints0856/1) | — | — | — | Easy | Yahoo | Arrays | [`02. Easy/66. Majority in a Sorted Array/`](02.%20Easy/66.%20Majority%20in%20a%20Sorted%20Array/) |
| 11 | [Unique Pair in Array](https://www.geeksforgeeks.org/problems/find-unique-pair-in-an-array-with-pairs-of-numbers2425/1) | — | — | — | Easy | — | Arrays, Bit Magic | [`02. Easy/103. Unique Pair in Array/`](02.%20Easy/103.%20Unique%20Pair%20in%20Array/) |
| 12 | [Positive Distinct Count](https://www.geeksforgeeks.org/problems/absolute-distinct-count5118/1) | — | — | — | Easy | — | Arrays | [`02. Easy/108. Positive Distinct Count/`](02.%20Easy/108.%20Positive%20Distinct%20Count/) |
| 13 | [Union of Two Arrays with Distinct Elements](https://www.geeksforgeeks.org/problems/union-of-two-arrays-with-distinct-elements/1) | — | — | — | Easy | — | Arrays | [`02. Easy/129. Union of Two Arrays with Distinct Elements/`](02.%20Easy/129.%20Union%20of%20Two%20Arrays%20with%20Distinct%20Elements/) |
| 14 | [Subsets with Distinct and Even Numbers](https://www.geeksforgeeks.org/problems/count-subsets-having-distinct-even-numbers5726/1) | — | — | — | Easy | — | Arrays, subset, Combinatorial | [`02. Easy/119. Subsets with Distinct and Even Numbers/`](02.%20Easy/119.%20Subsets%20with%20Distinct%20and%20Even%20Numbers/) |
| 15 | [Max Occured in n Ranges](https://www.geeksforgeeks.org/problems/maximum-occured-integer4602/1) | — | — | — | Medium | Amazon | Arrays, Mathematics | [`03. Medium/17. Max Occured in n Ranges/`](03.%20Medium/17.%20Max%20Occured%20in%20n%20Ranges/) |
| 16 | [Maximum Identical Bowls](https://www.geeksforgeeks.org/problems/maximum-identical-bowls--170647/1) | — | — | — | Medium | — | Arrays | [`03. Medium/51. Maximum Identical Bowls/`](03.%20Medium/51.%20Maximum%20Identical%20Bowls/) |
| 17 | [Distinct Difference](https://www.geeksforgeeks.org/problems/distinct-difference--170647/1) | — | — | — | Medium | — | Set, Arrays, Map | [`03. Medium/61. Distinct Difference/`](03.%20Medium/61.%20Distinct%20Difference/) |
| 18 | [Subsets Multiple of 3](https://www.geeksforgeeks.org/problems/possible-groups2013/1) | — | — | — | Medium | Amazon | Arrays | [`03. Medium/72. Subsets Multiple of 3/`](03.%20Medium/72.%20Subsets%20Multiple%20of%203/) |
| 19 | [Subset with Pair Sums Not Divisible by K](https://www.geeksforgeeks.org/problems/subset-with-no-pair-sum-divisible-by-k1105/1) | — | — | — | Medium | — | Arrays, Modular Arithmetic | [`03. Medium/76. Subset with Pair Sums Not Divisible by K/`](03.%20Medium/76.%20Subset%20with%20Pair%20Sums%20Not%20Divisible%20by%20K/) |
| 20 | [Queries for Counts of Multiples](https://www.geeksforgeeks.org/problems/queries-for-counts-of-multiples-in-an-array4028/1) | — | — | — | Medium | — | Arrays, Mathematics, sieve | [`03. Medium/81. Queries for Counts of Multiples/`](03.%20Medium/81.%20Queries%20for%20Counts%20of%20Multiples/) |
| 21 | [Pairs with Given Modulo Value](https://www.geeksforgeeks.org/problems/mr-modulo-and-pairs5610/1) | — | — | — | Medium | — | Arrays, Modular Arithmetic | [`03. Medium/84. Pairs with Given Modulo Value/`](03.%20Medium/84.%20Pairs%20with%20Given%20Modulo%20Value/) |
| 22 | [Max Modulo Pair in an Array](https://www.geeksforgeeks.org/problems/mr-modulo-and-arrays2827/1) | — | — | — | Medium | — | Arrays, Binary Search | [`03. Medium/92. Max Modulo Pair in an Array/`](03.%20Medium/92.%20Max%20Modulo%20Pair%20in%20an%20Array/) |
| 23 | [Values Present in At Least K Ranges](https://www.geeksforgeeks.org/problems/sick-pasha0323/1) | — | — | — | Medium | — | Arrays | [`03. Medium/97. Values Present in At Least K Ranges/`](03.%20Medium/97.%20Values%20Present%20in%20At%20Least%20K%20Ranges/) |
| 24 | [Pairs from Distict Element Subarrays](https://www.geeksforgeeks.org/problems/sub-array-pairs5530/1) | — | — | — | Medium | — | Arrays | [`03. Medium/101. Pairs from Distict Element Subarrays/`](03.%20Medium/101.%20Pairs%20from%20Distict%20Element%20Subarrays/) |

### Sorting-based (23)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Max and Min Product from 2 Arrays](https://www.geeksforgeeks.org/problems/product-of-maximum-in-first-array-and-minimum-in-second3943/1) | — | — | — | Basics | Adobe | Arrays | [`01. Basics/24. Max and Min Product from 2 Arrays/`](01.%20Basics/24.%20Max%20and%20Min%20Product%20from%202%20Arrays/) |
| 2 | [Minimum sum of two elements from two arrays](https://www.geeksforgeeks.org/problems/minimum-sum-of-two-elements-from-two-arrays0253/1) | — | — | — | Basics | — | Arrays | [`01. Basics/40. Minimum sum of two elements from two arrays/`](01.%20Basics/40.%20Minimum%20sum%20of%20two%20elements%20from%20two%20arrays/) |
| 3 | [Max Product K Sized Subarray](https://www.geeksforgeeks.org/problems/largest-product/1) | — | — | — | Basics | — | Arrays | [`01. Basics/42. Max Product K Sized Subarray/`](01.%20Basics/42.%20Max%20Product%20K%20Sized%20Subarray/) |
| 4 | [Fighting the Darkness](https://www.geeksforgeeks.org/problems/fighting-the-darkness3949/1) | — | — | — | Basics | Snapdeal | Arrays | [`01. Basics/26. Fighting the Darkness/`](01.%20Basics/26.%20Fighting%20the%20Darkness/) |
| 5 | [Min Decrement by K Operations to Limit Array](https://www.geeksforgeeks.org/problems/reducing-walls4443/1) | — | — | — | Basics | — | Arrays | [`01. Basics/44. Min Decrement by K Operations to Limit Array/`](01.%20Basics/44.%20Min%20Decrement%20by%20K%20Operations%20to%20Limit%20Array/) |
| 6 | [Minimum Time with Alternating Techniques](https://www.geeksforgeeks.org/problems/a-guy-with-a-mental-problem1604/1) | — | — | — | Basics | — | Arrays | [`01. Basics/51. Minimum Time with Alternating Techniques/`](01.%20Basics/51.%20Minimum%20Time%20with%20Alternating%20Techniques/) |
| 7 | [Third Largest](https://www.geeksforgeeks.org/problems/third-largest-element/1) | — | — | — | Easy | Amazon, Microsoft, MakeMyTrip | Arrays | [`02. Easy/09. Third Largest/`](02.%20Easy/09.%20Third%20Largest/) |
| 8 | [First and Second Smallests](https://www.geeksforgeeks.org/problems/find-the-smallest-and-second-smallest-element-in-an-array3226/1) | — | — | — | Easy | Amazon, Goldman Sachs, NPCI | Arrays | [`02. Easy/11. First and Second Smallests/`](02.%20Easy/11.%20First%20and%20Second%20Smallests/) |
| 9 | [Check if all array elements are distinct](https://www.geeksforgeeks.org/problems/professor-and-parties2000/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/51. Check if all array elements are distinct/`](02.%20Easy/51.%20Check%20if%20all%20array%20elements%20are%20distinct/) |
| 10 | [Largest from Digits](https://www.geeksforgeeks.org/problems/form-largest-number-from-digits5430/1) | — | — | — | Easy | Paytm | Arrays | [`02. Easy/55. Largest from Digits/`](02.%20Easy/55.%20Largest%20from%20Digits/) |
| 11 | [Maximum Gap](https://www.geeksforgeeks.org/problems/maximum-gap3845/1) | — | — | — | Easy | HunanAsset | Arrays, radix sort | [`02. Easy/67. Maximum Gap/`](02.%20Easy/67.%20Maximum%20Gap/) |
| 12 | [Sort Unsorted Subarray](https://www.geeksforgeeks.org/problems/length-unsorted-subarray3022/1) | — | — | — | Easy | Flipkart, Microsoft, MakeMyTrip, Adobe | Arrays | [`02. Easy/49. Sort Unsorted Subarray/`](02.%20Easy/49.%20Sort%20Unsorted%20Subarray/) |
| 13 | [Minimum Product Pair](https://www.geeksforgeeks.org/problems/minimum-product-pair3608/1) | — | — | — | Easy | — | Arrays | [`02. Easy/78. Minimum Product Pair/`](02.%20Easy/78.%20Minimum%20Product%20Pair/) |
| 14 | [Max Product of other Two in an Array](https://www.geeksforgeeks.org/problems/pair-with-greatest-product-in-array3342/1) | — | — | — | Easy | Linkedin | Arrays | [`02. Easy/81. Max Product of other Two in an Array/`](02.%20Easy/81.%20Max%20Product%20of%20other%20Two%20in%20an%20Array/) |
| 15 | [Chocolate Station](https://www.geeksforgeeks.org/problems/chocolate-station2951/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/84. Chocolate Station/`](02.%20Easy/84.%20Chocolate%20Station/) |
| 16 | [Maximum difference Indexes](https://www.geeksforgeeks.org/problems/maximum-difference-10429/1) | — | — | — | Easy | — | Arrays, Map | [`02. Easy/89. Maximum difference Indexes/`](02.%20Easy/89.%20Maximum%20difference%20Indexes/) |
| 17 | [Reading Books](https://www.geeksforgeeks.org/problems/reading-books3803/1) | — | — | — | Easy | — | Arrays, Mathematics | [`02. Easy/90. Reading Books/`](02.%20Easy/90.%20Reading%20Books/) |
| 18 | [Count Pairs With Maximum Sum](https://www.geeksforgeeks.org/problems/number-of-pairs-with-maximum-sum2924/1) | — | — | — | Easy | — | Arrays | [`02. Easy/97. Count Pairs With Maximum Sum/`](02.%20Easy/97.%20Count%20Pairs%20With%20Maximum%20Sum/) |
| 19 | [Maximum Difference by Choosing K Numbers](https://www.geeksforgeeks.org/problems/maximum-weight-difference5036/1) | — | — | — | Easy | — | Arrays | [`02. Easy/99. Maximum Difference by Choosing K Numbers/`](02.%20Easy/99.%20Maximum%20Difference%20by%20Choosing%20K%20Numbers/) |
| 20 | [Minimize Max Pair Sum](https://www.geeksforgeeks.org/problems/pair-the-minimum5535/1) | — | — | — | Easy | — | Arrays | [`02. Easy/104. Minimize Max Pair Sum/`](02.%20Easy/104.%20Minimize%20Max%20Pair%20Sum/) |
| 21 | [Check if Any Triplet  can Form a Triangle](https://www.geeksforgeeks.org/problems/form-a-triangle5935/1) | — | — | — | Easy | — | Arrays, Mathematics | [`02. Easy/109. Check if Any Triplet can Form a Triangle/`](02.%20Easy/109.%20Check%20if%20Any%20Triplet%20can%20Form%20a%20Triangle/) |
| 22 | [Count Pairs with Max Diff](https://www.geeksforgeeks.org/problems/count-the-pairs-with-maximum-difference4807/1) | — | — | — | Easy | — | Arrays, Mathematics | [`02. Easy/114. Count Pairs with Max Diff/`](02.%20Easy/114.%20Count%20Pairs%20with%20Max%20Diff/) |
| 23 | [Maximum k with k Larger Elements](https://www.geeksforgeeks.org/problems/maximum-value-k2745/1) | — | — | — | Easy | — | Arrays | [`02. Easy/120. Maximum k with k Larger Elements/`](02.%20Easy/120.%20Maximum%20k%20with%20k%20Larger%20Elements/) |

### Prefix / Suffix Aggregate (22)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Sum Except First and Last](https://www.geeksforgeeks.org/problems/max-length-chain/1) | — | — | — | Basics | Amazon, Microsoft | Arrays | [`01. Basics/13. Sum Except First and Last/`](01.%20Basics/13.%20Sum%20Except%20First%20and%20Last/) |
| 2 | [Multiply Left and Right Array Sums](https://www.geeksforgeeks.org/problems/multiply-left-and-right-array-sum1555/1) | — | — | — | Basics | — | Arrays | [`01. Basics/21. Multiply Left and Right Array Sums/`](01.%20Basics/21.%20Multiply%20Left%20and%20Right%20Array%20Sums/) |
| 3 | [Balanced Array](https://www.geeksforgeeks.org/problems/balanced-array07200720/1) | — | — | — | Basics | — | Arrays | [`01. Basics/23. Balanced Array/`](01.%20Basics/23.%20Balanced%20Array/) |
| 4 | [Count Prefix Maximums](https://www.geeksforgeeks.org/problems/elements-before-which-no-element-is-bigger0602/1) | — | — | — | Basics | — | Arrays | [`01. Basics/49. Count Prefix Maximums/`](01.%20Basics/49.%20Count%20Prefix%20Maximums/) |
| 5 | [Sum Array Puzzle](https://www.geeksforgeeks.org/problems/sum-array-puzzle/1) | — | — | — | Basics | — | Arrays, Mathematics | [`01. Basics/36. Sum Array Puzzle/`](01.%20Basics/36.%20Sum%20Array%20Puzzle/) |
| 6 | [Sum Triangle](https://www.geeksforgeeks.org/problems/sum-triangle-for-given-array1159/1) | — | — | — | Basics | — | Arrays | [`01. Basics/54. Sum Triangle/`](01.%20Basics/54.%20Sum%20Triangle/) |
| 7 | [Array Leaders](https://www.geeksforgeeks.org/problems/leaders-in-an-array-1587115620/1) | — | — | — | Easy | Payu, Adobe, Amazon | Arrays | [`02. Easy/01. Array Leaders/`](02.%20Easy/01.%20Array%20Leaders/) |
| 8 | [Product of Array](https://www.geeksforgeeks.org/problems/product-of-array-element/1) | — | — | — | Easy | — | Arrays | [`02. Easy/15. Product of Array/`](02.%20Easy/15.%20Product%20of%20Array/) |
| 9 | [Buildings with Sunlight](https://www.geeksforgeeks.org/problems/buildings-receiving-sunlight3032/1) | — | — | — | Easy | Amazon, Microsoft | Arrays | [`02. Easy/16. Buildings with Sunlight/`](02.%20Easy/16.%20Buildings%20with%20Sunlight/) |
| 10 | [Left Smaller Right Greater](https://www.geeksforgeeks.org/problems/unsorted-array4925/1) | — | — | — | Easy | Zoho, Amazon, OYO Rooms, Intuit | Arrays | [`02. Easy/14. Left Smaller Right Greater/`](02.%20Easy/14.%20Left%20Smaller%20Right%20Greater/) |
| 11 | [Greatest on Right Side](https://www.geeksforgeeks.org/problems/greater-on-right-side4305/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/33. Greatest on Right Side/`](02.%20Easy/33.%20Greatest%20on%20Right%20Side/) |
| 12 | [Sum of Submatrix Elements](https://www.geeksforgeeks.org/problems/addition-of-submatrix5835/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/71. Sum of Submatrix Elements/`](02.%20Easy/71.%20Sum%20of%20Submatrix%20Elements/) |
| 13 | [Bird and Max Fruit Gathering](https://www.geeksforgeeks.org/problems/bird-and-maximum-fruit-gathering--170645/1) | — | — | — | Easy | Facebook | Arrays | [`02. Easy/76. Bird and Max Fruit Gathering/`](02.%20Easy/76.%20Bird%20and%20Max%20Fruit%20Gathering/) |
| 14 | [Balanced Floor and Ceil Distance](https://www.geeksforgeeks.org/problems/balance-with-respect-to-an-array5443/1) | — | — | — | Easy | — | Arrays, Binary Search | [`02. Easy/96. Balanced Floor and Ceil Distance/`](02.%20Easy/96.%20Balanced%20Floor%20and%20Ceil%20Distance/) |
| 15 | [Max Sum Submatrix Queries](https://www.geeksforgeeks.org/problems/max-sum-submatrix2725/1) | — | — | — | Easy | Accolite | Arrays | [`02. Easy/118. Max Sum Submatrix Queries/`](02.%20Easy/118.%20Max%20Sum%20Submatrix%20Queries/) |
| 16 | [Distance Travelled in a Permutation of 1 to n](https://www.geeksforgeeks.org/problems/total-distance-travelled-in-an-array3628/1) | — | — | — | Easy | — | Arrays | [`02. Easy/98. Distance Travelled in a Permutation of 1 to n/`](02.%20Easy/98.%20Distance%20Travelled%20in%20a%20Permutation%20of%201%20to%20n/) |
| 17 | [Max Sum Subarray of Non-Negative](https://www.geeksforgeeks.org/problems/maximum-sub-array5443/1) | — | — | — | Medium | Amazon, Microsoft, Intuit | Arrays, Divide and Conquer | [`03. Medium/09. Max Sum Subarray of Non-Negative/`](03.%20Medium/09.%20Max%20Sum%20Subarray%20of%20Non-Negative/) |
| 18 | [Sum of Subarrays](https://www.geeksforgeeks.org/problems/sum-of-subarrays2229/1) | — | — | — | Medium | — | Arrays | [`03. Medium/33. Sum of Subarrays/`](03.%20Medium/33.%20Sum%20of%20Subarrays/) |
| 19 | [Smaller Sum for All](https://www.geeksforgeeks.org/problems/smaller-sum--170647/1) | — | — | — | Medium | — | Arrays, Binary Search | [`03. Medium/49. Smaller Sum for All/`](03.%20Medium/49.%20Smaller%20Sum%20for%20All/) |
| 20 | [Update Queries](https://www.geeksforgeeks.org/problems/update-queries--170647/1) | — | — | — | Medium | — | Arrays, Bit Magic | [`03. Medium/62. Update Queries/`](03.%20Medium/62.%20Update%20Queries/) |
| 21 | [Subarrays Having Even Sum](https://www.geeksforgeeks.org/problems/find-the-number-of-sub-arrays-having-even-sum1533/1) | — | — | — | Medium | — | Arrays | [`03. Medium/82. Subarrays Having Even Sum/`](03.%20Medium/82.%20Subarrays%20Having%20Even%20Sum/) |
| 22 | [Maximum Bitonic Subarray Sum](https://www.geeksforgeeks.org/problems/maximum-bitonic-subarray-sum5616/1) | — | — | — | Medium | — | Arrays | [`03. Medium/88. Maximum Bitonic Subarray Sum/`](03.%20Medium/88.%20Maximum%20Bitonic%20Subarray%20Sum/) |

### Binary Search on Sorted Array (20)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Floor and Ceil in Unsorted](https://www.geeksforgeeks.org/problems/ceil-the-floor2802/1) | — | — | — | Easy | — | Arrays | [`02. Easy/10. Floor and Ceil in Unsorted/`](02.%20Easy/10.%20Floor%20and%20Ceil%20in%20Unsorted/) |
| 2 | [Implement Lower Bound](https://www.geeksforgeeks.org/problems/implement-lower-bound/1) | — | — | — | Easy | — | Binary Search, Arrays | [`02. Easy/17. Implement Lower Bound/`](02.%20Easy/17.%20Implement%20Lower%20Bound/) |
| 3 | [First and Last in Unosrted](https://www.geeksforgeeks.org/problems/find-index4752/1) | — | — | — | Easy | — | Arrays | [`02. Easy/19. First and Last in Unosrted/`](02.%20Easy/19.%20First%20and%20Last%20in%20Unosrted/) |
| 4 | [Closest in Sorted Array](https://www.geeksforgeeks.org/problems/find-the-closest-number5513/1) | — | — | — | Easy | — | Arrays, Binary Search | [`02. Easy/21. Closest in Sorted Array/`](02.%20Easy/21.%20Closest%20in%20Sorted%20Array/) |
| 5 | [Implement Upper Bound](https://www.geeksforgeeks.org/problems/implement-upper-bound/1) | — | — | — | Easy | — | Binary Search, Arrays | [`02. Easy/26. Implement Upper Bound/`](02.%20Easy/26.%20Implement%20Upper%20Bound/) |
| 6 | [K-th Missing in Sorted](https://www.geeksforgeeks.org/problems/k-th-missing-element3635/1) | — | — | — | Easy | Amazon, Facebook, Apple, Google | Arrays | [`02. Easy/39. K-th Missing in Sorted/`](02.%20Easy/39.%20K-th%20Missing%20in%20Sorted/) |
| 7 | [Same Value as Index in Sorted](https://www.geeksforgeeks.org/problems/magical-number-1587115620/1) | — | — | — | Easy | — | Arrays, Binary Search | [`02. Easy/60. Same Value as Index in Sorted/`](02.%20Easy/60.%20Same%20Value%20as%20Index%20in%20Sorted/) |
| 8 | [Missing Number in Sorted Array of Natural Numbers](https://www.geeksforgeeks.org/problems/missing-number-in-sorted-array-of-natural-numbers/1) | — | — | — | Easy | — | Binary Search, Mathematics, Arrays | [`02. Easy/88. Missing Number in Sorted Array of Natural Numbers/`](02.%20Easy/88.%20Missing%20Number%20in%20Sorted%20Array%20of%20Natural%20Numbers/) |
| 9 | [K-th in a[] Missing from b[]](https://www.geeksforgeeks.org/problems/find-k-th-missing-element2556/1) | — | — | — | Easy | — | Arrays, STL | [`02. Easy/91. K-th in a[] Missing from b[]/`](02.%20Easy/91.%20K-th%20in%20a[]%20Missing%20from%20b[]/) |
| 10 | [Partition Point in Array](https://www.geeksforgeeks.org/problems/partition-point-in-the-array0004/1) | — | — | — | Easy | — | Arrays | [`02. Easy/92. Partition Point in Array/`](02.%20Easy/92.%20Partition%20Point%20in%20Array/) |
| 11 | [Equal Point in Sorted Array](https://www.geeksforgeeks.org/problems/equal-point-in-sorted-array0040/1) | — | — | — | Easy | — | Binary Search, Arrays | [`02. Easy/106. Equal Point in Sorted Array/`](02.%20Easy/106.%20Equal%20Point%20in%20Sorted%20Array/) |
| 12 | [Minimum N-th Power More Than Array Product](https://www.geeksforgeeks.org/problems/minimum-element-whose-n-th-power-is-greater-than-product-of-an-array4640/1) | — | — | — | Easy | — | Arrays, Mathematics | [`02. Easy/116. Minimum N-th Power More Than Array Product/`](02.%20Easy/116.%20Minimum%20N-th%20Power%20More%20Than%20Array%20Product/) |
| 13 | [First and Last in Sorted](https://www.geeksforgeeks.org/problems/first-and-last-occurrences-of-x3116/1) | — | — | — | Medium | Amazon, Google, Microsoft | Arrays, Binary Search | [`03. Medium/04. First and Last in Sorted/`](03.%20Medium/04.%20First%20and%20Last%20in%20Sorted/) |
| 14 | [K Closest in a Sorted Array](https://www.geeksforgeeks.org/problems/k-closest-elements3619/1) | — | — | — | Medium | Amazon, OYO Rooms | Arrays, Binary Search, STL, Priority Queue | [`03. Medium/16. K Closest in a Sorted Array/`](03.%20Medium/16.%20K%20Closest%20in%20a%20Sorted%20Array/) |
| 15 | [Kth Missing Positive Number in a Sorted Array](https://www.geeksforgeeks.org/problems/kth-missing-positive-number-in-a-sorted-array/1) | — | — | — | Medium | NPCI | Binary Search, Arrays | [`03. Medium/30. Kth Missing Positive Number in a Sorted Array/`](03.%20Medium/30.%20Kth%20Missing%20Positive%20Number%20in%20a%20Sorted%20Array/) |
| 16 | [Search in Rotated Array 2](https://www.geeksforgeeks.org/problems/search-in-rotated-array-2/1) | — | — | — | Medium | Adobe, Bloomberg, Yahoo, Uber | Binary Search, Arrays | [`03. Medium/41. Search in Rotated Array 2/`](03.%20Medium/41.%20Search%20in%20Rotated%20Array%202/) |
| 17 | [Count X in Range of a Sorted Array](https://www.geeksforgeeks.org/problems/count-x-in-range-of-a-sorted-array/1) | — | — | — | Medium | — | Binary Search, Arrays | [`03. Medium/70. Count X in Range of a Sorted Array/`](03.%20Medium/70.%20Count%20X%20in%20Range%20of%20a%20Sorted%20Array/) |
| 18 | [Count elements less than or equal to k in a sorted rotated array](https://www.geeksforgeeks.org/problems/count-elements-less-than-or-equal-to-k-in-a-sorted-rotated-array/1) | — | — | — | Medium | NPCI | Binary Search, Arrays | [`03. Medium/71. Count elements less than or equal to k in a sorted rotated array/`](03.%20Medium/71.%20Count%20elements%20less%20than%20or%20equal%20to%20k%20in%20a%20sorted%20rotated%20array/) |
| 19 | [Index Element After Rotations](https://www.geeksforgeeks.org/problems/find-the-element-at-given-index4630/1) | — | — | — | Medium | — | Arrays | [`03. Medium/93. Index Element After Rotations/`](03.%20Medium/93.%20Index%20Element%20After%20Rotations/) |
| 20 | [Successful Binary Searches Irrespective of Pivot](https://www.geeksforgeeks.org/problems/count-always-found/1) | — | — | — | Medium | — | constructive algo, Arrays | [`03. Medium/103. Successful Binary Searches Irrespective of Pivot/`](03.%20Medium/103.%20Successful%20Binary%20Searches%20Irrespective%20of%20Pivot/) |

### Math / Number-Theoretic Construction (16)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Adding One to Array](https://www.geeksforgeeks.org/problems/adding-one2529/1) | — | — | — | Easy | Google, Microsoft | Arrays | [`02. Easy/18. Adding One to Array/`](02.%20Easy/18.%20Adding%20One%20to%20Array/) |
| 2 | [Array Permutation Divisible by 3](https://www.geeksforgeeks.org/problems/form-a-number-divisible-by-3-using-array-digits0717/1) | — | — | — | Easy | — | Arrays, Mathematics | [`02. Easy/23. Array Permutation Divisible by 3/`](02.%20Easy/23.%20Array%20Permutation%20Divisible%20by%203/) |
| 3 | [Replace with XOR of Adjacent](https://www.geeksforgeeks.org/problems/replace-with-xor-of-adjacent/1) | — | — | — | Easy | — | Arrays, Bit Magic | [`02. Easy/25. Replace with XOR of Adjacent/`](02.%20Easy/25.%20Replace%20with%20XOR%20of%20Adjacent/) |
| 4 | [Adding Ones](https://www.geeksforgeeks.org/problems/adding-ones3628/1) | — | — | — | Easy | — | Arrays | [`02. Easy/34. Adding Ones/`](02.%20Easy/34.%20Adding%20Ones/) |
| 5 | [Sum of Two Represented as Arrays](https://www.geeksforgeeks.org/problems/sum-of-two-numbers-represented-as-arrays3110/1) | — | — | — | Easy | Zoho, Accolite, Amazon | Arrays | [`02. Easy/35. Sum of Two Represented as Arrays/`](02.%20Easy/35.%20Sum%20of%20Two%20Represented%20as%20Arrays/) |
| 6 | [Replace with Adjacent Multiplication](https://www.geeksforgeeks.org/problems/replace-with-adjacent-multiplication/1) | — | — | — | Easy | — | Arrays | [`02. Easy/125. Replace with Adjacent Multiplication/`](02.%20Easy/125.%20Replace%20with%20Adjacent%20Multiplication/) |
| 7 | [Array Transformation with Repeated Steps and Modulo Operation](https://www.geeksforgeeks.org/problems/array-transformation-with-repeated-steps-and-modulo-operation/1) | — | — | — | Easy | — | Arrays | [`02. Easy/135. Array Transformation with Repeated Steps and Modulo Operation/`](02.%20Easy/135.%20Array%20Transformation%20with%20Repeated%20Steps%20and%20Modulo%20Operation/) |
| 8 | [Pascal Triangle](https://www.geeksforgeeks.org/problems/pascal-triangle0652/1) | — | — | — | Medium | Amazon, Microsoft, Adobe | Arrays, Recursion | [`03. Medium/10. Pascal Triangle/`](03.%20Medium/10.%20Pascal%20Triangle/) |
| 9 | [Factorial of Array under Modulo](https://www.geeksforgeeks.org/problems/large-factorial4721/1) | — | — | — | Medium | — | Arrays, Mathematics | [`03. Medium/45. Factorial of Array under Modulo/`](03.%20Medium/45.%20Factorial%20of%20Array%20under%20Modulo/) |
| 10 | [Number to Words](https://www.geeksforgeeks.org/problems/number-to-words0335/1) | — | — | — | Medium | Zoho, Amazon, Microsoft, Oracle | Arrays | [`03. Medium/48. Number to Words/`](03.%20Medium/48.%20Number%20to%20Words/) |
| 11 | [Composite and  Prime Queries](https://www.geeksforgeeks.org/problems/composite-and-prime0359/1) | — | — | — | Medium | — | Prime Number, Arrays, sieve | [`03. Medium/50. Composite and Prime Queries/`](03.%20Medium/50.%20Composite%20and%20Prime%20Queries/) |
| 12 | [Tic Tac Toe](https://www.geeksforgeeks.org/problems/tic-tac-toe2412/1) | — | — | — | Medium | Flipkart, Accolite, Amazon, Microsoft | Arrays | [`03. Medium/64. Tic Tac Toe/`](03.%20Medium/64.%20Tic%20Tac%20Toe/) |
| 13 | [Sum of Permutations of Distinct Digits](https://www.geeksforgeeks.org/problems/sum-of-permutations/1) | — | — | — | Medium | — | Arrays, Modular Arithmetic | [`03. Medium/87. Sum of Permutations of Distinct Digits/`](03.%20Medium/87.%20Sum%20of%20Permutations%20of%20Distinct%20Digits/) |
| 14 | [Smallest Number from Power Digits](https://www.geeksforgeeks.org/problems/the-tiny-miny2541/1) | — | — | — | Medium | — | Arrays | [`03. Medium/89. Smallest Number from Power Digits/`](03.%20Medium/89.%20Smallest%20Number%20from%20Power%20Digits/) |
| 15 | [Leading Digit and Exponent of Factorial](https://www.geeksforgeeks.org/problems/large-factorials2539/1) | — | — | — | Medium | — | Arrays, factorial | [`03. Medium/90. Leading Digit and Exponent of Factorial/`](03.%20Medium/90.%20Leading%20Digit%20and%20Exponent%20of%20Factorial/) |
| 16 | [Rubik's Cube](https://www.geeksforgeeks.org/problems/rubiks-cube4626/1) | — | — | — | Medium | Ola Cabs | Arrays, constructive algo | [`03. Medium/102. Rubik's Cube/`](03.%20Medium/102.%20Rubik's%20Cube/) |

### In-Place Rearrangement (12)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Rotate Array by One](https://www.geeksforgeeks.org/problems/cyclically-rotate-an-array-by-one2614/1) | — | — | — | Basics | — | Arrays, implementation | [`01. Basics/03. Rotate Array by One/`](01.%20Basics/03.%20Rotate%20Array%20by%20One/) |
| 2 | [Swap kth elements](https://www.geeksforgeeks.org/problems/swap-kth-elements5500/1) | — | — | — | Basics | Morgan Stanley, Rockstand | Arrays | [`01. Basics/17. Swap kth elements/`](01.%20Basics/17.%20Swap%20kth%20elements/) |
| 3 | [Segregate Even and Odd numbers](https://www.geeksforgeeks.org/problems/segregate-even-and-odd-numbers4629/1) | — | — | — | Basics | Paytm, Accolite, Amazon, MakeMyTrip, Linkedin | Arrays | [`01. Basics/27. Segregate Even and Odd numbers/`](01.%20Basics/27.%20Segregate%20Even%20and%20Odd%20numbers/) |
| 4 | [Reverse Subarray](https://www.geeksforgeeks.org/problems/reverse-sub-array5620/1) | — | — | — | Basics | Amazon | Arrays | [`01. Basics/28. Reverse Subarray/`](01.%20Basics/28.%20Reverse%20Subarray/) |
| 5 | [Half Ascending and Half Descending Sort](https://www.geeksforgeeks.org/problems/sort-first-half-in-ascending-and-second-half-in-descending1714/1) | — | — | — | Basics | — | Arrays | [`01. Basics/37. Half Ascending and Half Descending Sort/`](01.%20Basics/37.%20Half%20Ascending%20and%20Half%20Descending%20Sort/) |
| 6 | [Even Odd Positions](https://www.geeksforgeeks.org/problems/find-the-fine4353/1) | — | — | — | Basics | Microsoft | Arrays, Mathematics | [`01. Basics/19. Even Odd Positions/`](01.%20Basics/19.%20Even%20Odd%20Positions/) |
| 7 | [Rotate Array](https://www.geeksforgeeks.org/problems/rotate-array-by-n-elements-1587115621/1) | — | — | — | Medium | Amazon, Microsoft, MAQ Software, Codenation | Arrays | [`03. Medium/01. Rotate Array/`](03.%20Medium/01.%20Rotate%20Array/) |
| 8 | [Reverse Array in Groups](https://www.geeksforgeeks.org/problems/reverse-array-in-groups0255/1) | — | — | — | Medium | Adobe | Arrays | [`03. Medium/03. Reverse Array in Groups/`](03.%20Medium/03.%20Reverse%20Array%20in%20Groups/) |
| 9 | [Next Permutation](https://www.geeksforgeeks.org/problems/next-permutation5226/1) | — | — | — | Medium | Infosys, Flipkart, Amazon, Microsoft, FactSet, Hike, MakeMyTrip, Google, Qualcomm, Salesforce | Arrays, permutation, constructive algo | [`03. Medium/07. Next Permutation/`](03.%20Medium/07.%20Next%20Permutation/) |
| 10 | [Transform Array In-Place](https://www.geeksforgeeks.org/problems/rearrange-an-array-with-o1-extra-space3142/1) | — | — | — | Medium | Amazon | Arrays | [`03. Medium/11. Transform Array In-Place/`](03.%20Medium/11.%20Transform%20Array%20In-Place/) |
| 11 | [Rotate and delete](https://www.geeksforgeeks.org/problems/rotate-and-delete-1587115621/1) | — | — | — | Medium | — | Arrays | [`03. Medium/31. Rotate and delete/`](03.%20Medium/31.%20Rotate%20and%20delete/) |
| 12 | [Shuffle Integers](https://www.geeksforgeeks.org/problems/shuffle-integers2401/1) | — | — | — | Medium | Amazon, OYO Rooms | Arrays, Recursion | [`03. Medium/32. Shuffle Integers/`](03.%20Medium/32.%20Shuffle%20Integers/) |

### Sliding Window (11)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Max Consecutive Bit](https://www.geeksforgeeks.org/problems/max-consecutive-one/1) | — | — | — | Easy | Accenture, TCS, Oracle, NPCI | Arrays | [`02. Easy/32. Max Consecutive Bit/`](02.%20Easy/32.%20Max%20Consecutive%20Bit/) |
| 2 | [Coount Subarrays with 0's Only](https://www.geeksforgeeks.org/problems/number-of-subarrays-of-0s--170647/1) | — | — | — | Easy | — | Arrays | [`02. Easy/56. Coount Subarrays with 0's Only/`](02.%20Easy/56.%20Coount%20Subarrays%20with%200's%20Only/) |
| 3 | [Maximum Average Subarray](https://www.geeksforgeeks.org/problems/maximum-average-subarray5859/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/62. Maximum Average Subarray/`](02.%20Easy/62.%20Maximum%20Average%20Subarray/) |
| 4 | [Longest Increasing Subarray](https://www.geeksforgeeks.org/problems/longest-increasing-subarray3811/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/64. Longest Increasing Subarray/`](02.%20Easy/64.%20Longest%20Increasing%20Subarray/) |
| 5 | [Sum of Lengths of Non-Overlapping SubArrays](https://www.geeksforgeeks.org/problems/sum-of-lengths-of-non-overlapping-subarrays2237/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/75. Sum of Lengths of Non-Overlapping SubArrays/`](02.%20Easy/75.%20Sum%20of%20Lengths%20of%20Non-Overlapping%20SubArrays/) |
| 6 | [Max Sum Strictly Increasing Subarray](https://www.geeksforgeeks.org/problems/find-maximum-sum-strictly-increasing-subarray4443/1) | — | — | — | Easy | — | Arrays | [`02. Easy/105. Max Sum Strictly Increasing Subarray/`](02.%20Easy/105.%20Max%20Sum%20Strictly%20Increasing%20Subarray/) |
| 7 | [Subarrays with Same Min and Max](https://www.geeksforgeeks.org/problems/number-of-subarrays-whose-minimum-and-maximum-are-same5259/1) | — | — | — | Easy | — | Arrays, Mathematics | [`02. Easy/123. Subarrays with Same Min and Max/`](02.%20Easy/123.%20Subarrays%20with%20Same%20Min%20and%20Max/) |
| 8 | [Maximum Consecutives Subset with K Additions](https://www.geeksforgeeks.org/problems/maximum-size-of-consecutives3154/1) | — | — | — | Easy | — | Arrays | [`02. Easy/132. Maximum Consecutives Subset with K Additions/`](02.%20Easy/132.%20Maximum%20Consecutives%20Subset%20with%20K%20Additions/) |
| 9 | [Consecutive Array Elements](https://www.geeksforgeeks.org/problems/consecutive-array-elements2711/1) | — | — | — | Easy | — | Arrays | [`02. Easy/86. Consecutive Array Elements/`](02.%20Easy/86.%20Consecutive%20Array%20Elements/) |
| 10 | [Equal Sum and Product Subarrays](https://www.geeksforgeeks.org/problems/equal-sum-and-product2057/1) | — | — | — | Easy | — | Arrays, subset | [`02. Easy/93. Equal Sum and Product Subarrays/`](02.%20Easy/93.%20Equal%20Sum%20and%20Product%20Subarrays/) |
| 11 | [Count Consecutive Adjacent Pairs](https://www.geeksforgeeks.org/problems/pairs-of-adjacent-elements4814/1) | — | — | — | Easy | — | Arrays | [`02. Easy/117. Count Consecutive Adjacent Pairs/`](02.%20Easy/117.%20Count%20Consecutive%20Adjacent%20Pairs/) |

### Array Modification / Insertion / Access (8)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Array Traversal](https://www.geeksforgeeks.org/problems/array-traversal/1) | — | — | — | Basics | — | Arrays | [`01. Basics/07. Array Traversal/`](01.%20Basics/07.%20Array%20Traversal/) |
| 2 | [Replace all 0's with 5](https://www.geeksforgeeks.org/problems/replace-all-0s-with-5/1) | — | — | — | Basics | Amazon | Arrays, Mathematics | [`01. Basics/09. Replace all 0's with 5/`](01.%20Basics/09.%20Replace%20all%200's%20with%205/) |
| 3 | [Array Insert at Index](https://www.geeksforgeeks.org/problems/array-insert-at-index/1) | — | — | — | Basics | — | Arrays | [`01. Basics/11. Array Insert at Index/`](01.%20Basics/11.%20Array%20Insert%20at%20Index/) |
| 4 | [Find element at a given Index](https://www.geeksforgeeks.org/problems/c-array-print-an-element-set-25933/1) | — | — | — | Basics | — | Arrays, CPP | [`01. Basics/14. Find element at a given Index/`](01.%20Basics/14.%20Find%20element%20at%20a%20given%20Index/) |
| 5 | [Array End Insert](https://www.geeksforgeeks.org/problems/array-insert-at-end/1) | — | — | — | Basics | — | Arrays | [`01. Basics/18. Array End Insert/`](01.%20Basics/18.%20Array%20End%20Insert/) |
| 6 | [Alternates in an Array](https://www.geeksforgeeks.org/problems/print-alternate-elements-of-an-array/1) | — | — | — | Basics | — | Arrays | [`01. Basics/05. Alternates in an Array/`](01.%20Basics/05.%20Alternates%20in%20an%20Array/) |
| 7 | [C++ 2-D Arrays | Set-1](https://www.geeksforgeeks.org/problems/c-2-d-arrays0708/1) | — | — | — | Basics | — | Arrays, CPP | [`01. Basics/31. C++ 2-D Arrays Set-1/`](01.%20Basics/31.%20C++%202-D%20Arrays%20Set-1/) |
| 8 | [Java 1-d and 2-d Array](https://www.geeksforgeeks.org/problems/java-1-d-and-2-d-array2952/1) | — | — | — | Basics | — | Arrays, Java | [`01. Basics/32. Java 1-d and 2-d Array/`](01.%20Basics/32.%20Java%201-d%20and%202-d%20Array/) |

### Digit / Bit Manipulation (8)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Absolute Digit Diff 1 in Array](https://www.geeksforgeeks.org/problems/absolute-difference-11156/1) | — | — | — | Basics | Amazon, Jabong | Arrays | [`01. Basics/33. Absolute Digit Diff 1 in Array/`](01.%20Basics/33.%20Absolute%20Digit%20Diff%201%20in%20Array/) |
| 2 | [Adjacent XOR Transformation](https://www.geeksforgeeks.org/problems/game-with-nos3123/1) | — | — | — | Basics | — | Arrays, Bit Magic | [`01. Basics/20. Adjacent XOR Transformation/`](01.%20Basics/20.%20Adjacent%20XOR%20Transformation/) |
| 3 | [Max Odd Sum](https://www.geeksforgeeks.org/problems/max-odd-sum0651/1) | — | — | — | Basics | — | Arrays | [`01. Basics/53. Max Odd Sum/`](01.%20Basics/53.%20Max%20Odd%20Sum/) |
| 4 | [Make Co-prime Array](https://www.geeksforgeeks.org/problems/make-coprime-array3058/1) | — | — | — | Basics | — | Arrays | [`01. Basics/55. Make Co-prime Array/`](01.%20Basics/55.%20Make%20Co-prime%20Array/) |
| 5 | [Flip to Maximize 1s](https://www.geeksforgeeks.org/problems/flip-bits0240/1) | — | — | — | Medium | Amazon | Arrays | [`03. Medium/22. Flip to Maximize 1s/`](03.%20Medium/22.%20Flip%20to%20Maximize%201s/) |
| 6 | [Sum of Pairwise Bit Differences](https://www.geeksforgeeks.org/problems/sum-of-bit-differences2937/1) | — | — | — | Medium | Google, Microsoft | Arrays, Bit Magic | [`03. Medium/25. Sum of Pairwise Bit Differences/`](03.%20Medium/25.%20Sum%20of%20Pairwise%20Bit%20Differences/) |
| 7 | [Total Hamming Distance](https://www.geeksforgeeks.org/problems/total-hamming-distance/1) | — | — | — | Medium | Microsoft, NPCI | Bit Magic, Arrays | [`03. Medium/95. Total Hamming Distance/`](03.%20Medium/95.%20Total%20Hamming%20Distance/) |
| 8 | [Next Smallest Palindrome](https://www.geeksforgeeks.org/problems/next-smallest-palindrome4740/1) | — | — | — | Hard | Flipkart, Amazon, Microsoft, OYO Rooms, Adobe, Media.net | Arrays | [`04. Hard/04. Next Smallest Palindrome/`](04.%20Hard/04.%20Next%20Smallest%20Palindrome/) |

### Binary Search on Answer (8)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Koko Eating Bananas](https://www.geeksforgeeks.org/problems/koko-eating-bananas/1) | — | — | — | Medium | Bloomberg, Amazon, Microsoft, Walmart, Adobe, Arcesium, Uber, NPCI | Binary Search, Arrays | [`03. Medium/28. Koko Eating Bananas/`](03.%20Medium/28.%20Koko%20Eating%20Bananas/) |
| 2 | [Minimum Days to Make m Bouquets](https://www.geeksforgeeks.org/problems/minimum-days-to-make-m-bouquets/1) | — | — | — | Medium | Bloomberg, Amazon, Microsoft, Google, Flipkart, NPCI | Binary Search, Arrays | [`03. Medium/43. Minimum Days to Make m Bouquets/`](03.%20Medium/43.%20Minimum%20Days%20to%20Make%20m%20Bouquets/) |
| 3 | [Capacity To Ship Packages Within d Days](https://www.geeksforgeeks.org/problems/capacity-to-ship-packages-within-d-days/1) | — | — | — | Medium | Amazon, D-E-Shaw | Arrays, Binary Search | [`03. Medium/44. Capacity To Ship Packages Within d Days/`](03.%20Medium/44.%20Capacity%20To%20Ship%20Packages%20Within%20d%20Days/) |
| 4 | [Smallest Divisor](https://www.geeksforgeeks.org/problems/smallest-divisor/1) | — | — | — | Medium | — | Binary Search, Arrays | [`03. Medium/46. Smallest Divisor/`](03.%20Medium/46.%20Smallest%20Divisor/) |
| 5 | [Minimize Max Distance of Adjacent Gas Stations](https://www.geeksforgeeks.org/problems/minimize-max-distance-to-gas-station/1) | — | — | — | Hard | — | Binary Search, Mathematics, Arrays | [`04. Hard/03. Minimize Max Distance of Adjacent Gas Stations/`](04.%20Hard/03.%20Minimize%20Max%20Distance%20of%20Adjacent%20Gas%20Stations/) |
| 6 | [Split Array Largest Sum](https://www.geeksforgeeks.org/problems/split-array-largest-sum--141634/1) | — | — | — | Hard | Google | Arrays, Binary Search | [`04. Hard/05. Split Array Largest Sum/`](04.%20Hard/05.%20Split%20Array%20Largest%20Sum/) |
| 7 | [Median of 2 Sorted Arrays of Different Sizes](https://www.geeksforgeeks.org/problems/median-of-2-sorted-arrays-of-different-sizes/1) | — | — | — | Hard | Amazon, Microsoft, Samsung, Google, NPCI | Arrays, Binary Search | [`04. Hard/02. Median of 2 Sorted Arrays of Different Sizes/`](04.%20Hard/02.%20Median%20of%202%20Sorted%20Arrays%20of%20Different%20Sizes/) |
| 8 | [Median of 2 Sorted Arrays of Same Size](https://www.geeksforgeeks.org/problems/median-of-2-sorted-arrays-of-same-size/1) | — | — | — | Hard | Amazon, Microsoft, Samsung, Google | Binary Search, Arrays | [`04. Hard/10. Median of 2 Sorted Arrays of Same Size/`](04.%20Hard/10.%20Median%20of%202%20Sorted%20Arrays%20of%20Same%20Size/) |

### K-th Element / Order Statistics (8)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [K-th of Two Sorted Arrays](https://www.geeksforgeeks.org/problems/k-th-element-of-two-sorted-array1317/1) | — | — | — | Medium | Flipkart, Microsoft, NPCI | Arrays, Divide and Conquer, Binary Search | [`03. Medium/02. K-th of Two Sorted Arrays/`](03.%20Medium/02.%20K-th%20of%20Two%20Sorted%20Arrays/) |
| 2 | [Sum of Middle of two sorted arrays](https://www.geeksforgeeks.org/problems/sum-of-middle-elements-of-two-sorted-arrays2305/1) | — | — | — | Medium | Amazon, D-E-Shaw | Arrays, Divide and Conquer, Binary Search | [`03. Medium/21. Sum of Middle of two sorted arrays/`](03.%20Medium/21.%20Sum%20of%20Middle%20of%20two%20sorted%20arrays/) |
| 3 | [Top k Frequent in Stream](https://www.geeksforgeeks.org/problems/top-k-numbers3425/1) | — | — | — | Medium | Accolite, Amazon, Media.net | Arrays, Map, Priority Queue | [`03. Medium/37. Top k Frequent in Stream/`](03.%20Medium/37.%20Top%20k%20Frequent%20in%20Stream/) |
| 4 | [K-th Largest Sum Contiguous Subarray](https://www.geeksforgeeks.org/problems/k-th-largest-sum-contiguous-subarray/1) | — | — | — | Medium | — | Arrays, Priority Queue | [`03. Medium/39. K-th Largest Sum Contiguous Subarray/`](03.%20Medium/39.%20K-th%20Largest%20Sum%20Contiguous%20Subarray/) |
| 5 | [Kth Smallest Pairwise Difference](https://www.geeksforgeeks.org/problems/smallest-absolute-difference4320/1) | — | — | — | Medium | — | Arrays | [`03. Medium/67. Kth Smallest Pairwise Difference/`](03.%20Medium/67.%20Kth%20Smallest%20Pairwise%20Difference/) |
| 6 | [Max Product Subsequence of Size K](https://www.geeksforgeeks.org/problems/maximum-product4633/1) | — | — | — | Medium | — | Arrays | [`03. Medium/68. Max Product Subsequence of Size K/`](03.%20Medium/68.%20Max%20Product%20Subsequence%20of%20Size%20K/) |
| 7 | [Count Pairs with i * arr[i] > j * arr[j]](https://www.geeksforgeeks.org/problems/count-pairs-in-an-array4145/1) | — | — | — | Hard | — | Arrays, Merge Sort | [`04. Hard/06. Count Pairs with i arr[i] j arr[j]/`](04.%20Hard/06.%20Count%20Pairs%20with%20i%20arr[i]%20j%20arr[j]/) |
| 8 | [Count Subarrays with Equal Occurrences of Two](https://www.geeksforgeeks.org/problems/sub-arrays-with-equal-number-of-occurences3901/1) | — | — | — | Hard | — | Arrays, STL | [`04. Hard/07. Count Subarrays with Equal Occurrences of Two/`](04.%20Hard/07.%20Count%20Subarrays%20with%20Equal%20Occurrences%20of%20Two/) |

### XOR / Prefix-XOR Techniques (8)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Count Subarrays with given XOR](https://www.geeksforgeeks.org/problems/count-subarray-with-given-xor/1) | — | — | — | Medium | — | Arrays, Map, Bit Magic | [`03. Medium/14. Count Subarrays with given XOR/`](03.%20Medium/14.%20Count%20Subarrays%20with%20given%20XOR/) |
| 2 | [Unique Number III](https://www.geeksforgeeks.org/problems/find-element-occuring-once-when-all-other-are-present-thrice/1) | — | — | — | Medium | Google, NPCI | Arrays, Mathematics, Bit Magic | [`03. Medium/26. Unique Number III/`](03.%20Medium/26.%20Unique%20Number%20III/) |
| 3 | [Sum of XOR of all pairs](https://www.geeksforgeeks.org/problems/sum-of-xor-of-all-pairs0723/1) | — | — | — | Medium | — | Arrays, Bit Magic | [`03. Medium/29. Sum of XOR of all pairs/`](03.%20Medium/29.%20Sum%20of%20XOR%20of%20all%20pairs/) |
| 4 | [Construct List using XOR Queries](https://www.geeksforgeeks.org/problems/construct-list-using-given-q-xor-queries/1) | — | — | — | Medium | Amazon, Google | Arrays, Bit Magic | [`03. Medium/35. Construct List using XOR Queries/`](03.%20Medium/35.%20Construct%20List%20using%20XOR%20Queries/) |
| 5 | [Maximum Subset XOR](https://www.geeksforgeeks.org/problems/maximum-subset-xor/1) | — | — | — | Medium | Microsoft | Arrays, Bit Magic | [`03. Medium/40. Maximum Subset XOR/`](03.%20Medium/40.%20Maximum%20Subset%20XOR/) |
| 6 | [Minimum XOR with given set bits](https://www.geeksforgeeks.org/problems/minimum-x-xor-a--170645/1) | — | — | — | Medium | Adobe, IBM | Arrays, Bit Magic | [`03. Medium/53. Minimum XOR with given set bits/`](03.%20Medium/53.%20Minimum%20XOR%20with%20given%20set%20bits/) |
| 7 | [Ways to Split into 2 with Same XOR](https://www.geeksforgeeks.org/problems/split-the-array0238/1) | — | — | — | Medium | — | Arrays, Bit Magic | [`03. Medium/57. Ways to Split into 2 with Same XOR/`](03.%20Medium/57.%20Ways%20to%20Split%20into%202%20with%20Same%20XOR/) |
| 8 | [Smallest Non-Zero Number](https://www.geeksforgeeks.org/problems/find-smallest-non-zero-number4510/1) | — | — | — | Medium | — | Arrays, Binary Search | [`03. Medium/65. Smallest Non-Zero Number/`](03.%20Medium/65.%20Smallest%20Non-Zero%20Number/) |

### Subset / Combinatorial Selection (7)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Max Product Subset](https://www.geeksforgeeks.org/problems/maximum-product-subset-of-an-array/1) | — | — | — | Medium | — | Arrays | [`03. Medium/13. Max Product Subset/`](03.%20Medium/13.%20Max%20Product%20Subset/) |
| 2 | [Not a Subset Sum](https://www.geeksforgeeks.org/problems/smallest-number-subset1220/1) | — | — | — | Medium | Salesforce | Arrays | [`03. Medium/19. Not a Subset Sum/`](03.%20Medium/19.%20Not%20a%20Subset%20Sum/) |
| 3 | [Min Product Subset](https://www.geeksforgeeks.org/problems/max-and-min-products3347/1) | — | — | — | Medium | — | Arrays | [`03. Medium/66. Min Product Subset/`](03.%20Medium/66.%20Min%20Product%20Subset/) |
| 4 | [Maximum GCD of K Partition Sums](https://www.geeksforgeeks.org/problems/gcd-array--170645/1) | — | — | — | Medium | — | Arrays, Mathematics | [`03. Medium/69. Maximum GCD of K Partition Sums/`](03.%20Medium/69.%20Maximum%20GCD%20of%20K%20Partition%20Sums/) |
| 5 | [Count Divisors of Array Product](https://www.geeksforgeeks.org/problems/count-divisors-of-product-of-array-elements0244/1) | — | — | — | Medium | — | Arrays, Prime Number | [`03. Medium/77. Count Divisors of Array Product/`](03.%20Medium/77.%20Count%20Divisors%20of%20Array%20Product/) |
| 6 | [Subsets with given Max Diff](https://www.geeksforgeeks.org/problems/count-number4832/1) | — | — | — | Medium | — | Arrays | [`03. Medium/94. Subsets with given Max Diff/`](03.%20Medium/94.%20Subsets%20with%20given%20Max%20Diff/) |
| 7 | [Sum of subset differences](https://www.geeksforgeeks.org/problems/sum-of-subset-differences/1) | — | — | — | Medium | — | Arrays | [`03. Medium/96. Sum of subset differences/`](03.%20Medium/96.%20Sum%20of%20subset%20differences/) |

### Duplicate / Distinct Element Handling (5)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Remove Duplicates from Unsorted](https://www.geeksforgeeks.org/problems/remove-duplicates-from-unsorted-array4141/1) | — | — | — | Basics | — | Arrays | [`01. Basics/25. Remove Duplicates from Unsorted/`](01.%20Basics/25.%20Remove%20Duplicates%20from%20Unsorted/) |
| 2 | [Sum of distinct elements](https://www.geeksforgeeks.org/problems/sum-of-distinct-elements4801/1) | — | — | — | Basics | Oxigen Wallet | Arrays | [`01. Basics/30. Sum of distinct elements/`](01.%20Basics/30.%20Sum%20of%20distinct%20elements/) |
| 3 | [Last Duplicate in a Sorted Array](https://www.geeksforgeeks.org/problems/last-duplicate-element-in-a-sorted-array5539/1) | — | — | — | Basics | — | Arrays | [`01. Basics/35. Last Duplicate in a Sorted Array/`](01.%20Basics/35.%20Last%20Duplicate%20in%20a%20Sorted%20Array/) |
| 4 | [Make a Distinct Digit Array](https://www.geeksforgeeks.org/problems/make-a-distinct-digit-array2007/1) | — | — | — | Basics | Zoho, Amazon, MakeMyTrip | Arrays | [`01. Basics/34. Make a Distinct Digit Array/`](01.%20Basics/34.%20Make%20a%20Distinct%20Digit%20Array/) |
| 5 | [Missing in Another Shuffled Array](https://www.geeksforgeeks.org/problems/missing-number-in-shuffled-array0938/1) | — | — | — | Basics | — | Arrays, Bit Magic | [`01. Basics/41. Missing in Another Shuffled Array/`](01.%20Basics/41.%20Missing%20in%20Another%20Shuffled%20Array/) |

### Stock Buy-Sell / Sequential Decision DP (4)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Stock Buy and Sell – Multiple Transaction Allowed](https://www.geeksforgeeks.org/problems/stock-buy-and-sell2615/1) | — | — | — | Medium | Paytm, Flipkart, Morgan Stanley, Accolite, Amazon, Microsoft, Samsung, D-E-Shaw, Hike, MakeMyTrip, Ola Cabs, Oracle, Walmart, Goldman Sachs, Directi, Intuit, SAP Labs, Quikr, Facebook, Salesforce, Pubmatic, Sapient, Swiggy | Arrays | [`03. Medium/08. Stock Buy and Sell – Multiple Transaction Allowed/`](03.%20Medium/08.%20Stock%20Buy%20and%20Sell%20–%20Multiple%20Transaction%20Allowed/) |
| 2 | [Max Sum Path in Two Arrays](https://www.geeksforgeeks.org/problems/max-sum-path-in-two-arrays/1) | — | — | — | Medium | Amazon | Arrays | [`03. Medium/20. Max Sum Path in Two Arrays/`](03.%20Medium/20.%20Max%20Sum%20Path%20in%20Two%20Arrays/) |
| 3 | [Longest Subsequence with Adjacent Diff as 1](https://www.geeksforgeeks.org/problems/longest-sub-sequence-such-that-difference-between-adjacents-is-one2558/1) | — | — | — | Medium | Flipkart | Arrays | [`03. Medium/27. Longest Subsequence with Adjacent Diff as 1/`](03.%20Medium/27.%20Longest%20Subsequence%20with%20Adjacent%20Diff%20as%201/) |
| 4 | [Longest Geometric Progression](https://www.geeksforgeeks.org/problems/longest-geometric-progression0131/1) | — | — | — | Medium | — | Misc, Mathematics, Arrays | [`03. Medium/98. Longest Geometric Progression/`](03.%20Medium/98.%20Longest%20Geometric%20Progression/) |

### Monotonic Run / Bitonic Subarray (4)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Longest Subarray of Evens and Odds](https://www.geeksforgeeks.org/problems/longest-subarray-of-evens-and-odds/1) | — | — | — | Medium | — | Arrays | [`03. Medium/42. Longest Subarray of Evens and Odds/`](03.%20Medium/42.%20Longest%20Subarray%20of%20Evens%20and%20Odds/) |
| 2 | [Longest Bitonic Subarray](https://www.geeksforgeeks.org/problems/maximum-length-bitonic-subarray5730/1) | — | — | — | Medium | Microsoft | Arrays | [`03. Medium/52. Longest Bitonic Subarray/`](03.%20Medium/52.%20Longest%20Bitonic%20Subarray/) |
| 3 | [Mountain Subarray Queries](https://www.geeksforgeeks.org/problems/mountain-subarray-problem/1) | — | — | — | Medium | Amazon | Arrays | [`03. Medium/59. Mountain Subarray Queries/`](03.%20Medium/59.%20Mountain%20Subarray%20Queries/) |
| 4 | [Local Min and Max Sequence Ordering](https://www.geeksforgeeks.org/problems/track-the-trail/1) | — | — | — | Medium | NPCI | Arrays | [`03. Medium/91. Local Min and Max Sequence Ordering/`](03.%20Medium/91.%20Local%20Min%20and%20Max%20Sequence%20Ordering/) |

### Cyclic Sort / Index-Value Mapping (3)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Missing And Repeating](https://www.geeksforgeeks.org/problems/find-missing-and-repeating2512/1) | — | — | — | Easy | — | Arrays | [`02. Easy/03. Missing And Repeating/`](02.%20Easy/03.%20Missing%20And%20Repeating/) |
| 2 | [Inverse Permutation](https://www.geeksforgeeks.org/problems/inverse-permutation0344/1) | — | — | — | Easy | — | Arrays | [`02. Easy/73. Inverse Permutation/`](02.%20Easy/73.%20Inverse%20Permutation/) |
| 3 | [Any Duplicate Within K Distance](https://www.geeksforgeeks.org/problems/kth-distance3757/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/31. Any Duplicate Within K Distance/`](02.%20Easy/31.%20Any%20Duplicate%20Within%20K%20Distance/) |

### Reconstruction / Simulation (3)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Construct an array from its pair-sum array](https://www.geeksforgeeks.org/problems/construct-an-array-from-its-pair-sum-array/1) | — | — | — | Easy | — | Mathematics, Arrays | [`02. Easy/77. Construct an array from its pair-sum array/`](02.%20Easy/77.%20Construct%20an%20array%20from%20its%20pair-sum%20array/) |
| 2 | [Equal Sum with Insertion](https://www.geeksforgeeks.org/problems/equal-sums4801/1) | — | — | — | Easy | — | Arrays | [`02. Easy/110. Equal Sum with Insertion/`](02.%20Easy/110.%20Equal%20Sum%20with%20Insertion/) |
| 3 | [Matrix Interchange](https://www.geeksforgeeks.org/problems/matrix-interchange/1) | — | — | — | Easy | — | Arrays | [`02. Easy/38. Matrix Interchange/`](02.%20Easy/38.%20Matrix%20Interchange/) |

### Monotonic Stack (3)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Farthest Smaller Right](https://www.geeksforgeeks.org/problems/farthest-smaller-right/1) | — | — | — | Medium | NPCI | Binary Search, Arrays | [`03. Medium/60. Farthest Smaller Right/`](03.%20Medium/60.%20Farthest%20Smaller%20Right/) |
| 2 | [Farthest Smaller on Right](https://www.geeksforgeeks.org/problems/farthest-number--170636/1) | — | — | — | Medium | Amazon | Arrays, Binary Search | [`03. Medium/73. Farthest Smaller on Right/`](03.%20Medium/73.%20Farthest%20Smaller%20on%20Right/) |
| 3 | [Subarray Inversions](https://www.geeksforgeeks.org/problems/subarray-inversions0512/1) | — | — | — | Medium | — | Arrays, Advanced Data Structure | [`03. Medium/100. Subarray Inversions/`](03.%20Medium/100.%20Subarray%20Inversions/) |

### Index-Value Difference / Max-Diff Tricks (2)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Max Diff Elements and Indexes](https://www.geeksforgeeks.org/problems/maximum-value-of-difference-of-a-pair-of-elements-and-their-index/1) | — | — | — | Medium | Microsoft | Arrays, Mathematics | [`03. Medium/56. Max Diff Elements and Indexes/`](03.%20Medium/56.%20Max%20Diff%20Elements%20and%20Indexes/) |
| 2 | [Array Elements Divisible by Any Others](https://www.geeksforgeeks.org/problems/count-special-numbers--170647/1) | — | — | — | Medium | Intuit, NPCI | Arrays, Mathematics, sieve | [`03. Medium/38. Array Elements Divisible by Any Others/`](03.%20Medium/38.%20Array%20Elements%20Divisible%20by%20Any%20Others/) |

### Brute-Force Enumeration / Generation (1)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Generating All Subarrays](https://www.geeksforgeeks.org/problems/generating-all-subarrays/1) | — | — | — | Easy | — | Arrays | [`02. Easy/82. Generating All Subarrays/`](02.%20Easy/82.%20Generating%20All%20Subarrays/) |

### Circular Array / Kadane's Algorithm (1)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Max Circular Subarray Sum](https://www.geeksforgeeks.org/problems/max-circular-subarray-sum-1587115620/1) | — | — | — | Hard | Amazon, Microsoft | Arrays, Kadane | [`04. Hard/01. Max Circular Subarray Sum/`](04.%20Hard/01.%20Max%20Circular%20Subarray%20Sum/) |


## Basics (56)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Largest in Array](https://www.geeksforgeeks.org/problems/largest-element-in-array4009/1) | — | — | — | Basics | Infosys, Oracle, Wipro, Morgan Stanley | Arrays | [`01. Basics/01. Largest in Array/`](01.%20Basics/01.%20Largest%20in%20Array/) |
| 2 | [Min and Max in Array](https://www.geeksforgeeks.org/problems/find-minimum-and-maximum-element-in-an-array4428/1) | — | — | — | Basics | NPCI | Arrays | [`01. Basics/02. Min and Max in Array/`](01.%20Basics/02.%20Min%20and%20Max%20in%20Array/) |
| 3 | [Rotate Array by One](https://www.geeksforgeeks.org/problems/cyclically-rotate-an-array-by-one2614/1) | — | — | — | Basics | — | Arrays, implementation | [`01. Basics/03. Rotate Array by One/`](01.%20Basics/03.%20Rotate%20Array%20by%20One/) |
| 4 | [Sum of Array](https://www.geeksforgeeks.org/problems/sum-all-array-elements/1) | — | — | — | Basics | — | Arrays | [`01. Basics/04. Sum of Array/`](01.%20Basics/04.%20Sum%20of%20Array/) |
| 5 | [Alternates in an Array](https://www.geeksforgeeks.org/problems/print-alternate-elements-of-an-array/1) | — | — | — | Basics | — | Arrays | [`01. Basics/05. Alternates in an Array/`](01.%20Basics/05.%20Alternates%20in%20an%20Array/) |
| 6 | [Array with All Palindromes](https://www.geeksforgeeks.org/problems/palindromic-array-1587115620/1) | — | — | — | Basics | — | Arrays | [`01. Basics/06. Array with All Palindromes/`](01.%20Basics/06.%20Array%20with%20All%20Palindromes/) |
| 7 | [Array Traversal](https://www.geeksforgeeks.org/problems/array-traversal/1) | — | — | — | Basics | — | Arrays | [`01. Basics/07. Array Traversal/`](01.%20Basics/07.%20Array%20Traversal/) |
| 8 | [Count Smaller in Array](https://www.geeksforgeeks.org/problems/count-of-smaller-elements5947/1) | — | — | — | Basics | — | Arrays | [`01. Basics/08. Count Smaller in Array/`](01.%20Basics/08.%20Count%20Smaller%20in%20Array/) |
| 9 | [Replace all 0's with 5](https://www.geeksforgeeks.org/problems/replace-all-0s-with-5/1) | — | — | — | Basics | Amazon | Arrays, Mathematics | [`01. Basics/09. Replace all 0's with 5/`](01.%20Basics/09.%20Replace%20all%200's%20with%205/) |
| 10 | [Count Odd and Even](https://www.geeksforgeeks.org/problems/count-odd-even/1) | — | — | — | Basics | — | Arrays | [`01. Basics/10. Count Odd and Even/`](01.%20Basics/10.%20Count%20Odd%20and%20Even/) |
| 11 | [Array Insert at Index](https://www.geeksforgeeks.org/problems/array-insert-at-index/1) | — | — | — | Basics | — | Arrays | [`01. Basics/11. Array Insert at Index/`](01.%20Basics/11.%20Array%20Insert%20at%20Index/) |
| 12 | [Most Frequent of Two](https://www.geeksforgeeks.org/problems/who-has-the-majority/1) | — | — | — | Basics | — | Arrays | [`01. Basics/12. Most Frequent of Two/`](01.%20Basics/12.%20Most%20Frequent%20of%20Two/) |
| 13 | [Sum Except First and Last](https://www.geeksforgeeks.org/problems/max-length-chain/1) | — | — | — | Basics | Amazon, Microsoft | Arrays | [`01. Basics/13. Sum Except First and Last/`](01.%20Basics/13.%20Sum%20Except%20First%20and%20Last/) |
| 14 | [Find element at a given Index](https://www.geeksforgeeks.org/problems/c-array-print-an-element-set-25933/1) | — | — | — | Basics | — | Arrays, CPP | [`01. Basics/14. Find element at a given Index/`](01.%20Basics/14.%20Find%20element%20at%20a%20given%20Index/) |
| 15 | [Smaller and Larger in Sorted](https://www.geeksforgeeks.org/problems/smaller-and-larger4005/1) | — | — | — | Basics | — | Arrays | [`01. Basics/15. Smaller and Larger in Sorted/`](01.%20Basics/15.%20Smaller%20and%20Larger%20in%20Sorted/) |
| 16 | [Palindrome Array](https://www.geeksforgeeks.org/problems/perfect-arrays4645/1) | — | — | — | Basics | — | Arrays | [`01. Basics/16. Palindrome Array/`](01.%20Basics/16.%20Palindrome%20Array/) |
| 17 | [Swap kth elements](https://www.geeksforgeeks.org/problems/swap-kth-elements5500/1) | — | — | — | Basics | Morgan Stanley, Rockstand | Arrays | [`01. Basics/17. Swap kth elements/`](01.%20Basics/17.%20Swap%20kth%20elements/) |
| 18 | [Array End Insert](https://www.geeksforgeeks.org/problems/array-insert-at-end/1) | — | — | — | Basics | — | Arrays | [`01. Basics/18. Array End Insert/`](01.%20Basics/18.%20Array%20End%20Insert/) |
| 19 | [Even Odd Positions](https://www.geeksforgeeks.org/problems/find-the-fine4353/1) | — | — | — | Basics | Microsoft | Arrays, Mathematics | [`01. Basics/19. Even Odd Positions/`](01.%20Basics/19.%20Even%20Odd%20Positions/) |
| 20 | [Adjacent XOR Transformation](https://www.geeksforgeeks.org/problems/game-with-nos3123/1) | — | — | — | Basics | — | Arrays, Bit Magic | [`01. Basics/20. Adjacent XOR Transformation/`](01.%20Basics/20.%20Adjacent%20XOR%20Transformation/) |
| 21 | [Multiply Left and Right Array Sums](https://www.geeksforgeeks.org/problems/multiply-left-and-right-array-sum1555/1) | — | — | — | Basics | — | Arrays | [`01. Basics/21. Multiply Left and Right Array Sums/`](01.%20Basics/21.%20Multiply%20Left%20and%20Right%20Array%20Sums/) |
| 22 | [Strongest Neighbour](https://www.geeksforgeeks.org/problems/strongest-neighbour/1) | — | — | — | Basics | — | Arrays | [`01. Basics/22. Strongest Neighbour/`](01.%20Basics/22.%20Strongest%20Neighbour/) |
| 23 | [Balanced Array](https://www.geeksforgeeks.org/problems/balanced-array07200720/1) | — | — | — | Basics | — | Arrays | [`01. Basics/23. Balanced Array/`](01.%20Basics/23.%20Balanced%20Array/) |
| 24 | [Max and Min Product from 2 Arrays](https://www.geeksforgeeks.org/problems/product-of-maximum-in-first-array-and-minimum-in-second3943/1) | — | — | — | Basics | Adobe | Arrays | [`01. Basics/24. Max and Min Product from 2 Arrays/`](01.%20Basics/24.%20Max%20and%20Min%20Product%20from%202%20Arrays/) |
| 25 | [Remove Duplicates from Unsorted](https://www.geeksforgeeks.org/problems/remove-duplicates-from-unsorted-array4141/1) | — | — | — | Basics | — | Arrays | [`01. Basics/25. Remove Duplicates from Unsorted/`](01.%20Basics/25.%20Remove%20Duplicates%20from%20Unsorted/) |
| 26 | [Fighting the Darkness](https://www.geeksforgeeks.org/problems/fighting-the-darkness3949/1) | — | — | — | Basics | Snapdeal | Arrays | [`01. Basics/26. Fighting the Darkness/`](01.%20Basics/26.%20Fighting%20the%20Darkness/) |
| 27 | [Segregate Even and Odd numbers](https://www.geeksforgeeks.org/problems/segregate-even-and-odd-numbers4629/1) | — | — | — | Basics | Paytm, Accolite, Amazon, MakeMyTrip, Linkedin | Arrays | [`01. Basics/27. Segregate Even and Odd numbers/`](01.%20Basics/27.%20Segregate%20Even%20and%20Odd%20numbers/) |
| 28 | [Reverse Subarray](https://www.geeksforgeeks.org/problems/reverse-sub-array5620/1) | — | — | — | Basics | Amazon | Arrays | [`01. Basics/28. Reverse Subarray/`](01.%20Basics/28.%20Reverse%20Subarray/) |
| 29 | [Type of array](https://www.geeksforgeeks.org/problems/type-of-array4605/1) | — | — | — | Basics | Amazon | Arrays | [`01. Basics/29. Type of array/`](01.%20Basics/29.%20Type%20of%20array/) |
| 30 | [Sum of distinct elements](https://www.geeksforgeeks.org/problems/sum-of-distinct-elements4801/1) | — | — | — | Basics | Oxigen Wallet | Arrays | [`01. Basics/30. Sum of distinct elements/`](01.%20Basics/30.%20Sum%20of%20distinct%20elements/) |
| 31 | [C++ 2-D Arrays | Set-1](https://www.geeksforgeeks.org/problems/c-2-d-arrays0708/1) | — | — | — | Basics | — | Arrays, CPP | [`01. Basics/31. C++ 2-D Arrays Set-1/`](01.%20Basics/31.%20C++%202-D%20Arrays%20Set-1/) |
| 32 | [Java 1-d and 2-d Array](https://www.geeksforgeeks.org/problems/java-1-d-and-2-d-array2952/1) | — | — | — | Basics | — | Arrays, Java | [`01. Basics/32. Java 1-d and 2-d Array/`](01.%20Basics/32.%20Java%201-d%20and%202-d%20Array/) |
| 33 | [Absolute Digit Diff 1 in Array](https://www.geeksforgeeks.org/problems/absolute-difference-11156/1) | — | — | — | Basics | Amazon, Jabong | Arrays | [`01. Basics/33. Absolute Digit Diff 1 in Array/`](01.%20Basics/33.%20Absolute%20Digit%20Diff%201%20in%20Array/) |
| 34 | [Make a Distinct Digit Array](https://www.geeksforgeeks.org/problems/make-a-distinct-digit-array2007/1) | — | — | — | Basics | Zoho, Amazon, MakeMyTrip | Arrays | [`01. Basics/34. Make a Distinct Digit Array/`](01.%20Basics/34.%20Make%20a%20Distinct%20Digit%20Array/) |
| 35 | [Last Duplicate in a Sorted Array](https://www.geeksforgeeks.org/problems/last-duplicate-element-in-a-sorted-array5539/1) | — | — | — | Basics | — | Arrays | [`01. Basics/35. Last Duplicate in a Sorted Array/`](01.%20Basics/35.%20Last%20Duplicate%20in%20a%20Sorted%20Array/) |
| 36 | [Sum Array Puzzle](https://www.geeksforgeeks.org/problems/sum-array-puzzle/1) | — | — | — | Basics | — | Arrays, Mathematics | [`01. Basics/36. Sum Array Puzzle/`](01.%20Basics/36.%20Sum%20Array%20Puzzle/) |
| 37 | [Half Ascending and Half Descending Sort](https://www.geeksforgeeks.org/problems/sort-first-half-in-ascending-and-second-half-in-descending1714/1) | — | — | — | Basics | — | Arrays | [`01. Basics/37. Half Ascending and Half Descending Sort/`](01.%20Basics/37.%20Half%20Ascending%20and%20Half%20Descending%20Sort/) |
| 38 | [Winner in Pairwise Army Battles](https://www.geeksforgeeks.org/problems/countries-at-war2936/1) | — | — | — | Basics | — | Arrays | [`01. Basics/38. Winner in Pairwise Army Battles/`](01.%20Basics/38.%20Winner%20in%20Pairwise%20Army%20Battles/) |
| 39 | [Max Triplet Sum](https://www.geeksforgeeks.org/problems/maximum-triplet-sum-in-array0129/1) | — | — | — | Basics | — | Arrays | [`01. Basics/39. Max Triplet Sum/`](01.%20Basics/39.%20Max%20Triplet%20Sum/) |
| 40 | [Minimum sum of two elements from two arrays](https://www.geeksforgeeks.org/problems/minimum-sum-of-two-elements-from-two-arrays0253/1) | — | — | — | Basics | — | Arrays | [`01. Basics/40. Minimum sum of two elements from two arrays/`](01.%20Basics/40.%20Minimum%20sum%20of%20two%20elements%20from%20two%20arrays/) |
| 41 | [Missing in Another Shuffled Array](https://www.geeksforgeeks.org/problems/missing-number-in-shuffled-array0938/1) | — | — | — | Basics | — | Arrays, Bit Magic | [`01. Basics/41. Missing in Another Shuffled Array/`](01.%20Basics/41.%20Missing%20in%20Another%20Shuffled%20Array/) |
| 42 | [Max Product K Sized Subarray](https://www.geeksforgeeks.org/problems/largest-product/1) | — | — | — | Basics | — | Arrays | [`01. Basics/42. Max Product K Sized Subarray/`](01.%20Basics/42.%20Max%20Product%20K%20Sized%20Subarray/) |
| 43 | [Average Count Array](https://www.geeksforgeeks.org/problems/average-count-array2215/1) | — | — | — | Basics | — | Arrays, Mathematics, logical-thinking | [`01. Basics/43. Average Count Array/`](01.%20Basics/43.%20Average%20Count%20Array/) |
| 44 | [Min Decrement by K Operations to Limit Array](https://www.geeksforgeeks.org/problems/reducing-walls4443/1) | — | — | — | Basics | — | Arrays | [`01. Basics/44. Min Decrement by K Operations to Limit Array/`](01.%20Basics/44.%20Min%20Decrement%20by%20K%20Operations%20to%20Limit%20Array/) |
| 45 | [Even Occurring Elements](https://www.geeksforgeeks.org/problems/even-occurring-elements4332/1) | — | — | — | Basics | — | Arrays, Bit Magic | [`01. Basics/45. Even Occurring Elements/`](01.%20Basics/45.%20Even%20Occurring%20Elements/) |
| 46 | [Two Max Adjacent in an Array](https://www.geeksforgeeks.org/problems/why-is-melody-so-chocolaty0446/1) | — | — | — | Basics | — | Arrays | [`01. Basics/46. Two Max Adjacent in an Array/`](01.%20Basics/46.%20Two%20Max%20Adjacent%20in%20an%20Array/) |
| 47 | [Different Adjacent Elements](https://www.geeksforgeeks.org/problems/distinct-adjacent-element2121/1) | — | — | — | Basics | — | Arrays | [`01. Basics/47. Different Adjacent Elements/`](01.%20Basics/47.%20Different%20Adjacent%20Elements/) |
| 48 | [Shortest Unsorted Subarray](https://www.geeksforgeeks.org/problems/shortest-un-ordered-subarray3634/1) | — | — | — | Basics | Oracle | Arrays | [`01. Basics/48. Shortest Unsorted Subarray/`](01.%20Basics/48.%20Shortest%20Unsorted%20Subarray/) |
| 49 | [Count Prefix Maximums](https://www.geeksforgeeks.org/problems/elements-before-which-no-element-is-bigger0602/1) | — | — | — | Basics | — | Arrays | [`01. Basics/49. Count Prefix Maximums/`](01.%20Basics/49.%20Count%20Prefix%20Maximums/) |
| 50 | [Check for Bitonic with Same Numbers](https://www.geeksforgeeks.org/problems/perfect-array2344/1) | — | — | — | Basics | — | Arrays | [`01. Basics/50. Check for Bitonic with Same Numbers/`](01.%20Basics/50.%20Check%20for%20Bitonic%20with%20Same%20Numbers/) |
| 51 | [Minimum Time with Alternating Techniques](https://www.geeksforgeeks.org/problems/a-guy-with-a-mental-problem1604/1) | — | — | — | Basics | — | Arrays | [`01. Basics/51. Minimum Time with Alternating Techniques/`](01.%20Basics/51.%20Minimum%20Time%20with%20Alternating%20Techniques/) |
| 52 | [Count Pairs Odd XOR](https://www.geeksforgeeks.org/problems/count-pairs-odd-xor0308/1) | — | — | — | Basics | — | Arrays, Mathematics | [`01. Basics/52. Count Pairs Odd XOR/`](01.%20Basics/52.%20Count%20Pairs%20Odd%20XOR/) |
| 53 | [Max Odd Sum](https://www.geeksforgeeks.org/problems/max-odd-sum0651/1) | — | — | — | Basics | — | Arrays | [`01. Basics/53. Max Odd Sum/`](01.%20Basics/53.%20Max%20Odd%20Sum/) |
| 54 | [Sum Triangle](https://www.geeksforgeeks.org/problems/sum-triangle-for-given-array1159/1) | — | — | — | Basics | — | Arrays | [`01. Basics/54. Sum Triangle/`](01.%20Basics/54.%20Sum%20Triangle/) |
| 55 | [Make Co-prime Array](https://www.geeksforgeeks.org/problems/make-coprime-array3058/1) | — | — | — | Basics | — | Arrays | [`01. Basics/55. Make Co-prime Array/`](01.%20Basics/55.%20Make%20Co-prime%20Array/) |
| 56 | [Occurrences of Consecutive 3 Numbers](https://www.geeksforgeeks.org/problems/special-integers/1) | — | — | — | Basics | — | Arrays, Map | [`01. Basics/56. Occurrences of Consecutive 3 Numbers/`](01.%20Basics/56.%20Occurrences%20of%20Consecutive%203%20Numbers/) |

## Easy (135)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Move All Zeroes to End](https://www.geeksforgeeks.org/problems/move-all-zeroes-to-end-of-array0751/1) | — | — | — | Easy | Paytm, Amazon, Microsoft, Samsung, SAP Labs, Linkedin, Bloomberg, NPCI | Arrays | [`02. Easy/04. Move All Zeroes to End/`](02.%20Easy/04.%20Move%20All%20Zeroes%20to%20End/) |
| 2 | [Reverse Array](https://www.geeksforgeeks.org/problems/reverse-an-array/1) | — | — | — | Easy | Bloomberg, Facebook, TCS, Adobe, Google, Infosys, Capgemini, Morgan Stanley, Amazon, Microsoft, Apple, Yahoo, PayPal, Uber | Arrays | [`02. Easy/05. Reverse Array/`](02.%20Easy/05.%20Reverse%20Array/) |
| 3 | [Move all negative elements to end](https://www.geeksforgeeks.org/problems/move-all-negative-elements-to-end1813/1) | — | — | — | Easy | — | Arrays | [`02. Easy/07. Move all negative elements to end/`](02.%20Easy/07.%20Move%20all%20negative%20elements%20to%20end/) |
| 4 | [Segregate 0s and 1s](https://www.geeksforgeeks.org/problems/segregate-0s-and-1s5106/1) | — | — | — | Easy | Paytm, Goldman Sachs, Fab.com | Arrays | [`02. Easy/12. Segregate 0s and 1s/`](02.%20Easy/12.%20Segregate%200s%20and%201s/) |
| 5 | [Implement Lower Bound](https://www.geeksforgeeks.org/problems/implement-lower-bound/1) | — | — | — | Easy | — | Binary Search, Arrays | [`02. Easy/17. Implement Lower Bound/`](02.%20Easy/17.%20Implement%20Lower%20Bound/) |
| 6 | [Adding One to Array](https://www.geeksforgeeks.org/problems/adding-one2529/1) | — | — | — | Easy | Google, Microsoft | Arrays | [`02. Easy/18. Adding One to Array/`](02.%20Easy/18.%20Adding%20One%20to%20Array/) |
| 7 | [Frogs and Jumps](https://www.geeksforgeeks.org/problems/frogs-and-jumps--170647/1) | — | — | — | Easy | PayPal | Arrays, sieve | [`02. Easy/24. Frogs and Jumps/`](02.%20Easy/24.%20Frogs%20and%20Jumps/) |
| 8 | [Replace with XOR of Adjacent](https://www.geeksforgeeks.org/problems/replace-with-xor-of-adjacent/1) | — | — | — | Easy | — | Arrays, Bit Magic | [`02. Easy/25. Replace with XOR of Adjacent/`](02.%20Easy/25.%20Replace%20with%20XOR%20of%20Adjacent/) |
| 9 | [Implement Upper Bound](https://www.geeksforgeeks.org/problems/implement-upper-bound/1) | — | — | — | Easy | — | Binary Search, Arrays | [`02. Easy/26. Implement Upper Bound/`](02.%20Easy/26.%20Implement%20Upper%20Bound/) |
| 10 | [Minimum Integer](https://www.geeksforgeeks.org/problems/minimum-integer--170647/1) | — | — | — | Easy | — | Mathematics, Arrays | [`02. Easy/27. Minimum Integer/`](02.%20Easy/27.%20Minimum%20Integer/) |
| 11 | [Split Array Elements into Bounded Parts](https://www.geeksforgeeks.org/problems/total-count2415/1) | — | — | — | Easy | Zoho | Arrays, Division, Mathematics | [`02. Easy/29. Split Array Elements into Bounded Parts/`](02.%20Easy/29.%20Split%20Array%20Elements%20into%20Bounded%20Parts/) |
| 12 | [Any Duplicate Within K Distance](https://www.geeksforgeeks.org/problems/kth-distance3757/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/31. Any Duplicate Within K Distance/`](02.%20Easy/31.%20Any%20Duplicate%20Within%20K%20Distance/) |
| 13 | [Adding Ones](https://www.geeksforgeeks.org/problems/adding-ones3628/1) | — | — | — | Easy | — | Arrays | [`02. Easy/34. Adding Ones/`](02.%20Easy/34.%20Adding%20Ones/) |
| 14 | [Matrix Interchange](https://www.geeksforgeeks.org/problems/matrix-interchange/1) | — | — | — | Easy | — | Arrays | [`02. Easy/38. Matrix Interchange/`](02.%20Easy/38.%20Matrix%20Interchange/) |
| 15 | [Make Array Elements Equal](https://www.geeksforgeeks.org/problems/make-array-elements-equal--170647/1) | — | — | — | Easy | Expedia | Arrays | [`02. Easy/42. Make Array Elements Equal/`](02.%20Easy/42.%20Make%20Array%20Elements%20Equal/) |
| 16 | [Compete the Skills](https://www.geeksforgeeks.org/problems/compete-the-skills5807/1) | — | — | — | Easy | — | Arrays | [`02. Easy/44. Compete the Skills/`](02.%20Easy/44.%20Compete%20the%20Skills/) |
| 17 | [Minimum Number](https://www.geeksforgeeks.org/problems/minimum-number--170647/1) | — | — | — | Easy | — | Arrays, Number Theory | [`02. Easy/53. Minimum Number/`](02.%20Easy/53.%20Minimum%20Number/) |
| 18 | [Java ArrayList Operation](https://www.geeksforgeeks.org/problems/arraylist-operation/1) | — | — | — | Easy | — | Arrays | [`02. Easy/59. Java ArrayList Operation/`](02.%20Easy/59.%20Java%20ArrayList%20Operation/) |
| 19 | [Maximum Average Subarray](https://www.geeksforgeeks.org/problems/maximum-average-subarray5859/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/62. Maximum Average Subarray/`](02.%20Easy/62.%20Maximum%20Average%20Subarray/) |
| 20 | [Jumping Caterpillars](https://www.geeksforgeeks.org/problems/jumping-caterpillars4412/1) | — | — | — | Easy | Myntra | Arrays, Mathematics | [`02. Easy/63. Jumping Caterpillars/`](02.%20Easy/63.%20Jumping%20Caterpillars/) |
| 21 | [Longest Increasing Subarray](https://www.geeksforgeeks.org/problems/longest-increasing-subarray3811/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/64. Longest Increasing Subarray/`](02.%20Easy/64.%20Longest%20Increasing%20Subarray/) |
| 22 | [Maximum Gap](https://www.geeksforgeeks.org/problems/maximum-gap3845/1) | — | — | — | Easy | HunanAsset | Arrays, radix sort | [`02. Easy/67. Maximum Gap/`](02.%20Easy/67.%20Maximum%20Gap/) |
| 23 | [Sum of Submatrix Elements](https://www.geeksforgeeks.org/problems/addition-of-submatrix5835/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/71. Sum of Submatrix Elements/`](02.%20Easy/71.%20Sum%20of%20Submatrix%20Elements/) |
| 24 | [Inverse Permutation](https://www.geeksforgeeks.org/problems/inverse-permutation0344/1) | — | — | — | Easy | — | Arrays | [`02. Easy/73. Inverse Permutation/`](02.%20Easy/73.%20Inverse%20Permutation/) |
| 25 | [Minimum Product Pair](https://www.geeksforgeeks.org/problems/minimum-product-pair3608/1) | — | — | — | Easy | — | Arrays | [`02. Easy/78. Minimum Product Pair/`](02.%20Easy/78.%20Minimum%20Product%20Pair/) |
| 26 | [Generating All Subarrays](https://www.geeksforgeeks.org/problems/generating-all-subarrays/1) | — | — | — | Easy | — | Arrays | [`02. Easy/82. Generating All Subarrays/`](02.%20Easy/82.%20Generating%20All%20Subarrays/) |
| 27 | [Chocolate Station](https://www.geeksforgeeks.org/problems/chocolate-station2951/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/84. Chocolate Station/`](02.%20Easy/84.%20Chocolate%20Station/) |
| 28 | [Consecutive Array Elements](https://www.geeksforgeeks.org/problems/consecutive-array-elements2711/1) | — | — | — | Easy | — | Arrays | [`02. Easy/86. Consecutive Array Elements/`](02.%20Easy/86.%20Consecutive%20Array%20Elements/) |
| 29 | [Left Out Candies](https://www.geeksforgeeks.org/problems/left-out-candies5652/1) | — | — | — | Easy | Amazon | Arrays | [`02. Easy/87. Left Out Candies/`](02.%20Easy/87.%20Left%20Out%20Candies/) |
| 30 | [Missing Number in Sorted Array of Natural Numbers](https://www.geeksforgeeks.org/problems/missing-number-in-sorted-array-of-natural-numbers/1) | — | — | — | Easy | — | Binary Search, Mathematics, Arrays | [`02. Easy/88. Missing Number in Sorted Array of Natural Numbers/`](02.%20Easy/88.%20Missing%20Number%20in%20Sorted%20Array%20of%20Natural%20Numbers/) |
| 31 | [Reading Books](https://www.geeksforgeeks.org/problems/reading-books3803/1) | — | — | — | Easy | — | Arrays, Mathematics | [`02. Easy/90. Reading Books/`](02.%20Easy/90.%20Reading%20Books/) |
| 32 | [Equal Sum and Product Subarrays](https://www.geeksforgeeks.org/problems/equal-sum-and-product2057/1) | — | — | — | Easy | — | Arrays, subset | [`02. Easy/93. Equal Sum and Product Subarrays/`](02.%20Easy/93.%20Equal%20Sum%20and%20Product%20Subarrays/) |
| 33 | [The Inverting Factor](https://www.geeksforgeeks.org/problems/the-inverting-factor3932/1) | — | — | — | Easy | — | Arrays, Numbers, Reverse | [`02. Easy/95. The Inverting Factor/`](02.%20Easy/95.%20The%20Inverting%20Factor/) |
| 34 | [Equal Point in Sorted Array](https://www.geeksforgeeks.org/problems/equal-point-in-sorted-array0040/1) | — | — | — | Easy | — | Binary Search, Arrays | [`02. Easy/106. Equal Point in Sorted Array/`](02.%20Easy/106.%20Equal%20Point%20in%20Sorted%20Array/) |
| 35 | [Almost Prime Numbers](https://www.geeksforgeeks.org/problems/almost-prime-numbers/1) | — | — | — | Easy | — | Arrays, Prime Number | [`02. Easy/111. Almost Prime Numbers/`](02.%20Easy/111.%20Almost%20Prime%20Numbers/) |
| 36 | [Max Sum Submatrix Queries](https://www.geeksforgeeks.org/problems/max-sum-submatrix2725/1) | — | — | — | Easy | Accolite | Arrays | [`02. Easy/118. Max Sum Submatrix Queries/`](02.%20Easy/118.%20Max%20Sum%20Submatrix%20Queries/) |
| 37 | [Left or Right Positioned Array](https://www.geeksforgeeks.org/problems/left-or-right-positioned-array5757/1) | — | — | — | Easy | — | Arrays | [`02. Easy/121. Left or Right Positioned Array/`](02.%20Easy/121.%20Left%20or%20Right%20Positioned%20Array/) |
| 38 | [Sum of a Numpy Array](https://www.geeksforgeeks.org/problems/find-the-sum-of-all-elements-in-a-numpy-array/1) | — | — | — | Easy | — | Arrays | [`02. Easy/124. Sum of a Numpy Array/`](02.%20Easy/124.%20Sum%20of%20a%20Numpy%20Array/) |
| 39 | [Replace with Adjacent Multiplication](https://www.geeksforgeeks.org/problems/replace-with-adjacent-multiplication/1) | — | — | — | Easy | — | Arrays | [`02. Easy/125. Replace with Adjacent Multiplication/`](02.%20Easy/125.%20Replace%20with%20Adjacent%20Multiplication/) |
| 40 | [Union of Two Arrays with Distinct Elements](https://www.geeksforgeeks.org/problems/union-of-two-arrays-with-distinct-elements/1) | — | — | — | Easy | — | Arrays | [`02. Easy/129. Union of Two Arrays with Distinct Elements/`](02.%20Easy/129.%20Union%20of%20Two%20Arrays%20with%20Distinct%20Elements/) |
| 41 | [Possible to Form a Regular Polygon](https://www.geeksforgeeks.org/problems/regular-polygon-12611/1) | — | — | — | Easy | — | Arrays | [`02. Easy/130. Possible to Form a Regular Polygon/`](02.%20Easy/130.%20Possible%20to%20Form%20a%20Regular%20Polygon/) |
| 42 | [Number of Matches](https://www.geeksforgeeks.org/problems/number-of-matches1120/1) | — | — | — | Easy | — | Arrays | [`02. Easy/131. Number of Matches/`](02.%20Easy/131.%20Number%20of%20Matches/) |
| 43 | [Flatten a 3D Array into a 1D Array](https://www.geeksforgeeks.org/problems/flatten-a-3d-array-into-a-1d-array/1) | — | — | — | Easy | — | Arrays | [`02. Easy/133. Flatten a 3D Array into a 1D Array/`](02.%20Easy/133.%20Flatten%20a%203D%20Array%20into%20a%201D%20Array/) |
| 44 | [Linear Algebra - Solve Linear System](https://www.geeksforgeeks.org/problems/linear-algebra-solve-linear-system/1) | — | — | — | Easy | — | Arrays | [`02. Easy/134. Linear Algebra - Solve Linear System/`](02.%20Easy/134.%20Linear%20Algebra%20-%20Solve%20Linear%20System/) |
| 45 | [Array Transformation with Repeated Steps and Modulo Operation](https://www.geeksforgeeks.org/problems/array-transformation-with-repeated-steps-and-modulo-operation/1) | — | — | — | Easy | — | Arrays | [`02. Easy/135. Array Transformation with Repeated Steps and Modulo Operation/`](02.%20Easy/135.%20Array%20Transformation%20with%20Repeated%20Steps%20and%20Modulo%20Operation/) |
| 46 | [Array of alternate +ve and -ve nos](https://www.geeksforgeeks.org/problems/array-of-alternate-ve-and-ve-nos1401/1) | — | — | — | Easy | — | — | — |
| 47 | [Convert Array into Zig-Zag Fashion](https://www.geeksforgeeks.org/problems/convert-array-into-zig-zag-fashion1638/1) | — | — | — | Easy | — | — | — |
| 48 | [Need Some Change (Swap Adjacent in Array)](https://www.geeksforgeeks.org/problems/need-some-change/1) | — | — | — | Easy | — | — | — |
| 49 | [Print an array in Pendulum Arrangement](https://www.geeksforgeeks.org/problems/print-an-array-in-pendulum-arrangement4004/1) | — | — | — | Easy | — | — | — |
| 50 | [Even and Odd (Even at Even Index and Odd at Odd)](https://www.geeksforgeeks.org/problems/even-and-odd/1) | — | — | — | Easy | — | — | — |
| 51 | [Even and odd elements at even and odd positions](https://www.geeksforgeeks.org/problems/even-and-odd-elements-at-even-and-odd-positions1342/1) | — | — | — | Easy | — | — | — |
| 52 | [Need Some Change (Java) — Swap All with Next of Next](https://www.geeksforgeeks.org/problems/need-some-change-java/1) | — | — | — | Easy | — | — | — |
| 53 | [Two Swaps (Sorted in Two Swaps)](https://www.geeksforgeeks.org/problems/two-swaps--155623/1) | — | — | — | Easy | — | — | — |
| 54 | [Rearrange an array such that arr[i] = i](https://www.geeksforgeeks.org/problems/rearrange-an-array-such-that-arri-i3618/1) | — | — | — | Easy | — | — | — |
| 55 | [Third Largest Element](https://www.geeksforgeeks.org/problems/third-largest-element/1) | — | — | — | Easy | — | — | — |
| 56 | [Find the smallest and second smallest element](https://www.geeksforgeeks.org/problems/find-the-smallest-and-second-smallest-element-in-an-array3226/1) | — | — | — | Easy | — | — | — |
| 57 | [Professor and Parties (all elements distinct)](https://www.geeksforgeeks.org/problems/professor-and-parties2000/1) | — | — | — | Easy | — | — | — |
| 58 | [Form Largest Number from Digits](https://www.geeksforgeeks.org/problems/form-largest-number-from-digits5430/1) | — | — | — | Easy | — | — | — |
| 59 | [Length of Unsorted Subarray](https://www.geeksforgeeks.org/problems/length-unsorted-subarray3022/1) | — | — | — | Easy | — | — | — |
| 60 | [Pair with Greatest Product in Array](https://www.geeksforgeeks.org/problems/pair-with-greatest-product-in-array3342/1) | — | — | — | Easy | — | — | — |
| 61 | [Maximum Difference Indexes](https://www.geeksforgeeks.org/problems/maximum-difference-10429/1) | — | — | — | Easy | — | — | — |
| 62 | [Number of Pairs with Maximum Sum](https://www.geeksforgeeks.org/problems/number-of-pairs-with-maximum-sum2924/1) | — | — | — | Easy | — | — | — |
| 63 | [Maximum Weight Difference (choosing K numbers)](https://www.geeksforgeeks.org/problems/maximum-weight-difference5036/1) | — | — | — | Easy | — | — | — |
| 64 | [Pair the Minimum (Minimize Max Pair Sum)](https://www.geeksforgeeks.org/problems/pair-the-minimum5535/1) | — | — | — | Easy | — | — | — |
| 65 | [Form a Triangle (triplet check)](https://www.geeksforgeeks.org/problems/form-a-triangle5935/1) | — | — | — | Easy | — | — | — |
| 66 | [Count the Pairs with Maximum Difference](https://www.geeksforgeeks.org/problems/count-the-pairs-with-maximum-difference4807/1) | — | — | — | Easy | — | — | — |
| 67 | [Maximum Value K (k larger elements)](https://www.geeksforgeeks.org/problems/maximum-value-k2745/1) | — | — | — | Easy | — | — | — |
| 68 | [Ceil the Floor (Floor and Ceil in Unsorted)](https://www.geeksforgeeks.org/problems/ceil-the-floor2802/1) | — | — | — | Easy | — | — | — |
| 69 | [Find Index (First and Last in Unsorted)](https://www.geeksforgeeks.org/problems/find-index4752/1) | — | — | — | Easy | — | — | — |
| 70 | [Find the Closest Number](https://www.geeksforgeeks.org/problems/find-the-closest-number5513/1) | — | — | — | Easy | — | — | — |
| 71 | [K-th Missing Element (sorted)](https://www.geeksforgeeks.org/problems/k-th-missing-element3635/1) | — | — | — | Easy | — | — | — |
| 72 | [Magical Number (Same Value as Index in Sorted)](https://www.geeksforgeeks.org/problems/magical-number-1587115620/1) | — | — | — | Easy | — | — | — |
| 73 | [Find K-th Missing Element (a[] missing from b[])](https://www.geeksforgeeks.org/problems/find-k-th-missing-element2556/1) | — | — | — | Easy | — | — | — |
| 74 | [Partition Point in the Array](https://www.geeksforgeeks.org/problems/partition-point-in-the-array0004/1) | — | — | — | Easy | — | — | — |
| 75 | [Minimum Element whose N-th Power is Greater than Product](https://www.geeksforgeeks.org/problems/minimum-element-whose-n-th-power-is-greater-than-product-of-an-array4640/1) | — | — | — | Easy | — | — | — |
| 76 | [Find Duplicates in an Array (Limited Range)](https://www.geeksforgeeks.org/problems/find-duplicates-in-an-array/1) | — | — | — | Easy | — | — | — |
| 77 | [Find Distinct Elements](https://www.geeksforgeeks.org/problems/find-distinct-elements--130928/1) | — | — | — | Easy | — | — | — |
| 78 | [Union of Two Sorted Arrays with Distinct Elements](https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays-with-distinct-elements/1) | — | — | — | Easy | — | — | — |
| 79 | [Count the Specials (n/k times occurring)](https://www.geeksforgeeks.org/problems/count-the-specials/1) | — | — | — | Easy | — | — | — |
| 80 | [Find Duplicates Under Given Constraints (Majority in Sorted)](https://www.geeksforgeeks.org/problems/find-duplicates-under-given-constraints0856/1) | — | — | — | Easy | — | — | — |
| 81 | [Find Unique Pair in an Array with Pairs of Numbers](https://www.geeksforgeeks.org/problems/find-unique-pair-in-an-array-with-pairs-of-numbers2425/1) | — | — | — | Easy | — | — | — |
| 82 | [Absolute Distinct Count](https://www.geeksforgeeks.org/problems/absolute-distinct-count5118/1) | — | — | — | Easy | — | — | — |
| 83 | [Count Subsets having Distinct Even Numbers](https://www.geeksforgeeks.org/problems/count-subsets-having-distinct-even-numbers5726/1) | — | — | — | Easy | — | — | — |
| 84 | [Leaders in an Array](https://www.geeksforgeeks.org/problems/leaders-in-an-array-1587115620/1) | — | — | — | Easy | — | — | — |
| 85 | [Product of Array Except Self](https://www.geeksforgeeks.org/problems/product-of-array-element/1) | — | — | — | Easy | — | — | — |
| 86 | [Buildings Receiving Sunlight](https://www.geeksforgeeks.org/problems/buildings-receiving-sunlight3032/1) | — | — | — | Easy | — | — | — |
| 87 | [Unsorted Array (Left Smaller Right Greater)](https://www.geeksforgeeks.org/problems/unsorted-array4925/1) | — | — | — | Easy | — | — | — |
| 88 | [Greater on Right Side](https://www.geeksforgeeks.org/problems/greater-on-right-side4305/1) | — | — | — | Easy | — | — | — |
| 89 | [Bird and Maximum Fruit Gathering](https://www.geeksforgeeks.org/problems/bird-and-maximum-fruit-gathering--170645/1) | — | — | — | Easy | — | — | — |
| 90 | [Balance with Respect to an Array](https://www.geeksforgeeks.org/problems/balance-with-respect-to-an-array5443/1) | — | — | — | Easy | — | — | — |
| 91 | [Total Distance Travelled in a Permutation of 1..n](https://www.geeksforgeeks.org/problems/total-distance-travelled-in-an-array3628/1) | — | — | — | Easy | — | — | — |
| 92 | [Max Consecutive Ones](https://www.geeksforgeeks.org/problems/max-consecutive-one/1) | — | — | — | Easy | — | — | — |
| 93 | [Number of Subarrays of 0s](https://www.geeksforgeeks.org/problems/number-of-subarrays-of-0s--170647/1) | — | — | — | Easy | — | — | — |
| 94 | [Sum of Lengths of Non-Overlapping Subarrays](https://www.geeksforgeeks.org/problems/sum-of-lengths-of-non-overlapping-subarrays2237/1) | — | — | — | Easy | — | — | — |
| 95 | [Find Maximum Sum Strictly Increasing Subarray](https://www.geeksforgeeks.org/problems/find-maximum-sum-strictly-increasing-subarray4443/1) | — | — | — | Easy | — | — | — |
| 96 | [Number of Subarrays whose Minimum and Maximum are Same](https://www.geeksforgeeks.org/problems/number-of-subarrays-whose-minimum-and-maximum-are-same5259/1) | — | — | — | Easy | — | — | — |
| 97 | [Maximum Size of Consecutives (with K Additions)](https://www.geeksforgeeks.org/problems/maximum-size-of-consecutives3154/1) | — | — | — | Easy | — | — | — |
| 98 | [Pairs of Adjacent Elements (count consecutive)](https://www.geeksforgeeks.org/problems/pairs-of-adjacent-elements4814/1) | — | — | — | Easy | — | — | — |
| 99 | [Pairs With Difference K](https://www.geeksforgeeks.org/problems/pairs-with-difference-k1713/1) | — | — | — | Easy | — | — | — |
| 100 | [Pairs with Difference Less than K](https://www.geeksforgeeks.org/problems/pairs-with-difference-less-than-k1348/1) | — | — | — | Easy | — | — | — |
| 101 | [Nth Item Through Sum (Kth in Two Arrays Sums)](https://www.geeksforgeeks.org/problems/nth-item-through-sum3544/1) | — | — | — | Easy | — | — | — |
| 102 | [Pair with Largest Sum Which is Less Than K](https://www.geeksforgeeks.org/problems/pair-with-largest-sum-which-is-less-than-k-in-the-array/1) | — | — | — | Easy | — | — | — |
| 103 | [Finding Pairs (Search Pairs in a String)](https://www.geeksforgeeks.org/problems/finding-pairs2835/1) | — | — | — | Easy | — | — | — |
| 104 | [Maximize Sum After K Negations](https://www.geeksforgeeks.org/problems/maximize-sum-after-k-negations1149/1) | — | — | — | Easy | — | — | — |
| 105 | [Minimum Steps to Make Product Equal to One](https://www.geeksforgeeks.org/problems/minimum-steps-to-make-product-equal-to-one/1) | — | — | — | Easy | — | — | — |
| 106 | [Array Operations (Make Array 0 with Subarray Ops)](https://www.geeksforgeeks.org/problems/array-operations--170648/1) | — | — | — | Easy | — | — | — |
| 107 | [Minimum Increment by K Operations to Make All Equal](https://www.geeksforgeeks.org/problems/minimum-increment-by-k-operations-to-make-all-equal/1) | — | — | — | Easy | — | — | — |
| 108 | [Faulty Wiring and Bulbs](https://www.geeksforgeeks.org/problems/faulty-wiring-and-bulbs2939/1) | — | — | — | Easy | — | — | — |
| 109 | [Equalization of an Array](https://www.geeksforgeeks.org/problems/equalization-of-an-array1656/1) | — | — | — | Easy | — | — | — |
| 110 | [Gifts Gifts Gifts (Distribution According to Preference)](https://www.geeksforgeeks.org/problems/gifts-gifts-gifts1524/1) | — | — | — | Easy | — | — | — |
| 111 | [Minimum Value Product (Replace All with Min Value)](https://www.geeksforgeeks.org/problems/minimum-value-product1814/1) | — | — | — | Easy | — | — | — |
| 112 | [Cross the Hurdles - the Game](https://www.geeksforgeeks.org/problems/cross-the-hurdles-the-game4734/1) | — | — | — | Easy | — | — | — |
| 113 | [Minimum Energy (Minimum Initial Energy to Cross)](https://www.geeksforgeeks.org/problems/minimum-energy1107/1) | — | — | — | Easy | — | — | — |
| 114 | [Decreasing Sequence with K Subtraction](https://www.geeksforgeeks.org/problems/decreasing-sequence2722/1) | — | — | — | Easy | — | — | — |
| 115 | [Stuffs Division (Distribution with i Allocated to arr[i])](https://www.geeksforgeeks.org/problems/stuffs-division5735/1) | — | — | — | Easy | — | — | — |
| 116 | [Drive the Car](https://www.geeksforgeeks.org/problems/drive-the-car2541/1) | — | — | — | Easy | — | — | — |
| 117 | [Minimum Distance Between Two Numbers](https://www.geeksforgeeks.org/problems/minimum-distance-between-two-numbers/1) | — | — | — | Easy | — | — | — |
| 118 | [Maximum in Struct Array (Max Pairwise Computed Value)](https://www.geeksforgeeks.org/problems/maximum-in-struct-array/1) | — | — | — | Easy | — | — | — |
| 119 | [K-Sorted Array (Check k Sorted)](https://www.geeksforgeeks.org/problems/k-sorted-array1610/1) | — | — | — | Easy | — | — | — |
| 120 | [Minimum Absolute Difference Between Adjacent Elements (Circular)](https://www.geeksforgeeks.org/problems/minimum-absloute-difference-between-adjacent-elements-in-a-circular-array-1587115620/1) | — | — | — | Easy | — | — | — |
| 121 | [Find Number of Numbers (Count a Digit in Array)](https://www.geeksforgeeks.org/problems/find-number-of-numbers/1) | — | — | — | Easy | — | — | — |
| 122 | [Play with an Array](https://www.geeksforgeeks.org/problems/play-with-an-array/1) | — | — | — | Easy | — | — | — |
| 123 | [Maximum Number of Zeroes](https://www.geeksforgeeks.org/problems/maximum-number-of-zeroes4048/1) | — | — | — | Easy | — | — | — |
| 124 | [Max Value](https://www.geeksforgeeks.org/problems/max-value1205/1) | — | — | — | Easy | — | — | — |
| 125 | [Missing Ranges of Numbers](https://www.geeksforgeeks.org/problems/missing-ranges-of-numbers1019/1) | — | — | — | Easy | — | — | — |
| 126 | [Digits in a Set (Count the Numbers)](https://www.geeksforgeeks.org/problems/count-the-numbers2359/1) | — | — | — | Easy | — | — | — |
| 127 | [Sum of Distinct Elements (1 to n)](https://www.geeksforgeeks.org/problems/sum-of-distinct-elements-15115/1) | — | — | — | Easy | — | — | — |
| 128 | [K-Modulus Array Element (Values with Equal Remainders)](https://www.geeksforgeeks.org/problems/k-modulus-array-element0255/1) | — | — | — | Easy | — | — | — |
| 129 | [Tracks (Check for Specific Order Around Mid)](https://www.geeksforgeeks.org/problems/tracks0436/1) | — | — | — | Easy | — | — | — |
| 130 | [Powers Game (Count Digit Occurrences in Powers)](https://www.geeksforgeeks.org/problems/powers-game3701/1) | — | — | — | Easy | — | — | — |
| 131 | [Form a Number Divisible by 3 Using Array Digits](https://www.geeksforgeeks.org/problems/form-a-number-divisible-by-3-using-array-digits0717/1) | — | — | — | Easy | — | — | — |
| 132 | [Sum of Two Numbers Represented as Arrays](https://www.geeksforgeeks.org/problems/sum-of-two-numbers-represented-as-arrays3110/1) | — | — | — | Easy | — | — | — |
| 133 | [Find Missing and Repeating](https://www.geeksforgeeks.org/problems/find-missing-and-repeating2512/1) | — | — | — | Easy | — | — | — |
| 134 | [Construct an Array from its Pair-Sum Array](https://www.geeksforgeeks.org/problems/construct-an-array-from-its-pair-sum-array/1) | — | — | — | Easy | — | — | — |
| 135 | [Equal Sums (Equal Sum with Insertion)](https://www.geeksforgeeks.org/problems/equal-sums4801/1) | — | — | — | Easy | — | — | — |

## Medium (103)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Rotate Array](https://www.geeksforgeeks.org/problems/rotate-array-by-n-elements-1587115621/1) | — | — | — | Medium | Amazon, Microsoft, MAQ Software, Codenation | Arrays | [`03. Medium/01. Rotate Array/`](03.%20Medium/01.%20Rotate%20Array/) |
| 2 | [K-th of Two Sorted Arrays](https://www.geeksforgeeks.org/problems/k-th-element-of-two-sorted-array1317/1) | — | — | — | Medium | Flipkart, Microsoft, NPCI | Arrays, Divide and Conquer, Binary Search | [`03. Medium/02. K-th of Two Sorted Arrays/`](03.%20Medium/02.%20K-th%20of%20Two%20Sorted%20Arrays/) |
| 3 | [Reverse Array in Groups](https://www.geeksforgeeks.org/problems/reverse-array-in-groups0255/1) | — | — | — | Medium | Adobe | Arrays | [`03. Medium/03. Reverse Array in Groups/`](03.%20Medium/03.%20Reverse%20Array%20in%20Groups/) |
| 4 | [First and Last in Sorted](https://www.geeksforgeeks.org/problems/first-and-last-occurrences-of-x3116/1) | — | — | — | Medium | Amazon, Google, Microsoft | Arrays, Binary Search | [`03. Medium/04. First and Last in Sorted/`](03.%20Medium/04.%20First%20and%20Last%20in%20Sorted/) |
| 5 | [Rearrange Array Alternately](https://www.geeksforgeeks.org/problems/-rearrange-array-alternately-1587115620/1) | — | — | — | Medium | Zoho | Arrays | [`03. Medium/05. Rearrange Array Alternately/`](03.%20Medium/05.%20Rearrange%20Array%20Alternately/) |
| 6 | [Pythagorean Triplet](https://www.geeksforgeeks.org/problems/pythagorean-triplet3018/1) | — | — | — | Medium | Amazon, Adobe | Arrays | [`03. Medium/06. Pythagorean Triplet/`](03.%20Medium/06.%20Pythagorean%20Triplet/) |
| 7 | [Next Permutation](https://www.geeksforgeeks.org/problems/next-permutation5226/1) | — | — | — | Medium | Infosys, Flipkart, Amazon, Microsoft, FactSet, Hike, MakeMyTrip, Google, Qualcomm, Salesforce | Arrays, permutation, constructive algo | [`03. Medium/07. Next Permutation/`](03.%20Medium/07.%20Next%20Permutation/) |
| 8 | [Stock Buy and Sell – Multiple Transaction Allowed](https://www.geeksforgeeks.org/problems/stock-buy-and-sell2615/1) | — | — | — | Medium | Paytm, Flipkart, Morgan Stanley, Accolite, Amazon, Microsoft, Samsung, D-E-Shaw, Hike, MakeMyTrip, Ola Cabs, Oracle, Walmart, Goldman Sachs, Directi, Intuit, SAP Labs, Quikr, Facebook, Salesforce, Pubmatic, Sapient, Swiggy | Arrays | [`03. Medium/08. Stock Buy and Sell – Multiple Transaction Allowed/`](03.%20Medium/08.%20Stock%20Buy%20and%20Sell%20–%20Multiple%20Transaction%20Allowed/) |
| 9 | [Max Sum Subarray of Non-Negative](https://www.geeksforgeeks.org/problems/maximum-sub-array5443/1) | — | — | — | Medium | Amazon, Microsoft, Intuit | Arrays, Divide and Conquer | [`03. Medium/09. Max Sum Subarray of Non-Negative/`](03.%20Medium/09.%20Max%20Sum%20Subarray%20of%20Non-Negative/) |
| 10 | [Pascal Triangle](https://www.geeksforgeeks.org/problems/pascal-triangle0652/1) | — | — | — | Medium | Amazon, Microsoft, Adobe | Arrays, Recursion | [`03. Medium/10. Pascal Triangle/`](03.%20Medium/10.%20Pascal%20Triangle/) |
| 11 | [Transform Array In-Place](https://www.geeksforgeeks.org/problems/rearrange-an-array-with-o1-extra-space3142/1) | — | — | — | Medium | Amazon | Arrays | [`03. Medium/11. Transform Array In-Place/`](03.%20Medium/11.%20Transform%20Array%20In-Place/) |
| 12 | [Max sum in the configuration](https://www.geeksforgeeks.org/problems/max-sum-in-the-configuration/1) | — | — | — | Medium | Amazon | Arrays, Mathematics | [`03. Medium/12. Max sum in the configuration/`](03.%20Medium/12.%20Max%20sum%20in%20the%20configuration/) |
| 13 | [Max Product Subset](https://www.geeksforgeeks.org/problems/maximum-product-subset-of-an-array/1) | — | — | — | Medium | — | Arrays | [`03. Medium/13. Max Product Subset/`](03.%20Medium/13.%20Max%20Product%20Subset/) |
| 14 | [Count Subarrays with given XOR](https://www.geeksforgeeks.org/problems/count-subarray-with-given-xor/1) | — | — | — | Medium | — | Arrays, Map, Bit Magic | [`03. Medium/14. Count Subarrays with given XOR/`](03.%20Medium/14.%20Count%20Subarrays%20with%20given%20XOR/) |
| 15 | [Product Pair](https://www.geeksforgeeks.org/problems/equal-to-product3836/1) | — | — | — | Medium | Amazon, Visa | Arrays | [`03. Medium/15. Product Pair/`](03.%20Medium/15.%20Product%20Pair/) |
| 16 | [K Closest in a Sorted Array](https://www.geeksforgeeks.org/problems/k-closest-elements3619/1) | — | — | — | Medium | Amazon, OYO Rooms | Arrays, Binary Search, STL, Priority Queue | [`03. Medium/16. K Closest in a Sorted Array/`](03.%20Medium/16.%20K%20Closest%20in%20a%20Sorted%20Array/) |
| 17 | [Max Occured in n Ranges](https://www.geeksforgeeks.org/problems/maximum-occured-integer4602/1) | — | — | — | Medium | Amazon | Arrays, Mathematics | [`03. Medium/17. Max Occured in n Ranges/`](03.%20Medium/17.%20Max%20Occured%20in%20n%20Ranges/) |
| 18 | [Sorted Subsequence of Size 3](https://www.geeksforgeeks.org/problems/sorted-subsequence-of-size-3/1) | — | — | — | Medium | Amazon, FactSet, Walmart | Arrays | [`03. Medium/18. Sorted Subsequence of Size 3/`](03.%20Medium/18.%20Sorted%20Subsequence%20of%20Size%203/) |
| 19 | [Not a Subset Sum](https://www.geeksforgeeks.org/problems/smallest-number-subset1220/1) | — | — | — | Medium | Salesforce | Arrays | [`03. Medium/19. Not a Subset Sum/`](03.%20Medium/19.%20Not%20a%20Subset%20Sum/) |
| 20 | [Max Sum Path in Two Arrays](https://www.geeksforgeeks.org/problems/max-sum-path-in-two-arrays/1) | — | — | — | Medium | Amazon | Arrays | [`03. Medium/20. Max Sum Path in Two Arrays/`](03.%20Medium/20.%20Max%20Sum%20Path%20in%20Two%20Arrays/) |
| 21 | [Sum of Middle of two sorted arrays](https://www.geeksforgeeks.org/problems/sum-of-middle-elements-of-two-sorted-arrays2305/1) | — | — | — | Medium | Amazon, D-E-Shaw | Arrays, Divide and Conquer, Binary Search | [`03. Medium/21. Sum of Middle of two sorted arrays/`](03.%20Medium/21.%20Sum%20of%20Middle%20of%20two%20sorted%20arrays/) |
| 22 | [Flip to Maximize 1s](https://www.geeksforgeeks.org/problems/flip-bits0240/1) | — | — | — | Medium | Amazon | Arrays | [`03. Medium/22. Flip to Maximize 1s/`](03.%20Medium/22.%20Flip%20to%20Maximize%201s/) |
| 23 | [Sum of 2 Primes](https://www.geeksforgeeks.org/problems/sum-of-prime4751/1) | — | — | — | Medium | Zoho, Yahoo | Number Theory, constructive algo, Prime Number, Arrays | [`03. Medium/23. Sum of 2 Primes/`](03.%20Medium/23.%20Sum%20of%202%20Primes/) |
| 24 | [Maximum Triplet product](https://www.geeksforgeeks.org/problems/maximum-triplet-product--170647/1) | — | — | — | Medium | VMWare, Amazon, Snapdeal, Flipkart | Arrays, Mathematics | [`03. Medium/24. Maximum Triplet product/`](03.%20Medium/24.%20Maximum%20Triplet%20product/) |
| 25 | [Sum of Pairwise Bit Differences](https://www.geeksforgeeks.org/problems/sum-of-bit-differences2937/1) | — | — | — | Medium | Google, Microsoft | Arrays, Bit Magic | [`03. Medium/25. Sum of Pairwise Bit Differences/`](03.%20Medium/25.%20Sum%20of%20Pairwise%20Bit%20Differences/) |
| 26 | [Unique Number III](https://www.geeksforgeeks.org/problems/find-element-occuring-once-when-all-other-are-present-thrice/1) | — | — | — | Medium | Google, NPCI | Arrays, Mathematics, Bit Magic | [`03. Medium/26. Unique Number III/`](03.%20Medium/26.%20Unique%20Number%20III/) |
| 27 | [Longest Subsequence with Adjacent Diff as 1](https://www.geeksforgeeks.org/problems/longest-sub-sequence-such-that-difference-between-adjacents-is-one2558/1) | — | — | — | Medium | Flipkart | Arrays | [`03. Medium/27. Longest Subsequence with Adjacent Diff as 1/`](03.%20Medium/27.%20Longest%20Subsequence%20with%20Adjacent%20Diff%20as%201/) |
| 28 | [Koko Eating Bananas](https://www.geeksforgeeks.org/problems/koko-eating-bananas/1) | — | — | — | Medium | Bloomberg, Amazon, Microsoft, Walmart, Adobe, Arcesium, Uber, NPCI | Binary Search, Arrays | [`03. Medium/28. Koko Eating Bananas/`](03.%20Medium/28.%20Koko%20Eating%20Bananas/) |
| 29 | [Sum of XOR of all pairs](https://www.geeksforgeeks.org/problems/sum-of-xor-of-all-pairs0723/1) | — | — | — | Medium | — | Arrays, Bit Magic | [`03. Medium/29. Sum of XOR of all pairs/`](03.%20Medium/29.%20Sum%20of%20XOR%20of%20all%20pairs/) |
| 30 | [Kth Missing Positive Number in a Sorted Array](https://www.geeksforgeeks.org/problems/kth-missing-positive-number-in-a-sorted-array/1) | — | — | — | Medium | NPCI | Binary Search, Arrays | [`03. Medium/30. Kth Missing Positive Number in a Sorted Array/`](03.%20Medium/30.%20Kth%20Missing%20Positive%20Number%20in%20a%20Sorted%20Array/) |
| 31 | [Rotate and delete](https://www.geeksforgeeks.org/problems/rotate-and-delete-1587115621/1) | — | — | — | Medium | — | Arrays | [`03. Medium/31. Rotate and delete/`](03.%20Medium/31.%20Rotate%20and%20delete/) |
| 32 | [Shuffle Integers](https://www.geeksforgeeks.org/problems/shuffle-integers2401/1) | — | — | — | Medium | Amazon, OYO Rooms | Arrays, Recursion | [`03. Medium/32. Shuffle Integers/`](03.%20Medium/32.%20Shuffle%20Integers/) |
| 33 | [Sum of Subarrays](https://www.geeksforgeeks.org/problems/sum-of-subarrays2229/1) | — | — | — | Medium | — | Arrays | [`03. Medium/33. Sum of Subarrays/`](03.%20Medium/33.%20Sum%20of%20Subarrays/) |
| 34 | [Minimum to Add for Prime Array Sum](https://www.geeksforgeeks.org/problems/transform-to-prime4635/1) | — | — | — | Medium | — | Arrays, Prime Number, sieve | [`03. Medium/34. Minimum to Add for Prime Array Sum/`](03.%20Medium/34.%20Minimum%20to%20Add%20for%20Prime%20Array%20Sum/) |
| 35 | [Construct List using XOR Queries](https://www.geeksforgeeks.org/problems/construct-list-using-given-q-xor-queries/1) | — | — | — | Medium | Amazon, Google | Arrays, Bit Magic | [`03. Medium/35. Construct List using XOR Queries/`](03.%20Medium/35.%20Construct%20List%20using%20XOR%20Queries/) |
| 36 | [Buy Maximum Stocks](https://www.geeksforgeeks.org/problems/buy-maximum-stocks-if-i-stocks-can-be-bought-on-i-th-day/1) | — | — | — | Medium | — | Arrays | [`03. Medium/36. Buy Maximum Stocks/`](03.%20Medium/36.%20Buy%20Maximum%20Stocks/) |
| 37 | [Top k Frequent in Stream](https://www.geeksforgeeks.org/problems/top-k-numbers3425/1) | — | — | — | Medium | Accolite, Amazon, Media.net | Arrays, Map, Priority Queue | [`03. Medium/37. Top k Frequent in Stream/`](03.%20Medium/37.%20Top%20k%20Frequent%20in%20Stream/) |
| 38 | [Array Elements Divisible by Any Others](https://www.geeksforgeeks.org/problems/count-special-numbers--170647/1) | — | — | — | Medium | Intuit, NPCI | Arrays, Mathematics, sieve | [`03. Medium/38. Array Elements Divisible by Any Others/`](03.%20Medium/38.%20Array%20Elements%20Divisible%20by%20Any%20Others/) |
| 39 | [K-th Largest Sum Contiguous Subarray](https://www.geeksforgeeks.org/problems/k-th-largest-sum-contiguous-subarray/1) | — | — | — | Medium | — | Arrays, Priority Queue | [`03. Medium/39. K-th Largest Sum Contiguous Subarray/`](03.%20Medium/39.%20K-th%20Largest%20Sum%20Contiguous%20Subarray/) |
| 40 | [Maximum Subset XOR](https://www.geeksforgeeks.org/problems/maximum-subset-xor/1) | — | — | — | Medium | Microsoft | Arrays, Bit Magic | [`03. Medium/40. Maximum Subset XOR/`](03.%20Medium/40.%20Maximum%20Subset%20XOR/) |
| 41 | [Search in Rotated Array 2](https://www.geeksforgeeks.org/problems/search-in-rotated-array-2/1) | — | — | — | Medium | Adobe, Bloomberg, Yahoo, Uber | Binary Search, Arrays | [`03. Medium/41. Search in Rotated Array 2/`](03.%20Medium/41.%20Search%20in%20Rotated%20Array%202/) |
| 42 | [Longest Subarray of Evens and Odds](https://www.geeksforgeeks.org/problems/longest-subarray-of-evens-and-odds/1) | — | — | — | Medium | — | Arrays | [`03. Medium/42. Longest Subarray of Evens and Odds/`](03.%20Medium/42.%20Longest%20Subarray%20of%20Evens%20and%20Odds/) |
| 43 | [Minimum Days to Make m Bouquets](https://www.geeksforgeeks.org/problems/minimum-days-to-make-m-bouquets/1) | — | — | — | Medium | Bloomberg, Amazon, Microsoft, Google, Flipkart, NPCI | Binary Search, Arrays | [`03. Medium/43. Minimum Days to Make m Bouquets/`](03.%20Medium/43.%20Minimum%20Days%20to%20Make%20m%20Bouquets/) |
| 44 | [Capacity To Ship Packages Within d Days](https://www.geeksforgeeks.org/problems/capacity-to-ship-packages-within-d-days/1) | — | — | — | Medium | Amazon, D-E-Shaw | Arrays, Binary Search | [`03. Medium/44. Capacity To Ship Packages Within d Days/`](03.%20Medium/44.%20Capacity%20To%20Ship%20Packages%20Within%20d%20Days/) |
| 45 | [Factorial of Array under Modulo](https://www.geeksforgeeks.org/problems/large-factorial4721/1) | — | — | — | Medium | — | Arrays, Mathematics | [`03. Medium/45. Factorial of Array under Modulo/`](03.%20Medium/45.%20Factorial%20of%20Array%20under%20Modulo/) |
| 46 | [Smallest Divisor](https://www.geeksforgeeks.org/problems/smallest-divisor/1) | — | — | — | Medium | — | Binary Search, Arrays | [`03. Medium/46. Smallest Divisor/`](03.%20Medium/46.%20Smallest%20Divisor/) |
| 47 | [Min Swaps to Group 1s](https://www.geeksforgeeks.org/problems/minimum-swaps-required-to-group-all-1s-together2451/1) | — | — | — | Medium | Adobe | Arrays | [`03. Medium/47. Min Swaps to Group 1s/`](03.%20Medium/47.%20Min%20Swaps%20to%20Group%201s/) |
| 48 | [Number to Words](https://www.geeksforgeeks.org/problems/number-to-words0335/1) | — | — | — | Medium | Zoho, Amazon, Microsoft, Oracle | Arrays | [`03. Medium/48. Number to Words/`](03.%20Medium/48.%20Number%20to%20Words/) |
| 49 | [Smaller Sum for All](https://www.geeksforgeeks.org/problems/smaller-sum--170647/1) | — | — | — | Medium | — | Arrays, Binary Search | [`03. Medium/49. Smaller Sum for All/`](03.%20Medium/49.%20Smaller%20Sum%20for%20All/) |
| 50 | [Composite and  Prime Queries](https://www.geeksforgeeks.org/problems/composite-and-prime0359/1) | — | — | — | Medium | — | Prime Number, Arrays, sieve | [`03. Medium/50. Composite and Prime Queries/`](03.%20Medium/50.%20Composite%20and%20Prime%20Queries/) |
| 51 | [Maximum Identical Bowls](https://www.geeksforgeeks.org/problems/maximum-identical-bowls--170647/1) | — | — | — | Medium | — | Arrays | [`03. Medium/51. Maximum Identical Bowls/`](03.%20Medium/51.%20Maximum%20Identical%20Bowls/) |
| 52 | [Longest Bitonic Subarray](https://www.geeksforgeeks.org/problems/maximum-length-bitonic-subarray5730/1) | — | — | — | Medium | Microsoft | Arrays | [`03. Medium/52. Longest Bitonic Subarray/`](03.%20Medium/52.%20Longest%20Bitonic%20Subarray/) |
| 53 | [Minimum XOR with given set bits](https://www.geeksforgeeks.org/problems/minimum-x-xor-a--170645/1) | — | — | — | Medium | Adobe, IBM | Arrays, Bit Magic | [`03. Medium/53. Minimum XOR with given set bits/`](03.%20Medium/53.%20Minimum%20XOR%20with%20given%20set%20bits/) |
| 54 | [Equalize the Towers](https://www.geeksforgeeks.org/problems/equalize-the-towers2804/1) | — | — | — | Medium | — | Arrays, Binary Search | [`03. Medium/54. Equalize the Towers/`](03.%20Medium/54.%20Equalize%20the%20Towers/) |
| 55 | [Count Sorted Subsequences of Size 3](https://www.geeksforgeeks.org/problems/magic-triplets4003/1) | — | — | — | Medium | D-E-Shaw | Arrays | [`03. Medium/55. Count Sorted Subsequences of Size 3/`](03.%20Medium/55.%20Count%20Sorted%20Subsequences%20of%20Size%203/) |
| 56 | [Max Diff Elements and Indexes](https://www.geeksforgeeks.org/problems/maximum-value-of-difference-of-a-pair-of-elements-and-their-index/1) | — | — | — | Medium | Microsoft | Arrays, Mathematics | [`03. Medium/56. Max Diff Elements and Indexes/`](03.%20Medium/56.%20Max%20Diff%20Elements%20and%20Indexes/) |
| 57 | [Ways to Split into 2 with Same XOR](https://www.geeksforgeeks.org/problems/split-the-array0238/1) | — | — | — | Medium | — | Arrays, Bit Magic | [`03. Medium/57. Ways to Split into 2 with Same XOR/`](03.%20Medium/57.%20Ways%20to%20Split%20into%202%20with%20Same%20XOR/) |
| 58 | [Make Arrays Equal with Min Operations](https://www.geeksforgeeks.org/problems/unequal-arrays--170647/1) | — | — | — | Medium | — | Arrays, logical-thinking | [`03. Medium/58. Make Arrays Equal with Min Operations/`](03.%20Medium/58.%20Make%20Arrays%20Equal%20with%20Min%20Operations/) |
| 59 | [Mountain Subarray Queries](https://www.geeksforgeeks.org/problems/mountain-subarray-problem/1) | — | — | — | Medium | Amazon | Arrays | [`03. Medium/59. Mountain Subarray Queries/`](03.%20Medium/59.%20Mountain%20Subarray%20Queries/) |
| 60 | [Farthest Smaller Right](https://www.geeksforgeeks.org/problems/farthest-smaller-right/1) | — | — | — | Medium | NPCI | Binary Search, Arrays | [`03. Medium/60. Farthest Smaller Right/`](03.%20Medium/60.%20Farthest%20Smaller%20Right/) |
| 61 | [Distinct Difference](https://www.geeksforgeeks.org/problems/distinct-difference--170647/1) | — | — | — | Medium | — | Set, Arrays, Map | [`03. Medium/61. Distinct Difference/`](03.%20Medium/61.%20Distinct%20Difference/) |
| 62 | [Update Queries](https://www.geeksforgeeks.org/problems/update-queries--170647/1) | — | — | — | Medium | — | Arrays, Bit Magic | [`03. Medium/62. Update Queries/`](03.%20Medium/62.%20Update%20Queries/) |
| 63 | [Minimum Increment or Double Operations to Convert](https://www.geeksforgeeks.org/problems/minimum-steps-to-get-desired-array5519/1) | — | — | — | Medium | — | Arrays | [`03. Medium/63. Minimum Increment or Double Operations to Convert/`](03.%20Medium/63.%20Minimum%20Increment%20or%20Double%20Operations%20to%20Convert/) |
| 64 | [Tic Tac Toe](https://www.geeksforgeeks.org/problems/tic-tac-toe2412/1) | — | — | — | Medium | Flipkart, Accolite, Amazon, Microsoft | Arrays | [`03. Medium/64. Tic Tac Toe/`](03.%20Medium/64.%20Tic%20Tac%20Toe/) |
| 65 | [Smallest Non-Zero Number](https://www.geeksforgeeks.org/problems/find-smallest-non-zero-number4510/1) | — | — | — | Medium | — | Arrays, Binary Search | [`03. Medium/65. Smallest Non-Zero Number/`](03.%20Medium/65.%20Smallest%20Non-Zero%20Number/) |
| 66 | [Min Product Subset](https://www.geeksforgeeks.org/problems/max-and-min-products3347/1) | — | — | — | Medium | — | Arrays | [`03. Medium/66. Min Product Subset/`](03.%20Medium/66.%20Min%20Product%20Subset/) |
| 67 | [Kth Smallest Pairwise Difference](https://www.geeksforgeeks.org/problems/smallest-absolute-difference4320/1) | — | — | — | Medium | — | Arrays | [`03. Medium/67. Kth Smallest Pairwise Difference/`](03.%20Medium/67.%20Kth%20Smallest%20Pairwise%20Difference/) |
| 68 | [Max Product Subsequence of Size K](https://www.geeksforgeeks.org/problems/maximum-product4633/1) | — | — | — | Medium | — | Arrays | [`03. Medium/68. Max Product Subsequence of Size K/`](03.%20Medium/68.%20Max%20Product%20Subsequence%20of%20Size%20K/) |
| 69 | [Maximum GCD of K Partition Sums](https://www.geeksforgeeks.org/problems/gcd-array--170645/1) | — | — | — | Medium | — | Arrays, Mathematics | [`03. Medium/69. Maximum GCD of K Partition Sums/`](03.%20Medium/69.%20Maximum%20GCD%20of%20K%20Partition%20Sums/) |
| 70 | [Count X in Range of a Sorted Array](https://www.geeksforgeeks.org/problems/count-x-in-range-of-a-sorted-array/1) | — | — | — | Medium | — | Binary Search, Arrays | [`03. Medium/70. Count X in Range of a Sorted Array/`](03.%20Medium/70.%20Count%20X%20in%20Range%20of%20a%20Sorted%20Array/) |
| 71 | [Count elements less than or equal to k in a sorted rotated array](https://www.geeksforgeeks.org/problems/count-elements-less-than-or-equal-to-k-in-a-sorted-rotated-array/1) | — | — | — | Medium | NPCI | Binary Search, Arrays | [`03. Medium/71. Count elements less than or equal to k in a sorted rotated array/`](03.%20Medium/71.%20Count%20elements%20less%20than%20or%20equal%20to%20k%20in%20a%20sorted%20rotated%20array/) |
| 72 | [Subsets Multiple of 3](https://www.geeksforgeeks.org/problems/possible-groups2013/1) | — | — | — | Medium | Amazon | Arrays | [`03. Medium/72. Subsets Multiple of 3/`](03.%20Medium/72.%20Subsets%20Multiple%20of%203/) |
| 73 | [Farthest Smaller on Right](https://www.geeksforgeeks.org/problems/farthest-number--170636/1) | — | — | — | Medium | Amazon | Arrays, Binary Search | [`03. Medium/73. Farthest Smaller on Right/`](03.%20Medium/73.%20Farthest%20Smaller%20on%20Right/) |
| 74 | [Min Removals to Make Max <= 2*Min](https://www.geeksforgeeks.org/problems/remove-minimum-elements4612/1) | — | — | — | Medium | Amazon | Arrays | [`03. Medium/74. Min Removals to Make Max = 2Min/`](03.%20Medium/74.%20Min%20Removals%20to%20Make%20Max%20=%202Min/) |
| 75 | [Fill 1's With Changes to Adjacent](https://www.geeksforgeeks.org/problems/fill-array-by-1s0920/1) | — | — | — | Medium | Amazon | Arrays, Mathematics | [`03. Medium/75. Fill 1's With Changes to Adjacent/`](03.%20Medium/75.%20Fill%201's%20With%20Changes%20to%20Adjacent/) |
| 76 | [Subset with Pair Sums Not Divisible by K](https://www.geeksforgeeks.org/problems/subset-with-no-pair-sum-divisible-by-k1105/1) | — | — | — | Medium | — | Arrays, Modular Arithmetic | [`03. Medium/76. Subset with Pair Sums Not Divisible by K/`](03.%20Medium/76.%20Subset%20with%20Pair%20Sums%20Not%20Divisible%20by%20K/) |
| 77 | [Count Divisors of Array Product](https://www.geeksforgeeks.org/problems/count-divisors-of-product-of-array-elements0244/1) | — | — | — | Medium | — | Arrays, Prime Number | [`03. Medium/77. Count Divisors of Array Product/`](03.%20Medium/77.%20Count%20Divisors%20of%20Array%20Product/) |
| 78 | [Minimum Picks for K Sock Pairs](https://www.geeksforgeeks.org/problems/number-of-minimum-picks-to-get-k-pairs-of-socks-from-a-drawer--141631/1) | — | — | — | Medium | Amazon | Arrays | [`03. Medium/78. Minimum Picks for K Sock Pairs/`](03.%20Medium/78.%20Minimum%20Picks%20for%20K%20Sock%20Pairs/) |
| 79 | [Max Product Sorted Subsequence of Size 3](https://www.geeksforgeeks.org/problems/maximum-product-of-increasing-subsequence-of-size-32027/1) | — | — | — | Medium | — | Set, Arrays | [`03. Medium/79. Max Product Sorted Subsequence of Size 3/`](03.%20Medium/79.%20Max%20Product%20Sorted%20Subsequence%20of%20Size%203/) |
| 80 | [Minimum Operations to Make Array Sorted](https://www.geeksforgeeks.org/problems/minimum-incrementdecrement-to-make-array-non-increasing--170637/1) | — | — | — | Medium | Amazon | Arrays, Priority Queue | [`03. Medium/80. Minimum Operations to Make Array Sorted/`](03.%20Medium/80.%20Minimum%20Operations%20to%20Make%20Array%20Sorted/) |
| 81 | [Queries for Counts of Multiples](https://www.geeksforgeeks.org/problems/queries-for-counts-of-multiples-in-an-array4028/1) | — | — | — | Medium | — | Arrays, Mathematics, sieve | [`03. Medium/81. Queries for Counts of Multiples/`](03.%20Medium/81.%20Queries%20for%20Counts%20of%20Multiples/) |
| 82 | [Subarrays Having Even Sum](https://www.geeksforgeeks.org/problems/find-the-number-of-sub-arrays-having-even-sum1533/1) | — | — | — | Medium | — | Arrays | [`03. Medium/82. Subarrays Having Even Sum/`](03.%20Medium/82.%20Subarrays%20Having%20Even%20Sum/) |
| 83 | [Distribute n Candies Among k People](https://www.geeksforgeeks.org/problems/distribute-n-candies/1) | — | — | — | Medium | Microsoft | Arrays, Mathematics, Binary Search | [`03. Medium/83. Distribute n Candies Among k People/`](03.%20Medium/83.%20Distribute%20n%20Candies%20Among%20k%20People/) |
| 84 | [Pairs with Given Modulo Value](https://www.geeksforgeeks.org/problems/mr-modulo-and-pairs5610/1) | — | — | — | Medium | — | Arrays, Modular Arithmetic | [`03. Medium/84. Pairs with Given Modulo Value/`](03.%20Medium/84.%20Pairs%20with%20Given%20Modulo%20Value/) |
| 85 | [Pairs with Sum Less Than Product](https://www.geeksforgeeks.org/problems/pair-array-product-sum4912/1) | — | — | — | Medium | — | Arrays | [`03. Medium/85. Pairs with Sum Less Than Product/`](03.%20Medium/85.%20Pairs%20with%20Sum%20Less%20Than%20Product/) |
| 86 | [4 Sum – Count Quadruplets with Sum](https://www.geeksforgeeks.org/problems/count-quadruplets-with-given-sum/1) | — | — | — | Medium | — | Arrays, Map | [`03. Medium/86. 4 Sum – Count Quadruplets with Sum/`](03.%20Medium/86.%204%20Sum%20–%20Count%20Quadruplets%20with%20Sum/) |
| 87 | [Sum of Permutations of Distinct Digits](https://www.geeksforgeeks.org/problems/sum-of-permutations/1) | — | — | — | Medium | — | Arrays, Modular Arithmetic | [`03. Medium/87. Sum of Permutations of Distinct Digits/`](03.%20Medium/87.%20Sum%20of%20Permutations%20of%20Distinct%20Digits/) |
| 88 | [Maximum Bitonic Subarray Sum](https://www.geeksforgeeks.org/problems/maximum-bitonic-subarray-sum5616/1) | — | — | — | Medium | — | Arrays | [`03. Medium/88. Maximum Bitonic Subarray Sum/`](03.%20Medium/88.%20Maximum%20Bitonic%20Subarray%20Sum/) |
| 89 | [Smallest Number from Power Digits](https://www.geeksforgeeks.org/problems/the-tiny-miny2541/1) | — | — | — | Medium | — | Arrays | [`03. Medium/89. Smallest Number from Power Digits/`](03.%20Medium/89.%20Smallest%20Number%20from%20Power%20Digits/) |
| 90 | [Leading Digit and Exponent of Factorial](https://www.geeksforgeeks.org/problems/large-factorials2539/1) | — | — | — | Medium | — | Arrays, factorial | [`03. Medium/90. Leading Digit and Exponent of Factorial/`](03.%20Medium/90.%20Leading%20Digit%20and%20Exponent%20of%20Factorial/) |
| 91 | [Local Min and Max Sequence Ordering](https://www.geeksforgeeks.org/problems/track-the-trail/1) | — | — | — | Medium | NPCI | Arrays | [`03. Medium/91. Local Min and Max Sequence Ordering/`](03.%20Medium/91.%20Local%20Min%20and%20Max%20Sequence%20Ordering/) |
| 92 | [Max Modulo Pair in an Array](https://www.geeksforgeeks.org/problems/mr-modulo-and-arrays2827/1) | — | — | — | Medium | — | Arrays, Binary Search | [`03. Medium/92. Max Modulo Pair in an Array/`](03.%20Medium/92.%20Max%20Modulo%20Pair%20in%20an%20Array/) |
| 93 | [Index Element After Rotations](https://www.geeksforgeeks.org/problems/find-the-element-at-given-index4630/1) | — | — | — | Medium | — | Arrays | [`03. Medium/93. Index Element After Rotations/`](03.%20Medium/93.%20Index%20Element%20After%20Rotations/) |
| 94 | [Subsets with given Max Diff](https://www.geeksforgeeks.org/problems/count-number4832/1) | — | — | — | Medium | — | Arrays | [`03. Medium/94. Subsets with given Max Diff/`](03.%20Medium/94.%20Subsets%20with%20given%20Max%20Diff/) |
| 95 | [Total Hamming Distance](https://www.geeksforgeeks.org/problems/total-hamming-distance/1) | — | — | — | Medium | Microsoft, NPCI | Bit Magic, Arrays | [`03. Medium/95. Total Hamming Distance/`](03.%20Medium/95.%20Total%20Hamming%20Distance/) |
| 96 | [Sum of subset differences](https://www.geeksforgeeks.org/problems/sum-of-subset-differences/1) | — | — | — | Medium | — | Arrays | [`03. Medium/96. Sum of subset differences/`](03.%20Medium/96.%20Sum%20of%20subset%20differences/) |
| 97 | [Values Present in At Least K Ranges](https://www.geeksforgeeks.org/problems/sick-pasha0323/1) | — | — | — | Medium | — | Arrays | [`03. Medium/97. Values Present in At Least K Ranges/`](03.%20Medium/97.%20Values%20Present%20in%20At%20Least%20K%20Ranges/) |
| 98 | [Longest Geometric Progression](https://www.geeksforgeeks.org/problems/longest-geometric-progression0131/1) | — | — | — | Medium | — | Misc, Mathematics, Arrays | [`03. Medium/98. Longest Geometric Progression/`](03.%20Medium/98.%20Longest%20Geometric%20Progression/) |
| 99 | [Minimum Platforms 2](https://www.geeksforgeeks.org/problems/minimum-platforms-2--170647/1) | — | — | — | Medium | — | Arrays | [`03. Medium/99. Minimum Platforms 2/`](03.%20Medium/99.%20Minimum%20Platforms%202/) |
| 100 | [Subarray Inversions](https://www.geeksforgeeks.org/problems/subarray-inversions0512/1) | — | — | — | Medium | — | Arrays, Advanced Data Structure | [`03. Medium/100. Subarray Inversions/`](03.%20Medium/100.%20Subarray%20Inversions/) |
| 101 | [Pairs from Distict Element Subarrays](https://www.geeksforgeeks.org/problems/sub-array-pairs5530/1) | — | — | — | Medium | — | Arrays | [`03. Medium/101. Pairs from Distict Element Subarrays/`](03.%20Medium/101.%20Pairs%20from%20Distict%20Element%20Subarrays/) |
| 102 | [Rubik's Cube](https://www.geeksforgeeks.org/problems/rubiks-cube4626/1) | — | — | — | Medium | Ola Cabs | Arrays, constructive algo | [`03. Medium/102. Rubik's Cube/`](03.%20Medium/102.%20Rubik's%20Cube/) |
| 103 | [Successful Binary Searches Irrespective of Pivot](https://www.geeksforgeeks.org/problems/count-always-found/1) | — | — | — | Medium | — | constructive algo, Arrays | [`03. Medium/103. Successful Binary Searches Irrespective of Pivot/`](03.%20Medium/103.%20Successful%20Binary%20Searches%20Irrespective%20of%20Pivot/) |

## Hard (10)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Max Circular Subarray Sum](https://www.geeksforgeeks.org/problems/max-circular-subarray-sum-1587115620/1) | — | — | — | Hard | Amazon, Microsoft | Arrays, Kadane | [`04. Hard/01. Max Circular Subarray Sum/`](04.%20Hard/01.%20Max%20Circular%20Subarray%20Sum/) |
| 2 | [Median of 2 Sorted Arrays of Different Sizes](https://www.geeksforgeeks.org/problems/median-of-2-sorted-arrays-of-different-sizes/1) | — | — | — | Hard | Amazon, Microsoft, Samsung, Google, NPCI | Arrays, Binary Search | [`04. Hard/02. Median of 2 Sorted Arrays of Different Sizes/`](04.%20Hard/02.%20Median%20of%202%20Sorted%20Arrays%20of%20Different%20Sizes/) |
| 3 | [Minimize Max Distance of Adjacent Gas Stations](https://www.geeksforgeeks.org/problems/minimize-max-distance-to-gas-station/1) | — | — | — | Hard | — | Binary Search, Mathematics, Arrays | [`04. Hard/03. Minimize Max Distance of Adjacent Gas Stations/`](04.%20Hard/03.%20Minimize%20Max%20Distance%20of%20Adjacent%20Gas%20Stations/) |
| 4 | [Next Smallest Palindrome](https://www.geeksforgeeks.org/problems/next-smallest-palindrome4740/1) | — | — | — | Hard | Flipkart, Amazon, Microsoft, OYO Rooms, Adobe, Media.net | Arrays | [`04. Hard/04. Next Smallest Palindrome/`](04.%20Hard/04.%20Next%20Smallest%20Palindrome/) |
| 5 | [Split Array Largest Sum](https://www.geeksforgeeks.org/problems/split-array-largest-sum--141634/1) | — | — | — | Hard | Google | Arrays, Binary Search | [`04. Hard/05. Split Array Largest Sum/`](04.%20Hard/05.%20Split%20Array%20Largest%20Sum/) |
| 6 | [Count Pairs with i * arr[i] > j * arr[j]](https://www.geeksforgeeks.org/problems/count-pairs-in-an-array4145/1) | — | — | — | Hard | — | Arrays, Merge Sort | [`04. Hard/06. Count Pairs with i arr[i] j arr[j]/`](04.%20Hard/06.%20Count%20Pairs%20with%20i%20arr[i]%20j%20arr[j]/) |
| 7 | [Count Subarrays with Equal Occurrences of Two](https://www.geeksforgeeks.org/problems/sub-arrays-with-equal-number-of-occurences3901/1) | — | — | — | Hard | — | Arrays, STL | [`04. Hard/07. Count Subarrays with Equal Occurrences of Two/`](04.%20Hard/07.%20Count%20Subarrays%20with%20Equal%20Occurrences%20of%20Two/) |
| 8 | [Cake Distribution Problem](https://www.geeksforgeeks.org/problems/cake-distribution-problem--170647/1) | — | — | — | Hard | — | Binary Search, Arrays | [`04. Hard/08. Cake Distribution Problem/`](04.%20Hard/08.%20Cake%20Distribution%20Problem/) |
| 9 | [Subset Count with Product Less Than k](https://www.geeksforgeeks.org/problems/number-of-subsets-with-product-less-than-k/1) | — | — | — | Hard | Morgan Stanley, Amazon | Arrays, subset | [`04. Hard/09. Subset Count with Product Less Than k/`](04.%20Hard/09.%20Subset%20Count%20with%20Product%20Less%20Than%20k/) |
| 10 | [Median of 2 Sorted Arrays of Same Size](https://www.geeksforgeeks.org/problems/median-of-2-sorted-arrays-of-same-size/1) | — | — | — | Hard | Amazon, Microsoft, Samsung, Google | Binary Search, Arrays | [`04. Hard/10. Median of 2 Sorted Arrays of Same Size/`](04.%20Hard/10.%20Median%20of%202%20Sorted%20Arrays%20of%20Same%20Size/) |
