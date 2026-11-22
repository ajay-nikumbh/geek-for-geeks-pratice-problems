# Hashing — Easy: Patterns

These are the recurring patterns across the 71 Easy-level Hashing problems. Frequency counting dominates, followed by first/last-occurrence tracking, complement lookup (the Two-Sum family), seen-set checks, and the first hash-table design problems (probing, HashMap).

## Pattern 1: Frequency Counting & Queries

The base hashing move: one pass to fill `count[x]`, then a second pass (over the input or the map) to answer the question. Questions include which element is unique or odd-occurring, which is most or second-most frequent, which first reaches k occurrences, whether frequencies meet a rule (prime, even, at most a limit), or how many substrings or groups the counts allow (`f*(f+1)/2`). For small value ranges, a plain array replaces the map.

| # | Problem | Link |
|---|---|---|
| 1 | [Frequencies in a Limited Array](https://www.geeksforgeeks.org/problems/frequency-of-array-elements-1587115620/1) | [`04. Frequencies in a Limited Array/`](04.%20Frequencies%20in%20a%20Limited%20Array/) |
| 2 | [At Least K Occurrences](https://www.geeksforgeeks.org/problems/first-element-to-occur-k-times5150/1) | [`08. At Least K Occurrences/`](08.%20At%20Least%20K%20Occurrences/) |
| 3 | [Election Winner](https://www.geeksforgeeks.org/problems/winner-of-an-election-where-votes-are-represented-as-candidate-names-1587115621/1) | [`13. Election Winner/`](13.%20Election%20Winner/) |
| 4 | [Second Most Frequent Word](https://www.geeksforgeeks.org/problems/second-most-repeated-string-in-a-sequence0534/1) | [`17. Second Most Frequent Word/`](17.%20Second%20Most%20Frequent%20Word/) |
| 5 | [Twice Counter](https://www.geeksforgeeks.org/problems/twice-counter4236/1) | [`24. Twice Counter/`](24.%20Twice%20Counter/) |
| 6 | [Check if Special Frequency Sum is Even](https://www.geeksforgeeks.org/problems/help-nobita0532/1) | [`26. Check if Special Frequency Sum is Even/`](26.%20Check%20if%20Special%20Frequency%20Sum%20is%20Even/) |
| 7 | [Count Non-Repeated Elements](https://www.geeksforgeeks.org/problems/count-distinct-elements-1587115620/1) | [`30. Count Non-Repeated Elements/`](30.%20Count%20Non-Repeated%20Elements/) |
| 8 | [Most Frequent in a Limited Range Array](https://www.geeksforgeeks.org/problems/maximum-repeating-number4858/1) | [`31. Most Frequent in a Limited Range Array/`](31.%20Most%20Frequent%20in%20a%20Limited%20Range%20Array/) |
| 9 | [Substrings with same first and last characters](https://www.geeksforgeeks.org/problems/substrings-with-similar-first-and-last-characters3644/1) | [`33. Substrings with same first and last characters/`](33.%20Substrings%20with%20same%20first%20and%20last%20characters/) |
| 10 | [Most Frequent in an Array](https://www.geeksforgeeks.org/problems/most-frequent-element-in-an-array/1) | [`35. Most Frequent in an Array/`](35.%20Most%20Frequent%20in%20an%20Array/) |
| 11 | [Frequency of Elements](https://www.geeksforgeeks.org/problems/frequency-of-elements--111353/1) | [`41. Frequency of Elements/`](41.%20Frequency%20of%20Elements/) |
| 12 | [First with K Occurrences](https://www.geeksforgeeks.org/problems/first-come-first-serve1328/1) | [`46. First with K Occurrences/`](46.%20First%20with%20K%20Occurrences/) |
| 13 | [Split Array into Minimum Subsets](https://www.geeksforgeeks.org/problems/split-array-into-minimum-subsets/1) | [`47. Split Array into Minimum Subsets/`](47.%20Split%20Array%20into%20Minimum%20Subsets/) |
| 14 | [Count Paired Elements](https://www.geeksforgeeks.org/problems/love-for-the-twins2623/1) | [`48. Count Paired Elements/`](48.%20Count%20Paired%20Elements/) |
| 15 | [Lucky Number](https://www.geeksforgeeks.org/problems/lucky-number0707/1) | [`51. Lucky Number/`](51.%20Lucky%20Number/) |
| 16 | [Prime Frequencies in Array](https://www.geeksforgeeks.org/problems/numbers-with-prime-frequencies-greater-than-or-equal-to-k5823/1) | [`61. Prime Frequencies in Array/`](61.%20Prime%20Frequencies%20in%20Array/) |
| 17 | [Partition into k Groups with Frequency Limit](https://www.geeksforgeeks.org/problems/ana-and-sweets5331/1) | [`63. Partition into k Groups with Frequency Limit/`](63.%20Partition%20into%20k%20Groups%20with%20Frequency%20Limit/) |
| 18 | [Count Even Letters](https://www.geeksforgeeks.org/problems/count-even-letters/1) | [`65. Count Even Letters/`](65.%20Count%20Even%20Letters/) |

## Pattern 2: Complement Lookup (Two-Sum / k-Sum Family)

Instead of sorting, store the values seen so far and ask whether the partner `target - x` exists. Use a set for yes/no, a count map to count pairs (handles duplicates), or a set of emitted pairs to keep results distinct. Two-array versions put one array in the set and scan the other. Triplets fix one element and run the same lookup on the rest. Difference-k and swap-to-equalise-sums problems are the same lookup with a different partner formula.

| # | Problem | Link |
|---|---|---|
| 1 | [Two Sum - Pair with Given Sum](https://www.geeksforgeeks.org/problems/key-pair5616/1) | [`01. Two Sum - Pair with Given Sum/`](01.%20Two%20Sum%20-%20Pair%20with%20Given%20Sum/) |
| 2 | [All Pairs with Sum from 2 Arrays](https://www.geeksforgeeks.org/problems/find-all-pairs-whose-sum-is-x5808/1) | [`09. All Pairs with Sum from 2 Arrays/`](09.%20All%20Pairs%20with%20Sum%20from%202%20Arrays/) |
| 3 | [Pairs with Positive Negative values](https://www.geeksforgeeks.org/problems/pairs-with-positive-negative-values3719/1) | [`15. Pairs with Positive Negative values/`](15.%20Pairs%20with%20Positive%20Negative%20values/) |
| 4 | [Count Pair Sum in 2 Arrays](https://www.geeksforgeeks.org/problems/count-pair-sum5956/1) | [`34. Count Pair Sum in 2 Arrays/`](34.%20Count%20Pair%20Sum%20in%202%20Arrays/) |
| 5 | [Distinct Pairs with Sum](https://www.geeksforgeeks.org/problems/all-distinct-pairs-with-given-sum/1) | [`64. Distinct Pairs with Sum/`](64.%20Distinct%20Pairs%20with%20Sum/) |
| 6 | [Count Indices with Complement in Third Array](https://www.geeksforgeeks.org/problems/sum-indexes5459/1) | [`66. Count Indices with Complement in Third Array/`](66.%20Count%20Indices%20with%20Complement%20in%20Third%20Array/) |
| 7 | [Pair Sum in Distinct Elements Array](https://www.geeksforgeeks.org/problems/hashing-for-pair-1--110939/1) | [`67. Pair Sum in Distinct Elements Array/`](67.%20Pair%20Sum%20in%20Distinct%20Elements%20Array/) |
| 8 | [All Triplets with Given Sum](https://www.geeksforgeeks.org/problems/find-all-triplets-with-given-sum/1) | [`68. All Triplets with Given Sum/`](68.%20All%20Triplets%20with%20Given%20Sum/) |
| 9 | [Count Distinct Pairs with Sum](https://www.geeksforgeeks.org/problems/2-sum-count-distinct-pairs-with-given-sum/1) | [`69. Count Distinct Pairs with Sum/`](69.%20Count%20Distinct%20Pairs%20with%20Sum/) |
| 10 | [All Pairs With Given Sum](https://www.geeksforgeeks.org/problems/find-all-pairs-with-given-sum/1) | [`71. All Pairs With Given Sum/`](71.%20All%20Pairs%20With%20Given%20Sum/) |

## Pattern 3: First / Last Occurrence & Index Tracking

Order matters here, so the map holds an index, not only a count. Keep `first[x]` and/or `last[x]`. Then the earliest repeat, earliest non-repeating element, widest distance between equal values, or the k-th distinct element in input order comes from one more scan. For strings, a 26-slot array is enough.

| # | Problem | Link |
|---|---|---|
| 1 | [Non Repeating Character](https://www.geeksforgeeks.org/problems/non-repeating-character-1587115620/1) | [`05. Non Repeating Character/`](05.%20Non%20Repeating%20Character/) |
| 2 | [First Repeating Element](https://www.geeksforgeeks.org/problems/first-repeating-element4018/1) | [`06. First Repeating Element/`](06.%20First%20Repeating%20Element/) |
| 3 | [Non-Repeating Element](https://www.geeksforgeeks.org/problems/non-repeating-element3958/1) | [`10. Non-Repeating Element/`](10.%20Non-Repeating%20Element/) |
| 4 | [Minimum Indexed Character](https://www.geeksforgeeks.org/problems/minimum-indexed-character-1587115620/1) | [`11. Minimum Indexed Character/`](11.%20Minimum%20Indexed%20Character/) |
| 5 | [First Repeated Character](https://www.geeksforgeeks.org/problems/find-first-repeated-character4108/1) | [`14. First Repeated Character/`](14.%20First%20Repeated%20Character/) |
| 6 | [Max distance between same elements](https://www.geeksforgeeks.org/problems/max-distance-between-same-elements/1) | [`18. Max distance between same elements/`](18.%20Max%20distance%20between%20same%20elements/) |
| 7 | [Total Traversal Time](https://www.geeksforgeeks.org/problems/total-traversal-time/1) | [`32. Total Traversal Time/`](32.%20Total%20Traversal%20Time/) |
| 8 | [Max Gap Between Two Same](https://www.geeksforgeeks.org/problems/maximum-number-of-characters-between-any-two-same-character4552/1) | [`37. Max Gap Between Two Same/`](37.%20Max%20Gap%20Between%20Two%20Same/) |
| 9 | [Earliest Last Occurrence](https://www.geeksforgeeks.org/problems/last-seen-array-element1501/1) | [`57. Earliest Last Occurrence/`](57.%20Earliest%20Last%20Occurrence/) |

## Pattern 4: Seen-Set Membership / Deduplication

A set answers 'have I seen this before?' in O(1). Use it to remove or detect duplicates, check that digits or letters are all distinct or all present (isogram, pangram, fascinating number), toggle on/off states (open tabs, computers), build sequences that forbid repeats (Recaman), or detect a cycle by remembering past states (the remainder in a repeating decimal).

| # | Problem | Link |
|---|---|---|
| 1 | [Remove Duplicates from an array](https://www.geeksforgeeks.org/problems/remove-duplicates-in-small-prime-array/1) | [`16. Remove Duplicates from an array/`](16.%20Remove%20Duplicates%20from%20an%20array/) |
| 2 | [Check for Isogram String](https://www.geeksforgeeks.org/problems/check-if-a-string-is-isogram-or-not-1587115620/1) | [`19. Check for Isogram String/`](19.%20Check%20for%20Isogram%20String/) |
| 3 | [K-Pangrams](https://www.geeksforgeeks.org/problems/k-pangrams0909/1) | [`20. K-Pangrams/`](20.%20K-Pangrams/) |
| 4 | [Numbers Containing 1, 2 and 3](https://www.geeksforgeeks.org/problems/numbers-containing-1-2-and-32555/1) | [`21. Numbers Containing 1, 2 and 3/`](21.%20Numbers%20Containing%201,%202%20and%203/) |
| 5 | [Recaman Sequence](https://www.geeksforgeeks.org/problems/recamans-sequence4856/1) | [`25. Recaman Sequence/`](25.%20Recaman%20Sequence/) |
| 6 | [Fascinating Number](https://www.geeksforgeeks.org/problems/fascinating-number3751/1) | [`28. Fascinating Number/`](28.%20Fascinating%20Number/) |
| 7 | [Largest Fibonacci Subsequence](https://www.geeksforgeeks.org/problems/largest-fibonacci-subsequence2206/1) | [`42. Largest Fibonacci Subsequence/`](42.%20Largest%20Fibonacci%20Subsequence/) |
| 8 | [Unoccupied Computers](https://www.geeksforgeeks.org/problems/unoccupied-computers-1646661078/1) | [`44. Unoccupied Computers/`](44.%20Unoccupied%20Computers/) |
| 9 | [Check if array contains duplicates](https://www.geeksforgeeks.org/problems/check-if-array-contains-duplicates/1) | [`53. Check if array contains duplicates/`](53.%20Check%20if%20array%20contains%20duplicates/) |
| 10 | [Number of Open Tabs](https://www.geeksforgeeks.org/problems/tiger-zinda-hai5531/1) | [`55. Number of Open Tabs/`](55.%20Number%20of%20Open%20Tabs/) |

## Pattern 5: Group-by Key / Bucket Counting

Items that are 'equivalent' share a key. Compute the key, then group by it in a map. Anagrams share their sorted letters. Shifted strings share their letter-gap pattern. Pairs divisible by k pair remainder `r` with `k - r`. Equal digit sums share a bucket for the best pair. Two pairs with the same sum or product share a pair-sum key. Strings with one mismatch share a wildcard key. Pairs inside a bucket are then `c*(c-1)/2`.

| # | Problem | Link |
|---|---|---|
| 1 | [Check Pairs of Equal Sum](https://www.geeksforgeeks.org/problems/sum-equals-to-sum4006/1) | [`38. Check Pairs of Equal Sum/`](38.%20Check%20Pairs%20of%20Equal%20Sum/) |
| 2 | [Sum of f(a[i], a[j]) over all pairs in an array of n integers](https://www.geeksforgeeks.org/problems/sum-of-fai-aj-over-all-pairs-in-an-array-of-n-integers4057/1) | [`43. Sum of f(a[i], a[j]) over all pairs in an array of n integers/`](43.%20Sum%20of%20f(a[i],%20a[j])%20over%20all%20pairs%20in%20an%20array%20of%20n%20integers/) |
| 3 | [Two Pairs with Same Product](https://www.geeksforgeeks.org/problems/find-pairs-with-given-relation1540/1) | [`60. Two Pairs with Same Product/`](60.%20Two%20Pairs%20with%20Same%20Product/) |

## Pattern 6: Set Operations on Collections (Union / Intersection / Subset / Disjoint)

Classic set algebra with hashing: insert array A, then scan B. Membership tests give the intersection (common elements, common across matrix rows), difference (missing in second array, uncommon characters), subset check, disjoint check, or the minimum removals to make two arrays disjoint. Union inserts both. Use a count map instead of a set when duplicates must be respected.

| # | Problem | Link |
|---|---|---|
| 1 | [Union of Arrays with Duplicates](https://www.geeksforgeeks.org/problems/union-of-two-arrays3538/1) | [`02. Union of Arrays with Duplicates/`](02.%20Union%20of%20Arrays%20with%20Duplicates/) |
| 2 | [Missing in Second Array](https://www.geeksforgeeks.org/problems/in-first-but-second5423/1) | [`12. Missing in Second Array/`](12.%20Missing%20in%20Second%20Array/) |
| 3 | [Union of Two Sets](https://www.geeksforgeeks.org/problems/union-of-two-arrays3538--171343/1) | [`45. Union of Two Sets/`](45.%20Union%20of%20Two%20Sets/) |
| 4 | [Remove Minimum to Make Disjoint](https://www.geeksforgeeks.org/problems/remove-minimum-number-of-elements4032/1) | [`52. Remove Minimum to Make Disjoint/`](52.%20Remove%20Minimum%20to%20Make%20Disjoint/) |
| 5 | [Check for Disjoint](https://www.geeksforgeeks.org/problems/check-for-disjoint-sets-or-arrays/1) | [`62. Check for Disjoint/`](62.%20Check%20for%20Disjoint/) |

## Pattern 7: Prefix Sum + Hash Map

A subarray `(i, j]` has sum `P[j] - P[i]`. So for each `j`, look up how many earlier prefixes equal `P[j] - k` (count subarrays) or where the first such prefix was (longest subarray). Zero-sum, sum-K, substrings with K ones, and equal 0/1/2 counts (key on the difference pair) all use this. Seed the map with prefix 0.

| # | Problem | Link |
|---|---|---|
| 1 | [Subarrays with given sum](https://www.geeksforgeeks.org/problems/subarray-range-with-given-sum2804/1) | [`40. Subarrays with given sum/`](40.%20Subarrays%20with%20given%20sum/) |

## Pattern 8: Frequency-Based Sorting / Top-K

After counting, the answer is an ordering. Sort by decreasing frequency (ties by value), take the top K with a heap or buckets, follow the order of another array, rebuild a string in descending order (counting sort), or greedily drop the least-frequent ids to minimise distinct count. Keeping the k smallest in original order is the same idea: pick the threshold, then filter in one pass.

| # | Problem | Link |
|---|---|---|
| 1 | [Minimum Distinct Ids](https://www.geeksforgeeks.org/problems/minimum-distinct-ids3251/1) | [`49. Minimum Distinct Ids/`](49.%20Minimum%20Distinct%20Ids/) |
| 2 | [K Smallests in the Original Order](https://www.geeksforgeeks.org/problems/print-k-smallest-elements-in-their-original-order5407/1) | [`50. K Smallests in the Original Order/`](50.%20K%20Smallests%20in%20the%20Original%20Order/) |
| 3 | [Cumulative Frequencies in an Array](https://www.geeksforgeeks.org/problems/frequency-of-each-element-in-an-unsorted-array0759/1) | [`56. Cumulative Frequencies in an Array/`](56.%20Cumulative%20Frequencies%20in%20an%20Array/) |

## Pattern 9: Sequence Membership (Consecutive / AP / Missing / Subsequence DP)

Problems about which numbers form a run or a progression. Longest consecutive sequence starts counting only at values with no predecessor, so total work stays linear. AP checks use min, common difference, and set membership for each expected term. Missing-in-range problems scan the range against the set. Longest subsequence with adjacent diff 0 or 1 keeps `best[x] = 1 + max(best[x-1], best[x], best[x+1])` in a map.

| # | Problem | Link |
|---|---|---|
| 1 | [Check if array contains contiguous integers](https://www.geeksforgeeks.org/problems/check-if-array-contains-contiguous-integers-with-duplicates-allowed2046/1) | [`36. Check if array contains contiguous integers/`](36.%20Check%20if%20array%20contains%20contiguous%20integers/) |
| 2 | [Incomplete Array](https://www.geeksforgeeks.org/problems/incomplete-array3859/1) | [`59. Incomplete Array/`](59.%20Incomplete%20Array/) |

## Pattern 10: Frequency Comparison (Anagram / Multiset Equality)

Two inputs are the same multiset if their frequency maps match. Increment for one and decrement for the other, then inspect what is left. Non-zero entries count the changes needed (k-anagram, transform string). At most one odd count means a palindrome permutation is possible. Checking each candidate removal tests if all frequencies can become equal.

| # | Problem | Link |
|---|---|---|
| 1 | [Check Equal Arrays](https://www.geeksforgeeks.org/problems/check-if-two-arrays-are-equal-or-not3847/1) | [`03. Check Equal Arrays/`](03.%20Check%20Equal%20Arrays/) |

## Pattern 11: String Hashing / Substring Patterns

Substring-level hashing: precompute prefix hashes so any substring hash is O(1), then compare substrings, count distinct ones, or match a pattern (frequency of a substring). Palindrome queries compare forward and reverse hashes. Period problems test candidate prefixes. The hardest variant combines Manacher's palindrome radii with prefix/suffix best sums.

| # | Problem | Link |
|---|---|---|
| 1 | [Distinct Substrings](https://www.geeksforgeeks.org/problems/distinct-substrings2516/1) | [`54. Distinct Substrings/`](54.%20Distinct%20Substrings/) |

## Pattern 12: Hash Table Design & Collision Resolution

Build the data structure, not only use it. Open addressing places a key at `h(k)` and probes `h(k)+i` (linear) or `h(k)+i^2` (quadratic) on collision. A HashMap design uses buckets with chaining. LRU keeps a map from key to list node plus a recency-ordered doubly linked list. LFU adds frequency buckets. A URL shortener maps a counter to a base-62 code and back.

| # | Problem | Link |
|---|---|---|
| 1 | [Linear Probing in Hashing](https://www.geeksforgeeks.org/problems/linear-probing-in-hashing-1587115620/1) | [`22. Linear Probing in Hashing/`](22.%20Linear%20Probing%20in%20Hashing/) |
| 2 | [Quadratic Probing in Hashing](https://www.geeksforgeeks.org/problems/quadratic-probing-in-hashing-1587115621/1) | [`29. Quadratic Probing in Hashing/`](29.%20Quadratic%20Probing%20in%20Hashing/) |
| 3 | [Design HashMap](https://www.geeksforgeeks.org/problems/design-hashmap/1) | [`70. Design HashMap/`](70.%20Design%20HashMap/) |

## Pattern 13: Ordered Structures & Sweep (Sorting + Hashing)

These problems need order, not only membership. Largest smaller on the left uses an ordered set (lower bound). Surpasser count uses merge sort or a BIT. Queries for count ≤ x sort one array and binary-search it. Overlapping intervals sort by start and merge. Powerful integer runs a difference-array sweep over interval endpoints. Making elements unique sorts and then bumps duplicates greedily.

| # | Problem | Link |
|---|---|---|
| 1 | [Queries to Count Smaller or Equal in Other Array](https://www.geeksforgeeks.org/problems/count-the-elements1529/1) | [`23. Queries to Count Smaller or Equal in Other Array/`](23.%20Queries%20to%20Count%20Smaller%20or%20Equal%20in%20Other%20Array/) |

## Pattern 14: One-to-One Mapping (Bijection & Lookup Tables)

Isomorphic strings and pattern matching need a bijection: keep `a→b` and `b→a` maps and fail as soon as either disagrees. Nuts and Bolts uses a fixed order map to match items. The keypad problem is a plain lookup table from each character to its key sequence.

| # | Problem | Link |
|---|---|---|
| 1 | [Isomorphic Strings](https://www.geeksforgeeks.org/problems/isomorphic-strings-1587115620/1) | [`07. Isomorphic Strings/`](07.%20Isomorphic%20Strings/) |
| 2 | [Convert a sentence into its equivalent mobile numeric keypad sequence](https://www.geeksforgeeks.org/problems/convert-a-sentence-into-its-equivalent-mobile-numeric-keypad-sequence0547/1) | [`27. Convert a sentence into its equivalent mobile numeric keypad sequence/`](27.%20Convert%20a%20sentence%20into%20its%20equivalent%20mobile%20numeric%20keypad%20sequence/) |
| 3 | [Match  Pattern with One to One Mapping](https://www.geeksforgeeks.org/problems/match-specific-pattern/1) | [`39. Match Pattern with One to One Mapping/`](39.%20Match%20Pattern%20with%20One%20to%20One%20Mapping/) |

## Pattern 15: Sliding Window + Hash Map

Same-direction two pointers with a hash map of what is inside the window. For distinct-element windows, shrink until the new element is unique, then add `window length` contributions or track the best window sum.

| # | Problem | Link |
|---|---|---|
| 1 | [Sum of Distinct Element Subarray Lengths](https://www.geeksforgeeks.org/problems/sum-of-length3345/1) | [`58. Sum of Distinct Element Subarray Lengths/`](58.%20Sum%20of%20Distinct%20Element%20Subarray%20Lengths/) |
