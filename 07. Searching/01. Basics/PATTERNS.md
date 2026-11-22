# Searching — Basics: Patterns

Basics-level Searching problems (10) contrast linear scans with the first binary search. Most walk the input once with a small running state, and a few use sortedness to find a boundary in O(log n).

## Pattern 1: Linear Scan with Running State

The baseline search: check each element in order. The running state is what changes between problems. Return the first match, the last index of a character, or every index where `a[i] == i`. Keep the largest and second largest, or the longest streak of increasing steps. Double the target whenever it is found and keep going. In a K-step array, adjacent values differ by at most k, so jump `|a[i] - x| / k` steps at once. Equilibrium points compare a running left sum to `total - left - a[i]`.

| # | Problem | Link |
|---|---|---|
| 1 | [Array Search](https://www.geeksforgeeks.org/problems/search-an-element-in-an-array-1587115621/1) | [`01. Array Search/`](01.%20Array%20Search/) |
| 2 | [Value Equal to Position](https://www.geeksforgeeks.org/problems/value-equal-to-index-value1330/1) | [`03. Value Equal to Position/`](03.%20Value%20Equal%20to%20Position/) |
| 3 | [Last index of One](https://www.geeksforgeeks.org/problems/last-index-of-15847/1) | [`04. Last index of One/`](04.%20Last%20index%20of%20One/) |
| 4 | [Remove Consonants](https://www.geeksforgeeks.org/problems/c-program-to-remove-consonants-from-a-string1945/1) | [`07. Remove Consonants/`](07.%20Remove%20Consonants/) |
| 5 | [Doubling the Value](https://www.geeksforgeeks.org/problems/doubling-the-value4859/1) | [`09. Doubling the Value/`](09.%20Doubling%20the%20Value/) |

## Pattern 2: Lower / Upper Bound Binary Search

Sorted input makes `a[i] >= x` a false-then-true sequence, so binary search finds where it flips. That flip is the lower bound. The upper bound uses `a[i] > x`. Together they give the first and last occurrence and the count `upper - lower`. A sorted binary array is the same problem: the first 1, the transition point, the count of 1s or 0s. Sorted insert position is the lower bound itself. Counting elements of one array that are `<=` each element of another sorts the second array and takes an upper bound per query.

| # | Problem | Link |
|---|---|---|
| 1 | [Binary Search](https://www.geeksforgeeks.org/problems/who-will-win-1587115621/1) | [`02. Binary Search/`](02.%20Binary%20Search/) |
| 2 | [First 1 in a Sorted Binary Array](https://www.geeksforgeeks.org/problems/index-of-first-1-in-a-sorted-array-of-0s-and-1s4048/1) | [`06. First 1 in a Sorted Binary Array/`](06.%20First%201%20in%20a%20Sorted%20Binary%20Array/) |

## Pattern 3: Missing / Repeated via Hashing, Math or Index Marking

Values come from a known range such as `1..n`, so the indices can stand in for the values. The missing number is `n(n+1)/2 - sum` or an XOR of indices and values. Two repeated elements, or the smallest positive missing, mark `a[|x| - 1]` negative or cyclic-sort each value to its home index. Checking that a whole range is present, or counting elements that occur more than a threshold, uses a hash set or a frequency map.

| # | Problem | Link |
|---|---|---|
| 1 | [Elements in the Range](https://www.geeksforgeeks.org/problems/elements-in-the-range2834/1) | [`05. Elements in the Range/`](05.%20Elements%20in%20the%20Range/) |

## Pattern 4: Search in Sorted Matrix

If rows and columns are each sorted, start at the top-right. Step left when the value is too large and step down when it is too small. Each step removes a row or a column. Counting zeros in a sorted binary matrix uses the same walk. If the matrix is sorted row after row, treat it as a single array and map index `k` to `(k / m, k % m)`.

| # | Problem | Link |
|---|---|---|
| 1 | [Count Zeros in a Sorted Matrix](https://www.geeksforgeeks.org/problems/count-zeros-in-a-sorted-matrix/1) | [`08. Count Zeros in a Sorted Matrix/`](08.%20Count%20Zeros%20in%20a%20Sorted%20Matrix/) |

## Pattern 5: Number Theory & Digit Manipulation

Some searching problems are really arithmetic. A number has exactly 9 divisors when it is `p^8` or `p^2 · q^2`, so sieve primes up to `sqrt(n)` and count the forms. Super primes are primes p where `p - 2` is also prime, counted from one sieve. The next greater number with the same digits is the next permutation: find the rightmost ascent, swap with the next larger digit to its right, and reverse the suffix. Repeated removal of the k-th element follows a direct arithmetic pattern.

| # | Problem | Link |
|---|---|---|
| 1 | [Repeated Removal of Kth](https://www.geeksforgeeks.org/problems/ishaans-internship4400/1) | [`10. Repeated Removal of Kth/`](10.%20Repeated%20Removal%20of%20Kth/) |
