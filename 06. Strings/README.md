# 6. Strings

[← Back to root](../README.md) · [GfG topic problems](https://www.geeksforgeeks.org/explore?category%5B%5D=Strings)

## Patterns (merged across all difficulty levels)

Same core technique shows up at every difficulty — this view merges those occurrences into one pattern, with problems ordered Basics → Easy → Medium → Hard. Logic/Time/Space are filled in as each problem's full article is written.

| # | Pattern | Logic | Typical Time | Typical Space | Total | Basics | Easy | Medium | Hard |
|---|---|---|---|---|---|---|---|---|---|
| 1 | [Character Frequency Counting & Comparison](#character-frequency-counting--comparison-24) | Fill a 26-slot (or map) count array, then query it (most frequent, distinct, missing) or compare two count arrays (anagram, removals, common characters). | O(n) | O(alphabet) | 24 | 9 | 10 | 5 | 0 |
| 2 | [Linear Character Scan & Filter](#linear-character-scan--filter-23) | Walk the string once, test each character (digit, vowel, letter, position, target), and count it, record its index, or keep/drop it in the output. | O(n) | O(1) / O(n) for output | 23 | 19 | 4 | 0 | 0 |
| 3 | [Big Number Arithmetic & Digit Divisibility](#big-number-arithmetic--digit-divisibility-20) | Treat the number as a digit string: add, multiply, divide, or compare digit by digit with a carry/remainder, and use divisibility rules (last digits, alternating sums, running mod). | O(n) / O(n·m) multiply | O(n) | 20 | 7 | 9 | 4 | 0 |
| 4 | [Parsing & Format / Base Conversion](#parsing--format--base-conversion-19) | Read a structured string (numbers, Roman numerals, IP, time, date, column name) with a careful scan or state machine, and convert it to or from another representation. | O(n) | O(1) / O(n) | 19 | 4 | 6 | 9 | 0 |
| 5 | [Pattern Matching & Rotation (Naive / KMP / Z / Rabin-Karp)](#pattern-matching--rotation-naive--kmp--z--rabin-karp-17) | Find a pattern in a text with naive search, the KMP LPS array, the Z-array, or a rolling hash; rotation checks search in s+s. | O(n + m) (O(n·m) naive) | O(m) / O(n + m) | 17 | 2 | 5 | 5 | 5 |
| 6 | [Greedy Digit / Character Choice & Next Permutation](#greedy-digit--character-choice--next-permutation-17) | Pick the best digit or character at each position from the left (one swap, next/previous permutation, keep largest prefix) to get the largest or smallest result. | O(n) / O(n log n) | O(1) / O(n) | 17 | 2 | 10 | 5 | 0 |
| 7 | [String Building & Simulation](#string-building--simulation-16) | Construct the output step by step following the stated rules (merge, insert, replace, rotate, move a robot, lay out text) using a buffer or StringBuilder. | O(n) to O(n·k) | O(n) | 16 | 5 | 6 | 5 | 0 |
| 8 | [Two Pointers, Reversal & Palindromes](#two-pointers-reversal--palindromes-13) | Move pointers inward from both ends to reverse or compare mirrored characters, or walk two strings side by side (subsequence check, backspace-style matching). | O(n) | O(1) | 13 | 3 | 5 | 5 | 0 |
| 9 | [Case Conversion & Character Mapping (ASCII Arithmetic)](#case-conversion--character-mapping-ascii-arithmetic-11) | Transform each character with ASCII arithmetic or a fixed lookup (lower/upper toggle, mirror 'a'+'z'-c, keypad digit, digit swap), often deciding per position or per word. | O(n) | O(1) / O(n) for output | 11 | 8 | 2 | 1 | 0 |
| 10 | [Consecutive Runs & Grouping](#consecutive-runs--grouping-11) | Scan and group equal adjacent characters into runs; act on run boundaries (compress, collapse, count longest run, check one block per character). | O(n) | O(1) / O(n) for output | 11 | 4 | 6 | 1 | 0 |
| 11 | [Counting & Combinatorics on Strings](#counting--combinatorics-on-strings-11) | Count substrings, strings, or arrangements with a closed formula (c·(c-1)/2, sum of (i+1), factorials, stars and bars) instead of enumerating them. | O(n) / O(1) | O(1) | 11 | 2 | 6 | 3 | 0 |
| 12 | [Word Tokenization & Sentence Processing](#word-tokenization--sentence-processing-10) | Split on spaces (or scan for word boundaries), then measure, reverse, compare, or transform whole words. | O(n) | O(n) | 10 | 5 | 5 | 0 | 0 |
| 13 | [Lexicographic Comparison & Sorting](#lexicographic-comparison--sorting-9) | Compare strings character by character (or with a custom rule), sort them, or track the best candidate: longest common prefix, smallest/largest string, max suffix, smallest rotation. | O(n·m) / O(n log n) | O(1) / O(n) | 9 | 1 | 7 | 0 | 1 |
| 14 | [Recursion, Backtracking & Generation](#recursion-backtracking--generation-7) | Generate all valid strings by choosing one character at a time and undoing the choice (permutations, wildcards, prefix-constrained binaries, adjacent-digit numbers). | O(n · n!) / O(2^n) | O(n) recursion | 7 | 0 | 2 | 4 | 1 |
| 15 | [Prefix Balance & Running Counts](#prefix-balance--running-counts-6) | Keep a running balance or prefix count (open-close, 0s-1s, upper-lower, difference array, Kadane sum) and use it to find split points or best substrings. | O(n) | O(1) / O(n) | 6 | 0 | 4 | 2 | 0 |
| 16 | [Stack-Based Reduction](#stack-based-reduction-5) | Push characters onto a stack and pop when the top forms a removable group with the new character (adjacent duplicates, 'ac', '100', triples), or use the stack to reverse runs. | O(n) | O(n) | 5 | 0 | 3 | 2 | 0 |
| 17 | [Implicit Expansion & K-th Character](#implicit-expansion--k-th-character-5) | Never build the huge expanded string: compute lengths per step, then walk back (or use bit/period math) to find which original character lands at index k. | O(n) / O(log k) | O(1) / O(n) | 5 | 0 | 1 | 3 | 1 |
| 18 | [Dynamic Programming on Strings](#dynamic-programming-on-strings-5) | Define dp over prefixes (or over the last character) and fill a table: regex matching, string conversion, decode counts, chain lengths, minimum operations. | O(n·m) | O(n·m) / O(m) | 5 | 0 | 1 | 3 | 1 |
| 19 | [Binary Strings & Bit Manipulation](#binary-strings--bit-manipulation-4) | Work on bits: set/unset/rotate bits, compare against an alternating target, or XOR characters. | O(n) / O(1) | O(1) | 4 | 1 | 2 | 1 | 0 |
| | **Total (19 patterns)** | | | | **233** | **72** | **94** | **58** | **9** |

### Character Frequency Counting & Comparison (24)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Remove Common and Concat](https://www.geeksforgeeks.org/problems/remove-common-characters-and-concatenate-1587115621/1) | — | — | — | Basics | Microsoft | Strings | [`01. Basics/08. Remove Common and Concat/`](01.%20Basics/08.%20Remove%20Common%20and%20Concat/) |
| 2 | [Make Anagram with Removals](https://www.geeksforgeeks.org/problems/anagram-of-string/1) | — | — | — | Basics | Amazon | Strings, anagram | [`01. Basics/10. Make Anagram with Removals/`](01.%20Basics/10.%20Make%20Anagram%20with%20Removals/) |
| 3 | [Red OR Green](https://www.geeksforgeeks.org/problems/red-or-green5711/1) | — | — | — | Basics | — | Strings | [`01. Basics/28. Red OR Green/`](01.%20Basics/28.%20Red%20OR%20Green/) |
| 4 | [Missing Characters in Panagram](https://www.geeksforgeeks.org/problems/missing-characters-in-panagram/1) | — | — | — | Basics | — | Strings | [`01. Basics/44. Missing Characters in Panagram/`](01.%20Basics/44.%20Missing%20Characters%20in%20Panagram/) |
| 5 | [Minimum String Value After K Removals](https://www.geeksforgeeks.org/problems/minimize-string-value1010/1) | — | — | — | Basics | Amazon, Microsoft, FactSet | Strings | [`01. Basics/45. Minimum String Value After K Removals/`](01.%20Basics/45.%20Minimum%20String%20Value%20After%20K%20Removals/) |
| 6 | [Same Frequency in Two Halves](https://www.geeksforgeeks.org/problems/riyas-test1450/1) | — | — | — | Basics | — | Strings | [`01. Basics/54. Same Frequency in Two Halves/`](01.%20Basics/54.%20Same%20Frequency%20in%20Two%20Halves/) |
| 7 | [Count Distinct Vowels in String](https://www.geeksforgeeks.org/problems/count-distinct-vowels-in-string/1) | — | — | — | Basics | — | Strings | [`01. Basics/56. Count Distinct Vowels in String/`](01.%20Basics/56.%20Count%20Distinct%20Vowels%20in%20String/) |
| 8 | [Any Common Word in Two Lists](https://www.geeksforgeeks.org/problems/sort-the-fest0016/1) | — | — | — | Basics | — | Strings | [`01. Basics/64. Any Common Word in Two Lists/`](01.%20Basics/64.%20Any%20Common%20Word%20in%20Two%20Lists/) |
| 9 | [Count Equal Pairs in String](https://www.geeksforgeeks.org/problems/count-number-of-equal-pairs-in-a-string0520/1) | — | — | — | Basics | — | Strings | [`01. Basics/68. Count Equal Pairs in String/`](01.%20Basics/68.%20Count%20Equal%20Pairs%20in%20String/) |
| 10 | [String Duplicates Removal](https://www.geeksforgeeks.org/problems/remove-all-duplicates-from-a-given-string4321/1) | — | — | — | Easy | Amazon, Microsoft, Adobe | Arrays, Strings | [`02. Easy/04. String Duplicates Removal/`](02.%20Easy/04.%20String%20Duplicates%20Removal/) |
| 11 | [Most Frequent Character](https://www.geeksforgeeks.org/problems/maximum-occuring-character-1587115620/1) | — | — | — | Easy | Flipkart | Strings | [`02. Easy/06. Most Frequent Character/`](02.%20Easy/06.%20Most%20Frequent%20Character/) |
| 12 | [Panagram Checking](https://www.geeksforgeeks.org/problems/pangram-checking-1587115620/1) | — | — | — | Easy | Snapdeal | Strings | [`02. Easy/08. Panagram Checking/`](02.%20Easy/08.%20Panagram%20Checking/) |
| 13 | [Remove Characters Present in  Other](https://www.geeksforgeeks.org/problems/remove-character3815/1) | — | — | — | Easy | Zoho, Amazon | Strings | [`02. Easy/14. Remove Characters Present in Other/`](02.%20Easy/14.%20Remove%20Characters%20Present%20in%20Other/) |
| 14 | [Max Frequency Word](https://www.geeksforgeeks.org/problems/word-with-maximum-frequency0120/1) | — | — | — | Easy | Amazon, Adobe, Microsoft, Citrix | Arrays, Strings, Map | [`02. Easy/21. Max Frequency Word/`](02.%20Easy/21.%20Max%20Frequency%20Word/) |
| 15 | [Repeating Character](https://www.geeksforgeeks.org/problems/repeating-character-first-appearance-leftmost/1) | — | — | — | Easy | Goldman Sachs | Strings | [`02. Easy/24. Repeating Character/`](02.%20Easy/24.%20Repeating%20Character/) |
| 16 | [Common Subsequence](https://www.geeksforgeeks.org/problems/common-subsequence4049/1) | — | — | — | Easy | Amazon | Strings | [`02. Easy/39. Common Subsequence/`](02.%20Easy/39.%20Common%20Subsequence/) |
| 17 | [Make all Substrings Distinct](https://www.geeksforgeeks.org/problems/minimum-changes-to-make-all-substrings-distinct4722/1) | — | — | — | Easy | — | Strings | [`02. Easy/46. Make all Substrings Distinct/`](02.%20Easy/46.%20Make%20all%20Substrings%20Distinct/) |
| 18 | [Minimum Replacements to Make Anagram](https://www.geeksforgeeks.org/problems/min-manipulations-to-make-strings-anagram1421/1) | — | — | — | Easy | Flipkart, Yatra.com | Strings, anagram | [`02. Easy/55. Minimum Replacements to Make Anagram/`](02.%20Easy/55.%20Minimum%20Replacements%20to%20Make%20Anagram/) |
| 19 | [Make a String with Deletion and Rearrangement](https://www.geeksforgeeks.org/problems/make-a-string-from-another-string--141625/1) | — | — | — | Easy | — | Strings | [`02. Easy/89. Make a String with Deletion and Rearrangement/`](02.%20Easy/89.%20Make%20a%20String%20with%20Deletion%20and%20Rearrangement/) |
| 20 | [Check Repeated Substring with K Replacements](https://www.geeksforgeeks.org/problems/check-if-a-string-is-repetition-of-its-substring-of-k-length3302/1) | — | — | — | Medium | — | Strings, Map | [`03. Medium/13. Check Repeated Substring with K Replacements/`](03.%20Medium/13.%20Check%20Repeated%20Substring%20with%20K%20Replacements/) |
| 21 | [Exactly one swap](https://www.geeksforgeeks.org/problems/exactly-one-swap--170637/1) | — | — | — | Medium | — | Strings | [`03. Medium/19. Exactly one swap/`](03.%20Medium/19.%20Exactly%20one%20swap/) |
| 22 | [Sum of Beauty of All Substrings](https://www.geeksforgeeks.org/problems/sum-of-beauty-of-all-substrings-1662962118/1) | — | — | — | Medium | — | Strings | [`03. Medium/25. Sum of Beauty of All Substrings/`](03.%20Medium/25.%20Sum%20of%20Beauty%20of%20All%20Substrings/) |
| 23 | [Maximum Reachable Index Difference](https://www.geeksforgeeks.org/problems/maximum-reachable-index-difference/1) | — | — | — | Medium | — | Strings | [`03. Medium/32. Maximum Reachable Index Difference/`](03.%20Medium/32.%20Maximum%20Reachable%20Index%20Difference/) |
| 24 | [Concatenate Equal to Target](https://www.geeksforgeeks.org/problems/concatenate-equal-to-target/1) | — | — | — | Medium | — | Strings, Arrays, Map | [`03. Medium/45. Concatenate Equal to Target/`](03.%20Medium/45.%20Concatenate%20Equal%20to%20Target/) |

### Linear Character Scan & Filter (23)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Check for Binary String](https://www.geeksforgeeks.org/problems/check-for-binary/1) | — | — | — | Basics | — | Strings | [`01. Basics/03. Check for Binary String/`](01.%20Basics/03.%20Check%20for%20Binary%20String/) |
| 2 | [Even Positioned Characters](https://www.geeksforgeeks.org/problems/for-loop-2/1) | — | — | — | Basics | — | Strings | [`01. Basics/04. Even Positioned Characters/`](01.%20Basics/04.%20Even%20Positioned%20Characters/) |
| 3 | [Remove Spaces](https://www.geeksforgeeks.org/problems/remove-spaces0128/1) | — | — | — | Basics | SAP Labs | Strings | [`01. Basics/07. Remove Spaces/`](01.%20Basics/07.%20Remove%20Spaces/) |
| 4 | [Remove Vowels](https://www.geeksforgeeks.org/problems/remove-vowels-from-string1446/1) | — | — | — | Basics | GE | Strings | [`01. Basics/12. Remove Vowels/`](01.%20Basics/12.%20Remove%20Vowels/) |
| 5 | [Delete alternate characters](https://www.geeksforgeeks.org/problems/java-delete-alternate-characters4036/1) | — | — | — | Basics | — | Strings, Java | [`01. Basics/17. Delete alternate characters/`](01.%20Basics/17.%20Delete%20alternate%20characters/) |
| 6 | [Length of String](https://www.geeksforgeeks.org/problems/length-of-string/1) | — | — | — | Basics | — | Strings | [`01. Basics/18. Length of String/`](01.%20Basics/18.%20Length%20of%20String/) |
| 7 | [Check if All Characters Same](https://www.geeksforgeeks.org/problems/check-string1818/1) | — | — | — | Basics | — | Strings | [`01. Basics/19. Check if All Characters Same/`](01.%20Basics/19.%20Check%20if%20All%20Characters%20Same/) |
| 8 | [String with Number at End](https://www.geeksforgeeks.org/problems/string-with-numbers-at-its-end5749/1) | — | — | — | Basics | Codenation | Strings | [`01. Basics/24. String with Number at End/`](01.%20Basics/24.%20String%20with%20Number%20at%20End/) |
| 9 | [Count of camel case characters](https://www.geeksforgeeks.org/problems/find-the-camel3348/1) | — | — | — | Basics | — | Strings | [`01. Basics/25. Count of camel case characters/`](01.%20Basics/25.%20Count%20of%20camel%20case%20characters/) |
| 10 | [Count Types of Characters](https://www.geeksforgeeks.org/problems/count-type-of-characters3635/1) | — | — | — | Basics | Amazon, MakeMyTrip | Strings | [`01. Basics/26. Count Types of Characters/`](01.%20Basics/26.%20Count%20Types%20of%20Characters/) |
| 11 | [Remove All Except Alphabets](https://www.geeksforgeeks.org/problems/remove-all-characters-other-than-alphabets4923/1) | — | — | — | Basics | — | Strings | [`01. Basics/29. Remove All Except Alphabets/`](01.%20Basics/29.%20Remove%20All%20Except%20Alphabets/) |
| 12 | [Remove Characters from Alphanumeric String](https://www.geeksforgeeks.org/problems/remove-characters-from-alphanumeric-string0648/1) | — | — | — | Basics | — | Strings | [`01. Basics/33. Remove Characters from Alphanumeric String/`](01.%20Basics/33.%20Remove%20Characters%20from%20Alphanumeric%20String/) |
| 13 | [Last index of a character](https://www.geeksforgeeks.org/problems/last-index-of-a-character-in-the-string4516/1) | — | — | — | Basics | — | Strings | [`01. Basics/41. Last index of a character/`](01.%20Basics/41.%20Last%20index%20of%20a%20character/) |
| 14 | [Segregate Different Types of Characters](https://www.geeksforgeeks.org/problems/split-strings5211/1) | — | — | — | Basics | — | Strings | [`01. Basics/42. Segregate Different Types of Characters/`](01.%20Basics/42.%20Segregate%20Different%20Types%20of%20Characters/) |
| 15 | [Successful Penalty Conversions](https://www.geeksforgeeks.org/problems/the-penalty-shootout3810/1) | — | — | — | Basics | — | Strings | [`01. Basics/43. Successful Penalty Conversions/`](01.%20Basics/43.%20Successful%20Penalty%20Conversions/) |
| 16 | [Remove Sandwiched Vowels](https://www.geeksforgeeks.org/problems/sandwiched-vowels5158/1) | — | — | — | Basics | — | Arrays, Strings | [`01. Basics/46. Remove Sandwiched Vowels/`](01.%20Basics/46.%20Remove%20Sandwiched%20Vowels/) |
| 17 | [Numbers with Given Digit](https://www.geeksforgeeks.org/problems/find-the-number-which-contain-the-digit-d4144/1) | — | — | — | Basics | — | Strings, Mathematics, Numbers | [`01. Basics/47. Numbers with Given Digit/`](01.%20Basics/47.%20Numbers%20with%20Given%20Digit/) |
| 18 | [Duck Number](https://www.geeksforgeeks.org/problems/zero-number2158/1) | — | — | — | Basics | — | Strings | [`01. Basics/49. Duck Number/`](01.%20Basics/49.%20Duck%20Number/) |
| 19 | [Good String](https://www.geeksforgeeks.org/problems/good-string5712/1) | — | — | — | Basics | — | Strings | [`01. Basics/51. Good String/`](01.%20Basics/51.%20Good%20String/) |
| 20 | [Remaining String](https://www.geeksforgeeks.org/problems/remaining-string3515/1) | — | — | — | Easy | Zoho, Oracle | Strings | [`02. Easy/13. Remaining String/`](02.%20Easy/13.%20Remaining%20String/) |
| 21 | [Sum of Digits in a String](https://www.geeksforgeeks.org/problems/rearrange-a-string4100/1) | — | — | — | Easy | Facebook | Strings | [`02. Easy/35. Sum of Digits in a String/`](02.%20Easy/35.%20Sum%20of%20Digits%20in%20a%20String/) |
| 22 | [Remove all occurrences of a character in a string](https://www.geeksforgeeks.org/problems/remove-all-occurrences-of-a-character-in-a-string/1) | — | — | — | Easy | — | Strings | [`02. Easy/57. Remove all occurrences of a character in a string/`](02.%20Easy/57.%20Remove%20all%20occurrences%20of%20a%20character%20in%20a%20string/) |
| 23 | [Search a Character in a String](https://www.geeksforgeeks.org/problems/search-a-character-in-a-string/1) | — | — | — | Easy | — | Strings | [`02. Easy/71. Search a Character in a String/`](02.%20Easy/71.%20Search%20a%20Character%20in%20a%20String/) |

### Big Number Arithmetic & Digit Divisibility (20)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Array Product Even or Odd](https://www.geeksforgeeks.org/problems/product-is-even-or-odd3020/1) | — | — | — | Basics | — | Strings, Mathematics | [`01. Basics/32. Array Product Even or Odd/`](01.%20Basics/32.%20Array%20Product%20Even%20or%20Odd/) |
| 2 | [Check if divisible by 4](https://www.geeksforgeeks.org/problems/check-if-divisible-by-43813/1) | — | — | — | Basics | — | Strings, Mathematics | [`01. Basics/35. Check if divisible by 4/`](01.%20Basics/35.%20Check%20if%20divisible%20by%204/) |
| 3 | [Remainder with 7](https://www.geeksforgeeks.org/problems/remainder-with-7/1) | — | — | — | Basics | — | Strings | [`01. Basics/38. Remainder with 7/`](01.%20Basics/38.%20Remainder%20with%207/) |
| 4 | [Check if divisible by 11](https://www.geeksforgeeks.org/problems/check-if-divisible-by-114724/1) | — | — | — | Basics | — | Strings | [`01. Basics/48. Check if divisible by 11/`](01.%20Basics/48.%20Check%20if%20divisible%20by%2011/) |
| 5 | [Compare two Large Numbers](https://www.geeksforgeeks.org/problems/compare-two-large-numbers3413/1) | — | — | — | Basics | — | Strings | [`01. Basics/52. Compare two Large Numbers/`](01.%20Basics/52.%20Compare%20two%20Large%20Numbers/) |
| 6 | [Floating Point Number Even or Odd](https://www.geeksforgeeks.org/problems/floating-point-number-even-or-odd0146/1) | — | — | — | Basics | — | Strings | [`01. Basics/53. Floating Point Number Even or Odd/`](01.%20Basics/53.%20Floating%20Point%20Number%20Even%20or%20Odd/) |
| 7 | [Binary Addition of 1](https://www.geeksforgeeks.org/problems/dr-stranges-powers3333/1) | — | — | — | Basics | — | Strings, Mathematics | [`01. Basics/72. Binary Addition of 1/`](01.%20Basics/72.%20Binary%20Addition%20of%201/) |
| 8 | [Nearest Multiple of 10](https://www.geeksforgeeks.org/problems/nearest-multiple-of-102437/1) | — | — | — | Easy | Microsoft | Arrays, Strings, Mathematics | [`02. Easy/09. Nearest Multiple of 10/`](02.%20Easy/09.%20Nearest%20Multiple%20of%2010/) |
| 9 | [Divisible by 7](https://www.geeksforgeeks.org/problems/divisible-by-73224/1) | — | — | — | Easy | — | Strings | [`02. Easy/29. Divisible by 7/`](02.%20Easy/29.%20Divisible%20by%207/) |
| 10 | [Check if the number is balanced](https://www.geeksforgeeks.org/problems/check-if-the-number-is-balanced3014/1) | — | — | — | Easy | — | Strings | [`02. Easy/34. Check if the number is balanced/`](02.%20Easy/34.%20Check%20if%20the%20number%20is%20balanced/) |
| 11 | [Partition a number into two divisible parts](https://www.geeksforgeeks.org/problems/partition-a-number-into-two-divisible-parts3605/1) | — | — | — | Easy | Oracle | Strings, Mathematics, Modular Arithmetic | [`02. Easy/51. Partition a number into two divisible parts/`](02.%20Easy/51.%20Partition%20a%20number%20into%20two%20divisible%20parts/) |
| 12 | [Multiply by 11](https://www.geeksforgeeks.org/problems/multiply-by-111820/1) | — | — | — | Easy | — | Strings, Mathematics | [`02. Easy/53. Multiply by 11/`](02.%20Easy/53.%20Multiply%20by%2011/) |
| 13 | [Divisibility by 5 for Binary](https://www.geeksforgeeks.org/problems/divisible-by-5-or-not-14509/1) | — | — | — | Easy | — | Strings, Binary Representation | [`02. Easy/62. Divisibility by 5 for Binary/`](02.%20Easy/62.%20Divisibility%20by%205%20for%20Binary/) |
| 14 | [Large Number Division](https://www.geeksforgeeks.org/problems/large-number-division0207/1) | — | — | — | Easy | — | Strings | [`02. Easy/68. Large Number Division/`](02.%20Easy/68.%20Large%20Number%20Division/) |
| 15 | [Divisibility by 999](https://www.geeksforgeeks.org/problems/divisibility-by-9990149/1) | — | — | — | Easy | — | Strings, Division | [`02. Easy/74. Divisibility by 999/`](02.%20Easy/74.%20Divisibility%20by%20999/) |
| 16 | [Permutation Divisibility by 4](https://www.geeksforgeeks.org/problems/permutation-divisibility0447/1) | — | — | — | Easy | — | Strings, Mathematics | [`02. Easy/82. Permutation Divisibility by 4/`](02.%20Easy/82.%20Permutation%20Divisibility%20by%204/) |
| 17 | [Multiply Two Strings](https://www.geeksforgeeks.org/problems/multiply-two-strings/1) | — | — | — | Medium | Flipkart, Amazon, Microsoft, Samsung, Adobe, Google, Facebook, NPCI | Strings, Mathematics | [`03. Medium/04. Multiply Two Strings/`](03.%20Medium/04.%20Multiply%20Two%20Strings/) |
| 18 | [Factorials of Large](https://www.geeksforgeeks.org/problems/factorials-of-large-numbers2508/1) | — | — | — | Medium | Morgan Stanley, Microsoft, Samsung, MakeMyTrip, MAQ Software, Adobe, Philips, BrowserStack | Number Theory, Strings, Combinatorial | [`03. Medium/06. Factorials of Large/`](03.%20Medium/06.%20Factorials%20of%20Large/) |
| 19 | [Sum Two Large Numbers](https://www.geeksforgeeks.org/problems/sum-of-numbers-or-number1219/1) | — | — | — | Medium | Zoho, Amazon, Microsoft | Strings | [`03. Medium/07. Sum Two Large Numbers/`](03.%20Medium/07.%20Sum%20Two%20Large%20Numbers/) |
| 20 | [Add Binary Strings](https://www.geeksforgeeks.org/problems/add-binary-strings3805/1) | — | — | — | Medium | Amazon, Microsoft, Facebook | Strings, Mathematics | [`03. Medium/08. Add Binary Strings/`](03.%20Medium/08.%20Add%20Binary%20Strings/) |

### Parsing & Format / Base Conversion (19)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Maximum Number in a String](https://www.geeksforgeeks.org/problems/extract-maximum2943/1) | — | — | — | Basics | Amazon, TCS | Strings, Mathematics | [`01. Basics/11. Maximum Number in a String/`](01.%20Basics/11.%20Maximum%20Number%20in%20a%20String/) |
| 2 | [C++ Basic Data types](https://www.geeksforgeeks.org/problems/c-basic-data-types3128/1) | — | — | — | Basics | — | Strings, CPP, Data Type | [`01. Basics/31. C++ Basic Data types/`](01.%20Basics/31.%20C++%20Basic%20Data%20types/) |
| 3 | [Time to Words](https://www.geeksforgeeks.org/problems/time-to-words3728/1) | — | — | — | Basics | — | Strings | [`01. Basics/58. Time to Words/`](01.%20Basics/58.%20Time%20to%20Words/) |
| 4 | [Java Date and Day](https://www.geeksforgeeks.org/problems/java-date-and-day5024/1) | — | — | — | Basics | — | Strings, Java, Date-Time | [`01. Basics/71. Java Date and Day/`](01.%20Basics/71.%20Java%20Date%20and%20Day/) |
| 5 | [Roman to Integer](https://www.geeksforgeeks.org/problems/roman-number-to-integer3201/1) | — | — | — | Easy | Zoho, Amazon, Microsoft, Facebook, Twitter, Uber, NPCI | Strings | [`02. Easy/05. Roman to Integer/`](02.%20Easy/05.%20Roman%20to%20Integer/) |
| 6 | [Sum Numbers in a String](https://www.geeksforgeeks.org/problems/sum-of-numbers-in-string-1587115621/1) | — | — | — | Easy | — | Strings | [`02. Easy/12. Sum Numbers in a String/`](02.%20Easy/12.%20Sum%20Numbers%20in%20a%20String/) |
| 7 | [Decimal to Roman](https://www.geeksforgeeks.org/problems/convert-to-roman-no/1) | — | — | — | Easy | Amazon, Microsoft, InfoEdge, Facebook, Twitter | Strings | [`02. Easy/19. Decimal to Roman/`](02.%20Easy/19.%20Decimal%20to%20Roman/) |
| 8 | [Time Difference](https://www.geeksforgeeks.org/problems/time-difference5528/1) | — | — | — | Easy | — | Strings, Mathematics | [`02. Easy/85. Time Difference/`](02.%20Easy/85.%20Time%20Difference/) |
| 9 | [Kth Boom Number](https://www.geeksforgeeks.org/problems/kth-boom-number5609/1) | — | — | — | Easy | — | Arrays, Strings | [`02. Easy/86. Kth Boom Number/`](02.%20Easy/86.%20Kth%20Boom%20Number/) |
| 10 | [Patients with Hypertension](https://www.geeksforgeeks.org/problems/patients-with-hypertension/1) | — | — | — | Easy | — | Strings | [`02. Easy/92. Patients with Hypertension/`](02.%20Easy/92.%20Patients%20with%20Hypertension/) |
| 11 | [Validate an IP Address](https://www.geeksforgeeks.org/problems/validate-an-ip-address-1587115621/1) | — | — | — | Medium | Zoho, Amazon, Microsoft, Qualcomm | Strings | [`03. Medium/02. Validate an IP Address/`](03.%20Medium/02.%20Validate%20an%20IP%20Address/) |
| 12 | [Implement Atoi](https://www.geeksforgeeks.org/problems/implement-atoi/1) | — | — | — | Medium | Morgan Stanley, Amazon, Microsoft, Payu, Adobe, Code Brew | Strings, Design-Pattern | [`03. Medium/03. Implement Atoi/`](03.%20Medium/03.%20Implement%20Atoi/) |
| 13 | [Excel Column Name from Number](https://www.geeksforgeeks.org/problems/column-name-from-a-given-column-number4244/1) | — | — | — | Medium | Paytm, Amazon, Microsoft, Samsung, Goldman Sachs, Directi | Strings, Mathematics | [`03. Medium/09. Excel Column Name from Number/`](03.%20Medium/09.%20Excel%20Column%20Name%20from%20Number/) |
| 14 | [Nth Number with Prime Digits](https://www.geeksforgeeks.org/problems/nth-number-made-of-prime-digits4319/1) | — | — | — | Medium | — | Arrays, Strings, Mathematics | [`03. Medium/24. Nth Number with Prime Digits/`](03.%20Medium/24.%20Nth%20Number%20with%20Prime%20Digits/) |
| 15 | [Leading Zeros in IP Address Style String](https://www.geeksforgeeks.org/problems/remove-leading-zeros-from-an-ip-address3530/1) | — | — | — | Medium | — | Strings | [`03. Medium/40. Leading Zeros in IP Address Style String/`](03.%20Medium/40.%20Leading%20Zeros%20in%20IP%20Address%20Style%20String/) |
| 16 | [Encode and Decode Strings](https://www.geeksforgeeks.org/problems/encode-and-decode-strings/1) | — | — | — | Medium | — | Strings, Arrays | [`03. Medium/44. Encode and Decode Strings/`](03.%20Medium/44.%20Encode%20and%20Decode%20Strings/) |
| 17 | [Missing in  String of Consecutive Numbers](https://www.geeksforgeeks.org/problems/find-the-missing-no-in-string/1) | — | — | — | Medium | Intuit | Strings | [`03. Medium/48. Missing in String of Consecutive Numbers/`](03.%20Medium/48.%20Missing%20in%20String%20of%20Consecutive%20Numbers/) |
| 18 | [Comment Removal](https://www.geeksforgeeks.org/problems/comment-removal2017/1) | — | — | — | Medium | BrowserStack | Strings | [`03. Medium/51. Comment Removal/`](03.%20Medium/51.%20Comment%20Removal/) |
| 19 | [Longest Arithmetic Progression in a String](https://www.geeksforgeeks.org/problems/archana-and-her-tricky-string2910/1) | — | — | — | Medium | — | Strings, Mathematics, series | [`03. Medium/55. Longest Arithmetic Progression in a String/`](03.%20Medium/55.%20Longest%20Arithmetic%20Progression%20in%20a%20String/) |

### Pattern Matching & Rotation (Naive / KMP / Z / Rabin-Karp) (17)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [First Occurence](https://www.geeksforgeeks.org/problems/implement-strstr/1) | — | — | — | Basics | Amazon, Microsoft, Facebook, Qualcomm | Strings, Pattern Searching, Design-Pattern, implementation | [`01. Basics/02. First Occurence/`](01.%20Basics/02.%20First%20Occurence/) |
| 2 | [Replace Substring with Space](https://www.geeksforgeeks.org/problems/extraction-of-secret-message0616/1) | — | — | — | Basics | — | Strings | [`01. Basics/67. Replace Substring with Space/`](01.%20Basics/67.%20Replace%20Substring%20with%20Space/) |
| 3 | [String Rotated by 2 Places](https://www.geeksforgeeks.org/problems/check-if-string-is-rotated-by-two-places-1587115620/1) | — | — | — | Easy | Accolite, Amazon | Strings | [`02. Easy/03. String Rotated by 2 Places/`](02.%20Easy/03.%20String%20Rotated%20by%202%20Places/) |
| 4 | [Type it!](https://www.geeksforgeeks.org/problems/type-it--170645/1) | — | — | — | Easy | — | Strings | [`02. Easy/33. Type it!/`](02.%20Easy/33.%20Type%20it!/) |
| 5 | [Longest Prefix as a Substring](https://www.geeksforgeeks.org/problems/minimum-shift-for-longest-common-prefix0759/1) | — | — | — | Easy | — | Strings | [`02. Easy/41. Longest Prefix as a Substring/`](02.%20Easy/41.%20Longest%20Prefix%20as%20a%20Substring/) |
| 6 | [Replace Word](https://www.geeksforgeeks.org/problems/replace-a-word5553/1) | — | — | — | Easy | Adobe | Strings | [`02. Easy/60. Replace Word/`](02.%20Easy/60.%20Replace%20Word/) |
| 7 | [Overlapping Substrings](https://www.geeksforgeeks.org/problems/overlapping-substrings2654/1) | — | — | — | Easy | — | Strings | [`02. Easy/91. Overlapping Substrings/`](02.%20Easy/91.%20Overlapping%20Substrings/) |
| 8 | [Strings Rotations of Each Other](https://www.geeksforgeeks.org/problems/check-if-strings-are-rotations-of-each-other-or-not-1587115620/1) | — | — | — | Medium | Oracle, Adobe, NPCI | Strings | [`03. Medium/01. Strings Rotations of Each Other/`](03.%20Medium/01.%20Strings%20Rotations%20of%20Each%20Other/) |
| 9 | [Cat and Hat](https://www.geeksforgeeks.org/problems/cat-and-hat-python/1) | — | — | — | Medium | — | Strings | [`03. Medium/17. Cat and Hat/`](03.%20Medium/17.%20Cat%20and%20Hat/) |
| 10 | [Add Minimum Characters](https://www.geeksforgeeks.org/problems/add-minimum-characters--170648/1) | — | — | — | Medium | Samsung | Strings | [`03. Medium/18. Add Minimum Characters/`](03.%20Medium/18.%20Add%20Minimum%20Characters/) |
| 11 | [String formation from substring](https://www.geeksforgeeks.org/problems/string-formation-from-substring2734/1) | — | — | — | Medium | Amazon, MakeMyTrip | Strings | [`03. Medium/21. String formation from substring/`](03.%20Medium/21.%20String%20formation%20from%20substring/) |
| 12 | [Case Insensitive Search](https://www.geeksforgeeks.org/problems/case-insensitive-search/1) | — | — | — | Medium | — | Strings, Pattern Searching | [`03. Medium/58. Case Insensitive Search/`](03.%20Medium/58.%20Case%20Insensitive%20Search/) |
| 13 | [Search Pattern](https://www.geeksforgeeks.org/problems/search-pattern0205/1) | — | — | — | Hard | Microsoft, Payu, MAQ Software, Oracle | Strings, Pattern Searching | [`04. Hard/01. Search Pattern/`](04.%20Hard/01.%20Search%20Pattern/) |
| 14 | [Longest Prefix Suffix](https://www.geeksforgeeks.org/problems/longest-prefix-suffix2527/1) | — | — | — | Hard | Accolite, Amazon, Microsoft, MakeMyTrip, NPCI | Strings | [`04. Hard/02. Longest Prefix Suffix/`](04.%20Hard/02.%20Longest%20Prefix%20Suffix/) |
| 15 | [Min Chars to Add for Palindrome](https://www.geeksforgeeks.org/problems/minimum-characters-to-be-added-at-front-to-make-string-palindrome/1) | — | — | — | Hard | NPCI | Strings | [`04. Hard/03. Min Chars to Add for Palindrome/`](04.%20Hard/03.%20Min%20Chars%20to%20Add%20for%20Palindrome/) |
| 16 | [Search Pattern (Rabin-Karp Algorithm)](https://www.geeksforgeeks.org/problems/search-pattern-rabin-karp-algorithm--141631/1) | — | — | — | Hard | Microsoft | Strings, Pattern Searching | [`04. Hard/04. Search Pattern (Rabin-Karp Algorithm)/`](04.%20Hard/04.%20Search%20Pattern%20(Rabin-Karp%20Algorithm)/) |
| 17 | [Max Occurring Prefix Suffix Substring](https://www.geeksforgeeks.org/problems/elixir-of-life--141631/1) | — | — | — | Hard | — | Strings | [`04. Hard/07. Max Occurring Prefix Suffix Substring/`](04.%20Hard/07.%20Max%20Occurring%20Prefix%20Suffix%20Substring/) |

### Greedy Digit / Character Choice & Next Permutation (17)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Odd to Largest Even with One Swap](https://www.geeksforgeeks.org/problems/odd-to-even0537/1) | — | — | — | Basics | Morgan Stanley | Strings | [`01. Basics/39. Odd to Largest Even with One Swap/`](01.%20Basics/39.%20Odd%20to%20Largest%20Even%20with%20One%20Swap/) |
| 2 | [Maximum Integer Value](https://www.geeksforgeeks.org/problems/maximum-integer-value1434/1) | — | — | — | Basics | Facebook | Strings, Mathematics | [`01. Basics/57. Maximum Integer Value/`](01.%20Basics/57.%20Maximum%20Integer%20Value/) |
| 3 | [Wifi Range](https://www.geeksforgeeks.org/problems/wifi-range--170647/1) | — | — | — | Easy | — | Strings | [`02. Easy/17. Wifi Range/`](02.%20Easy/17.%20Wifi%20Range/) |
| 4 | [String Mirror](https://www.geeksforgeeks.org/problems/string-mirror--170647/1) | — | — | — | Easy | — | Strings, Mathematics | [`02. Easy/26. String Mirror/`](02.%20Easy/26.%20String%20Mirror/) |
| 5 | [Append Smaller at Both Ends](https://www.geeksforgeeks.org/problems/repeat-the-strings/1) | — | — | — | Easy | — | Strings, implementation | [`02. Easy/28. Append Smaller at Both Ends/`](02.%20Easy/28.%20Append%20Smaller%20at%20Both%20Ends/) |
| 6 | [Largest odd number in string](https://www.geeksforgeeks.org/problems/largest-odd-number-in-string/1) | — | — | — | Easy | — | Strings | [`02. Easy/31. Largest odd number in string/`](02.%20Easy/31.%20Largest%20odd%20number%20in%20string/) |
| 7 | [Smallest Number In One Swap](https://www.geeksforgeeks.org/problems/smallest-number-in-one-swap0010/1) | — | — | — | Easy | — | Strings | [`02. Easy/64. Smallest Number In One Swap/`](02.%20Easy/64.%20Smallest%20Number%20In%20One%20Swap/) |
| 8 | [Make All Even with Minimum Operations](https://www.geeksforgeeks.org/problems/the-even-array3825/1) | — | — | — | Easy | — | Strings | [`02. Easy/65. Make All Even with Minimum Operations/`](02.%20Easy/65.%20Make%20All%20Even%20with%20Minimum%20Operations/) |
| 9 | [Make x times 0's and y times 1's](https://www.geeksforgeeks.org/problems/rearrange-string-as-alternate-x-and-y-occurences3835/1) | — | — | — | Easy | — | Strings | [`02. Easy/76. Make x times 0's and y times 1's/`](02.%20Easy/76.%20Make%20x%20times%200's%20and%20y%20times%201's/) |
| 10 | [Lexicographically Previous Permutation](https://www.geeksforgeeks.org/problems/lexicographically-previous-permutation3620/1) | — | — | — | Easy | — | Strings, permutation | [`02. Easy/77. Lexicographically Previous Permutation/`](02.%20Easy/77.%20Lexicographically%20Previous%20Permutation/) |
| 11 | [Largest Permutation Smaller than Other Number](https://www.geeksforgeeks.org/problems/maximize-permutations2915/1) | — | — | — | Easy | — | Strings, Mathematics, permutation | [`02. Easy/87. Largest Permutation Smaller than Other Number/`](02.%20Easy/87.%20Largest%20Permutation%20Smaller%20than%20Other%20Number/) |
| 12 | [Smallest Greater Date with Same Digits](https://www.geeksforgeeks.org/problems/the-wedding-date5302/1) | — | — | — | Easy | — | Strings, Date-Time | [`02. Easy/88. Smallest Greater Date with Same Digits/`](02.%20Easy/88.%20Smallest%20Greater%20Date%20with%20Same%20Digits/) |
| 13 | [Alternate Vowel and Consonant String](https://www.geeksforgeeks.org/problems/alternate-vowel-and-consonant-string2939/1) | — | — | — | Medium | — | Strings | [`03. Medium/20. Alternate Vowel and Consonant String/`](03.%20Medium/20.%20Alternate%20Vowel%20and%20Consonant%20String/) |
| 14 | [Maximum Length](https://www.geeksforgeeks.org/problems/maximum-length--170647/1) | — | — | — | Medium | — | Strings | [`03. Medium/22. Maximum Length/`](03.%20Medium/22.%20Maximum%20Length/) |
| 15 | [Next Palindromic with Same Digits](https://www.geeksforgeeks.org/problems/next-higher-palindromic-number-using-the-same-set-of-digits5859/1) | — | — | — | Medium | Microsoft, Adobe | Strings, Numbers, palindrome | [`03. Medium/34. Next Palindromic with Same Digits/`](03.%20Medium/34.%20Next%20Palindromic%20with%20Same%20Digits/) |
| 16 | [Previous Number in One Swap](https://www.geeksforgeeks.org/problems/previous-number-in-one-swap5707/1) | — | — | — | Medium | — | Strings, Numbers | [`03. Medium/39. Previous Number in One Swap/`](03.%20Medium/39.%20Previous%20Number%20in%20One%20Swap/) |
| 17 | [Next Greater with One Swap](https://www.geeksforgeeks.org/problems/next-higher-number-in-one-swap1703/1) | — | — | — | Medium | — | Strings, Numbers | [`03. Medium/50. Next Greater with One Swap/`](03.%20Medium/50.%20Next%20Greater%20with%20One%20Swap/) |

### String Building & Simulation (16)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Alternate Merge Two Strings](https://www.geeksforgeeks.org/problems/merge-two-strings2736/1) | — | — | — | Basics | Goldman Sachs | Strings | [`01. Basics/16. Alternate Merge Two Strings/`](01.%20Basics/16.%20Alternate%20Merge%20Two%20Strings/) |
| 2 | [Concatenate and Reverse](https://www.geeksforgeeks.org/problems/java-strings-set-15112/1) | — | — | — | Basics | — | Strings, Java | [`01. Basics/21. Concatenate and Reverse/`](01.%20Basics/21.%20Concatenate%20and%20Reverse/) |
| 3 | [Concatenate a List of Characters](https://www.geeksforgeeks.org/problems/convert-a-list-of-characters-into-a-string5142/1) | — | — | — | Basics | — | Strings | [`01. Basics/27. Concatenate a List of Characters/`](01.%20Basics/27.%20Concatenate%20a%20List%20of%20Characters/) |
| 4 | [Shortest direction](https://www.geeksforgeeks.org/problems/shortest-direction4201/1) | — | — | — | Basics | Flipkart | Strings | [`01. Basics/55. Shortest direction/`](01.%20Basics/55.%20Shortest%20direction/) |
| 5 | [URLify a given string](https://www.geeksforgeeks.org/problems/urlify-a-given-string--141625/1) | — | — | — | Basics | — | Strings | [`01. Basics/69. URLify a given string/`](01.%20Basics/69.%20URLify%20a%20given%20string/) |
| 6 | [License Key Formatting](https://www.geeksforgeeks.org/problems/license-key-formatting/1) | — | — | — | Easy | Google | Strings | [`02. Easy/27. License Key Formatting/`](02.%20Easy/27.%20License%20Key%20Formatting/) |
| 7 | [Rock Paper Scissors!](https://www.geeksforgeeks.org/problems/rock-paper-scissors2830/1) | — | — | — | Easy | — | Strings | [`02. Easy/42. Rock Paper Scissors!/`](02.%20Easy/42.%20Rock%20Paper%20Scissors!/) |
| 8 | [Does Robot Move Circular](https://www.geeksforgeeks.org/problems/does-robot-moves-circular0414/1) | — | — | — | Easy | Amazon, Visa | Strings | [`02. Easy/49. Does Robot Move Circular/`](02.%20Easy/49.%20Does%20Robot%20Move%20Circular/) |
| 9 | [Fizz Buzz](https://www.geeksforgeeks.org/problems/fizz-buzz/1) | — | — | — | Easy | — | Strings, Arrays | [`02. Easy/50. Fizz Buzz/`](02.%20Easy/50.%20Fizz%20Buzz/) |
| 10 | [String Concatenation](https://www.geeksforgeeks.org/problems/string-concatenation-1614157859/1) | — | — | — | Easy | — | Strings | [`02. Easy/56. String Concatenation/`](02.%20Easy/56.%20String%20Concatenation/) |
| 11 | [Remove a Character from a Given Position](https://www.geeksforgeeks.org/problems/remove-a-character-from-a-given-position/1) | — | — | — | Easy | — | Strings | [`02. Easy/81. Remove a Character from a Given Position/`](02.%20Easy/81.%20Remove%20a%20Character%20from%20a%20Given%20Position/) |
| 12 | [Minimum Days](https://www.geeksforgeeks.org/problems/minimum-days--170646/1) | — | — | — | Medium | — | Strings, permutation | [`03. Medium/28. Minimum Days/`](03.%20Medium/28.%20Minimum%20Days/) |
| 13 | [Concatenation of Zig-Zag String in n Rows](https://www.geeksforgeeks.org/problems/concatenation-of-zig-zag-string-in-n-rows0308/1) | — | — | — | Medium | PayPal | Strings | [`03. Medium/36. Concatenation of Zig-Zag String in n Rows/`](03.%20Medium/36.%20Concatenation%20of%20Zig-Zag%20String%20in%20n%20Rows/) |
| 14 | [Rotate String Queries](https://www.geeksforgeeks.org/problems/lazy-pasha1646/1) | — | — | — | Medium | — | Strings, implementation | [`03. Medium/38. Rotate String Queries/`](03.%20Medium/38.%20Rotate%20String%20Queries/) |
| 15 | [Find and Replace in String](https://www.geeksforgeeks.org/problems/find-an-replace-in-string/1) | — | — | — | Medium | Google | Strings | [`03. Medium/41. Find and Replace in String/`](03.%20Medium/41.%20Find%20and%20Replace%20in%20String/) |
| 16 | [Justified Text](https://www.geeksforgeeks.org/problems/justified-text/1) | — | — | — | Medium | Google | Arrays, Strings, implementation | [`03. Medium/57. Justified Text/`](03.%20Medium/57.%20Justified%20Text/) |

### Two Pointers, Reversal & Palindromes (13)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Reverse a String](https://www.geeksforgeeks.org/problems/reverse-a-string/1) | — | — | — | Basics | — | Strings | [`01. Basics/01. Reverse a String/`](01.%20Basics/01.%20Reverse%20a%20String/) |
| 2 | [Reverse Vowels](https://www.geeksforgeeks.org/problems/reversing-the-vowels5304/1) | — | — | — | Basics | Zoho, Flipkart | Strings | [`01. Basics/13. Reverse Vowels/`](01.%20Basics/13.%20Reverse%20Vowels/) |
| 3 | [Perfect Reversible String](https://www.geeksforgeeks.org/problems/perfect-reversible-string4828/1) | — | — | — | Basics | — | Strings | [`01. Basics/61. Perfect Reversible String/`](01.%20Basics/61.%20Perfect%20Reversible%20String/) |
| 4 | [Make Palindrome](https://www.geeksforgeeks.org/problems/make-palindrome--170647/1) | — | — | — | Easy | — | Strings, palindrome | [`02. Easy/23. Make Palindrome/`](02.%20Easy/23.%20Make%20Palindrome/) |
| 5 | [Check if it is possible to convert one string into another with given constraints](https://www.geeksforgeeks.org/problems/check-if-it-is-possible-to-convert-one-string-into-another-with-given-constraints4116/1) | — | — | — | Easy | — | Strings, constructive algo | [`02. Easy/37. Check if it is possible to convert one string into another with given constraints/`](02.%20Easy/37.%20Check%20if%20it%20is%20possible%20to%20convert%20one%20string%20into%20another%20with%20given%20constraints/) |
| 6 | [Check for Rotation of a Palindrome](https://www.geeksforgeeks.org/problems/check-if-a-given-string-is-a-rotation-of-a-palindrome0317/1) | — | — | — | Easy | — | Strings | [`02. Easy/52. Check for Rotation of a Palindrome/`](02.%20Easy/52.%20Check%20for%20Rotation%20of%20a%20Palindrome/) |
| 7 | [Remove  Palindromic Subsequences to Make Empty](https://www.geeksforgeeks.org/problems/palindromic-subsequences1335/1) | — | — | — | Easy | — | Strings, palindrome | [`02. Easy/78. Remove Palindromic Subsequences to Make Empty/`](02.%20Easy/78.%20Remove%20Palindromic%20Subsequences%20to%20Make%20Empty/) |
| 8 | [Palindrome Numbers in a Range](https://www.geeksforgeeks.org/problems/print-all-palindromes-in-the-given-range/1) | — | — | — | Easy | Flipkart | Strings | [`02. Easy/84. Palindrome Numbers in a Range/`](02.%20Easy/84.%20Palindrome%20Numbers%20in%20a%20Range/) |
| 9 | [String stack](https://www.geeksforgeeks.org/problems/string-stack--165812/1) | — | — | — | Medium | — | Strings | [`03. Medium/23. String stack/`](03.%20Medium/23.%20String%20stack/) |
| 10 | [Longest Matching in Dictionary with Removals](https://www.geeksforgeeks.org/problems/find-largest-word-in-dictionary2430/1) | — | — | — | Medium | Walmart, Google | Strings | [`03. Medium/27. Longest Matching in Dictionary with Removals/`](03.%20Medium/27.%20Longest%20Matching%20in%20Dictionary%20with%20Removals/) |
| 11 | [Palindrome with Replacement](https://www.geeksforgeeks.org/problems/palindrome-with-minimum-sum--170648/1) | — | — | — | Medium | — | Strings | [`03. Medium/29. Palindrome with Replacement/`](03.%20Medium/29.%20Palindrome%20with%20Replacement/) |
| 12 | [Special Palindrome Substrings](https://www.geeksforgeeks.org/problems/special-palindrome-substrings--170647/1) | — | — | — | Medium | MakeMyTrip | Strings | [`03. Medium/35. Special Palindrome Substrings/`](03.%20Medium/35.%20Special%20Palindrome%20Substrings/) |
| 13 | [Count Special Palindromic Substrings](https://www.geeksforgeeks.org/problems/count-special-palindromic0421/1) | — | — | — | Medium | — | Strings | [`03. Medium/52. Count Special Palindromic Substrings/`](03.%20Medium/52.%20Count%20Special%20Palindromic%20Substrings/) |

### Case Conversion & Character Mapping (ASCII Arithmetic) (11)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Convert String to Lower Case](https://www.geeksforgeeks.org/problems/convert-string-to-lowercase/1) | — | — | — | Basics | — | Strings | [`01. Basics/05. Convert String to Lower Case/`](01.%20Basics/05.%20Convert%20String%20to%20Lower%20Case/) |
| 2 | [Keypad Typing](https://www.geeksforgeeks.org/problems/keypad-typing0119/1) | — | — | — | Basics | Amazon | Strings | [`01. Basics/20. Keypad Typing/`](01.%20Basics/20.%20Keypad%20Typing/) |
| 3 | [Lower case to upper case](https://www.geeksforgeeks.org/problems/lower-case-to-upper-case3410/1) | — | — | — | Basics | — | Strings | [`01. Basics/22. Lower case to upper case/`](01.%20Basics/22.%20Lower%20case%20to%20upper%20case/) |
| 4 | [Change the Case based on First Character](https://www.geeksforgeeks.org/problems/change-the-string3541/1) | — | — | — | Basics | Oracle | Strings | [`01. Basics/23. Change the Case based on First Character/`](01.%20Basics/23.%20Change%20the%20Case%20based%20on%20First%20Character/) |
| 5 | [Front-Back Transformation  of String](https://www.geeksforgeeks.org/problems/front-back-transformation1659/1) | — | — | — | Basics | — | Strings | [`01. Basics/30. Front-Back Transformation of String/`](01.%20Basics/30.%20Front-Back%20Transformation%20of%20String/) |
| 6 | [Snake Case](https://www.geeksforgeeks.org/problems/snake-case0219/1) | — | — | — | Basics | — | Strings | [`01. Basics/50. Snake Case/`](01.%20Basics/50.%20Snake%20Case/) |
| 7 | [Alternate Lowercase and Uppercase](https://www.geeksforgeeks.org/problems/crazy-string1157/1) | — | — | — | Basics | — | Strings | [`01. Basics/59. Alternate Lowercase and Uppercase/`](01.%20Basics/59.%20Alternate%20Lowercase%20and%20Uppercase/) |
| 8 | [Max-Min Conversion](https://www.geeksforgeeks.org/problems/max-min-conversion5257/1) | — | — | — | Basics | — | Strings | [`01. Basics/66. Max-Min Conversion/`](01.%20Basics/66.%20Max-Min%20Conversion/) |
| 9 | [Convert CamelCase to Sentence](https://www.geeksforgeeks.org/problems/amend-the-sentence3235/1) | — | — | — | Easy | Adobe | Strings | [`02. Easy/47. Convert CamelCase to Sentence/`](02.%20Easy/47.%20Convert%20CamelCase%20to%20Sentence/) |
| 10 | [Toggle Case](https://www.geeksforgeeks.org/problems/toggle-case/1) | — | — | — | Easy | — | Strings | [`02. Easy/59. Toggle Case/`](02.%20Easy/59.%20Toggle%20Case/) |
| 11 | [Convert Sentence to Camel Case](https://www.geeksforgeeks.org/problems/convert-sentence-to-camel-case/1) | — | — | — | Medium | — | Strings | [`03. Medium/43. Convert Sentence to Camel Case/`](03.%20Medium/43.%20Convert%20Sentence%20to%20Camel%20Case/) |

### Consecutive Runs & Grouping (11)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Longest Substring with All 1's](https://www.geeksforgeeks.org/problems/longest-substring-containing-1/1) | — | — | — | Basics | Microsoft | Strings | [`01. Basics/34. Longest Substring with All 1's/`](01.%20Basics/34.%20Longest%20Substring%20with%20All%201's/) |
| 2 | [Remove Repeated Digits](https://www.geeksforgeeks.org/problems/remove-repeated-digits-in-a-given-number4014/1) | — | — | — | Basics | — | Strings, Mathematics | [`01. Basics/36. Remove Repeated Digits/`](01.%20Basics/36.%20Remove%20Repeated%20Digits/) |
| 3 | [Check for 0 Between 1's in Binary String](https://www.geeksforgeeks.org/problems/check-binary-string0402/1) | — | — | — | Basics | — | Strings, Binary Representation | [`01. Basics/62. Check for 0 Between 1's in Binary String/`](01.%20Basics/62.%20Check%20for%200%20Between%201's%20in%20Binary%20String/) |
| 4 | [All 0s Together in a Binary String](https://www.geeksforgeeks.org/problems/the-muskteers3519/1) | — | — | — | Basics | — | Strings | [`01. Basics/63. All 0s Together in a Binary String/`](01.%20Basics/63.%20All%200s%20Together%20in%20a%20Binary%20String/) |
| 5 | [Replace Consecutive Two Same with One](https://www.geeksforgeeks.org/problems/consecutive-elements2306/1) | — | — | — | Easy | — | Strings | [`02. Easy/07. Replace Consecutive Two Same with One/`](02.%20Easy/07.%20Replace%20Consecutive%20Two%20Same%20with%20One/) |
| 6 | [Run Length Encoding](https://www.geeksforgeeks.org/problems/run-length-encoding/1) | — | — | — | Easy | VMWare, Zoho, Amazon, Microsoft, FactSet, Goldman Sachs, CouponDunia | Strings | [`02. Easy/10. Run Length Encoding/`](02.%20Easy/10.%20Run%20Length%20Encoding/) |
| 7 | [The Modified String](https://www.geeksforgeeks.org/problems/the-modified-string-1587115621/1) | — | — | — | Easy | — | Strings | [`02. Easy/22. The Modified String/`](02.%20Easy/22.%20The%20Modified%20String/) |
| 8 | [1[0]1 Pattern Count](https://www.geeksforgeeks.org/problems/101-pattern-count1341/1) | — | — | — | Easy | Samsung | Strings, Pattern Searching | [`02. Easy/36. 1[0]1 Pattern Count/`](02.%20Easy/36.%201[0]1%20Pattern%20Count/) |
| 9 | [Same Characters and Same Order](https://www.geeksforgeeks.org/problems/c-corresponding-position-in-the-two-strings-that-hold-exactly-the-same-characters5013/1) | — | — | — | Easy | — | Strings | [`02. Easy/44. Same Characters and Same Order/`](02.%20Easy/44.%20Same%20Characters%20and%20Same%20Order/) |
| 10 | [Non-Repetitive String](https://www.geeksforgeeks.org/problems/the-non-repetitive-string5955/1) | — | — | — | Easy | — | Strings | [`02. Easy/69. Non-Repetitive String/`](02.%20Easy/69.%20Non-Repetitive%20String/) |
| 11 | [Look and Say Pattern](https://www.geeksforgeeks.org/problems/decode-the-pattern1138/1) | — | — | — | Medium | Zoho, Amazon, Microsoft, Facebook | Strings, pattern-printing | [`03. Medium/16. Look and Say Pattern/`](03.%20Medium/16.%20Look%20and%20Say%20Pattern/) |

### Counting & Combinatorics on Strings (11)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Binary Substrings with Corners as 1](https://www.geeksforgeeks.org/problems/binary-string-1587115620/1) | — | — | — | Basics | Flipkart, Amazon | Strings | [`01. Basics/06. Binary Substrings with Corners as 1/`](01.%20Basics/06.%20Binary%20Substrings%20with%20Corners%20as%201/) |
| 2 | [Sum of All Digit Subsequences](https://www.geeksforgeeks.org/problems/sum-of-all-sub-sequences-of-a-number3437/1) | — | — | — | Basics | — | Strings, CPP | [`01. Basics/70. Sum of All Digit Subsequences/`](01.%20Basics/70.%20Sum%20of%20All%20Digit%20Subsequences/) |
| 3 | [Count Strings](https://www.geeksforgeeks.org/problems/count-of-strings-that-can-be-formed-using-a-b-and-c-under-given-constraints1135/1) | — | — | — | Easy | Amazon, Google | Strings | [`02. Easy/18. Count Strings/`](02.%20Easy/18.%20Count%20Strings/) |
| 4 | [Count Occurrences in Prefix of a Repeated String](https://www.geeksforgeeks.org/problems/aryas-long-string5840/1) | — | — | — | Easy | — | Strings | [`02. Easy/40. Count Occurrences in Prefix of a Repeated String/`](02.%20Easy/40.%20Count%20Occurrences%20in%20Prefix%20of%20a%20Repeated%20String/) |
| 5 | [Colorful Strings](https://www.geeksforgeeks.org/problems/geek-and-its-colored-strings1355/1) | — | — | — | Easy | Directi | Strings, permutation | [`02. Easy/63. Colorful Strings/`](02.%20Easy/63.%20Colorful%20Strings/) |
| 6 | [Count Even Substrings](https://www.geeksforgeeks.org/problems/count-even-substrings3857/1) | — | — | — | Easy | — | Strings | [`02. Easy/66. Count Even Substrings/`](02.%20Easy/66.%20Count%20Even%20Substrings/) |
| 7 | [Ways to Split String with Distinct Partition Starts](https://www.geeksforgeeks.org/problems/ways-to-split-string-such-that-each-partition-starts-with-distinct-letter5723/1) | — | — | — | Easy | — | Strings | [`02. Easy/83. Ways to Split String with Distinct Partition Starts/`](02.%20Easy/83.%20Ways%20to%20Split%20String%20with%20Distinct%20Partition%20Starts/) |
| 8 | [Even Decimal Binary String](https://www.geeksforgeeks.org/problems/even-decimal-binary-string4748/1) | — | — | — | Easy | — | Strings, Binary Representation | [`02. Easy/90. Even Decimal Binary String/`](02.%20Easy/90.%20Even%20Decimal%20Binary%20String/) |
| 9 | [Rank The Permutations](https://www.geeksforgeeks.org/problems/rank-the-permutations2229/1) | — | — | — | Medium | Amazon, Microsoft, FactSet | Number Theory, Strings | [`03. Medium/14. Rank The Permutations/`](03.%20Medium/14.%20Rank%20The%20Permutations/) |
| 10 | [Count Unique Vowel Strings](https://www.geeksforgeeks.org/problems/count-unique-vowel-strings/1) | — | — | — | Medium | — | Strings, Combinatorial, Mathematics | [`03. Medium/33. Count Unique Vowel Strings/`](03.%20Medium/33.%20Count%20Unique%20Vowel%20Strings/) |
| 11 | [Number of Positive Integral Solutions](https://www.geeksforgeeks.org/problems/number-of-positive-integral-solutions2115/1) | — | — | — | Medium | — | Strings, Mathematics, permutation, Combinatorial | [`03. Medium/42. Number of Positive Integral Solutions/`](03.%20Medium/42.%20Number%20of%20Positive%20Integral%20Solutions/) |

### Word Tokenization & Sentence Processing (10)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Longest Word](https://www.geeksforgeeks.org/problems/display-longest-name0853/1) | — | — | — | Basics | — | Arrays, Strings | [`01. Basics/09. Longest Word/`](01.%20Basics/09.%20Longest%20Word/) |
| 2 | [Capitalize First Letter of Words](https://www.geeksforgeeks.org/problems/upper-case-conversion5419/1) | — | — | — | Basics | Nagarro | Strings | [`01. Basics/14. Capitalize First Letter of Words/`](01.%20Basics/14.%20Capitalize%20First%20Letter%20of%20Words/) |
| 3 | [First Letter of Every Word](https://www.geeksforgeeks.org/problems/print-first-letter-of-every-word-in-the-string3632/1) | — | — | — | Basics | Amazon | Strings | [`01. Basics/15. First Letter of Every Word/`](01.%20Basics/15.%20First%20Letter%20of%20Every%20Word/) |
| 4 | [Length of the Last Word](https://www.geeksforgeeks.org/problems/length-of-last-word5721/1) | — | — | — | Basics | — | Strings | [`01. Basics/40. Length of the Last Word/`](01.%20Basics/40.%20Length%20of%20the%20Last%20Word/) |
| 5 | [Word Lengths](https://www.geeksforgeeks.org/problems/count-the-characters-in-each-word-in-a-given-sentence3451/1) | — | — | — | Basics | — | Strings | [`01. Basics/60. Word Lengths/`](01.%20Basics/60.%20Word%20Lengths/) |
| 6 | [Reverse Words](https://www.geeksforgeeks.org/problems/reverse-words-in-a-given-string5459/1) | — | — | — | Easy | Paytm, Accolite, Amazon, Microsoft, Samsung, MakeMyTrip, Goldman Sachs, Adobe, SAP Labs, Cisco, NPCI | Strings | [`02. Easy/01. Reverse Words/`](02.%20Easy/01.%20Reverse%20Words/) |
| 7 | [Count Words in a String](https://www.geeksforgeeks.org/problems/count-number-of-words1500/1) | — | — | — | Easy | Amazon | Strings | [`02. Easy/15. Count Words in a String/`](02.%20Easy/15.%20Count%20Words%20in%20a%20String/) |
| 8 | [Difficulty of a Sentence](https://www.geeksforgeeks.org/problems/difficulty-of-sentence5856/1) | — | — | — | Easy | Microsoft | Strings | [`02. Easy/48. Difficulty of a Sentence/`](02.%20Easy/48.%20Difficulty%20of%20a%20Sentence/) |
| 9 | [Smallest and Largest Words](https://www.geeksforgeeks.org/problems/smallest-and-largest/1) | — | — | — | Easy | — | Strings | [`02. Easy/54. Smallest and Largest Words/`](02.%20Easy/54.%20Smallest%20and%20Largest%20Words/) |
| 10 | [Count Sentences and Words](https://www.geeksforgeeks.org/problems/counting-number-of-sentences-and-words-in-text3226/1) | — | — | — | Easy | — | Strings | [`02. Easy/80. Count Sentences and Words/`](02.%20Easy/80.%20Count%20Sentences%20and%20Words/) |

### Lexicographic Comparison & Sorting (9)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Just One Mismatch](https://www.geeksforgeeks.org/problems/just-one-mismatch1714/1) | — | — | — | Basics | — | Strings | [`01. Basics/65. Just One Mismatch/`](01.%20Basics/65.%20Just%20One%20Mismatch/) |
| 2 | [Longest Common Prefix of Strings](https://www.geeksforgeeks.org/problems/longest-common-prefix-in-an-array5129/1) | — | — | — | Easy | VMWare, Microsoft, Google | Arrays, Strings | [`02. Easy/02. Longest Common Prefix of Strings/`](02.%20Easy/02.%20Longest%20Common%20Prefix%20of%20Strings/) |
| 3 | [Meta Strings](https://www.geeksforgeeks.org/problems/meta-strings5713/1) | — | — | — | Easy | Google | Strings | [`02. Easy/38. Meta Strings/`](02.%20Easy/38.%20Meta%20Strings/) |
| 4 | [Special String Comparison](https://www.geeksforgeeks.org/problems/string-comparison5858/1) | — | — | — | Easy | Microsoft | Strings | [`02. Easy/43. Special String Comparison/`](02.%20Easy/43.%20Special%20String%20Comparison/) |
| 5 | [Lexicographically Smallest and Largest](https://www.geeksforgeeks.org/problems/ordering-of-strings5527/1) | — | — | — | Easy | — | Strings | [`02. Easy/58. Lexicographically Smallest and Largest/`](02.%20Easy/58.%20Lexicographically%20Smallest%20and%20Largest/) |
| 6 | [Check if two strings are same or not](https://www.geeksforgeeks.org/problems/check-if-two-strings-are-same-or-not--155406/1) | — | — | — | Easy | — | Strings | [`02. Easy/61. Check if two strings are same or not/`](02.%20Easy/61.%20Check%20if%20two%20strings%20are%20same%20or%20not/) |
| 7 | [String Comparison](https://www.geeksforgeeks.org/problems/string-comparison--141631/1) | — | — | — | Easy | — | Strings | [`02. Easy/75. String Comparison/`](02.%20Easy/75.%20String%20Comparison/) |
| 8 | [Lexicographical maximum substring of String](https://www.geeksforgeeks.org/problems/lexicographical-maximum-substring/1) | — | — | — | Easy | — | Strings | [`02. Easy/93. Lexicographical maximum substring of String/`](02.%20Easy/93.%20Lexicographical%20maximum%20substring%20of%20String/) |
| 9 | [Lexicographically Smallest Rotation](https://www.geeksforgeeks.org/problems/lexicographically-smallest-string--151951/1) | — | — | — | Hard | — | Strings | [`04. Hard/09. Lexicographically Smallest Rotation/`](04.%20Hard/09.%20Lexicographically%20Smallest%20Rotation/) |

### Recursion, Backtracking & Generation (7)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Generate Binary Strings](https://www.geeksforgeeks.org/problems/generate-binary-string3642/1) | — | — | — | Easy | Google | Strings | [`02. Easy/45. Generate Binary Strings/`](02.%20Easy/45.%20Generate%20Binary%20Strings/) |
| 2 | [Split Into 4 Distinct Substrings](https://www.geeksforgeeks.org/problems/split-the-string2424/1) | — | — | — | Easy | — | Strings | [`02. Easy/70. Split Into 4 Distinct Substrings/`](02.%20Easy/70.%20Split%20Into%204%20Distinct%20Substrings/) |
| 3 | [Check Sum String](https://www.geeksforgeeks.org/problems/additive-sequence/1) | — | — | — | Medium | Nutanix | Strings, Recursion | [`03. Medium/10. Check Sum String/`](03.%20Medium/10.%20Check%20Sum%20String/) |
| 4 | [Binary Numbers with More 1s in All Prefixes](https://www.geeksforgeeks.org/problems/print-n-bit-binary-numbers-having-more-1s-than-0s0252/1) | — | — | — | Medium | — | Strings, Recursion | [`03. Medium/15. Binary Numbers with More 1s in All Prefixes/`](03.%20Medium/15.%20Binary%20Numbers%20with%20More%201s%20in%20All%20Prefixes/) |
| 5 | [Numbers with Adjacent Digit Diff as 1](https://www.geeksforgeeks.org/problems/numbers-with-one-absolute-difference2416/1) | — | — | — | Medium | Jabong, Amazon | Strings, Numbers | [`03. Medium/31. Numbers with Adjacent Digit Diff as 1/`](03.%20Medium/31.%20Numbers%20with%20Adjacent%20Digit%20Diff%20as%201/) |
| 6 | [Palindromic Permutations](https://www.geeksforgeeks.org/problems/pallindrome-patterns0809/1) | — | — | — | Medium | — | Strings, palindrome | [`03. Medium/49. Palindromic Permutations/`](03.%20Medium/49.%20Palindromic%20Permutations/) |
| 7 | [All String Permutations in Sorted Order](https://www.geeksforgeeks.org/problems/permutations-of-a-given-string-1587115620/1) | — | — | — | Hard | Accolite, Amazon, OYO Rooms, Samsung, Citrix, MAQ Software, Cisco | Strings, Recursion | [`04. Hard/05. All String Permutations in Sorted Order/`](04.%20Hard/05.%20All%20String%20Permutations%20in%20Sorted%20Order/) |

### Prefix Balance & Running Counts (6)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Equal Point in Brackets](https://www.geeksforgeeks.org/problems/find-equal-point-in-string-of-brackets2542/1) | — | — | — | Easy | Amazon | Arrays, Strings | [`02. Easy/20. Equal Point in Brackets/`](02.%20Easy/20.%20Equal%20Point%20in%20Brackets/) |
| 2 | [Balanced Splits of a Binary  String](https://www.geeksforgeeks.org/problems/split-the-binary-string-into-substrings-with-equal-number-of-0s-and-1s/1) | — | — | — | Easy | — | Strings | [`02. Easy/25. Balanced Splits of a Binary String/`](02.%20Easy/25.%20Balanced%20Splits%20of%20a%20Binary%20String/) |
| 3 | [Count Substrings with Same Lower and Upper](https://www.geeksforgeeks.org/problems/count-the-substrings--141634/1) | — | — | — | Easy | — | Strings | [`02. Easy/32. Count Substrings with Same Lower and Upper/`](02.%20Easy/32.%20Count%20Substrings%20with%20Same%20Lower%20and%20Upper/) |
| 4 | [Longest Balanced Substring](https://www.geeksforgeeks.org/problems/longest-even-length-substring--113837/1) | — | — | — | Easy | — | Strings, constructive algo | [`02. Easy/94. Longest Balanced Substring/`](02.%20Easy/94.%20Longest%20Balanced%20Substring/) |
| 5 | [Maximum ASCII Sum Substring](https://www.geeksforgeeks.org/problems/save-your-life4601/1) | — | — | — | Medium | — | Kadane, Strings, Arrays | [`03. Medium/26. Maximum ASCII Sum Substring/`](03.%20Medium/26.%20Maximum%20ASCII%20Sum%20Substring/) |
| 6 | [Roll Characters of String](https://www.geeksforgeeks.org/problems/roll-the-characters-of-a-string2127/1) | — | — | — | Medium | Airtel | Arrays, Strings | [`03. Medium/37. Roll Characters of String/`](03.%20Medium/37.%20Roll%20Characters%20of%20String/) |

### Stack-Based Reduction (5)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Remove b and ac from a given string](https://www.geeksforgeeks.org/problems/remove-b-and-ac-from-a-given-string4336/1) | — | — | — | Easy | Amazon, Google | Strings | [`02. Easy/30. Remove b and ac from a given string/`](02.%20Easy/30.%20Remove%20b%20and%20ac%20from%20a%20given%20string/) |
| 2 | [Repeated Removal of 3 Consecutive Duplicates](https://www.geeksforgeeks.org/problems/three-consecutive-duplicates2434/1) | — | — | — | Easy | — | Strings | [`02. Easy/72. Repeated Removal of 3 Consecutive Duplicates/`](02.%20Easy/72.%20Repeated%20Removal%20of%203%20Consecutive%20Duplicates/) |
| 3 | [Max Length Removal with 100](https://www.geeksforgeeks.org/problems/max-length-removal0452/1) | — | — | — | Easy | — | Arrays, Strings | [`02. Easy/79. Max Length Removal with 100/`](02.%20Easy/79.%20Max%20Length%20Removal%20with%20100/) |
| 4 | [Recursively Remove All Adjacent Duplicates](https://www.geeksforgeeks.org/problems/recursively-remove-all-adjacent-duplicates0744/1) | — | — | — | Medium | Paytm, Samsung | Strings, Recursion | [`03. Medium/05. Recursively Remove All Adjacent Duplicates/`](03.%20Medium/05.%20Recursively%20Remove%20All%20Adjacent%20Duplicates/) |
| 5 | [Form Number using Pattern](https://www.geeksforgeeks.org/problems/number-following-a-pattern3126/1) | — | — | — | Medium | Amazon, Goldman Sachs, Google | Strings | [`03. Medium/12. Form Number using Pattern/`](03.%20Medium/12.%20Form%20Number%20using%20Pattern/) |

### Implicit Expansion & K-th Character (5)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Kth Character in an Encoded String](https://www.geeksforgeeks.org/problems/decode-it1646/1) | — | — | — | Easy | Amazon, National Instruments | Strings | [`02. Easy/67. Kth Character in an Encoded String/`](02.%20Easy/67.%20Kth%20Character%20in%20an%20Encoded%20String/) |
| 2 | [N-th after Binary String Expansion](https://www.geeksforgeeks.org/problems/find-the-n-th-character5925/1) | — | — | — | Medium | — | Strings | [`03. Medium/11. N-th after Binary String Expansion/`](03.%20Medium/11.%20N-th%20after%20Binary%20String%20Expansion/) |
| 3 | [Kth Character After Binary String Transformations](https://www.geeksforgeeks.org/problems/find-k-th-character-in-string3841/1) | — | — | — | Medium | Amazon | Strings, Bit Magic, implementation, Recursion, Divide and Conquer | [`03. Medium/30. Kth Character After Binary String Transformations/`](03.%20Medium/30.%20Kth%20Character%20After%20Binary%20String%20Transformations/) |
| 4 | [The Infinite String](https://www.geeksforgeeks.org/problems/the-infinite-string1049/1) | — | — | — | Medium | National Instruments | Mathematics, Strings, Recursion | [`03. Medium/54. The Infinite String/`](03.%20Medium/54.%20The%20Infinite%20String/) |
| 5 | [Print kth Character](https://www.geeksforgeeks.org/problems/print-kth-character-in-sorted-concatenated-substrings-of-a-string0302/1) | — | — | — | Hard | — | Strings | [`04. Hard/08. Print kth Character/`](04.%20Hard/08.%20Print%20kth%20Character/) |

### Dynamic Programming on Strings (5)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [String Conversion](https://www.geeksforgeeks.org/problems/convert-the-string1022/1) | — | — | — | Easy | — | Strings | [`02. Easy/73. String Conversion/`](02.%20Easy/73.%20String%20Conversion/) |
| 2 | [Minimum Operations to Print 'A' N Times](https://www.geeksforgeeks.org/problems/special-keyboard-2/1) | — | — | — | Medium | — | Strings | [`03. Medium/46. Minimum Operations to Print 'A' N Times/`](03.%20Medium/46.%20Minimum%20Operations%20to%20Print%20'A'%20N%20Times/) |
| 3 | [Max Chain Length with Matching Endpoints](https://www.geeksforgeeks.org/problems/combine-the-strings3459/1) | — | — | — | Medium | Walmart | Strings | [`03. Medium/47. Max Chain Length with Matching Endpoints/`](03.%20Medium/47.%20Max%20Chain%20Length%20with%20Matching%20Endpoints/) |
| 4 | [Mapped String](https://www.geeksforgeeks.org/problems/mapped-string0501/1) | — | — | — | Medium | — | Strings, Combinatorial | [`03. Medium/56. Mapped String/`](03.%20Medium/56.%20Mapped%20String/) |
| 5 | [RegEx  Matching](https://www.geeksforgeeks.org/problems/-regex-matching1145/1) | — | — | — | Hard | Microsoft, Amazon | Strings | [`04. Hard/06. RegEx Matching/`](04.%20Hard/06.%20RegEx%20Matching/) |

### Binary Strings & Bit Manipulation (4)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Unset Kth Bit](https://www.geeksforgeeks.org/problems/replace-the-bit3212/1) | — | — | — | Basics | Microsoft | Strings, Bit Magic | [`01. Basics/37. Unset Kth Bit/`](01.%20Basics/37.%20Unset%20Kth%20Bit/) |
| 2 | [Rotate Bits](https://www.geeksforgeeks.org/problems/rotate-bits4524/1) | — | — | — | Easy | — | Strings, Bit Magic | [`02. Easy/11. Rotate Bits/`](02.%20Easy/11.%20Rotate%20Bits/) |
| 3 | [Min Number of Flips](https://www.geeksforgeeks.org/problems/min-number-of-flips3210/1) | — | — | — | Easy | Goldman Sachs | Strings, Binary Representation | [`02. Easy/16. Min Number of Flips/`](02.%20Easy/16.%20Min%20Number%20of%20Flips/) |
| 4 | [XOR Cipher](https://www.geeksforgeeks.org/problems/xor-cipher3009/1) | — | — | — | Medium | — | Strings, Bit Magic, Binary Representation | [`03. Medium/53. XOR Cipher/`](03.%20Medium/53.%20XOR%20Cipher/) |
