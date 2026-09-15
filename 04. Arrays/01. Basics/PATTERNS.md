# Arrays — Basics: Patterns

The 56 problems in this folder are simple individually, but they repeat a small set of core ideas over and over. Grouping them this way makes it easier to recognize the underlying technique the next time a similar problem shows up, instead of treating each one as a one-off.

## Pattern 1: Single Pass Linear Scan / Aggregation

The most fundamental pattern: walk the array once (sometimes twice) tracking a running value — max, min, sum, count — without extra data structures. No sorting, no hashing, just an accumulator updated as you go.

| # | Problem | Link |
|---|---|---|
| 1 | [Largest in Array](https://www.geeksforgeeks.org/problems/largest-element-in-array4009/1) | [`01. Largest in Array/`](01.%20Largest%20in%20Array/) |
| 2 | [Min and Max in Array](https://www.geeksforgeeks.org/problems/find-minimum-and-maximum-element-in-an-array4428/1) | [`02. Min and Max in Array/`](02.%20Min%20and%20Max%20in%20Array/) |
| 3 | [Sum of Array](https://www.geeksforgeeks.org/problems/sum-all-array-elements/1) | [`04. Sum of Array/`](04.%20Sum%20of%20Array/) |
| 4 | [Count Odd and Even](https://www.geeksforgeeks.org/problems/count-odd-even/1) | [`10. Count Odd and Even/`](10.%20Count%20Odd%20and%20Even/) |
| 5 | [Strongest Neighbour](https://www.geeksforgeeks.org/problems/strongest-neighbour/1) | [`22. Strongest Neighbour/`](22.%20Strongest%20Neighbour/) |
| 6 | [Type of array](https://www.geeksforgeeks.org/problems/type-of-array4605/1) | [`29. Type of array/`](29.%20Type%20of%20array/) |
| 7 | [Two Max Adjacent in an Array](https://www.geeksforgeeks.org/problems/why-is-melody-so-chocolaty0446/1) | [`46. Two Max Adjacent in an Array/`](46.%20Two%20Max%20Adjacent%20in%20an%20Array/) |
| 8 | [Different Adjacent Elements](https://www.geeksforgeeks.org/problems/distinct-adjacent-element2121/1) | [`47. Different Adjacent Elements/`](47.%20Different%20Adjacent%20Elements/) |
| 9 | [Max Triplet Sum](https://www.geeksforgeeks.org/problems/maximum-triplet-sum-in-array0129/1) | [`39. Max Triplet Sum/`](39.%20Max%20Triplet%20Sum/) |
| 10 | [Winner in Pairwise Army Battles](https://www.geeksforgeeks.org/problems/countries-at-war2936/1) | [`38. Winner in Pairwise Army Battles/`](38.%20Winner%20in%20Pairwise%20Army%20Battles/) |
| 11 | [Occurrences of Consecutive 3 Numbers](https://www.geeksforgeeks.org/problems/special-integers/1) | [`56. Occurrences of Consecutive 3 Numbers/`](56.%20Occurrences%20of%20Consecutive%203%20Numbers/) |

## Pattern 2: Prefix / Suffix Aggregate

Precompute a running total, product, or max from the left (and/or right) so that a later query — "sum except first/last", "left vs right product", "prefix maximum count" — can be answered from the precomputed values instead of rescanning.

| # | Problem | Link |
|---|---|---|
| 1 | [Sum Except First and Last](https://www.geeksforgeeks.org/problems/max-length-chain/1) | [`13. Sum Except First and Last/`](13.%20Sum%20Except%20First%20and%20Last/) |
| 2 | [Multiply Left and Right Array Sums](https://www.geeksforgeeks.org/problems/multiply-left-and-right-array-sum1555/1) | [`21. Multiply Left and Right Array Sums/`](21.%20Multiply%20Left%20and%20Right%20Array%20Sums/) |
| 3 | [Balanced Array](https://www.geeksforgeeks.org/problems/balanced-array07200720/1) | [`23. Balanced Array/`](23.%20Balanced%20Array/) |
| 4 | [Count Prefix Maximums](https://www.geeksforgeeks.org/problems/elements-before-which-no-element-is-bigger0602/1) | [`49. Count Prefix Maximums/`](49.%20Count%20Prefix%20Maximums/) |
| 5 | [Sum Array Puzzle](https://www.geeksforgeeks.org/problems/sum-array-puzzle/1) | [`36. Sum Array Puzzle/`](36.%20Sum%20Array%20Puzzle/) |
| 6 | [Sum Triangle](https://www.geeksforgeeks.org/problems/sum-triangle-for-given-array1159/1) | [`54. Sum Triangle/`](54.%20Sum%20Triangle/) |

## Pattern 3: In-place Rearrangement / Rotation / Swap

Manipulate elements directly within the array (no extra array of the same size) — rotating, swapping specific positions, segregating by parity, or reversing a window — typically using index arithmetic and constant extra space.

| # | Problem | Link |
|---|---|---|
| 1 | [Rotate Array by One](https://www.geeksforgeeks.org/problems/cyclically-rotate-an-array-by-one2614/1) | [`03. Rotate Array by One/`](03.%20Rotate%20Array%20by%20One/) |
| 2 | [Swap kth elements](https://www.geeksforgeeks.org/problems/swap-kth-elements5500/1) | [`17. Swap kth elements/`](17.%20Swap%20kth%20elements/) |
| 3 | [Segregate Even and Odd numbers](https://www.geeksforgeeks.org/problems/segregate-even-and-odd-numbers4629/1) | [`27. Segregate Even and Odd numbers/`](27.%20Segregate%20Even%20and%20Odd%20numbers/) |
| 4 | [Reverse Subarray](https://www.geeksforgeeks.org/problems/reverse-sub-array5620/1) | [`28. Reverse Subarray/`](28.%20Reverse%20Subarray/) |
| 5 | [Half Ascending and Half Descending Sort](https://www.geeksforgeeks.org/problems/sort-first-half-in-ascending-and-second-half-in-descending1714/1) | [`37. Half Ascending and Half Descending Sort/`](37.%20Half%20Ascending%20and%20Half%20Descending%20Sort/) |
| 6 | [Even Odd Positions](https://www.geeksforgeeks.org/problems/find-the-fine4353/1) | [`19. Even Odd Positions/`](19.%20Even%20Odd%20Positions/) |

## Pattern 4: Array Modification / Insertion / Access Basics

Fundamental array operations dealing with shifting elements to insert/access a value, or transforming each element by a fixed rule (like replacing digits). These are language/API-basics exercises more than algorithmic patterns.

| # | Problem | Link |
|---|---|---|
| 1 | [Array Traversal](https://www.geeksforgeeks.org/problems/array-traversal/1) | [`07. Array Traversal/`](07.%20Array%20Traversal/) |
| 2 | [Replace all 0's with 5](https://www.geeksforgeeks.org/problems/replace-all-0s-with-5/1) | [`09. Replace all 0's with 5/`](09.%20Replace%20all%200's%20with%205/) |
| 3 | [Array Insert at Index](https://www.geeksforgeeks.org/problems/array-insert-at-index/1) | [`11. Array Insert at Index/`](11.%20Array%20Insert%20at%20Index/) |
| 4 | [Find element at a given Index](https://www.geeksforgeeks.org/problems/c-array-print-an-element-set-25933/1) | [`14. Find element at a given Index/`](14.%20Find%20element%20at%20a%20given%20Index/) |
| 5 | [Array End Insert](https://www.geeksforgeeks.org/problems/array-insert-at-end/1) | [`18. Array End Insert/`](18.%20Array%20End%20Insert/) |
| 6 | [Alternates in an Array](https://www.geeksforgeeks.org/problems/print-alternate-elements-of-an-array/1) | [`05. Alternates in an Array/`](05.%20Alternates%20in%20an%20Array/) |
| 7 | [C++ 2-D Arrays | Set-1](https://www.geeksforgeeks.org/problems/c-2-d-arrays0708/1) | [`31. C++ 2-D Arrays Set-1/`](31.%20C++%202-D%20Arrays%20Set-1/) |
| 8 | [Java 1-d and 2-d Array](https://www.geeksforgeeks.org/problems/java-1-d-and-2-d-array2952/1) | [`32. Java 1-d and 2-d Array/`](32.%20Java%201-d%20and%202-d%20Array/) |

## Pattern 5: Counting / Frequency

Tally occurrences of elements or properties (via hashing, frequency maps, or brute-force comparison) to answer questions like "how many are smaller", "which value is majority", or "which elements occur an even number of times".

| # | Problem | Link |
|---|---|---|
| 1 | [Count Smaller in Array](https://www.geeksforgeeks.org/problems/count-of-smaller-elements5947/1) | [`08. Count Smaller in Array/`](08.%20Count%20Smaller%20in%20Array/) |
| 2 | [Most Frequent of Two](https://www.geeksforgeeks.org/problems/who-has-the-majority/1) | [`12. Most Frequent of Two/`](12.%20Most%20Frequent%20of%20Two/) |
| 3 | [Even Occurring Elements](https://www.geeksforgeeks.org/problems/even-occurring-elements4332/1) | [`45. Even Occurring Elements/`](45.%20Even%20Occurring%20Elements/) |
| 4 | [Average Count Array](https://www.geeksforgeeks.org/problems/average-count-array2215/1) | [`43. Average Count Array/`](43.%20Average%20Count%20Array/) |
| 5 | [Count Pairs Odd XOR](https://www.geeksforgeeks.org/problems/count-pairs-odd-xor0308/1) | [`52. Count Pairs Odd XOR/`](52.%20Count%20Pairs%20Odd%20XOR/) |

## Pattern 6: Duplicate / Distinct Element Handling

Identify, remove, or sum distinct/duplicate values, often relying on sorting or hashing to detect repeats efficiently.

| # | Problem | Link |
|---|---|---|
| 1 | [Remove Duplicates from Unsorted](https://www.geeksforgeeks.org/problems/remove-duplicates-from-unsorted-array4141/1) | [`25. Remove Duplicates from Unsorted/`](25.%20Remove%20Duplicates%20from%20Unsorted/) |
| 2 | [Sum of distinct elements](https://www.geeksforgeeks.org/problems/sum-of-distinct-elements4801/1) | [`30. Sum of distinct elements/`](30.%20Sum%20of%20distinct%20elements/) |
| 3 | [Last Duplicate in a Sorted Array](https://www.geeksforgeeks.org/problems/last-duplicate-element-in-a-sorted-array5539/1) | [`35. Last Duplicate in a Sorted Array/`](35.%20Last%20Duplicate%20in%20a%20Sorted%20Array/) |
| 4 | [Make a Distinct Digit Array](https://www.geeksforgeeks.org/problems/make-a-distinct-digit-array2007/1) | [`34. Make a Distinct Digit Array/`](34.%20Make%20a%20Distinct%20Digit%20Array/) |
| 5 | [Missing in Another Shuffled Array](https://www.geeksforgeeks.org/problems/missing-number-in-shuffled-array0938/1) | [`41. Missing in Another Shuffled Array/`](41.%20Missing%20in%20Another%20Shuffled%20Array/) |

## Pattern 7: Two Pointer on Sorted / Boundary Comparison

Compare elements from opposite ends, or check symmetry/order, typically after (or requiring) sorted input — useful for palindrome checks, sorted-array boundary lookups, and unsorted-region detection.

| # | Problem | Link |
|---|---|---|
| 1 | [Array with All Palindromes](https://www.geeksforgeeks.org/problems/palindromic-array-1587115620/1) | [`06. Array with All Palindromes/`](06.%20Array%20with%20All%20Palindromes/) |
| 2 | [Smaller and Larger in Sorted](https://www.geeksforgeeks.org/problems/smaller-and-larger4005/1) | [`15. Smaller and Larger in Sorted/`](15.%20Smaller%20and%20Larger%20in%20Sorted/) |
| 3 | [Palindrome Array](https://www.geeksforgeeks.org/problems/perfect-arrays4645/1) | [`16. Palindrome Array/`](16.%20Palindrome%20Array/) |
| 4 | [Shortest Unsorted Subarray](https://www.geeksforgeeks.org/problems/shortest-un-ordered-subarray3634/1) | [`48. Shortest Unsorted Subarray/`](48.%20Shortest%20Unsorted%20Subarray/) |
| 5 | [Check for Bitonic with Same Numbers](https://www.geeksforgeeks.org/problems/perfect-array2344/1) | [`50. Check for Bitonic with Same Numbers/`](50.%20Check%20for%20Bitonic%20with%20Same%20Numbers/) |

## Pattern 8: Digit / Bit Manipulation

Operate on the digits or binary representation of numbers within the array rather than the array structure itself — digit differences, XOR transformations, parity/odd-sum tricks.

| # | Problem | Link |
|---|---|---|
| 1 | [Absolute Digit Diff 1 in Array](https://www.geeksforgeeks.org/problems/absolute-difference-11156/1) | [`33. Absolute Digit Diff 1 in Array/`](33.%20Absolute%20Digit%20Diff%201%20in%20Array/) |
| 2 | [Adjacent XOR Transformation](https://www.geeksforgeeks.org/problems/game-with-nos3123/1) | [`20. Adjacent XOR Transformation/`](20.%20Adjacent%20XOR%20Transformation/) |
| 3 | [Max Odd Sum](https://www.geeksforgeeks.org/problems/max-odd-sum0651/1) | [`53. Max Odd Sum/`](53.%20Max%20Odd%20Sum/) |
| 4 | [Make Co-prime Array](https://www.geeksforgeeks.org/problems/make-coprime-array3058/1) | [`55. Make Co-prime Array/`](55.%20Make%20Co-prime%20Array/) |

## Pattern 9: Sorting-based / Greedy Combination

Sort (or partially sort) the array first, then greedily combine or pick elements — smallest-with-smallest, kth window products, or minimum sums across two arrays — to reach the optimal answer.

| # | Problem | Link |
|---|---|---|
| 1 | [Max and Min Product from 2 Arrays](https://www.geeksforgeeks.org/problems/product-of-maximum-in-first-array-and-minimum-in-second3943/1) | [`24. Max and Min Product from 2 Arrays/`](24.%20Max%20and%20Min%20Product%20from%202%20Arrays/) |
| 2 | [Minimum sum of two elements from two arrays](https://www.geeksforgeeks.org/problems/minimum-sum-of-two-elements-from-two-arrays0253/1) | [`40. Minimum sum of two elements from two arrays/`](40.%20Minimum%20sum%20of%20two%20elements%20from%20two%20arrays/) |
| 3 | [Max Product K Sized Subarray](https://www.geeksforgeeks.org/problems/largest-product/1) | [`42. Max Product K Sized Subarray/`](42.%20Max%20Product%20K%20Sized%20Subarray/) |
| 4 | [Fighting the Darkness](https://www.geeksforgeeks.org/problems/fighting-the-darkness3949/1) | [`26. Fighting the Darkness/`](26.%20Fighting%20the%20Darkness/) |
| 5 | [Min Decrement by K Operations to Limit Array](https://www.geeksforgeeks.org/problems/reducing-walls4443/1) | [`44. Min Decrement by K Operations to Limit Array/`](44.%20Min%20Decrement%20by%20K%20Operations%20to%20Limit%20Array/) |
| 6 | [Minimum Time with Alternating Techniques](https://www.geeksforgeeks.org/problems/a-guy-with-a-mental-problem1604/1) | [`51. Minimum Time with Alternating Techniques/`](51.%20Minimum%20Time%20with%20Alternating%20Techniques/) |
