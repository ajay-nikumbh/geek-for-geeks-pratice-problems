# Strings — Easy: Patterns

These are the recurring patterns across the 94 Easy-level Strings problems. Frequency counting and big-number digit arithmetic are the largest families, followed by greedy digit choice (one swap, next permutation), lexicographic comparison, parsing, and the first stack-based reductions and pattern searches.

## Pattern 1: Character Frequency Counting & Comparison

Count each character in one pass, then answer from the counts. Single-string questions ask for the most frequent character, the first repeat, distinct count, or missing letters (pangram). Two-string questions compare count arrays: the sum of absolute differences gives removals for an anagram, half of it gives replacements, and set-style checks find common or uncommon characters. Word-level versions use a hash map keyed by word.

| # | Problem | Link |
|---|---|---|
| 1 | [String Duplicates Removal](https://www.geeksforgeeks.org/problems/remove-all-duplicates-from-a-given-string4321/1) | [`04. String Duplicates Removal/`](04.%20String%20Duplicates%20Removal/) |
| 2 | [Most Frequent Character](https://www.geeksforgeeks.org/problems/maximum-occuring-character-1587115620/1) | [`06. Most Frequent Character/`](06.%20Most%20Frequent%20Character/) |
| 3 | [Panagram Checking](https://www.geeksforgeeks.org/problems/pangram-checking-1587115620/1) | [`08. Panagram Checking/`](08.%20Panagram%20Checking/) |
| 4 | [Remove Characters Present in  Other](https://www.geeksforgeeks.org/problems/remove-character3815/1) | [`14. Remove Characters Present in Other/`](14.%20Remove%20Characters%20Present%20in%20Other/) |
| 5 | [Max Frequency Word](https://www.geeksforgeeks.org/problems/word-with-maximum-frequency0120/1) | [`21. Max Frequency Word/`](21.%20Max%20Frequency%20Word/) |
| 6 | [Repeating Character](https://www.geeksforgeeks.org/problems/repeating-character-first-appearance-leftmost/1) | [`24. Repeating Character/`](24.%20Repeating%20Character/) |
| 7 | [Common Subsequence](https://www.geeksforgeeks.org/problems/common-subsequence4049/1) | [`39. Common Subsequence/`](39.%20Common%20Subsequence/) |
| 8 | [Make all Substrings Distinct](https://www.geeksforgeeks.org/problems/minimum-changes-to-make-all-substrings-distinct4722/1) | [`46. Make all Substrings Distinct/`](46.%20Make%20all%20Substrings%20Distinct/) |
| 9 | [Minimum Replacements to Make Anagram](https://www.geeksforgeeks.org/problems/min-manipulations-to-make-strings-anagram1421/1) | [`55. Minimum Replacements to Make Anagram/`](55.%20Minimum%20Replacements%20to%20Make%20Anagram/) |
| 10 | [Make a String with Deletion and Rearrangement](https://www.geeksforgeeks.org/problems/make-a-string-from-another-string--141625/1) | [`89. Make a String with Deletion and Rearrangement/`](89.%20Make%20a%20String%20with%20Deletion%20and%20Rearrangement/) |

## Pattern 2: Linear Character Scan & Filter

The base string move: one loop over the characters with a simple test on each. Count matches, return the first or last index of a target, check that every character meets a rule, or build a new string from the characters that pass a filter (no spaces, no vowels, only letters). Stable segregation is the same filter run once per character class. No extra structure is needed beyond the output buffer.

| # | Problem | Link |
|---|---|---|
| 1 | [Remaining String](https://www.geeksforgeeks.org/problems/remaining-string3515/1) | [`13. Remaining String/`](13.%20Remaining%20String/) |
| 2 | [Sum of Digits in a String](https://www.geeksforgeeks.org/problems/rearrange-a-string4100/1) | [`35. Sum of Digits in a String/`](35.%20Sum%20of%20Digits%20in%20a%20String/) |
| 3 | [Remove all occurrences of a character in a string](https://www.geeksforgeeks.org/problems/remove-all-occurrences-of-a-character-in-a-string/1) | [`57. Remove all occurrences of a character in a string/`](57.%20Remove%20all%20occurrences%20of%20a%20character%20in%20a%20string/) |
| 4 | [Search a Character in a String](https://www.geeksforgeeks.org/problems/search-a-character-in-a-string/1) | [`71. Search a Character in a String/`](71.%20Search%20a%20Character%20in%20a%20String/) |

## Pattern 3: Big Number Arithmetic & Digit Divisibility

The number is too large for built-in types, so work on its digits. Addition and binary addition walk from the right with a carry. Multiplication accumulates partial products into a result array. Division and modulus keep a running remainder `r = (r*10 + d) % k` from the left. Divisibility by 4, 5, 11, or 999 uses the known shortcut (last two digits, last digit, alternating sum, groups of three). Comparing large numbers checks length first, then digits.

| # | Problem | Link |
|---|---|---|
| 1 | [Nearest Multiple of 10](https://www.geeksforgeeks.org/problems/nearest-multiple-of-102437/1) | [`09. Nearest Multiple of 10/`](09.%20Nearest%20Multiple%20of%2010/) |
| 2 | [Divisible by 7](https://www.geeksforgeeks.org/problems/divisible-by-73224/1) | [`29. Divisible by 7/`](29.%20Divisible%20by%207/) |
| 3 | [Check if the number is balanced](https://www.geeksforgeeks.org/problems/check-if-the-number-is-balanced3014/1) | [`34. Check if the number is balanced/`](34.%20Check%20if%20the%20number%20is%20balanced/) |
| 4 | [Partition a number into two divisible parts](https://www.geeksforgeeks.org/problems/partition-a-number-into-two-divisible-parts3605/1) | [`51. Partition a number into two divisible parts/`](51.%20Partition%20a%20number%20into%20two%20divisible%20parts/) |
| 5 | [Multiply by 11](https://www.geeksforgeeks.org/problems/multiply-by-111820/1) | [`53. Multiply by 11/`](53.%20Multiply%20by%2011/) |
| 6 | [Divisibility by 5 for Binary](https://www.geeksforgeeks.org/problems/divisible-by-5-or-not-14509/1) | [`62. Divisibility by 5 for Binary/`](62.%20Divisibility%20by%205%20for%20Binary/) |
| 7 | [Large Number Division](https://www.geeksforgeeks.org/problems/large-number-division0207/1) | [`68. Large Number Division/`](68.%20Large%20Number%20Division/) |
| 8 | [Divisibility by 999](https://www.geeksforgeeks.org/problems/divisibility-by-9990149/1) | [`74. Divisibility by 999/`](74.%20Divisibility%20by%20999/) |
| 9 | [Permutation Divisibility by 4](https://www.geeksforgeeks.org/problems/permutation-divisibility0447/1) | [`82. Permutation Divisibility by 4/`](82.%20Permutation%20Divisibility%20by%204/) |

## Pattern 4: Parsing & Format / Base Conversion

The input follows a grammar, and the job is to read it correctly. Extract integers from mixed text, convert Roman numerals both ways (subtract when a smaller value precedes a larger one), implement atoi with sign and overflow checks, validate IP addresses, and read times and dates. Base-style conversions (Excel columns, numbers built from a fixed digit set) are repeated division by the base with an offset. Comment removal and length-prefixed encoding use a small state machine.

| # | Problem | Link |
|---|---|---|
| 1 | [Roman to Integer](https://www.geeksforgeeks.org/problems/roman-number-to-integer3201/1) | [`05. Roman to Integer/`](05.%20Roman%20to%20Integer/) |
| 2 | [Sum Numbers in a String](https://www.geeksforgeeks.org/problems/sum-of-numbers-in-string-1587115621/1) | [`12. Sum Numbers in a String/`](12.%20Sum%20Numbers%20in%20a%20String/) |
| 3 | [Decimal to Roman](https://www.geeksforgeeks.org/problems/convert-to-roman-no/1) | [`19. Decimal to Roman/`](19.%20Decimal%20to%20Roman/) |
| 4 | [Time Difference](https://www.geeksforgeeks.org/problems/time-difference5528/1) | [`85. Time Difference/`](85.%20Time%20Difference/) |
| 5 | [Kth Boom Number](https://www.geeksforgeeks.org/problems/kth-boom-number5609/1) | [`86. Kth Boom Number/`](86.%20Kth%20Boom%20Number/) |
| 6 | [Patients with Hypertension](https://www.geeksforgeeks.org/problems/patients-with-hypertension/1) | [`92. Patients with Hypertension/`](92.%20Patients%20with%20Hypertension/) |

## Pattern 5: Pattern Matching & Rotation (Naive / KMP / Z / Rabin-Karp)

Substring search at the core. The naive method tries every start. KMP builds the longest-proper-prefix-that-is-also-suffix (LPS) array so the text pointer never moves back. The Z-array gives the match length at each position. Rabin-Karp compares rolling hashes and checks on a hit. Many problems reduce to these: a rotation of `s` is a substring of `s + s`, the minimum characters to make a palindrome come from the LPS of `s + '$' + reverse(s)`, and a repeated-substring check uses `n % (n - lps) == 0`.

| # | Problem | Link |
|---|---|---|
| 1 | [String Rotated by 2 Places](https://www.geeksforgeeks.org/problems/check-if-string-is-rotated-by-two-places-1587115620/1) | [`03. String Rotated by 2 Places/`](03.%20String%20Rotated%20by%202%20Places/) |
| 2 | [Type it!](https://www.geeksforgeeks.org/problems/type-it--170645/1) | [`33. Type it!/`](33.%20Type%20it!/) |
| 3 | [Longest Prefix as a Substring](https://www.geeksforgeeks.org/problems/minimum-shift-for-longest-common-prefix0759/1) | [`41. Longest Prefix as a Substring/`](41.%20Longest%20Prefix%20as%20a%20Substring/) |
| 4 | [Replace Word](https://www.geeksforgeeks.org/problems/replace-a-word5553/1) | [`60. Replace Word/`](60.%20Replace%20Word/) |
| 5 | [Overlapping Substrings](https://www.geeksforgeeks.org/problems/overlapping-substrings2654/1) | [`91. Overlapping Substrings/`](91.%20Overlapping%20Substrings/) |

## Pattern 6: Greedy Digit / Character Choice & Next Permutation

The leftmost position matters most, so decide it first. For one swap, find the first position that can be improved and swap with the best digit to its right (the last occurrence for largest). Next and previous permutation find the pivot from the right, swap with the nearest larger or smaller digit, and reverse the suffix. Other variants keep the best prefix (string mirror), choose + or * per digit, or place characters so no rule is broken.

| # | Problem | Link |
|---|---|---|
| 1 | [Wifi Range](https://www.geeksforgeeks.org/problems/wifi-range--170647/1) | [`17. Wifi Range/`](17.%20Wifi%20Range/) |
| 2 | [String Mirror](https://www.geeksforgeeks.org/problems/string-mirror--170647/1) | [`26. String Mirror/`](26.%20String%20Mirror/) |
| 3 | [Append Smaller at Both Ends](https://www.geeksforgeeks.org/problems/repeat-the-strings/1) | [`28. Append Smaller at Both Ends/`](28.%20Append%20Smaller%20at%20Both%20Ends/) |
| 4 | [Largest odd number in string](https://www.geeksforgeeks.org/problems/largest-odd-number-in-string/1) | [`31. Largest odd number in string/`](31.%20Largest%20odd%20number%20in%20string/) |
| 5 | [Smallest Number In One Swap](https://www.geeksforgeeks.org/problems/smallest-number-in-one-swap0010/1) | [`64. Smallest Number In One Swap/`](64.%20Smallest%20Number%20In%20One%20Swap/) |
| 6 | [Make All Even with Minimum Operations](https://www.geeksforgeeks.org/problems/the-even-array3825/1) | [`65. Make All Even with Minimum Operations/`](65.%20Make%20All%20Even%20with%20Minimum%20Operations/) |
| 7 | [Make x times 0's and y times 1's](https://www.geeksforgeeks.org/problems/rearrange-string-as-alternate-x-and-y-occurences3835/1) | [`76. Make x times 0's and y times 1's/`](76.%20Make%20x%20times%200's%20and%20y%20times%201's/) |
| 8 | [Lexicographically Previous Permutation](https://www.geeksforgeeks.org/problems/lexicographically-previous-permutation3620/1) | [`77. Lexicographically Previous Permutation/`](77.%20Lexicographically%20Previous%20Permutation/) |
| 9 | [Largest Permutation Smaller than Other Number](https://www.geeksforgeeks.org/problems/maximize-permutations2915/1) | [`87. Largest Permutation Smaller than Other Number/`](87.%20Largest%20Permutation%20Smaller%20than%20Other%20Number/) |
| 10 | [Smallest Greater Date with Same Digits](https://www.geeksforgeeks.org/problems/the-wedding-date5302/1) | [`88. Smallest Greater Date with Same Digits/`](88.%20Smallest%20Greater%20Date%20with%20Same%20Digits/) |

## Pattern 7: String Building & Simulation

No trick, just follow the process exactly. Interleave two strings, concatenate and reverse, URL-encode spaces, format a license key, emit Fizz Buzz, simulate robot moves to see if they return to the origin, track a rotation offset across queries, lay out characters in zig-zag rows, or justify text to a fixed width. Use a mutable buffer so each append is O(1).

| # | Problem | Link |
|---|---|---|
| 1 | [License Key Formatting](https://www.geeksforgeeks.org/problems/license-key-formatting/1) | [`27. License Key Formatting/`](27.%20License%20Key%20Formatting/) |
| 2 | [Rock Paper Scissors!](https://www.geeksforgeeks.org/problems/rock-paper-scissors2830/1) | [`42. Rock Paper Scissors!/`](42.%20Rock%20Paper%20Scissors!/) |
| 3 | [Does Robot Move Circular](https://www.geeksforgeeks.org/problems/does-robot-moves-circular0414/1) | [`49. Does Robot Move Circular/`](49.%20Does%20Robot%20Move%20Circular/) |
| 4 | [Fizz Buzz](https://www.geeksforgeeks.org/problems/fizz-buzz/1) | [`50. Fizz Buzz/`](50.%20Fizz%20Buzz/) |
| 5 | [String Concatenation](https://www.geeksforgeeks.org/problems/string-concatenation-1614157859/1) | [`56. String Concatenation/`](56.%20String%20Concatenation/) |
| 6 | [Remove a Character from a Given Position](https://www.geeksforgeeks.org/problems/remove-a-character-from-a-given-position/1) | [`81. Remove a Character from a Given Position/`](81.%20Remove%20a%20Character%20from%20a%20Given%20Position/) |

## Pattern 8: Two Pointers, Reversal & Palindromes

Mirrored positions decide the answer. Swap `s[l]` and `s[r]` to reverse, or compare them to test a palindrome, skipping characters that do not take part. Palindrome variants count mismatches to fix with replacements, test all rotations, or note that any string is removable in at most two palindromic subsequences. Same-direction pointers over two strings check subsequence membership or simulate moves from the end.

| # | Problem | Link |
|---|---|---|
| 1 | [Make Palindrome](https://www.geeksforgeeks.org/problems/make-palindrome--170647/1) | [`23. Make Palindrome/`](23.%20Make%20Palindrome/) |
| 2 | [Check if it is possible to convert one string into another with given constraints](https://www.geeksforgeeks.org/problems/check-if-it-is-possible-to-convert-one-string-into-another-with-given-constraints4116/1) | [`37. Check if it is possible to convert one string into another with given constraints/`](37.%20Check%20if%20it%20is%20possible%20to%20convert%20one%20string%20into%20another%20with%20given%20constraints/) |
| 3 | [Check for Rotation of a Palindrome](https://www.geeksforgeeks.org/problems/check-if-a-given-string-is-a-rotation-of-a-palindrome0317/1) | [`52. Check for Rotation of a Palindrome/`](52.%20Check%20for%20Rotation%20of%20a%20Palindrome/) |
| 4 | [Remove  Palindromic Subsequences to Make Empty](https://www.geeksforgeeks.org/problems/palindromic-subsequences1335/1) | [`78. Remove Palindromic Subsequences to Make Empty/`](78.%20Remove%20Palindromic%20Subsequences%20to%20Make%20Empty/) |
| 5 | [Palindrome Numbers in a Range](https://www.geeksforgeeks.org/problems/print-all-palindromes-in-the-given-range/1) | [`84. Palindrome Numbers in a Range/`](84.%20Palindrome%20Numbers%20in%20a%20Range/) |

## Pattern 9: Case Conversion & Character Mapping (ASCII Arithmetic)

Each character maps to another by a fixed rule. Case changes add or subtract 32 (or use `tolower`/`toupper`). Mirroring uses `'a' + 'z' - c`. Keypad and digit-swap problems use a small lookup table. Camel case and snake case conversions combine the mapping with a check for word boundaries. The work is one pass with constant-time work per character.

| # | Problem | Link |
|---|---|---|
| 1 | [Convert CamelCase to Sentence](https://www.geeksforgeeks.org/problems/amend-the-sentence3235/1) | [`47. Convert CamelCase to Sentence/`](47.%20Convert%20CamelCase%20to%20Sentence/) |
| 2 | [Toggle Case](https://www.geeksforgeeks.org/problems/toggle-case/1) | [`59. Toggle Case/`](59.%20Toggle%20Case/) |

## Pattern 10: Consecutive Runs & Grouping

Many problems depend on blocks of equal adjacent characters. Track where the current run started and its length. When the character changes, emit the run (run-length encoding, look-and-say), collapse it to one character, update the longest run, or check that each character forms one block. Binary-string checks such as 'all 0s together' or '0 between 1s' are run counts in disguise.

| # | Problem | Link |
|---|---|---|
| 1 | [Replace Consecutive Two Same with One](https://www.geeksforgeeks.org/problems/consecutive-elements2306/1) | [`07. Replace Consecutive Two Same with One/`](07.%20Replace%20Consecutive%20Two%20Same%20with%20One/) |
| 2 | [Run Length Encoding](https://www.geeksforgeeks.org/problems/run-length-encoding/1) | [`10. Run Length Encoding/`](10.%20Run%20Length%20Encoding/) |
| 3 | [The Modified String](https://www.geeksforgeeks.org/problems/the-modified-string-1587115621/1) | [`22. The Modified String/`](22.%20The%20Modified%20String/) |
| 4 | [1[0]1 Pattern Count](https://www.geeksforgeeks.org/problems/101-pattern-count1341/1) | [`36. 1[0]1 Pattern Count/`](36.%201[0]1%20Pattern%20Count/) |
| 5 | [Same Characters and Same Order](https://www.geeksforgeeks.org/problems/c-corresponding-position-in-the-two-strings-that-hold-exactly-the-same-characters5013/1) | [`44. Same Characters and Same Order/`](44.%20Same%20Characters%20and%20Same%20Order/) |
| 6 | [Non-Repetitive String](https://www.geeksforgeeks.org/problems/the-non-repetitive-string5955/1) | [`69. Non-Repetitive String/`](69.%20Non-Repetitive%20String/) |

## Pattern 11: Counting & Combinatorics on Strings

The answer is a count, and enumeration is too slow. Substrings with 1s at both ends are `c*(c-1)/2` for `c` ones. Substrings ending at an even digit add `i + 1` for each such position. Sum of all digit subsequences is `digitSum * 2^(n-1)`. Permutation rank uses the factorial number system. Equation solutions use stars and bars. Bounded-letter strings of length n come from a small case formula.

| # | Problem | Link |
|---|---|---|
| 1 | [Count Strings](https://www.geeksforgeeks.org/problems/count-of-strings-that-can-be-formed-using-a-b-and-c-under-given-constraints1135/1) | [`18. Count Strings/`](18.%20Count%20Strings/) |
| 2 | [Count Occurrences in Prefix of a Repeated String](https://www.geeksforgeeks.org/problems/aryas-long-string5840/1) | [`40. Count Occurrences in Prefix of a Repeated String/`](40.%20Count%20Occurrences%20in%20Prefix%20of%20a%20Repeated%20String/) |
| 3 | [Colorful Strings](https://www.geeksforgeeks.org/problems/geek-and-its-colored-strings1355/1) | [`63. Colorful Strings/`](63.%20Colorful%20Strings/) |
| 4 | [Count Even Substrings](https://www.geeksforgeeks.org/problems/count-even-substrings3857/1) | [`66. Count Even Substrings/`](66.%20Count%20Even%20Substrings/) |
| 5 | [Ways to Split String with Distinct Partition Starts](https://www.geeksforgeeks.org/problems/ways-to-split-string-such-that-each-partition-starts-with-distinct-letter5723/1) | [`83. Ways to Split String with Distinct Partition Starts/`](83.%20Ways%20to%20Split%20String%20with%20Distinct%20Partition%20Starts/) |
| 6 | [Even Decimal Binary String](https://www.geeksforgeeks.org/problems/even-decimal-binary-string4748/1) | [`90. Even Decimal Binary String/`](90.%20Even%20Decimal%20Binary%20String/) |

## Pattern 12: Word Tokenization & Sentence Processing

The unit of work is a word, not a character. Split the sentence on spaces, or scan and mark where each word starts and ends. Then find the longest, shortest, or last word, take first letters, capitalise words, reverse word order, or count words and sentences. Watch for leading, trailing, and repeated spaces.

| # | Problem | Link |
|---|---|---|
| 1 | [Reverse Words](https://www.geeksforgeeks.org/problems/reverse-words-in-a-given-string5459/1) | [`01. Reverse Words/`](01.%20Reverse%20Words/) |
| 2 | [Count Words in a String](https://www.geeksforgeeks.org/problems/count-number-of-words1500/1) | [`15. Count Words in a String/`](15.%20Count%20Words%20in%20a%20String/) |
| 3 | [Difficulty of a Sentence](https://www.geeksforgeeks.org/problems/difficulty-of-sentence5856/1) | [`48. Difficulty of a Sentence/`](48.%20Difficulty%20of%20a%20Sentence/) |
| 4 | [Smallest and Largest Words](https://www.geeksforgeeks.org/problems/smallest-and-largest/1) | [`54. Smallest and Largest Words/`](54.%20Smallest%20and%20Largest%20Words/) |
| 5 | [Count Sentences and Words](https://www.geeksforgeeks.org/problems/counting-number-of-sentences-and-words-in-text3226/1) | [`80. Count Sentences and Words/`](80.%20Count%20Sentences%20and%20Words/) |

## Pattern 13: Lexicographic Comparison & Sorting

Lexicographic order decides the answer. Longest common prefix compares the first and last strings after sorting, or all strings column by column. Smallest and largest strings in a list come from one comparison pass. Custom comparisons treat a multi-letter unit as one character or ignore case. The lexicographically largest substring is the largest suffix. The smallest rotation compares candidate starts on `s + s` (or uses Booth's algorithm).

| # | Problem | Link |
|---|---|---|
| 1 | [Longest Common Prefix of Strings](https://www.geeksforgeeks.org/problems/longest-common-prefix-in-an-array5129/1) | [`02. Longest Common Prefix of Strings/`](02.%20Longest%20Common%20Prefix%20of%20Strings/) |
| 2 | [Meta Strings](https://www.geeksforgeeks.org/problems/meta-strings5713/1) | [`38. Meta Strings/`](38.%20Meta%20Strings/) |
| 3 | [Special String Comparison](https://www.geeksforgeeks.org/problems/string-comparison5858/1) | [`43. Special String Comparison/`](43.%20Special%20String%20Comparison/) |
| 4 | [Lexicographically Smallest and Largest](https://www.geeksforgeeks.org/problems/ordering-of-strings5527/1) | [`58. Lexicographically Smallest and Largest/`](58.%20Lexicographically%20Smallest%20and%20Largest/) |
| 5 | [Check if two strings are same or not](https://www.geeksforgeeks.org/problems/check-if-two-strings-are-same-or-not--155406/1) | [`61. Check if two strings are same or not/`](61.%20Check%20if%20two%20strings%20are%20same%20or%20not/) |
| 6 | [String Comparison](https://www.geeksforgeeks.org/problems/string-comparison--141631/1) | [`75. String Comparison/`](75.%20String%20Comparison/) |
| 7 | [Lexicographical maximum substring of String](https://www.geeksforgeeks.org/problems/lexicographical-maximum-substring/1) | [`93. Lexicographical maximum substring of String/`](93.%20Lexicographical%20maximum%20substring%20of%20String/) |

## Pattern 14: Recursion, Backtracking & Generation

The output is a list of strings, so recursion builds them. At each position, try every allowed character, recurse, then undo. Pruning keeps it fast: track the count of 1s versus 0s for prefix rules, skip repeated characters at the same depth for distinct permutations, and build only half of a palindrome. Additive sequence checks try every split of the first two numbers and recurse on the rest.

| # | Problem | Link |
|---|---|---|
| 1 | [Generate Binary Strings](https://www.geeksforgeeks.org/problems/generate-binary-string3642/1) | [`45. Generate Binary Strings/`](45.%20Generate%20Binary%20Strings/) |
| 2 | [Split Into 4 Distinct Substrings](https://www.geeksforgeeks.org/problems/split-the-string2424/1) | [`70. Split Into 4 Distinct Substrings/`](70.%20Split%20Into%204%20Distinct%20Substrings/) |

## Pattern 15: Prefix Balance & Running Counts

Turn characters into +1/-1 (or a value) and keep a running sum. A split point where both sides balance is where the prefix and suffix counts agree. Longest balanced substring and equal upper/lower counts look up earlier equal prefixes. Roll operations use a difference array on prefix sums. Maximum-weight substring is Kadane's algorithm over character values.

| # | Problem | Link |
|---|---|---|
| 1 | [Equal Point in Brackets](https://www.geeksforgeeks.org/problems/find-equal-point-in-string-of-brackets2542/1) | [`20. Equal Point in Brackets/`](20.%20Equal%20Point%20in%20Brackets/) |
| 2 | [Balanced Splits of a Binary  String](https://www.geeksforgeeks.org/problems/split-the-binary-string-into-substrings-with-equal-number-of-0s-and-1s/1) | [`25. Balanced Splits of a Binary String/`](25.%20Balanced%20Splits%20of%20a%20Binary%20String/) |
| 3 | [Count Substrings with Same Lower and Upper](https://www.geeksforgeeks.org/problems/count-the-substrings--141634/1) | [`32. Count Substrings with Same Lower and Upper/`](32.%20Count%20Substrings%20with%20Same%20Lower%20and%20Upper/) |
| 4 | [Longest Balanced Substring](https://www.geeksforgeeks.org/problems/longest-even-length-substring--113837/1) | [`94. Longest Balanced Substring/`](94.%20Longest%20Balanced%20Substring/) |

## Pattern 16: Stack-Based Reduction

Removals that can expose new removable neighbours need a stack. Push each character. If the top of the stack plus the new character forms a deletable pattern (two equal, three equal, 'ac', '100'), pop instead. What remains on the stack is the answer, and indices on the stack give the longest removable segment. The decreasing/increasing number pattern uses a stack to reverse each run of 'D'.

| # | Problem | Link |
|---|---|---|
| 1 | [Remove b and ac from a given string](https://www.geeksforgeeks.org/problems/remove-b-and-ac-from-a-given-string4336/1) | [`30. Remove b and ac from a given string/`](30.%20Remove%20b%20and%20ac%20from%20a%20given%20string/) |
| 2 | [Repeated Removal of 3 Consecutive Duplicates](https://www.geeksforgeeks.org/problems/three-consecutive-duplicates2434/1) | [`72. Repeated Removal of 3 Consecutive Duplicates/`](72.%20Repeated%20Removal%20of%203%20Consecutive%20Duplicates/) |
| 3 | [Max Length Removal with 100](https://www.geeksforgeeks.org/problems/max-length-removal0452/1) | [`79. Max Length Removal with 100/`](79.%20Max%20Length%20Removal%20with%20100/) |

## Pattern 17: Implicit Expansion & K-th Character

The string is defined by repeated expansion (repeat counts, binary transformations, infinite doubling) and would be far too long to build. Track how long each stage would be. To find the k-th character, go backwards: reduce `k` modulo the repeat length, or map it back through each transformation step. Binary transformation versions use the parity of set bits or the block that `k` falls in.

| # | Problem | Link |
|---|---|---|
| 1 | [Kth Character in an Encoded String](https://www.geeksforgeeks.org/problems/decode-it1646/1) | [`67. Kth Character in an Encoded String/`](67.%20Kth%20Character%20in%20an%20Encoded%20String/) |

## Pattern 18: Dynamic Programming on Strings

Overlapping subproblems over prefixes. `dp[i][j]` asks whether (or how cheaply) the first `i` characters of one string can produce the first `j` of another. Regex matching handles `.` and `*` by looking back one or two pattern characters. String conversion decides per character whether to capitalise or delete. Chain problems keep the best length ending at each character. Copy-paste minimum operations build up from divisors.

| # | Problem | Link |
|---|---|---|
| 1 | [String Conversion](https://www.geeksforgeeks.org/problems/convert-the-string1022/1) | [`73. String Conversion/`](73.%20String%20Conversion/) |

## Pattern 19: Binary Strings & Bit Manipulation

Problems where the string is a bit pattern or bit operations do the work. Unset or rotate bits with masks and shifts. Minimum flips to an alternating string counts mismatches against both '0101...' and '1010...' and takes the smaller. XOR cipher recovers the original by XORing adjacent prefix values.

| # | Problem | Link |
|---|---|---|
| 1 | [Rotate Bits](https://www.geeksforgeeks.org/problems/rotate-bits4524/1) | [`11. Rotate Bits/`](11.%20Rotate%20Bits/) |
| 2 | [Min Number of Flips](https://www.geeksforgeeks.org/problems/min-number-of-flips3210/1) | [`16. Min Number of Flips/`](16.%20Min%20Number%20of%20Flips/) |
