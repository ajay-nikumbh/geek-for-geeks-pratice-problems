# Hashing — Medium: Patterns

Medium-level Hashing problems (46) move from 'count things' to 'pick the right key'. Group-by-key bucketing, prefix sum + hash map for subarrays, and frequency-ordered output take over, and some problems need sorting or an ordered set on top of hashing.

## Pattern 1: Frequency Counting & Queries

The base hashing move: one pass to fill `count[x]`, then a second pass (over the input or the map) to answer the question. Questions include which element is unique or odd-occurring, which is most or second-most frequent, which first reaches k occurrences, whether frequencies meet a rule (prime, even, at most a limit), or how many substrings or groups the counts allow (`f*(f+1)/2`). For small value ranges, a plain array replaces the map.

| # | Problem | Link |
|---|---|---|
| 1 | [Majority Element - More Than n/3](https://www.geeksforgeeks.org/problems/majority-vote/1) | [`03. Majority Element - More Than n3/`](03.%20Majority%20Element%20-%20More%20Than%20n3/) |
| 2 | [Subsequences Start with Vowel and End with Consonant](https://www.geeksforgeeks.org/problems/string-subsequence-game5515/1) | [`36. Subsequences Start with Vowel and End with Consonant/`](36.%20Subsequences%20Start%20with%20Vowel%20and%20End%20with%20Consonant/) |

## Pattern 2: Complement Lookup (Two-Sum / k-Sum Family)

Instead of sorting, store the values seen so far and ask whether the partner `target - x` exists. Use a set for yes/no, a count map to count pairs (handles duplicates), or a set of emitted pairs to keep results distinct. Two-array versions put one array in the set and scan the other. Triplets fix one element and run the same lookup on the rest. Difference-k and swap-to-equalise-sums problems are the same lookup with a different partner formula.

| # | Problem | Link |
|---|---|---|
| 1 | [Swap Pairs Make Sum Equal](https://www.geeksforgeeks.org/problems/swapping-pairs-make-sum-equal4142/1) | [`10. Swap Pairs Make Sum Equal/`](10.%20Swap%20Pairs%20Make%20Sum%20Equal/) |
| 2 | [All Triplets with Zero Sum](https://www.geeksforgeeks.org/problems/find-all-triplets-with-zero-sum/1) | [`15. All Triplets with Zero Sum/`](15.%20All%20Triplets%20with%20Zero%20Sum/) |
| 3 | [Count pairs Sum in matrices](https://www.geeksforgeeks.org/problems/count-pairs-sum-in-matrices4332/1) | [`21. Count pairs Sum in matrices/`](21.%20Count%20pairs%20Sum%20in%20matrices/) |
| 4 | [Distinct Pairs with Diff K](https://www.geeksforgeeks.org/problems/count-distinct-pairs-with-difference-k1233/1) | [`25. Distinct Pairs with Diff K/`](25.%20Distinct%20Pairs%20with%20Diff%20K/) |

## Pattern 3: First / Last Occurrence & Index Tracking

Order matters here, so the map holds an index, not only a count. Keep `first[x]` and/or `last[x]`. Then the earliest repeat, earliest non-repeating element, widest distance between equal values, or the k-th distinct element in input order comes from one more scan. For strings, a 26-slot array is enough.

| # | Problem | Link |
|---|---|---|
| 1 | [Smallest Subarray with All of Most Frequent](https://www.geeksforgeeks.org/problems/smallest-subarray-with-all-occurrences-of-a-most-frequent-element2258/1) | [`39. Smallest Subarray with All of Most Frequent/`](39.%20Smallest%20Subarray%20with%20All%20of%20Most%20Frequent/) |

## Pattern 4: Seen-Set Membership / Deduplication

A set answers 'have I seen this before?' in O(1). Use it to remove or detect duplicates, check that digits or letters are all distinct or all present (isogram, pangram, fascinating number), toggle on/off states (open tabs, computers), build sequences that forbid repeats (Recaman), or detect a cycle by remembering past states (the remainder in a repeating decimal).

| # | Problem | Link |
|---|---|---|
| 1 | [Fraction to Repeating Decimal](https://www.geeksforgeeks.org/problems/a-simple-fraction0921/1) | [`24. Fraction to Repeating Decimal/`](24.%20Fraction%20to%20Repeating%20Decimal/) |
| 2 | [Count 0s After Setting Rows and Columns as 1](https://www.geeksforgeeks.org/problems/count-number-of-free-cell--170646/1) | [`29. Count 0s After Setting Rows and Columns as 1/`](29.%20Count%200s%20After%20Setting%20Rows%20and%20Columns%20as%201/) |

## Pattern 5: Group-by Key / Bucket Counting

Items that are 'equivalent' share a key. Compute the key, then group by it in a map. Anagrams share their sorted letters. Shifted strings share their letter-gap pattern. Pairs divisible by k pair remainder `r` with `k - r`. Equal digit sums share a bucket for the best pair. Two pairs with the same sum or product share a pair-sum key. Strings with one mismatch share a wildcard key. Pairs inside a bucket are then `c*(c-1)/2`.

| # | Problem | Link |
|---|---|---|
| 1 | [Divide Array into Pairs with Sum Divisible by K](https://www.geeksforgeeks.org/problems/array-pair-sum-divisibility-problem3257/1) | [`09. Divide Array into Pairs with Sum Divisible by K/`](09.%20Divide%20Array%20into%20Pairs%20with%20Sum%20Divisible%20by%20K/) |
| 2 | [Arrange Anagrams Together](https://www.geeksforgeeks.org/problems/print-anagrams-together/1) | [`13. Arrange Anagrams Together/`](13.%20Arrange%20Anagrams%20Together/) |
| 3 | [Count Pairs Divisible By K](https://www.geeksforgeeks.org/problems/count-pairs-in-array-divisible-by-k/1) | [`22. Count Pairs Divisible By K/`](22.%20Count%20Pairs%20Divisible%20By%20K/) |
| 4 | [Absolute Difference Divisible by K](https://www.geeksforgeeks.org/problems/absolute-difference-divisible-by-k/1) | [`28. Absolute Difference Divisible by K/`](28.%20Absolute%20Difference%20Divisible%20by%20K/) |
| 5 | [Two Pairs with Same Sum](https://www.geeksforgeeks.org/problems/satisfy-the-equation5847/1) | [`32. Two Pairs with Same Sum/`](32.%20Two%20Pairs%20with%20Same%20Sum/) |
| 6 | [Pairs of Non Coinciding Points](https://www.geeksforgeeks.org/problems/pairs-of-non-coinciding-points4141/1) | [`37. Pairs of Non Coinciding Points/`](37.%20Pairs%20of%20Non%20Coinciding%20Points/) |
| 7 | [Maximum Pair Sum with Equal Digit Sum](https://www.geeksforgeeks.org/problems/ruling-pair--141631/1) | [`38. Maximum Pair Sum with Equal Digit Sum/`](38.%20Maximum%20Pair%20Sum%20with%20Equal%20Digit%20Sum/) |
| 8 | [Group Shifted String](https://www.geeksforgeeks.org/problems/group-shifted-string/1) | [`42. Group Shifted String/`](42.%20Group%20Shifted%20String/) |
| 9 | [Count pairs of strings with one mismatch](https://www.geeksforgeeks.org/problems/count-pairs-of-strings-with-one-mismatch/1) | [`45. Count pairs of strings with one mismatch/`](45.%20Count%20pairs%20of%20strings%20with%20one%20mismatch/) |

## Pattern 6: Set Operations on Collections (Union / Intersection / Subset / Disjoint)

Classic set algebra with hashing: insert array A, then scan B. Membership tests give the intersection (common elements, common across matrix rows), difference (missing in second array, uncommon characters), subset check, disjoint check, or the minimum removals to make two arrays disjoint. Union inserts both. Use a count map instead of a set when duplicates must be respected.

| # | Problem | Link |
|---|---|---|
| 1 | [Common in Rows of a Matrix](https://www.geeksforgeeks.org/problems/find-distinct-elements2054/1) | [`26. Common in Rows of a Matrix/`](26.%20Common%20in%20Rows%20of%20a%20Matrix/) |

## Pattern 7: Prefix Sum + Hash Map

A subarray `(i, j]` has sum `P[j] - P[i]`. So for each `j`, look up how many earlier prefixes equal `P[j] - k` (count subarrays) or where the first such prefix was (longest subarray). Zero-sum, sum-K, substrings with K ones, and equal 0/1/2 counts (key on the difference pair) all use this. Seed the map with prefix 0.

| # | Problem | Link |
|---|---|---|
| 1 | [Largest subarray with 0 sum](https://www.geeksforgeeks.org/problems/largest-subarray-with-0-sum/1) | [`01. Largest subarray with 0 sum/`](01.%20Largest%20subarray%20with%200%20sum/) |
| 2 | [Zero Sum Subarrays](https://www.geeksforgeeks.org/problems/zero-sum-subarrays1825/1) | [`05. Zero Sum Subarrays/`](05.%20Zero%20Sum%20Subarrays/) |
| 3 | [Subarrays with Sum K](https://www.geeksforgeeks.org/problems/subarrays-with-sum-k/1) | [`06. Subarrays with Sum K/`](06.%20Subarrays%20with%20Sum%20K/) |
| 4 | [Substring with Equal 0, 1 and 2](https://www.geeksforgeeks.org/problems/equal-0-1-and-23208/1) | [`33. Substring with Equal 0, 1 and 2/`](33.%20Substring%20with%20Equal%200,%201%20and%202/) |
| 5 | [Count Indices to Balance Even and Odd Sums](https://www.geeksforgeeks.org/problems/count-indices-to-balance-even-and-odd-sums/1) | [`35. Count Indices to Balance Even and Odd Sums/`](35.%20Count%20Indices%20to%20Balance%20Even%20and%20Odd%20Sums/) |
| 6 | [Count Substrings With K 1's](https://www.geeksforgeeks.org/problems/count-of-substrings-containing-k-ones2304/1) | [`41. Count Substrings With K 1's/`](41.%20Count%20Substrings%20With%20K%201's/) |

## Pattern 8: Frequency-Based Sorting / Top-K

After counting, the answer is an ordering. Sort by decreasing frequency (ties by value), take the top K with a heap or buckets, follow the order of another array, rebuild a string in descending order (counting sort), or greedily drop the least-frequent ids to minimise distinct count. Keeping the k smallest in original order is the same idea: pick the threshold, then filter in one pass.

| # | Problem | Link |
|---|---|---|
| 1 | [Sort Elements by Decreasing Frequency](https://www.geeksforgeeks.org/problems/sorting-elements-of-an-array-by-frequency-1587115621/1) | [`04. Sort Elements by Decreasing Frequency/`](04.%20Sort%20Elements%20by%20Decreasing%20Frequency/) |
| 2 | [Top K Frequent in Array](https://www.geeksforgeeks.org/problems/top-k-frequent-elements-in-array/1) | [`11. Top K Frequent in Array/`](11.%20Top%20K%20Frequent%20in%20Array/) |
| 3 | [Sort according to an Array](https://www.geeksforgeeks.org/problems/relative-sorting4323/1) | [`12. Sort according to an Array/`](12.%20Sort%20according%20to%20an%20Array/) |

## Pattern 9: Sequence Membership (Consecutive / AP / Missing / Subsequence DP)

Problems about which numbers form a run or a progression. Longest consecutive sequence starts counting only at values with no predecessor, so total work stays linear. AP checks use min, common difference, and set membership for each expected term. Missing-in-range problems scan the range against the set. Longest subsequence with adjacent diff 0 or 1 keeps `best[x] = 1 + max(best[x-1], best[x], best[x+1])` in a map.

| # | Problem | Link |
|---|---|---|
| 1 | [Longest Consecutive Subsequence](https://www.geeksforgeeks.org/problems/longest-consecutive-subsequence2449/1) | [`02. Longest Consecutive Subsequence/`](02.%20Longest%20Consecutive%20Subsequence/) |
| 2 | [Missing element of AP](https://www.geeksforgeeks.org/problems/missing-element-of-ap2228/1) | [`14. Missing element of AP/`](14.%20Missing%20element%20of%20AP/) |
| 3 | [Missing Element in Range](https://www.geeksforgeeks.org/problems/missing-element-in-range/1) | [`27. Missing Element in Range/`](27.%20Missing%20Element%20in%20Range/) |
| 4 | [Longest Subsequence with Adjacent Diff 0 or 1](https://www.geeksforgeeks.org/problems/longest-subsequence-with-difference/1) | [`44. Longest Subsequence with Adjacent Diff 0 or 1/`](44.%20Longest%20Subsequence%20with%20Adjacent%20Diff%200%20or%201/) |

## Pattern 10: Frequency Comparison (Anagram / Multiset Equality)

Two inputs are the same multiset if their frequency maps match. Increment for one and decrement for the other, then inspect what is left. Non-zero entries count the changes needed (k-anagram, transform string). At most one odd count means a palindrome permutation is possible. Checking each candidate removal tests if all frequencies can become equal.

| # | Problem | Link |
|---|---|---|
| 1 | [Same Character Frequencies with One Removal](https://www.geeksforgeeks.org/problems/check-frequencies4211/1) | [`07. Same Character Frequencies with One Removal/`](07.%20Same%20Character%20Frequencies%20with%20One%20Removal/) |
| 2 | [k-Anagram](https://www.geeksforgeeks.org/problems/check-if-two-strings-are-k-anagrams-or-not/1) | [`17. k-Anagram/`](17.%20k-Anagram/) |
| 3 | [Transform String](https://www.geeksforgeeks.org/problems/transform-string5648/1) | [`20. Transform String/`](20.%20Transform%20String/) |
| 4 | [Transfiguration](https://www.geeksforgeeks.org/problems/transfiguration--141631/1) | [`30. Transfiguration/`](30.%20Transfiguration/) |

## Pattern 11: String Hashing / Substring Patterns

Substring-level hashing: precompute prefix hashes so any substring hash is O(1), then compare substrings, count distinct ones, or match a pattern (frequency of a substring). Palindrome queries compare forward and reverse hashes. Period problems test candidate prefixes. The hardest variant combines Manacher's palindrome radii with prefix/suffix best sums.

| # | Problem | Link |
|---|---|---|
| 1 | [Repeated Pattern Removal](https://www.geeksforgeeks.org/problems/demonitisation0013/1) | [`40. Repeated Pattern Removal/`](40.%20Repeated%20Pattern%20Removal/) |
| 2 | [Frequency of a Substring in a String](https://www.geeksforgeeks.org/problems/frequency-of-a-substring-in-a-string/1) | [`46. Frequency of a Substring in a String/`](46.%20Frequency%20of%20a%20Substring%20in%20a%20String/) |

## Pattern 12: Hash Table Design & Collision Resolution

Build the data structure, not only use it. Open addressing places a key at `h(k)` and probes `h(k)+i` (linear) or `h(k)+i^2` (quadratic) on collision. A HashMap design uses buckets with chaining. LRU keeps a map from key to list node plus a recency-ordered doubly linked list. LFU adds frequency buckets. A URL shortener maps a counter to a base-62 code and back.

| # | Problem | Link |
|---|---|---|
| 1 | [Design a tiny URL or URL shortener](https://www.geeksforgeeks.org/problems/design-a-tiny-url-or-url-shortener2031/1) | [`31. Design a tiny URL or URL shortener/`](31.%20Design%20a%20tiny%20URL%20or%20URL%20shortener/) |

## Pattern 13: Ordered Structures & Sweep (Sorting + Hashing)

These problems need order, not only membership. Largest smaller on the left uses an ordered set (lower bound). Surpasser count uses merge sort or a BIT. Queries for count ≤ x sort one array and binary-search it. Overlapping intervals sort by start and merge. Powerful integer runs a difference-array sweep over interval endpoints. Making elements unique sorts and then bumps duplicates greedily.

| # | Problem | Link |
|---|---|---|
| 1 | [Overlapping Intervals](https://www.geeksforgeeks.org/problems/overlapping-intervals--170633/1) | [`08. Overlapping Intervals/`](08.%20Overlapping%20Intervals/) |
| 2 | [Largest Smaller on Left](https://www.geeksforgeeks.org/problems/smaller-on-left20360700/1) | [`18. Largest Smaller on Left/`](18.%20Largest%20Smaller%20on%20Left/) |
| 3 | [Make array elements unique](https://www.geeksforgeeks.org/problems/make-array-elements-unique--170645/1) | [`19. Make array elements unique/`](19.%20Make%20array%20elements%20unique/) |
| 4 | [Powerful Integer](https://www.geeksforgeeks.org/problems/powerfull-integer--170647/1) | [`23. Powerful Integer/`](23.%20Powerful%20Integer/) |
| 5 | [Surpasser Count](https://www.geeksforgeeks.org/problems/surpasser-count0615/1) | [`34. Surpasser Count/`](34.%20Surpasser%20Count/) |

## Pattern 14: One-to-One Mapping (Bijection & Lookup Tables)

Isomorphic strings and pattern matching need a bijection: keep `a→b` and `b→a` maps and fail as soon as either disagrees. Nuts and Bolts uses a fixed order map to match items. The keypad problem is a plain lookup table from each character to its key sequence.

| # | Problem | Link |
|---|---|---|
| 1 | [Nuts and Bolts Problem](https://www.geeksforgeeks.org/problems/nuts-and-bolts-problem0431/1) | [`16. Nuts and Bolts Problem/`](16.%20Nuts%20and%20Bolts%20Problem/) |

## Pattern 15: Sliding Window + Hash Map

Same-direction two pointers with a hash map of what is inside the window. For distinct-element windows, shrink until the new element is unique, then add `window length` contributions or track the best window sum.

| # | Problem | Link |
|---|---|---|
| 1 | [Maximum Sum Unique-Mapped Window](https://www.geeksforgeeks.org/problems/maximum-possible-sum4134/1) | [`43. Maximum Sum Unique-Mapped Window/`](43.%20Maximum%20Sum%20Unique-Mapped%20Window/) |
