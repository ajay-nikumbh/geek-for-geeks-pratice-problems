# Strings — Medium: Patterns

Medium-level Strings problems (58) lean on structure: parsing with state machines (atoi, IP validation, comment removal), full big-number arithmetic (multiply, factorial), KMP-based rotation and palindrome checks, recursion over generated strings, and implicit expansion where the k-th character is found without building the string.

## Pattern 1: Character Frequency Counting & Comparison

Count each character in one pass, then answer from the counts. Single-string questions ask for the most frequent character, the first repeat, distinct count, or missing letters (pangram). Two-string questions compare count arrays: the sum of absolute differences gives removals for an anagram, half of it gives replacements, and set-style checks find common or uncommon characters. Word-level versions use a hash map keyed by word.

| # | Problem | Link |
|---|---|---|
| 1 | [Check Repeated Substring with K Replacements](https://www.geeksforgeeks.org/problems/check-if-a-string-is-repetition-of-its-substring-of-k-length3302/1) | [`13. Check Repeated Substring with K Replacements/`](13.%20Check%20Repeated%20Substring%20with%20K%20Replacements/) |
| 2 | [Exactly one swap](https://www.geeksforgeeks.org/problems/exactly-one-swap--170637/1) | [`19. Exactly one swap/`](19.%20Exactly%20one%20swap/) |
| 3 | [Sum of Beauty of All Substrings](https://www.geeksforgeeks.org/problems/sum-of-beauty-of-all-substrings-1662962118/1) | [`25. Sum of Beauty of All Substrings/`](25.%20Sum%20of%20Beauty%20of%20All%20Substrings/) |
| 4 | [Maximum Reachable Index Difference](https://www.geeksforgeeks.org/problems/maximum-reachable-index-difference/1) | [`32. Maximum Reachable Index Difference/`](32.%20Maximum%20Reachable%20Index%20Difference/) |
| 5 | [Concatenate Equal to Target](https://www.geeksforgeeks.org/problems/concatenate-equal-to-target/1) | [`45. Concatenate Equal to Target/`](45.%20Concatenate%20Equal%20to%20Target/) |

## Pattern 2: Big Number Arithmetic & Digit Divisibility

The number is too large for built-in types, so work on its digits. Addition and binary addition walk from the right with a carry. Multiplication accumulates partial products into a result array. Division and modulus keep a running remainder `r = (r*10 + d) % k` from the left. Divisibility by 4, 5, 11, or 999 uses the known shortcut (last two digits, last digit, alternating sum, groups of three). Comparing large numbers checks length first, then digits.

| # | Problem | Link |
|---|---|---|
| 1 | [Multiply Two Strings](https://www.geeksforgeeks.org/problems/multiply-two-strings/1) | [`04. Multiply Two Strings/`](04.%20Multiply%20Two%20Strings/) |
| 2 | [Factorials of Large](https://www.geeksforgeeks.org/problems/factorials-of-large-numbers2508/1) | [`06. Factorials of Large/`](06.%20Factorials%20of%20Large/) |
| 3 | [Sum Two Large Numbers](https://www.geeksforgeeks.org/problems/sum-of-numbers-or-number1219/1) | [`07. Sum Two Large Numbers/`](07.%20Sum%20Two%20Large%20Numbers/) |
| 4 | [Add Binary Strings](https://www.geeksforgeeks.org/problems/add-binary-strings3805/1) | [`08. Add Binary Strings/`](08.%20Add%20Binary%20Strings/) |

## Pattern 3: Parsing & Format / Base Conversion

The input follows a grammar, and the job is to read it correctly. Extract integers from mixed text, convert Roman numerals both ways (subtract when a smaller value precedes a larger one), implement atoi with sign and overflow checks, validate IP addresses, and read times and dates. Base-style conversions (Excel columns, numbers built from a fixed digit set) are repeated division by the base with an offset. Comment removal and length-prefixed encoding use a small state machine.

| # | Problem | Link |
|---|---|---|
| 1 | [Validate an IP Address](https://www.geeksforgeeks.org/problems/validate-an-ip-address-1587115621/1) | [`02. Validate an IP Address/`](02.%20Validate%20an%20IP%20Address/) |
| 2 | [Implement Atoi](https://www.geeksforgeeks.org/problems/implement-atoi/1) | [`03. Implement Atoi/`](03.%20Implement%20Atoi/) |
| 3 | [Excel Column Name from Number](https://www.geeksforgeeks.org/problems/column-name-from-a-given-column-number4244/1) | [`09. Excel Column Name from Number/`](09.%20Excel%20Column%20Name%20from%20Number/) |
| 4 | [Nth Number with Prime Digits](https://www.geeksforgeeks.org/problems/nth-number-made-of-prime-digits4319/1) | [`24. Nth Number with Prime Digits/`](24.%20Nth%20Number%20with%20Prime%20Digits/) |
| 5 | [Leading Zeros in IP Address Style String](https://www.geeksforgeeks.org/problems/remove-leading-zeros-from-an-ip-address3530/1) | [`40. Leading Zeros in IP Address Style String/`](40.%20Leading%20Zeros%20in%20IP%20Address%20Style%20String/) |
| 6 | [Encode and Decode Strings](https://www.geeksforgeeks.org/problems/encode-and-decode-strings/1) | [`44. Encode and Decode Strings/`](44.%20Encode%20and%20Decode%20Strings/) |
| 7 | [Missing in  String of Consecutive Numbers](https://www.geeksforgeeks.org/problems/find-the-missing-no-in-string/1) | [`48. Missing in String of Consecutive Numbers/`](48.%20Missing%20in%20String%20of%20Consecutive%20Numbers/) |
| 8 | [Comment Removal](https://www.geeksforgeeks.org/problems/comment-removal2017/1) | [`51. Comment Removal/`](51.%20Comment%20Removal/) |
| 9 | [Longest Arithmetic Progression in a String](https://www.geeksforgeeks.org/problems/archana-and-her-tricky-string2910/1) | [`55. Longest Arithmetic Progression in a String/`](55.%20Longest%20Arithmetic%20Progression%20in%20a%20String/) |

## Pattern 4: Pattern Matching & Rotation (Naive / KMP / Z / Rabin-Karp)

Substring search at the core. The naive method tries every start. KMP builds the longest-proper-prefix-that-is-also-suffix (LPS) array so the text pointer never moves back. The Z-array gives the match length at each position. Rabin-Karp compares rolling hashes and checks on a hit. Many problems reduce to these: a rotation of `s` is a substring of `s + s`, the minimum characters to make a palindrome come from the LPS of `s + '$' + reverse(s)`, and a repeated-substring check uses `n % (n - lps) == 0`.

| # | Problem | Link |
|---|---|---|
| 1 | [Strings Rotations of Each Other](https://www.geeksforgeeks.org/problems/check-if-strings-are-rotations-of-each-other-or-not-1587115620/1) | [`01. Strings Rotations of Each Other/`](01.%20Strings%20Rotations%20of%20Each%20Other/) |
| 2 | [Cat and Hat](https://www.geeksforgeeks.org/problems/cat-and-hat-python/1) | [`17. Cat and Hat/`](17.%20Cat%20and%20Hat/) |
| 3 | [Add Minimum Characters](https://www.geeksforgeeks.org/problems/add-minimum-characters--170648/1) | [`18. Add Minimum Characters/`](18.%20Add%20Minimum%20Characters/) |
| 4 | [String formation from substring](https://www.geeksforgeeks.org/problems/string-formation-from-substring2734/1) | [`21. String formation from substring/`](21.%20String%20formation%20from%20substring/) |
| 5 | [Case Insensitive Search](https://www.geeksforgeeks.org/problems/case-insensitive-search/1) | [`58. Case Insensitive Search/`](58.%20Case%20Insensitive%20Search/) |

## Pattern 5: Greedy Digit / Character Choice & Next Permutation

The leftmost position matters most, so decide it first. For one swap, find the first position that can be improved and swap with the best digit to its right (the last occurrence for largest). Next and previous permutation find the pivot from the right, swap with the nearest larger or smaller digit, and reverse the suffix. Other variants keep the best prefix (string mirror), choose + or * per digit, or place characters so no rule is broken.

| # | Problem | Link |
|---|---|---|
| 1 | [Alternate Vowel and Consonant String](https://www.geeksforgeeks.org/problems/alternate-vowel-and-consonant-string2939/1) | [`20. Alternate Vowel and Consonant String/`](20.%20Alternate%20Vowel%20and%20Consonant%20String/) |
| 2 | [Maximum Length](https://www.geeksforgeeks.org/problems/maximum-length--170647/1) | [`22. Maximum Length/`](22.%20Maximum%20Length/) |
| 3 | [Next Palindromic with Same Digits](https://www.geeksforgeeks.org/problems/next-higher-palindromic-number-using-the-same-set-of-digits5859/1) | [`34. Next Palindromic with Same Digits/`](34.%20Next%20Palindromic%20with%20Same%20Digits/) |
| 4 | [Previous Number in One Swap](https://www.geeksforgeeks.org/problems/previous-number-in-one-swap5707/1) | [`39. Previous Number in One Swap/`](39.%20Previous%20Number%20in%20One%20Swap/) |
| 5 | [Next Greater with One Swap](https://www.geeksforgeeks.org/problems/next-higher-number-in-one-swap1703/1) | [`50. Next Greater with One Swap/`](50.%20Next%20Greater%20with%20One%20Swap/) |

## Pattern 6: String Building & Simulation

No trick, just follow the process exactly. Interleave two strings, concatenate and reverse, URL-encode spaces, format a license key, emit Fizz Buzz, simulate robot moves to see if they return to the origin, track a rotation offset across queries, lay out characters in zig-zag rows, or justify text to a fixed width. Use a mutable buffer so each append is O(1).

| # | Problem | Link |
|---|---|---|
| 1 | [Minimum Days](https://www.geeksforgeeks.org/problems/minimum-days--170646/1) | [`28. Minimum Days/`](28.%20Minimum%20Days/) |
| 2 | [Concatenation of Zig-Zag String in n Rows](https://www.geeksforgeeks.org/problems/concatenation-of-zig-zag-string-in-n-rows0308/1) | [`36. Concatenation of Zig-Zag String in n Rows/`](36.%20Concatenation%20of%20Zig-Zag%20String%20in%20n%20Rows/) |
| 3 | [Rotate String Queries](https://www.geeksforgeeks.org/problems/lazy-pasha1646/1) | [`38. Rotate String Queries/`](38.%20Rotate%20String%20Queries/) |
| 4 | [Find and Replace in String](https://www.geeksforgeeks.org/problems/find-an-replace-in-string/1) | [`41. Find and Replace in String/`](41.%20Find%20and%20Replace%20in%20String/) |
| 5 | [Justified Text](https://www.geeksforgeeks.org/problems/justified-text/1) | [`57. Justified Text/`](57.%20Justified%20Text/) |

## Pattern 7: Two Pointers, Reversal & Palindromes

Mirrored positions decide the answer. Swap `s[l]` and `s[r]` to reverse, or compare them to test a palindrome, skipping characters that do not take part. Palindrome variants count mismatches to fix with replacements, test all rotations, or note that any string is removable in at most two palindromic subsequences. Same-direction pointers over two strings check subsequence membership or simulate moves from the end.

| # | Problem | Link |
|---|---|---|
| 1 | [String stack](https://www.geeksforgeeks.org/problems/string-stack--165812/1) | [`23. String stack/`](23.%20String%20stack/) |
| 2 | [Longest Matching in Dictionary with Removals](https://www.geeksforgeeks.org/problems/find-largest-word-in-dictionary2430/1) | [`27. Longest Matching in Dictionary with Removals/`](27.%20Longest%20Matching%20in%20Dictionary%20with%20Removals/) |
| 3 | [Palindrome with Replacement](https://www.geeksforgeeks.org/problems/palindrome-with-minimum-sum--170648/1) | [`29. Palindrome with Replacement/`](29.%20Palindrome%20with%20Replacement/) |
| 4 | [Special Palindrome Substrings](https://www.geeksforgeeks.org/problems/special-palindrome-substrings--170647/1) | [`35. Special Palindrome Substrings/`](35.%20Special%20Palindrome%20Substrings/) |
| 5 | [Count Special Palindromic Substrings](https://www.geeksforgeeks.org/problems/count-special-palindromic0421/1) | [`52. Count Special Palindromic Substrings/`](52.%20Count%20Special%20Palindromic%20Substrings/) |

## Pattern 8: Case Conversion & Character Mapping (ASCII Arithmetic)

Each character maps to another by a fixed rule. Case changes add or subtract 32 (or use `tolower`/`toupper`). Mirroring uses `'a' + 'z' - c`. Keypad and digit-swap problems use a small lookup table. Camel case and snake case conversions combine the mapping with a check for word boundaries. The work is one pass with constant-time work per character.

| # | Problem | Link |
|---|---|---|
| 1 | [Convert Sentence to Camel Case](https://www.geeksforgeeks.org/problems/convert-sentence-to-camel-case/1) | [`43. Convert Sentence to Camel Case/`](43.%20Convert%20Sentence%20to%20Camel%20Case/) |

## Pattern 9: Consecutive Runs & Grouping

Many problems depend on blocks of equal adjacent characters. Track where the current run started and its length. When the character changes, emit the run (run-length encoding, look-and-say), collapse it to one character, update the longest run, or check that each character forms one block. Binary-string checks such as 'all 0s together' or '0 between 1s' are run counts in disguise.

| # | Problem | Link |
|---|---|---|
| 1 | [Look and Say Pattern](https://www.geeksforgeeks.org/problems/decode-the-pattern1138/1) | [`16. Look and Say Pattern/`](16.%20Look%20and%20Say%20Pattern/) |

## Pattern 10: Counting & Combinatorics on Strings

The answer is a count, and enumeration is too slow. Substrings with 1s at both ends are `c*(c-1)/2` for `c` ones. Substrings ending at an even digit add `i + 1` for each such position. Sum of all digit subsequences is `digitSum * 2^(n-1)`. Permutation rank uses the factorial number system. Equation solutions use stars and bars. Bounded-letter strings of length n come from a small case formula.

| # | Problem | Link |
|---|---|---|
| 1 | [Rank The Permutations](https://www.geeksforgeeks.org/problems/rank-the-permutations2229/1) | [`14. Rank The Permutations/`](14.%20Rank%20The%20Permutations/) |
| 2 | [Count Unique Vowel Strings](https://www.geeksforgeeks.org/problems/count-unique-vowel-strings/1) | [`33. Count Unique Vowel Strings/`](33.%20Count%20Unique%20Vowel%20Strings/) |
| 3 | [Number of Positive Integral Solutions](https://www.geeksforgeeks.org/problems/number-of-positive-integral-solutions2115/1) | [`42. Number of Positive Integral Solutions/`](42.%20Number%20of%20Positive%20Integral%20Solutions/) |

## Pattern 11: Recursion, Backtracking & Generation

The output is a list of strings, so recursion builds them. At each position, try every allowed character, recurse, then undo. Pruning keeps it fast: track the count of 1s versus 0s for prefix rules, skip repeated characters at the same depth for distinct permutations, and build only half of a palindrome. Additive sequence checks try every split of the first two numbers and recurse on the rest.

| # | Problem | Link |
|---|---|---|
| 1 | [Check Sum String](https://www.geeksforgeeks.org/problems/additive-sequence/1) | [`10. Check Sum String/`](10.%20Check%20Sum%20String/) |
| 2 | [Binary Numbers with More 1s in All Prefixes](https://www.geeksforgeeks.org/problems/print-n-bit-binary-numbers-having-more-1s-than-0s0252/1) | [`15. Binary Numbers with More 1s in All Prefixes/`](15.%20Binary%20Numbers%20with%20More%201s%20in%20All%20Prefixes/) |
| 3 | [Numbers with Adjacent Digit Diff as 1](https://www.geeksforgeeks.org/problems/numbers-with-one-absolute-difference2416/1) | [`31. Numbers with Adjacent Digit Diff as 1/`](31.%20Numbers%20with%20Adjacent%20Digit%20Diff%20as%201/) |
| 4 | [Palindromic Permutations](https://www.geeksforgeeks.org/problems/pallindrome-patterns0809/1) | [`49. Palindromic Permutations/`](49.%20Palindromic%20Permutations/) |

## Pattern 12: Prefix Balance & Running Counts

Turn characters into +1/-1 (or a value) and keep a running sum. A split point where both sides balance is where the prefix and suffix counts agree. Longest balanced substring and equal upper/lower counts look up earlier equal prefixes. Roll operations use a difference array on prefix sums. Maximum-weight substring is Kadane's algorithm over character values.

| # | Problem | Link |
|---|---|---|
| 1 | [Maximum ASCII Sum Substring](https://www.geeksforgeeks.org/problems/save-your-life4601/1) | [`26. Maximum ASCII Sum Substring/`](26.%20Maximum%20ASCII%20Sum%20Substring/) |
| 2 | [Roll Characters of String](https://www.geeksforgeeks.org/problems/roll-the-characters-of-a-string2127/1) | [`37. Roll Characters of String/`](37.%20Roll%20Characters%20of%20String/) |

## Pattern 13: Stack-Based Reduction

Removals that can expose new removable neighbours need a stack. Push each character. If the top of the stack plus the new character forms a deletable pattern (two equal, three equal, 'ac', '100'), pop instead. What remains on the stack is the answer, and indices on the stack give the longest removable segment. The decreasing/increasing number pattern uses a stack to reverse each run of 'D'.

| # | Problem | Link |
|---|---|---|
| 1 | [Recursively Remove All Adjacent Duplicates](https://www.geeksforgeeks.org/problems/recursively-remove-all-adjacent-duplicates0744/1) | [`05. Recursively Remove All Adjacent Duplicates/`](05.%20Recursively%20Remove%20All%20Adjacent%20Duplicates/) |
| 2 | [Form Number using Pattern](https://www.geeksforgeeks.org/problems/number-following-a-pattern3126/1) | [`12. Form Number using Pattern/`](12.%20Form%20Number%20using%20Pattern/) |

## Pattern 14: Implicit Expansion & K-th Character

The string is defined by repeated expansion (repeat counts, binary transformations, infinite doubling) and would be far too long to build. Track how long each stage would be. To find the k-th character, go backwards: reduce `k` modulo the repeat length, or map it back through each transformation step. Binary transformation versions use the parity of set bits or the block that `k` falls in.

| # | Problem | Link |
|---|---|---|
| 1 | [N-th after Binary String Expansion](https://www.geeksforgeeks.org/problems/find-the-n-th-character5925/1) | [`11. N-th after Binary String Expansion/`](11.%20N-th%20after%20Binary%20String%20Expansion/) |
| 2 | [Kth Character After Binary String Transformations](https://www.geeksforgeeks.org/problems/find-k-th-character-in-string3841/1) | [`30. Kth Character After Binary String Transformations/`](30.%20Kth%20Character%20After%20Binary%20String%20Transformations/) |
| 3 | [The Infinite String](https://www.geeksforgeeks.org/problems/the-infinite-string1049/1) | [`54. The Infinite String/`](54.%20The%20Infinite%20String/) |

## Pattern 15: Dynamic Programming on Strings

Overlapping subproblems over prefixes. `dp[i][j]` asks whether (or how cheaply) the first `i` characters of one string can produce the first `j` of another. Regex matching handles `.` and `*` by looking back one or two pattern characters. String conversion decides per character whether to capitalise or delete. Chain problems keep the best length ending at each character. Copy-paste minimum operations build up from divisors.

| # | Problem | Link |
|---|---|---|
| 1 | [Minimum Operations to Print 'A' N Times](https://www.geeksforgeeks.org/problems/special-keyboard-2/1) | [`46. Minimum Operations to Print 'A' N Times/`](46.%20Minimum%20Operations%20to%20Print%20'A'%20N%20Times/) |
| 2 | [Max Chain Length with Matching Endpoints](https://www.geeksforgeeks.org/problems/combine-the-strings3459/1) | [`47. Max Chain Length with Matching Endpoints/`](47.%20Max%20Chain%20Length%20with%20Matching%20Endpoints/) |
| 3 | [Mapped String](https://www.geeksforgeeks.org/problems/mapped-string0501/1) | [`56. Mapped String/`](56.%20Mapped%20String/) |

## Pattern 16: Binary Strings & Bit Manipulation

Problems where the string is a bit pattern or bit operations do the work. Unset or rotate bits with masks and shifts. Minimum flips to an alternating string counts mismatches against both '0101...' and '1010...' and takes the smaller. XOR cipher recovers the original by XORing adjacent prefix values.

| # | Problem | Link |
|---|---|---|
| 1 | [XOR Cipher](https://www.geeksforgeeks.org/problems/xor-cipher3009/1) | [`53. XOR Cipher/`](53.%20XOR%20Cipher/) |
