# Hashing — Basics: Patterns

Basics-level Hashing problems (15) teach the two core tools: a frequency map (count, then query) and a seen-set (membership in O(1)). Most problems here are one counting pass followed by one question about the counts or the first occurrence.

## Pattern 1: Frequency Counting & Queries

The base hashing move: one pass to fill `count[x]`, then a second pass (over the input or the map) to answer the question. Questions include which element is unique or odd-occurring, which is most or second-most frequent, which first reaches k occurrences, whether frequencies meet a rule (prime, even, at most a limit), or how many substrings or groups the counts allow (`f*(f+1)/2`). For small value ranges, a plain array replaces the map.

| # | Problem | Link |
|---|---|---|
| 1 | [One Odd Occuring](https://www.geeksforgeeks.org/problems/find-the-odd-occurence4820/1) | [`02. One Odd Occuring/`](02.%20One%20Odd%20Occuring/) |
| 2 | [Count Group Occurrences](https://www.geeksforgeeks.org/problems/count-the-characters1821/1) | [`06. Count Group Occurrences/`](06.%20Count%20Group%20Occurrences/) |
| 3 | [Find unique element](https://www.geeksforgeeks.org/problems/find-unique-element2632/1) | [`07. Find unique element/`](07.%20Find%20unique%20element/) |
| 4 | [Highest and Lowest Frequencies](https://www.geeksforgeeks.org/problems/difference-between-highest-and-lowest-occurrence4613/1) | [`10. Highest and Lowest Frequencies/`](10.%20Highest%20and%20Lowest%20Frequencies/) |
| 5 | [Smallest Repeating K Times](https://www.geeksforgeeks.org/problems/smallest-number-repeating-k-times3239/1) | [`13. Smallest Repeating K Times/`](13.%20Smallest%20Repeating%20K%20Times/) |
| 6 | [Distinct in a Stream with Insertions and Deletions](https://www.geeksforgeeks.org/problems/distinct-elements-in-a-stream1557/1) | [`15. Distinct in a Stream with Insertions and Deletions/`](15.%20Distinct%20in%20a%20Stream%20with%20Insertions%20and%20Deletions/) |

## Pattern 2: First / Last Occurrence & Index Tracking

Order matters here, so the map holds an index, not only a count. Keep `first[x]` and/or `last[x]`. Then the earliest repeat, earliest non-repeating element, widest distance between equal values, or the k-th distinct element in input order comes from one more scan. For strings, a 26-slot array is enough.

| # | Problem | Link |
|---|---|---|
| 1 | [Repeated Character](https://www.geeksforgeeks.org/problems/repeated-character2058/1) | [`04. Repeated Character/`](04.%20Repeated%20Character/) |
| 2 | [Max Distance Between Two in Array](https://www.geeksforgeeks.org/problems/count-number-of-elements-between-two-given-elements-in-array4044/1) | [`08. Max Distance Between Two in Array/`](08.%20Max%20Distance%20Between%20Two%20in%20Array/) |
| 3 | [K-th Distinct in Order of Appearance](https://www.geeksforgeeks.org/problems/k-th-distinct-element4510/1) | [`14. K-th Distinct in Order of Appearance/`](14.%20K-th%20Distinct%20in%20Order%20of%20Appearance/) |

## Pattern 3: Seen-Set Membership / Deduplication

A set answers 'have I seen this before?' in O(1). Use it to remove or detect duplicates, check that digits or letters are all distinct or all present (isogram, pangram, fascinating number), toggle on/off states (open tabs, computers), build sequences that forbid repeats (Recaman), or detect a cycle by remembering past states (the remainder in a repeating decimal).

| # | Problem | Link |
|---|---|---|
| 1 | [Distinct-Digit Numbers in Range](https://www.geeksforgeeks.org/problems/unique-numbers3019/1) | [`12. Distinct-Digit Numbers in Range/`](12.%20Distinct-Digit%20Numbers%20in%20Range/) |

## Pattern 4: Set Operations on Collections (Union / Intersection / Subset / Disjoint)

Classic set algebra with hashing: insert array A, then scan B. Membership tests give the intersection (common elements, common across matrix rows), difference (missing in second array, uncommon characters), subset check, disjoint check, or the minimum removals to make two arrays disjoint. Union inserts both. Use a count map instead of a set when duplicates must be respected.

| # | Problem | Link |
|---|---|---|
| 1 | [Array Subset](https://www.geeksforgeeks.org/problems/array-subset-of-another-array2317/1) | [`01. Array Subset/`](01.%20Array%20Subset/) |
| 2 | [Uncommon characters](https://www.geeksforgeeks.org/problems/uncommon-characters4932/1) | [`03. Uncommon characters/`](03.%20Uncommon%20characters/) |

## Pattern 5: Frequency-Based Sorting / Top-K

After counting, the answer is an ordering. Sort by decreasing frequency (ties by value), take the top K with a heap or buckets, follow the order of another array, rebuild a string in descending order (counting sort), or greedily drop the least-frequent ids to minimise distinct count. Keeping the k smallest in original order is the same idea: pick the threshold, then filter in one pass.

| # | Problem | Link |
|---|---|---|
| 1 | [Sort String in Descending Order](https://www.geeksforgeeks.org/problems/sort-the-string-in-descending-order3542/1) | [`09. Sort String in Descending Order/`](09.%20Sort%20String%20in%20Descending%20Order/) |

## Pattern 6: Sequence Membership (Consecutive / AP / Missing / Subsequence DP)

Problems about which numbers form a run or a progression. Longest consecutive sequence starts counting only at values with no predecessor, so total work stays linear. AP checks use min, common difference, and set membership for each expected term. Missing-in-range problems scan the range against the set. Longest subsequence with adjacent diff 0 or 1 keeps `best[x] = 1 + max(best[x-1], best[x], best[x+1])` in a map.

| # | Problem | Link |
|---|---|---|
| 1 | [Check Arithmetic Progression](https://www.geeksforgeeks.org/problems/check-arithmetic-progression1842/1) | [`11. Check Arithmetic Progression/`](11.%20Check%20Arithmetic%20Progression/) |

## Pattern 7: Frequency Comparison (Anagram / Multiset Equality)

Two inputs are the same multiset if their frequency maps match. Increment for one and decrement for the other, then inspect what is left. Non-zero entries count the changes needed (k-anagram, transform string). At most one odd count means a palindrome permutation is possible. Checking each candidate removal tests if all frequencies can become equal.

| # | Problem | Link |
|---|---|---|
| 1 | [Anagram Palindrome](https://www.geeksforgeeks.org/problems/anagram-palindrome4720/1) | [`05. Anagram Palindrome/`](05.%20Anagram%20Palindrome/) |
