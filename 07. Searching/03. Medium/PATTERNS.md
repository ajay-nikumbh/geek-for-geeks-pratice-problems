# Searching — Medium: Patterns

Medium-level Searching problems (18) shift from finding a value to searching a space: binary search on the answer (pages, teams, factorial zeros), modified binary search on rotated and unimodal arrays, index-marking tricks for missing values, and sieve-based counting.

## Pattern 1: Linear Scan with Running State

The baseline search: check each element in order. The running state is what changes between problems. Return the first match, the last index of a character, or every index where `a[i] == i`. Keep the largest and second largest, or the longest streak of increasing steps. Double the target whenever it is found and keep going. In a K-step array, adjacent values differ by at most k, so jump `|a[i] - x| / k` steps at once. Equilibrium points compare a running left sum to `total - left - a[i]`.

| # | Problem | Link |
|---|---|---|
| 1 | [Marks from Ranks](https://www.geeksforgeeks.org/problems/find-marks-from-ranks/1) | [`16. Marks from Ranks/`](16.%20Marks%20from%20Ranks/) |
| 2 | [Equilibrium Points](https://www.geeksforgeeks.org/problems/magnet-array-problem3743/1) | [`17. Equilibrium Points/`](17.%20Equilibrium%20Points/) |

## Pattern 2: Lower / Upper Bound Binary Search

Sorted input makes `a[i] >= x` a false-then-true sequence, so binary search finds where it flips. That flip is the lower bound. The upper bound uses `a[i] > x`. Together they give the first and last occurrence and the count `upper - lower`. A sorted binary array is the same problem: the first 1, the transition point, the count of 1s or 0s. Sorted insert position is the lower bound itself. Counting elements of one array that are `<=` each element of another sorts the second array and takes an upper bound per query.

| # | Problem | Link |
|---|---|---|
| 1 | [Counting elements in two arrays](https://www.geeksforgeeks.org/problems/counting-elements-in-two-arrays/1) | [`08. Counting elements in two arrays/`](08.%20Counting%20elements%20in%20two%20arrays/) |

## Pattern 3: Modified Binary Search (Rotated / Bitonic / Peak)

The array is not fully sorted, but one half is always predictable. In a rotated array, compare `a[mid]` with `a[high]`: the minimum (and the rotation count) lies in the unsorted half. To search for a target, find the sorted half and check whether the target falls inside it. For a bitonic array or a peak, compare `a[mid]` with `a[mid + 1]` and move toward the larger side. Ternary search splits a unimodal range into three parts and drops one third per step.

| # | Problem | Link |
|---|---|---|
| 1 | [Peak element](https://www.geeksforgeeks.org/problems/peak-element/1) | [`01. Peak element/`](01.%20Peak%20element/) |
| 2 | [Search in Rotated Sorted Array](https://www.geeksforgeeks.org/problems/search-in-a-rotated-array4618/1) | [`04. Search in Rotated Sorted Array/`](04.%20Search%20in%20Rotated%20Sorted%20Array/) |
| 3 | [Ternary Search](https://www.geeksforgeeks.org/problems/searching-an-element-in-a-sorted-array-ternary-search--141631/1) | [`15. Ternary Search/`](15.%20Ternary%20Search/) |

## Pattern 4: Binary Search on the Answer

When the answer is a number and 'is answer <= v feasible' is monotone in v, binary search on v. Square root finds the largest x with `x * x <= n`. Allocate Minimum Pages checks whether students can be given at most v pages each by a greedy pass. Maximum Teams checks `sum(min(a_i, t)) >= t * k`. The smallest n with at least k trailing zeros in n! counts factors of 5 with Legendre's formula. Number and the Digit Sum counts values where `x - digitsum(x)` reaches the threshold.

| # | Problem | Link |
|---|---|---|
| 1 | [Allocate Minimum Pages](https://www.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1) | [`03. Allocate Minimum Pages/`](03.%20Allocate%20Minimum%20Pages/) |
| 2 | [Smallest number with at least n trailing zeroes in factorial](https://www.geeksforgeeks.org/problems/smallest-factorial-number5929/1) | [`11. Smallest number with at least n trailing zeroes in factorial/`](11.%20Smallest%20number%20with%20at%20least%20n%20trailing%20zeroes%20in%20factorial/) |
| 3 | [Maximum Teams of Size K](https://www.geeksforgeeks.org/problems/maximum-team-of-k-player/1) | [`18. Maximum Teams of Size K/`](18.%20Maximum%20Teams%20of%20Size%20K/) |

## Pattern 5: Missing / Repeated via Hashing, Math or Index Marking

Values come from a known range such as `1..n`, so the indices can stand in for the values. The missing number is `n(n+1)/2 - sum` or an XOR of indices and values. Two repeated elements, or the smallest positive missing, mark `a[|x| - 1]` negative or cyclic-sort each value to its home index. Checking that a whole range is present, or counting elements that occur more than a threshold, uses a hash set or a frequency map.

| # | Problem | Link |
|---|---|---|
| 1 | [Smallest Positive Missing](https://www.geeksforgeeks.org/problems/smallest-positive-missing-number-1587115621/1) | [`02. Smallest Positive Missing/`](02.%20Smallest%20Positive%20Missing/) |
| 2 | [Two Repeated Elements](https://www.geeksforgeeks.org/problems/two-repeated-elements-1587115621/1) | [`06. Two Repeated Elements/`](06.%20Two%20Repeated%20Elements/) |

## Pattern 6: Search in Sorted Matrix

If rows and columns are each sorted, start at the top-right. Step left when the value is too large and step down when it is too small. Each step removes a row or a column. Counting zeros in a sorted binary matrix uses the same walk. If the matrix is sorted row after row, treat it as a single array and map index `k` to `(k / m, k % m)`.

| # | Problem | Link |
|---|---|---|
| 1 | [Search in a sorted Matrix](https://www.geeksforgeeks.org/problems/search-in-a-matrix-1587115621/1) | [`05. Search in a sorted Matrix/`](05.%20Search%20in%20a%20sorted%20Matrix/) |

## Pattern 7: Number Theory & Digit Manipulation

Some searching problems are really arithmetic. A number has exactly 9 divisors when it is `p^8` or `p^2 · q^2`, so sieve primes up to `sqrt(n)` and count the forms. Super primes are primes p where `p - 2` is also prime, counted from one sieve. The next greater number with the same digits is the next permutation: find the rightmost ascent, swap with the next larger digit to its right, and reverse the suffix. Repeated removal of the k-th element follows a direct arithmetic pattern.

| # | Problem | Link |
|---|---|---|
| 1 | [Nine Divisors](https://www.geeksforgeeks.org/problems/nine-divisors3751/1) | [`13. Nine Divisors/`](13.%20Nine%20Divisors/) |
| 2 | [Super Primes](https://www.geeksforgeeks.org/problems/super-primes2443/1) | [`14. Super Primes/`](14.%20Super%20Primes/) |

## Pattern 8: Binary Search on an Index Invariant

A single anomaly shifts the positions of everything after it. Before a single element among doubles, pairs start at even indices, and after it they start at odd ones. Before the extra element in the longer array, `a[i] == b[i]`, and after it they differ. In a sorted run of consecutive numbers with one repeat, `a[i] - i` changes at the repeat. Binary search for the first index where the invariant breaks.

| # | Problem | Link |
|---|---|---|
| 1 | [Single Among Doubles in a Sorted](https://www.geeksforgeeks.org/problems/find-the-element-that-appears-once-in-sorted-array0624/1) | [`07. Single Among Doubles in a Sorted/`](07.%20Single%20Among%20Doubles%20in%20a%20Sorted/) |
| 2 | [Count Only Repeated](https://www.geeksforgeeks.org/problems/count-only-repeated2047/1) | [`12. Count Only Repeated/`](12.%20Count%20Only%20Repeated/) |

## Pattern 9: Two / Three Pointers on Sorted Arrays

Sorted order lets pointers replace nested loops. Common elements in three sorted arrays advance the pointer at the smallest value until all three match. The closest pair across two arrays starts at the start of one and the end of the other. Pair sum closest to 0 sorts and moves the end pointers inward, tracking the smallest absolute sum.

| # | Problem | Link |
|---|---|---|
| 1 | [Pair Sum Closest to 0](https://www.geeksforgeeks.org/problems/two-numbers-with-sum-closest-to-zero1737/1) | [`10. Pair Sum Closest to 0/`](10.%20Pair%20Sum%20Closest%20to%200/) |

## Pattern 10: String Repetition + Pattern Match

The pattern can only fit inside `ceil(m / n)` or `ceil(m / n) + 1` copies of the base string. Build the shorter repetition and search for the pattern. If it is missing, add one copy and search again. If it is still missing, return -1.

| # | Problem | Link |
|---|---|---|
| 1 | [Minimum repeat to make substring](https://www.geeksforgeeks.org/problems/minimum-times-a-has-to-be-repeated-such-that-b-is-a-substring-of-it--170645/1) | [`09. Minimum repeat to make substring/`](09.%20Minimum%20repeat%20to%20make%20substring/) |
