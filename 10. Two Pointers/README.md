# 10. Two Pointers

[← Back to root](../README.md) · [GfG topic problems](https://www.geeksforgeeks.org/explore?category%5B%5D=Two%20Pointers)

## Patterns (merged across all difficulty levels)

Same core technique shows up at every difficulty — this view merges those occurrences into one pattern, with problems ordered Basics → Easy → Medium → Hard. Logic/Time/Space are filled in as each problem's full article is written.

| # | Pattern | Logic | Typical Time | Typical Space | Total | Basics | Easy | Medium | Hard |
|---|---|---|---|---|---|---|---|---|---|
| 1 | [Opposite-Ends Pair Search (Sorted Input)](#opposite-ends-pair-search-sorted-input-12) | Sort (or use sorted input), put one pointer at each end, and move the pointer whose value pushes the pair sum toward the target — find, count, or approximate a pair. | O(n log n) with sort / O(n) if sorted | O(1) | 12 | 0 | 10 | 2 | 0 |
| 2 | [Fix One + Pair Search (3-Sum / 4-Sum / k-Sum)](#fix-one--pair-search-3-sum--4-sum--k-sum-9) | Sort, fix the outer one (or two) elements in a loop, then run opposite-ends pair search on the rest for the remaining target. | O(n^2) 3-sum / O(n^3) 4-sum | O(1) extra (excluding output) | 9 | 0 | 3 | 6 | 0 |
| 3 | [Merge-Style Scan of Sorted Sequences](#merge-style-scan-of-sorted-sequences-8) | Walk one pointer per sorted sequence (arrays, halves, or interval lists), always advancing the pointer at the smaller value — merge, union, intersect, or compare. | O(n + m) | O(1) to O(n + m) for output | 8 | 0 | 4 | 4 | 0 |
| 4 | [Palindrome / Reverse from Both Ends (Strings)](#palindrome--reverse-from-both-ends-strings-5) | Move two pointers inward from the ends of a string, comparing or swapping characters and skipping ones that do not take part (spaces, symbols). | O(n) | O(1) (O(n) if strings are immutable) | 5 | 2 | 2 | 1 | 0 |
| 5 | [Container / Greedy Shrink from Both Ends](#container--greedy-shrink-from-both-ends-4) | Start with the widest window and always move the pointer at the shorter (limiting) side — the only move that can improve a width × min(height) style objective. | O(n) | O(1) (O(n) for prefix/suffix arrays) | 4 | 0 | 1 | 3 | 0 |
| 6 | [Variable-Size Sliding Window](#variable-size-sliding-window-3) | Expand the right end, shrink the left end while the window breaks a constraint (distinct count, replacements, required chars), and record the best or count windows. | O(n) | O(alphabet) / O(k) | 3 | 0 | 0 | 3 | 0 |
| 7 | [Read-Write / Slow-Fast Pointers (In-Place)](#read-write--slow-fast-pointers-in-place-3) | A slow write pointer marks where the next kept element goes while a fast read pointer scans — or slow/fast move at different speeds to detect a cycle. | O(n) | O(1) | 3 | 0 | 2 | 1 | 0 |
| 8 | [Linear Scan with Start/End Markers](#linear-scan-with-startend-markers-3) | Single pass that marks where a run or group starts and ends (digits, brackets, positive streak) and acts when it closes. | O(n) | O(1) | 3 | 1 | 2 | 0 | 0 |
| 9 | [Multiple Split Pointers with Prefix Sums](#multiple-split-pointers-with-prefix-sums-1) | Fix the middle cut, then move left and right cut pointers monotonically on prefix sums so each side splits as evenly as possible. | O(n) | O(n) | 1 | 0 | 0 | 0 | 1 |
| | **Total (9 patterns)** | | | | **48** | **3** | **24** | **20** | **1** |

### Opposite-Ends Pair Search (Sorted Input) (12)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Pairs with 0 Sum](https://www.geeksforgeeks.org/problems/count-pairs-with-given-sum5022/1) | — | — | — | Easy | Flipkart, Accolite, Amazon, FactSet, Hike, MakeMyTrip, Goldman Sachs, Adobe, Salesforce | Arrays, Sorting, two-pointer-algorithm | [`02. Easy/01. Pairs with 0 Sum/`](02.%20Easy/01.%20Pairs%20with%200%20Sum/) |
| 2 | [Pair Sum in Sorted Doubly Linked List](https://www.geeksforgeeks.org/problems/find-pairs-with-given-sum-in-doubly-linked-list/1) | — | — | — | Easy | — | Doubly Linked List, two-pointer-algorithm | [`02. Easy/05. Pair Sum in Sorted Doubly Linked List/`](02.%20Easy/05.%20Pair%20Sum%20in%20Sorted%20Doubly%20Linked%20List/) |
| 3 | [Count Sum Pairs in Sorted](https://www.geeksforgeeks.org/problems/pair-with-given-sum-in-a-sorted-array4940/1) | — | — | — | Easy | Adobe | two-pointer-algorithm, Arrays | [`02. Easy/06. Count Sum Pairs in Sorted/`](02.%20Easy/06.%20Count%20Sum%20Pairs%20in%20Sorted/) |
| 4 | [Closest Pair Sum](https://www.geeksforgeeks.org/problems/pair-in-array-whose-sum-is-closest-to-x1124/1) | — | — | — | Easy | Ola Cabs | Arrays, two-pointer-algorithm | [`02. Easy/07. Closest Pair Sum/`](02.%20Easy/07.%20Closest%20Pair%20Sum/) |
| 5 | [Pairs with Limited Sum](https://www.geeksforgeeks.org/problems/count-pairs-whose-sum-is-less-than-target/1) | — | — | — | Easy | — | Sorting, two-pointer-algorithm, Arrays | [`02. Easy/11. Pairs with Limited Sum/`](02.%20Easy/11.%20Pairs%20with%20Limited%20Sum/) |
| 6 | [Dominant Pairs](https://www.geeksforgeeks.org/problems/dominant-pairs/1) | — | — | — | Easy | — | two-pointer-algorithm, Sorting | [`02. Easy/12. Dominant Pairs/`](02.%20Easy/12.%20Dominant%20Pairs/) |
| 7 | [Largest Pair Sum](https://www.geeksforgeeks.org/problems/pair-sum--120604/1) | — | — | — | Easy | — | two-pointer-algorithm, Arrays, Searching | [`02. Easy/13. Largest Pair Sum/`](02.%20Easy/13.%20Largest%20Pair%20Sum/) |
| 8 | [Two Sum in Sorted Array](https://www.geeksforgeeks.org/problems/two-sum-in-sorted-array/1) | — | — | — | Easy | — | two-pointer-algorithm, Arrays | [`02. Easy/18. Two Sum in Sorted Array/`](02.%20Easy/18.%20Two%20Sum%20in%20Sorted%20Array/) |
| 9 | [2 Sum - Find a pair with given sum](https://www.geeksforgeeks.org/problems/2-sum-find-a-pair-with-given-sum/1) | — | — | — | Easy | — | Sorting, two-pointer-algorithm, Arrays, Hash | [`02. Easy/20. 2 Sum - Find a pair with given sum/`](02.%20Easy/20.%202%20Sum%20-%20Find%20a%20pair%20with%20given%20sum/) |
| 10 | [Count Pairs in a sorted array whose sum is less than target](https://www.geeksforgeeks.org/problems/count-pairs-in-a-sorted-array-whose-sum-is-less-than-target/1) | — | — | — | Easy | — | two-pointer-algorithm, Arrays | [`02. Easy/23. Count Pairs in a sorted array whose sum is less than target/`](02.%20Easy/23.%20Count%20Pairs%20in%20a%20sorted%20array%20whose%20sum%20is%20less%20than%20target/) |
| 11 | [Count Pairs with Sum](https://www.geeksforgeeks.org/problems/count-pairs-with-given-sum--150253/1) | — | — | — | Medium | — | Arrays, Hash, two-pointer-algorithm | [`03. Medium/12. Count Pairs with Sum/`](03.%20Medium/12.%20Count%20Pairs%20with%20Sum/) |
| 12 | [Pair Sum in a Sorted and Rotated Array](https://www.geeksforgeeks.org/problems/pair-sum-in-a-sorted-and-rotated-array/1) | — | — | — | Medium | — | two-pointer-algorithm | [`03. Medium/17. Pair Sum in a Sorted and Rotated Array/`](03.%20Medium/17.%20Pair%20Sum%20in%20a%20Sorted%20and%20Rotated%20Array/) |

### Fix One + Pair Search (3-Sum / 4-Sum / k-Sum) (9)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Triplets Where One is Sum of Other Two](https://www.geeksforgeeks.org/problems/count-the-triplets4615/1) | — | — | — | Easy | Amazon, Arcesium | two-pointer-algorithm, Sorting | [`02. Easy/04. Triplets Where One is Sum of Other Two/`](02.%20Easy/04.%20Triplets%20Where%20One%20is%20Sum%20of%20Other%20Two/) |
| 2 | [Check for 4 Sum](https://www.geeksforgeeks.org/problems/four-elements2452/1) | — | — | — | Easy | Amazon, OYO Rooms | two-pointer-algorithm, Arrays | [`02. Easy/08. Check for 4 Sum/`](02.%20Easy/08.%20Check%20for%204%20Sum/) |
| 3 | [Distinct Triplets with Given Sum](https://www.geeksforgeeks.org/problems/find-all-distinct-triplets-with-given-sum/1) | — | — | — | Easy | — | Sorting, two-pointer-algorithm, Arrays, Hash | [`02. Easy/22. Distinct Triplets with Given Sum/`](02.%20Easy/22.%20Distinct%20Triplets%20with%20Given%20Sum/) |
| 4 | [Triplet Sum in Array](https://www.geeksforgeeks.org/problems/triplet-sum-in-array-1587115621/1) | — | — | — | Medium | Accolite, Amazon, Microsoft, OYO Rooms, Samsung, CarWale | two-pointer-algorithm, Arrays, Hash, Sorting | [`03. Medium/02. Triplet Sum in Array/`](03.%20Medium/02.%20Triplet%20Sum%20in%20Array/) |
| 5 | [Find triplets with zero sum](https://www.geeksforgeeks.org/problems/find-triplets-with-zero-sum/1) | — | — | — | Medium | Amazon, Google, Facebook | two-pointer-algorithm, Arrays, Searching, Hash, Sorting | [`03. Medium/04. Find triplets with zero sum/`](03.%20Medium/04.%20Find%20triplets%20with%20zero%20sum/) |
| 6 | [4 Sum - All Quadruples](https://www.geeksforgeeks.org/problems/find-all-four-sum-numbers1732/1) | — | — | — | Medium | Amazon, Microsoft, OYO Rooms, Adobe, Google, NPCI | Hash, Sorting, two-pointer-algorithm | [`03. Medium/07. 4 Sum - All Quadruples/`](03.%20Medium/07.%204%20Sum%20-%20All%20Quadruples/) |
| 7 | [Triplets with Smaller Sum](https://www.geeksforgeeks.org/problems/count-triplets-with-sum-smaller-than-x5549/1) | — | — | — | Medium | Amazon, SAP Labs | two-pointer-algorithm, Arrays | [`03. Medium/09. Triplets with Smaller Sum/`](03.%20Medium/09.%20Triplets%20with%20Smaller%20Sum/) |
| 8 | [Closest Three Sum](https://www.geeksforgeeks.org/problems/three-sum-closest/1) | — | — | — | Medium | Amazon, Microsoft, Google, Apple, Facebook, Adobe, Zoho, NPCI, Uber | Arrays, Hash, two-pointer-algorithm | [`03. Medium/11. Closest Three Sum/`](03.%20Medium/11.%20Closest%20Three%20Sum/) |
| 9 | [Count all triplets with given sum in sorted array](https://www.geeksforgeeks.org/problems/count-all-triplets-with-given-sum-in-sorted-array/1) | — | — | — | Medium | — | two-pointer-algorithm, Hash | [`03. Medium/13. Count all triplets with given sum in sorted array/`](03.%20Medium/13.%20Count%20all%20triplets%20with%20given%20sum%20in%20sorted%20array/) |

### Merge-Style Scan of Sorted Sequences (8)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Intersection of Arrays with Distinct](https://www.geeksforgeeks.org/problems/intersection-of-two-arrays2404/1) | — | — | — | Easy | Accolite, Amazon, Microsoft, PayPal, Rockstand | two-pointer-algorithm, Arrays, Hash | [`02. Easy/03. Intersection of Arrays with Distinct/`](02.%20Easy/03.%20Intersection%20of%20Arrays%20with%20Distinct/) |
| 2 | [Intersection of Two arrays with Duplicate Elements](https://www.geeksforgeeks.org/problems/intersection-of-two-arrays-with-duplicate-elements/1) | — | — | — | Easy | — | Sorting, two-pointer-algorithm, Arrays, Hash | [`02. Easy/10. Intersection of Two arrays with Duplicate Elements/`](02.%20Easy/10.%20Intersection%20of%20Two%20arrays%20with%20Duplicate%20Elements/) |
| 3 | [Sort Two Parts  Sorted](https://www.geeksforgeeks.org/problems/sort-the-half-sorted2157/1) | — | — | — | Easy | — | two-pointer-algorithm, Sorting | [`02. Easy/19. Sort Two Parts Sorted/`](02.%20Easy/19.%20Sort%20Two%20Parts%20Sorted/) |
| 4 | [Closest Triplet Diff in Three Arrays](https://www.geeksforgeeks.org/problems/closest-triplet3807/1) | — | — | — | Easy | — | two-pointer-algorithm | [`02. Easy/24. Closest Triplet Diff in Three Arrays/`](02.%20Easy/24.%20Closest%20Triplet%20Diff%20in%20Three%20Arrays/) |
| 5 | [Union of 2 Sorted Arrays](https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays-1587115621/1) | — | — | — | Medium | Amazon | Arrays, two-pointer-algorithm | [`03. Medium/01. Union of 2 Sorted Arrays/`](03.%20Medium/01.%20Union%20of%202%20Sorted%20Arrays/) |
| 6 | [Merge Without Extra Space](https://www.geeksforgeeks.org/problems/merge-two-sorted-arrays-1587115620/1) | — | — | — | Medium | Zoho, Microsoft, Snapdeal, Goldman Sachs, Adobe, Linkedin, Amdocs, Brocade, Juniper Networks, Quikr, Synopsys | Sorting, Arrays, two-pointer-algorithm | [`03. Medium/05. Merge Without Extra Space/`](03.%20Medium/05.%20Merge%20Without%20Extra%20Space/) |
| 7 | [Earliest Common Slot](https://www.geeksforgeeks.org/problems/earliest-common-slot/1) | — | — | — | Medium | Amazon, Microsoft, PayPal, Google, Uber | Sorting, two-pointer-algorithm, Arrays | [`03. Medium/19. Earliest Common Slot/`](03.%20Medium/19.%20Earliest%20Common%20Slot/) |
| 8 | [Interval List Intersections](https://www.geeksforgeeks.org/problems/interval-list-intersections/1) | — | — | — | Medium | Bloomberg, Amazon, Microsoft, Google, Uber | two-pointer-algorithm, Arrays | [`03. Medium/20. Interval List Intersections/`](03.%20Medium/20.%20Interval%20List%20Intersections/) |

### Palindrome / Reverse from Both Ends (Strings) (5)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Palindrome String](https://www.geeksforgeeks.org/problems/palindrome-string0817/1) | — | — | — | Basics | Paytm, Zoho, Morgan Stanley, Amazon, D-E-Shaw, FactSet, Cisco, Facebook | Strings, two-pointer-algorithm | [`01. Basics/01. Palindrome String/`](01.%20Basics/01.%20Palindrome%20String/) |
| 2 | [Reverse String with Spaces Intact](https://www.geeksforgeeks.org/problems/reverse-a-string-with-spaces-intact5213/1) | — | — | — | Basics | Zoho | two-pointer-algorithm, Strings | [`01. Basics/03. Reverse String with Spaces Intact/`](01.%20Basics/03.%20Reverse%20String%20with%20Spaces%20Intact/) |
| 3 | [Palindrome Sentence](https://www.geeksforgeeks.org/problems/string-palindromic-ignoring-spaces4723/1) | — | — | — | Easy | Facebook | two-pointer-algorithm, Strings, palindrome | [`02. Easy/09. Palindrome Sentence/`](02.%20Easy/09.%20Palindrome%20Sentence/) |
| 4 | [Special String Reversal](https://www.geeksforgeeks.org/problems/special-array-reversal2328/1) | — | — | — | Easy | Zoho | two-pointer-algorithm, Strings | [`02. Easy/15. Special String Reversal/`](02.%20Easy/15.%20Special%20String%20Reversal/) |
| 5 | [Remove and Reverse](https://www.geeksforgeeks.org/problems/remove-and-reverse--170634/1) | — | — | — | Medium | — | two-pointer-algorithm, Arrays, Strings | [`03. Medium/15. Remove and Reverse/`](03.%20Medium/15.%20Remove%20and%20Reverse/) |

### Container / Greedy Shrink from Both Ends (4)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Max of Index Diff and Min Value Product](https://www.geeksforgeeks.org/problems/find-maximum-value/1) | — | — | — | Easy | — | Arrays, two-pointer-algorithm | [`02. Easy/21. Max of Index Diff and Min Value Product/`](02.%20Easy/21.%20Max%20of%20Index%20Diff%20and%20Min%20Value%20Product/) |
| 2 | [Maximum Index](https://www.geeksforgeeks.org/problems/maximum-index-1587115620/1) | — | — | — | Medium | VMWare, Amazon, Microsoft, MakeMyTrip, Google, Snapdeal | Arrays, two-pointer-algorithm | [`03. Medium/03. Maximum Index/`](03.%20Medium/03.%20Maximum%20Index/) |
| 3 | [Container With Most Water](https://www.geeksforgeeks.org/problems/container-with-most-water0535/1) | — | — | — | Medium | Flipkart, Amazon, Google | Arrays, Mathematics, two-pointer-algorithm | [`03. Medium/10. Container With Most Water/`](03.%20Medium/10.%20Container%20With%20Most%20Water/) |
| 4 | [Maximum Area Between Bars](https://www.geeksforgeeks.org/problems/maximum-area-between-bars/1) | — | — | — | Medium | — | two-pointer-algorithm | [`03. Medium/16. Maximum Area Between Bars/`](03.%20Medium/16.%20Maximum%20Area%20Between%20Bars/) |

### Variable-Size Sliding Window (3)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Longest Substring with K Uniques](https://www.geeksforgeeks.org/problems/longest-k-unique-characters-substring0853/1) | — | — | — | Medium | Amazon, Google, SAP Labs | two-pointer-algorithm, Hash, Strings, Map | [`03. Medium/06. Longest Substring with K Uniques/`](03.%20Medium/06.%20Longest%20Substring%20with%20K%20Uniques/) |
| 2 | [Longest Repeating Character Replacement](https://www.geeksforgeeks.org/problems/longest-repeating-character-replacement/1) | — | — | — | Medium | Amazon | two-pointer-algorithm, Strings | [`03. Medium/14. Longest Repeating Character Replacement/`](03.%20Medium/14.%20Longest%20Repeating%20Character%20Replacement/) |
| 3 | [Count Substrings with a, b and c](https://www.geeksforgeeks.org/problems/count-substring/1) | — | — | — | Medium | — | two-pointer-algorithm | [`03. Medium/18. Count Substrings with a, b and c/`](03.%20Medium/18.%20Count%20Substrings%20with%20a,%20b%20and%20c/) |

### Read-Write / Slow-Fast Pointers (In-Place) (3)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Remove Duplicates Sorted Array](https://www.geeksforgeeks.org/problems/remove-duplicate-elements-from-sorted-array/1) | — | — | — | Easy | Zoho, Morgan Stanley, Microsoft, Samsung, Google, Wipro, Xome | two-pointer-algorithm, Arrays | [`02. Easy/02. Remove Duplicates Sorted Array/`](02.%20Easy/02.%20Remove%20Duplicates%20Sorted%20Array/) |
| 2 | [Find Only Repetitive Element from 1 to n-1](https://www.geeksforgeeks.org/problems/find-repetitive-element-from-1-to-n-1/1) | — | — | — | Easy | NPCI | two-pointer-algorithm, Arrays | [`02. Easy/14. Find Only Repetitive Element from 1 to n-1/`](02.%20Easy/14.%20Find%20Only%20Repetitive%20Element%20from%201%20to%20n-1/) |
| 3 | [Binary Array Sorting](https://www.geeksforgeeks.org/problems/binary-array-sorting-1587115620/1) | — | — | — | Medium | — | Sorting, Arrays, two-pointer-algorithm | [`03. Medium/08. Binary Array Sorting/`](03.%20Medium/08.%20Binary%20Array%20Sorting/) |

### Linear Scan with Start/End Markers (3)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Extract Integers from String](https://www.geeksforgeeks.org/problems/extract-the-integers4428/1) | — | — | — | Basics | — | two-pointer-algorithm, Strings | [`01. Basics/02. Extract Integers from String/`](01.%20Basics/02.%20Extract%20Integers%20from%20String/) |
| 2 | [Length of longest subarray](https://www.geeksforgeeks.org/problems/length-of-longest-subarray0440/1) | — | — | — | Easy | — | two-pointer-algorithm, Arrays | [`02. Easy/16. Length of longest subarray/`](02.%20Easy/16.%20Length%20of%20longest%20subarray/) |
| 3 | [Closing Bracket Index](https://www.geeksforgeeks.org/problems/closing-bracket-index5900/1) | — | — | — | Easy | — | Strings, two-pointer-algorithm | [`02. Easy/17. Closing Bracket Index/`](02.%20Easy/17.%20Closing%20Bracket%20Index/) |

### Multiple Split Pointers with Prefix Sums (1)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Partition Into 4 with Min Sum Diff](https://www.geeksforgeeks.org/problems/partition-the-array--170647/1) | — | — | — | Hard | — | two-pointer-algorithm, Arrays, Binary Search | [`04. Hard/01. Partition Into 4 with Min Sum Diff/`](04.%20Hard/01.%20Partition%20Into%204%20with%20Min%20Sum%20Diff/) |
