# Hashing — Hard: Patterns

Hard-level Hashing problems (5) are either full cache designs (LRU, LFU: hash map + doubly linked list) or substring problems that need rolling hashes or palindrome structure (Manacher).

## Pattern 1: String Hashing / Substring Patterns

Substring-level hashing: precompute prefix hashes so any substring hash is O(1), then compare substrings, count distinct ones, or match a pattern (frequency of a substring). Palindrome queries compare forward and reverse hashes. Period problems test candidate prefixes. The hardest variant combines Manacher's palindrome radii with prefix/suffix best sums.

| # | Problem | Link |
|---|---|---|
| 1 | [Maximum Non-Overlapping Odd Palindrome Sum](https://www.geeksforgeeks.org/problems/maximum-non-overlapping-odd-palindrome-sum/1) | [`02. Maximum Non-Overlapping Odd Palindrome Sum/`](02.%20Maximum%20Non-Overlapping%20Odd%20Palindrome%20Sum/) |
| 2 | [Longest Periodic Proper Prefix](https://www.geeksforgeeks.org/problems/longest-periodic-proper-prefix/1) | [`03. Longest Periodic Proper Prefix/`](03.%20Longest%20Periodic%20Proper%20Prefix/) |
| 3 | [Palindrome Substring Queries](https://www.geeksforgeeks.org/problems/palindrome-substring-queries/1) | [`05. Palindrome Substring Queries/`](05.%20Palindrome%20Substring%20Queries/) |

## Pattern 2: Hash Table Design & Collision Resolution

Build the data structure, not only use it. Open addressing places a key at `h(k)` and probes `h(k)+i` (linear) or `h(k)+i^2` (quadratic) on collision. A HashMap design uses buckets with chaining. LRU keeps a map from key to list node plus a recency-ordered doubly linked list. LFU adds frequency buckets. A URL shortener maps a counter to a base-62 code and back.

| # | Problem | Link |
|---|---|---|
| 1 | [LRU Cache](https://www.geeksforgeeks.org/problems/lru-cache/1) | [`01. LRU Cache/`](01.%20LRU%20Cache/) |
| 2 | [LFU Cache](https://www.geeksforgeeks.org/problems/lfu-cache-1665050355/1) | [`04. LFU Cache/`](04.%20LFU%20Cache/) |
