# Two Pointers — Basics: Patterns

Basics-level Two Pointers problems (3) are string warm-ups: compare or swap characters from both ends, or mark where a run starts and ends. They build the habit of moving two indices with a clear rule before the harder pair-search problems.

## Pattern 1: Palindrome / Reverse from Both Ends (Strings)

String problems where the answer depends on mirrored positions. Compare `s[left]` and `s[right]` for palindromes, or swap them to reverse. The twist in each variant is which characters to skip: spaces stay in place, non-letters are ignored, or reversal happens only among selected characters.

| # | Problem | Link |
|---|---|---|
| 1 | [Palindrome String](https://www.geeksforgeeks.org/problems/palindrome-string0817/1) | [`01. Palindrome String/`](01.%20Palindrome%20String/) |
| 2 | [Reverse String with Spaces Intact](https://www.geeksforgeeks.org/problems/reverse-a-string-with-spaces-intact5213/1) | [`03. Reverse String with Spaces Intact/`](03.%20Reverse%20String%20with%20Spaces%20Intact/) |

## Pattern 2: Linear Scan with Start/End Markers

One index scans the input while a second index (or a counter) remembers where the current segment began. When the segment ends, emit it or update the answer. Examples: extract the integers from a string, find the matching closing bracket by counting depth, and find the longest run of non-negative values.

| # | Problem | Link |
|---|---|---|
| 1 | [Extract Integers from String](https://www.geeksforgeeks.org/problems/extract-the-integers4428/1) | [`02. Extract Integers from String/`](02.%20Extract%20Integers%20from%20String/) |
