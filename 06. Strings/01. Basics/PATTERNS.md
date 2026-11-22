# Strings — Basics: Patterns

Basics-level Strings problems (72) are mostly single-pass character work: scan and filter, change case with ASCII arithmetic, split into words, and count characters. A handful introduce digit strings (divisibility rules, comparing large numbers) and simple runs in binary strings.

## Pattern 1: Character Frequency Counting & Comparison

Count each character in one pass, then answer from the counts. Single-string questions ask for the most frequent character, the first repeat, distinct count, or missing letters (pangram). Two-string questions compare count arrays: the sum of absolute differences gives removals for an anagram, half of it gives replacements, and set-style checks find common or uncommon characters. Word-level versions use a hash map keyed by word.

| # | Problem | Link |
|---|---|---|
| 1 | [Remove Common and Concat](https://www.geeksforgeeks.org/problems/remove-common-characters-and-concatenate-1587115621/1) | [`08. Remove Common and Concat/`](08.%20Remove%20Common%20and%20Concat/) |
| 2 | [Make Anagram with Removals](https://www.geeksforgeeks.org/problems/anagram-of-string/1) | [`10. Make Anagram with Removals/`](10.%20Make%20Anagram%20with%20Removals/) |
| 3 | [Red OR Green](https://www.geeksforgeeks.org/problems/red-or-green5711/1) | [`28. Red OR Green/`](28.%20Red%20OR%20Green/) |
| 4 | [Missing Characters in Panagram](https://www.geeksforgeeks.org/problems/missing-characters-in-panagram/1) | [`44. Missing Characters in Panagram/`](44.%20Missing%20Characters%20in%20Panagram/) |
| 5 | [Minimum String Value After K Removals](https://www.geeksforgeeks.org/problems/minimize-string-value1010/1) | [`45. Minimum String Value After K Removals/`](45.%20Minimum%20String%20Value%20After%20K%20Removals/) |
| 6 | [Same Frequency in Two Halves](https://www.geeksforgeeks.org/problems/riyas-test1450/1) | [`54. Same Frequency in Two Halves/`](54.%20Same%20Frequency%20in%20Two%20Halves/) |
| 7 | [Count Distinct Vowels in String](https://www.geeksforgeeks.org/problems/count-distinct-vowels-in-string/1) | [`56. Count Distinct Vowels in String/`](56.%20Count%20Distinct%20Vowels%20in%20String/) |
| 8 | [Any Common Word in Two Lists](https://www.geeksforgeeks.org/problems/sort-the-fest0016/1) | [`64. Any Common Word in Two Lists/`](64.%20Any%20Common%20Word%20in%20Two%20Lists/) |
| 9 | [Count Equal Pairs in String](https://www.geeksforgeeks.org/problems/count-number-of-equal-pairs-in-a-string0520/1) | [`68. Count Equal Pairs in String/`](68.%20Count%20Equal%20Pairs%20in%20String/) |

## Pattern 2: Linear Character Scan & Filter

The base string move: one loop over the characters with a simple test on each. Count matches, return the first or last index of a target, check that every character meets a rule, or build a new string from the characters that pass a filter (no spaces, no vowels, only letters). Stable segregation is the same filter run once per character class. No extra structure is needed beyond the output buffer.

| # | Problem | Link |
|---|---|---|
| 1 | [Check for Binary String](https://www.geeksforgeeks.org/problems/check-for-binary/1) | [`03. Check for Binary String/`](03.%20Check%20for%20Binary%20String/) |
| 2 | [Even Positioned Characters](https://www.geeksforgeeks.org/problems/for-loop-2/1) | [`04. Even Positioned Characters/`](04.%20Even%20Positioned%20Characters/) |
| 3 | [Remove Spaces](https://www.geeksforgeeks.org/problems/remove-spaces0128/1) | [`07. Remove Spaces/`](07.%20Remove%20Spaces/) |
| 4 | [Remove Vowels](https://www.geeksforgeeks.org/problems/remove-vowels-from-string1446/1) | [`12. Remove Vowels/`](12.%20Remove%20Vowels/) |
| 5 | [Delete alternate characters](https://www.geeksforgeeks.org/problems/java-delete-alternate-characters4036/1) | [`17. Delete alternate characters/`](17.%20Delete%20alternate%20characters/) |
| 6 | [Length of String](https://www.geeksforgeeks.org/problems/length-of-string/1) | [`18. Length of String/`](18.%20Length%20of%20String/) |
| 7 | [Check if All Characters Same](https://www.geeksforgeeks.org/problems/check-string1818/1) | [`19. Check if All Characters Same/`](19.%20Check%20if%20All%20Characters%20Same/) |
| 8 | [String with Number at End](https://www.geeksforgeeks.org/problems/string-with-numbers-at-its-end5749/1) | [`24. String with Number at End/`](24.%20String%20with%20Number%20at%20End/) |
| 9 | [Count of camel case characters](https://www.geeksforgeeks.org/problems/find-the-camel3348/1) | [`25. Count of camel case characters/`](25.%20Count%20of%20camel%20case%20characters/) |
| 10 | [Count Types of Characters](https://www.geeksforgeeks.org/problems/count-type-of-characters3635/1) | [`26. Count Types of Characters/`](26.%20Count%20Types%20of%20Characters/) |
| 11 | [Remove All Except Alphabets](https://www.geeksforgeeks.org/problems/remove-all-characters-other-than-alphabets4923/1) | [`29. Remove All Except Alphabets/`](29.%20Remove%20All%20Except%20Alphabets/) |
| 12 | [Remove Characters from Alphanumeric String](https://www.geeksforgeeks.org/problems/remove-characters-from-alphanumeric-string0648/1) | [`33. Remove Characters from Alphanumeric String/`](33.%20Remove%20Characters%20from%20Alphanumeric%20String/) |
| 13 | [Last index of a character](https://www.geeksforgeeks.org/problems/last-index-of-a-character-in-the-string4516/1) | [`41. Last index of a character/`](41.%20Last%20index%20of%20a%20character/) |
| 14 | [Segregate Different Types of Characters](https://www.geeksforgeeks.org/problems/split-strings5211/1) | [`42. Segregate Different Types of Characters/`](42.%20Segregate%20Different%20Types%20of%20Characters/) |
| 15 | [Successful Penalty Conversions](https://www.geeksforgeeks.org/problems/the-penalty-shootout3810/1) | [`43. Successful Penalty Conversions/`](43.%20Successful%20Penalty%20Conversions/) |
| 16 | [Remove Sandwiched Vowels](https://www.geeksforgeeks.org/problems/sandwiched-vowels5158/1) | [`46. Remove Sandwiched Vowels/`](46.%20Remove%20Sandwiched%20Vowels/) |
| 17 | [Numbers with Given Digit](https://www.geeksforgeeks.org/problems/find-the-number-which-contain-the-digit-d4144/1) | [`47. Numbers with Given Digit/`](47.%20Numbers%20with%20Given%20Digit/) |
| 18 | [Duck Number](https://www.geeksforgeeks.org/problems/zero-number2158/1) | [`49. Duck Number/`](49.%20Duck%20Number/) |
| 19 | [Good String](https://www.geeksforgeeks.org/problems/good-string5712/1) | [`51. Good String/`](51.%20Good%20String/) |

## Pattern 3: Big Number Arithmetic & Digit Divisibility

The number is too large for built-in types, so work on its digits. Addition and binary addition walk from the right with a carry. Multiplication accumulates partial products into a result array. Division and modulus keep a running remainder `r = (r*10 + d) % k` from the left. Divisibility by 4, 5, 11, or 999 uses the known shortcut (last two digits, last digit, alternating sum, groups of three). Comparing large numbers checks length first, then digits.

| # | Problem | Link |
|---|---|---|
| 1 | [Array Product Even or Odd](https://www.geeksforgeeks.org/problems/product-is-even-or-odd3020/1) | [`32. Array Product Even or Odd/`](32.%20Array%20Product%20Even%20or%20Odd/) |
| 2 | [Check if divisible by 4](https://www.geeksforgeeks.org/problems/check-if-divisible-by-43813/1) | [`35. Check if divisible by 4/`](35.%20Check%20if%20divisible%20by%204/) |
| 3 | [Remainder with 7](https://www.geeksforgeeks.org/problems/remainder-with-7/1) | [`38. Remainder with 7/`](38.%20Remainder%20with%207/) |
| 4 | [Check if divisible by 11](https://www.geeksforgeeks.org/problems/check-if-divisible-by-114724/1) | [`48. Check if divisible by 11/`](48.%20Check%20if%20divisible%20by%2011/) |
| 5 | [Compare two Large Numbers](https://www.geeksforgeeks.org/problems/compare-two-large-numbers3413/1) | [`52. Compare two Large Numbers/`](52.%20Compare%20two%20Large%20Numbers/) |
| 6 | [Floating Point Number Even or Odd](https://www.geeksforgeeks.org/problems/floating-point-number-even-or-odd0146/1) | [`53. Floating Point Number Even or Odd/`](53.%20Floating%20Point%20Number%20Even%20or%20Odd/) |
| 7 | [Binary Addition of 1](https://www.geeksforgeeks.org/problems/dr-stranges-powers3333/1) | [`72. Binary Addition of 1/`](72.%20Binary%20Addition%20of%201/) |

## Pattern 4: Parsing & Format / Base Conversion

The input follows a grammar, and the job is to read it correctly. Extract integers from mixed text, convert Roman numerals both ways (subtract when a smaller value precedes a larger one), implement atoi with sign and overflow checks, validate IP addresses, and read times and dates. Base-style conversions (Excel columns, numbers built from a fixed digit set) are repeated division by the base with an offset. Comment removal and length-prefixed encoding use a small state machine.

| # | Problem | Link |
|---|---|---|
| 1 | [Maximum Number in a String](https://www.geeksforgeeks.org/problems/extract-maximum2943/1) | [`11. Maximum Number in a String/`](11.%20Maximum%20Number%20in%20a%20String/) |
| 2 | [C++ Basic Data types](https://www.geeksforgeeks.org/problems/c-basic-data-types3128/1) | [`31. C++ Basic Data types/`](31.%20C++%20Basic%20Data%20types/) |
| 3 | [Time to Words](https://www.geeksforgeeks.org/problems/time-to-words3728/1) | [`58. Time to Words/`](58.%20Time%20to%20Words/) |
| 4 | [Java Date and Day](https://www.geeksforgeeks.org/problems/java-date-and-day5024/1) | [`71. Java Date and Day/`](71.%20Java%20Date%20and%20Day/) |

## Pattern 5: Pattern Matching & Rotation (Naive / KMP / Z / Rabin-Karp)

Substring search at the core. The naive method tries every start. KMP builds the longest-proper-prefix-that-is-also-suffix (LPS) array so the text pointer never moves back. The Z-array gives the match length at each position. Rabin-Karp compares rolling hashes and checks on a hit. Many problems reduce to these: a rotation of `s` is a substring of `s + s`, the minimum characters to make a palindrome come from the LPS of `s + '$' + reverse(s)`, and a repeated-substring check uses `n % (n - lps) == 0`.

| # | Problem | Link |
|---|---|---|
| 1 | [First Occurence](https://www.geeksforgeeks.org/problems/implement-strstr/1) | [`02. First Occurence/`](02.%20First%20Occurence/) |
| 2 | [Replace Substring with Space](https://www.geeksforgeeks.org/problems/extraction-of-secret-message0616/1) | [`67. Replace Substring with Space/`](67.%20Replace%20Substring%20with%20Space/) |

## Pattern 6: Greedy Digit / Character Choice & Next Permutation

The leftmost position matters most, so decide it first. For one swap, find the first position that can be improved and swap with the best digit to its right (the last occurrence for largest). Next and previous permutation find the pivot from the right, swap with the nearest larger or smaller digit, and reverse the suffix. Other variants keep the best prefix (string mirror), choose + or * per digit, or place characters so no rule is broken.

| # | Problem | Link |
|---|---|---|
| 1 | [Odd to Largest Even with One Swap](https://www.geeksforgeeks.org/problems/odd-to-even0537/1) | [`39. Odd to Largest Even with One Swap/`](39.%20Odd%20to%20Largest%20Even%20with%20One%20Swap/) |
| 2 | [Maximum Integer Value](https://www.geeksforgeeks.org/problems/maximum-integer-value1434/1) | [`57. Maximum Integer Value/`](57.%20Maximum%20Integer%20Value/) |

## Pattern 7: String Building & Simulation

No trick, just follow the process exactly. Interleave two strings, concatenate and reverse, URL-encode spaces, format a license key, emit Fizz Buzz, simulate robot moves to see if they return to the origin, track a rotation offset across queries, lay out characters in zig-zag rows, or justify text to a fixed width. Use a mutable buffer so each append is O(1).

| # | Problem | Link |
|---|---|---|
| 1 | [Alternate Merge Two Strings](https://www.geeksforgeeks.org/problems/merge-two-strings2736/1) | [`16. Alternate Merge Two Strings/`](16.%20Alternate%20Merge%20Two%20Strings/) |
| 2 | [Concatenate and Reverse](https://www.geeksforgeeks.org/problems/java-strings-set-15112/1) | [`21. Concatenate and Reverse/`](21.%20Concatenate%20and%20Reverse/) |
| 3 | [Concatenate a List of Characters](https://www.geeksforgeeks.org/problems/convert-a-list-of-characters-into-a-string5142/1) | [`27. Concatenate a List of Characters/`](27.%20Concatenate%20a%20List%20of%20Characters/) |
| 4 | [Shortest direction](https://www.geeksforgeeks.org/problems/shortest-direction4201/1) | [`55. Shortest direction/`](55.%20Shortest%20direction/) |
| 5 | [URLify a given string](https://www.geeksforgeeks.org/problems/urlify-a-given-string--141625/1) | [`69. URLify a given string/`](69.%20URLify%20a%20given%20string/) |

## Pattern 8: Two Pointers, Reversal & Palindromes

Mirrored positions decide the answer. Swap `s[l]` and `s[r]` to reverse, or compare them to test a palindrome, skipping characters that do not take part. Palindrome variants count mismatches to fix with replacements, test all rotations, or note that any string is removable in at most two palindromic subsequences. Same-direction pointers over two strings check subsequence membership or simulate moves from the end.

| # | Problem | Link |
|---|---|---|
| 1 | [Reverse a String](https://www.geeksforgeeks.org/problems/reverse-a-string/1) | [`01. Reverse a String/`](01.%20Reverse%20a%20String/) |
| 2 | [Reverse Vowels](https://www.geeksforgeeks.org/problems/reversing-the-vowels5304/1) | [`13. Reverse Vowels/`](13.%20Reverse%20Vowels/) |
| 3 | [Perfect Reversible String](https://www.geeksforgeeks.org/problems/perfect-reversible-string4828/1) | [`61. Perfect Reversible String/`](61.%20Perfect%20Reversible%20String/) |

## Pattern 9: Case Conversion & Character Mapping (ASCII Arithmetic)

Each character maps to another by a fixed rule. Case changes add or subtract 32 (or use `tolower`/`toupper`). Mirroring uses `'a' + 'z' - c`. Keypad and digit-swap problems use a small lookup table. Camel case and snake case conversions combine the mapping with a check for word boundaries. The work is one pass with constant-time work per character.

| # | Problem | Link |
|---|---|---|
| 1 | [Convert String to Lower Case](https://www.geeksforgeeks.org/problems/convert-string-to-lowercase/1) | [`05. Convert String to Lower Case/`](05.%20Convert%20String%20to%20Lower%20Case/) |
| 2 | [Keypad Typing](https://www.geeksforgeeks.org/problems/keypad-typing0119/1) | [`20. Keypad Typing/`](20.%20Keypad%20Typing/) |
| 3 | [Lower case to upper case](https://www.geeksforgeeks.org/problems/lower-case-to-upper-case3410/1) | [`22. Lower case to upper case/`](22.%20Lower%20case%20to%20upper%20case/) |
| 4 | [Change the Case based on First Character](https://www.geeksforgeeks.org/problems/change-the-string3541/1) | [`23. Change the Case based on First Character/`](23.%20Change%20the%20Case%20based%20on%20First%20Character/) |
| 5 | [Front-Back Transformation  of String](https://www.geeksforgeeks.org/problems/front-back-transformation1659/1) | [`30. Front-Back Transformation of String/`](30.%20Front-Back%20Transformation%20of%20String/) |
| 6 | [Snake Case](https://www.geeksforgeeks.org/problems/snake-case0219/1) | [`50. Snake Case/`](50.%20Snake%20Case/) |
| 7 | [Alternate Lowercase and Uppercase](https://www.geeksforgeeks.org/problems/crazy-string1157/1) | [`59. Alternate Lowercase and Uppercase/`](59.%20Alternate%20Lowercase%20and%20Uppercase/) |
| 8 | [Max-Min Conversion](https://www.geeksforgeeks.org/problems/max-min-conversion5257/1) | [`66. Max-Min Conversion/`](66.%20Max-Min%20Conversion/) |

## Pattern 10: Consecutive Runs & Grouping

Many problems depend on blocks of equal adjacent characters. Track where the current run started and its length. When the character changes, emit the run (run-length encoding, look-and-say), collapse it to one character, update the longest run, or check that each character forms one block. Binary-string checks such as 'all 0s together' or '0 between 1s' are run counts in disguise.

| # | Problem | Link |
|---|---|---|
| 1 | [Longest Substring with All 1's](https://www.geeksforgeeks.org/problems/longest-substring-containing-1/1) | [`34. Longest Substring with All 1's/`](34.%20Longest%20Substring%20with%20All%201's/) |
| 2 | [Remove Repeated Digits](https://www.geeksforgeeks.org/problems/remove-repeated-digits-in-a-given-number4014/1) | [`36. Remove Repeated Digits/`](36.%20Remove%20Repeated%20Digits/) |
| 3 | [Check for 0 Between 1's in Binary String](https://www.geeksforgeeks.org/problems/check-binary-string0402/1) | [`62. Check for 0 Between 1's in Binary String/`](62.%20Check%20for%200%20Between%201's%20in%20Binary%20String/) |
| 4 | [All 0s Together in a Binary String](https://www.geeksforgeeks.org/problems/the-muskteers3519/1) | [`63. All 0s Together in a Binary String/`](63.%20All%200s%20Together%20in%20a%20Binary%20String/) |

## Pattern 11: Counting & Combinatorics on Strings

The answer is a count, and enumeration is too slow. Substrings with 1s at both ends are `c*(c-1)/2` for `c` ones. Substrings ending at an even digit add `i + 1` for each such position. Sum of all digit subsequences is `digitSum * 2^(n-1)`. Permutation rank uses the factorial number system. Equation solutions use stars and bars. Bounded-letter strings of length n come from a small case formula.

| # | Problem | Link |
|---|---|---|
| 1 | [Binary Substrings with Corners as 1](https://www.geeksforgeeks.org/problems/binary-string-1587115620/1) | [`06. Binary Substrings with Corners as 1/`](06.%20Binary%20Substrings%20with%20Corners%20as%201/) |
| 2 | [Sum of All Digit Subsequences](https://www.geeksforgeeks.org/problems/sum-of-all-sub-sequences-of-a-number3437/1) | [`70. Sum of All Digit Subsequences/`](70.%20Sum%20of%20All%20Digit%20Subsequences/) |

## Pattern 12: Word Tokenization & Sentence Processing

The unit of work is a word, not a character. Split the sentence on spaces, or scan and mark where each word starts and ends. Then find the longest, shortest, or last word, take first letters, capitalise words, reverse word order, or count words and sentences. Watch for leading, trailing, and repeated spaces.

| # | Problem | Link |
|---|---|---|
| 1 | [Longest Word](https://www.geeksforgeeks.org/problems/display-longest-name0853/1) | [`09. Longest Word/`](09.%20Longest%20Word/) |
| 2 | [Capitalize First Letter of Words](https://www.geeksforgeeks.org/problems/upper-case-conversion5419/1) | [`14. Capitalize First Letter of Words/`](14.%20Capitalize%20First%20Letter%20of%20Words/) |
| 3 | [First Letter of Every Word](https://www.geeksforgeeks.org/problems/print-first-letter-of-every-word-in-the-string3632/1) | [`15. First Letter of Every Word/`](15.%20First%20Letter%20of%20Every%20Word/) |
| 4 | [Length of the Last Word](https://www.geeksforgeeks.org/problems/length-of-last-word5721/1) | [`40. Length of the Last Word/`](40.%20Length%20of%20the%20Last%20Word/) |
| 5 | [Word Lengths](https://www.geeksforgeeks.org/problems/count-the-characters-in-each-word-in-a-given-sentence3451/1) | [`60. Word Lengths/`](60.%20Word%20Lengths/) |

## Pattern 13: Lexicographic Comparison & Sorting

Lexicographic order decides the answer. Longest common prefix compares the first and last strings after sorting, or all strings column by column. Smallest and largest strings in a list come from one comparison pass. Custom comparisons treat a multi-letter unit as one character or ignore case. The lexicographically largest substring is the largest suffix. The smallest rotation compares candidate starts on `s + s` (or uses Booth's algorithm).

| # | Problem | Link |
|---|---|---|
| 1 | [Just One Mismatch](https://www.geeksforgeeks.org/problems/just-one-mismatch1714/1) | [`65. Just One Mismatch/`](65.%20Just%20One%20Mismatch/) |

## Pattern 14: Binary Strings & Bit Manipulation

Problems where the string is a bit pattern or bit operations do the work. Unset or rotate bits with masks and shifts. Minimum flips to an alternating string counts mismatches against both '0101...' and '1010...' and takes the smaller. XOR cipher recovers the original by XORing adjacent prefix values.

| # | Problem | Link |
|---|---|---|
| 1 | [Unset Kth Bit](https://www.geeksforgeeks.org/problems/replace-the-bit3212/1) | [`37. Unset Kth Bit/`](37.%20Unset%20Kth%20Bit/) |
