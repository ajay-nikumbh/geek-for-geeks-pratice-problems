# Strings — Hard: Patterns

Hard-level Strings problems (9) are dominated by linear-time pattern matching (KMP, Z, Rabin-Karp and the LPS array), plus regex matching DP, sorted permutation generation, k-th character of an expanded string, and the smallest rotation.

## Pattern 1: Pattern Matching & Rotation (Naive / KMP / Z / Rabin-Karp)

Substring search at the core. The naive method tries every start. KMP builds the longest-proper-prefix-that-is-also-suffix (LPS) array so the text pointer never moves back. The Z-array gives the match length at each position. Rabin-Karp compares rolling hashes and checks on a hit. Many problems reduce to these: a rotation of `s` is a substring of `s + s`, the minimum characters to make a palindrome come from the LPS of `s + '$' + reverse(s)`, and a repeated-substring check uses `n % (n - lps) == 0`.

| # | Problem | Link |
|---|---|---|
| 1 | [Search Pattern](https://www.geeksforgeeks.org/problems/search-pattern0205/1) | [`01. Search Pattern/`](01.%20Search%20Pattern/) |
| 2 | [Longest Prefix Suffix](https://www.geeksforgeeks.org/problems/longest-prefix-suffix2527/1) | [`02. Longest Prefix Suffix/`](02.%20Longest%20Prefix%20Suffix/) |
| 3 | [Min Chars to Add for Palindrome](https://www.geeksforgeeks.org/problems/minimum-characters-to-be-added-at-front-to-make-string-palindrome/1) | [`03. Min Chars to Add for Palindrome/`](03.%20Min%20Chars%20to%20Add%20for%20Palindrome/) |
| 4 | [Search Pattern (Rabin-Karp Algorithm)](https://www.geeksforgeeks.org/problems/search-pattern-rabin-karp-algorithm--141631/1) | [`04. Search Pattern (Rabin-Karp Algorithm)/`](04.%20Search%20Pattern%20(Rabin-Karp%20Algorithm)/) |
| 5 | [Max Occurring Prefix Suffix Substring](https://www.geeksforgeeks.org/problems/elixir-of-life--141631/1) | [`07. Max Occurring Prefix Suffix Substring/`](07.%20Max%20Occurring%20Prefix%20Suffix%20Substring/) |

## Pattern 2: Lexicographic Comparison & Sorting

Lexicographic order decides the answer. Longest common prefix compares the first and last strings after sorting, or all strings column by column. Smallest and largest strings in a list come from one comparison pass. Custom comparisons treat a multi-letter unit as one character or ignore case. The lexicographically largest substring is the largest suffix. The smallest rotation compares candidate starts on `s + s` (or uses Booth's algorithm).

| # | Problem | Link |
|---|---|---|
| 1 | [Lexicographically Smallest Rotation](https://www.geeksforgeeks.org/problems/lexicographically-smallest-string--151951/1) | [`09. Lexicographically Smallest Rotation/`](09.%20Lexicographically%20Smallest%20Rotation/) |

## Pattern 3: Recursion, Backtracking & Generation

The output is a list of strings, so recursion builds them. At each position, try every allowed character, recurse, then undo. Pruning keeps it fast: track the count of 1s versus 0s for prefix rules, skip repeated characters at the same depth for distinct permutations, and build only half of a palindrome. Additive sequence checks try every split of the first two numbers and recurse on the rest.

| # | Problem | Link |
|---|---|---|
| 1 | [All String Permutations in Sorted Order](https://www.geeksforgeeks.org/problems/permutations-of-a-given-string-1587115620/1) | [`05. All String Permutations in Sorted Order/`](05.%20All%20String%20Permutations%20in%20Sorted%20Order/) |

## Pattern 4: Implicit Expansion & K-th Character

The string is defined by repeated expansion (repeat counts, binary transformations, infinite doubling) and would be far too long to build. Track how long each stage would be. To find the k-th character, go backwards: reduce `k` modulo the repeat length, or map it back through each transformation step. Binary transformation versions use the parity of set bits or the block that `k` falls in.

| # | Problem | Link |
|---|---|---|
| 1 | [Print kth Character](https://www.geeksforgeeks.org/problems/print-kth-character-in-sorted-concatenated-substrings-of-a-string0302/1) | [`08. Print kth Character/`](08.%20Print%20kth%20Character/) |

## Pattern 5: Dynamic Programming on Strings

Overlapping subproblems over prefixes. `dp[i][j]` asks whether (or how cheaply) the first `i` characters of one string can produce the first `j` of another. Regex matching handles `.` and `*` by looking back one or two pattern characters. String conversion decides per character whether to capitalise or delete. Chain problems keep the best length ending at each character. Copy-paste minimum operations build up from divisors.

| # | Problem | Link |
|---|---|---|
| 1 | [RegEx  Matching](https://www.geeksforgeeks.org/problems/-regex-matching1145/1) | [`06. RegEx Matching/`](06.%20RegEx%20Matching/) |
