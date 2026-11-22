# Searching — Easy: Patterns

These are the recurring patterns across the 24 Easy-level Searching problems. Lower/upper-bound binary search dominates, followed by linear scans, rotated and bitonic searches, and the first binary-search-on-the-answer problems.

## Pattern 1: Linear Scan with Running State

The baseline search: check each element in order. The running state is what changes between problems. Return the first match, the last index of a character, or every index where `a[i] == i`. Keep the largest and second largest, or the longest streak of increasing steps. Double the target whenever it is found and keep going. In a K-step array, adjacent values differ by at most k, so jump `|a[i] - x| / k` steps at once. Equilibrium points compare a running left sum to `total - left - a[i]`.

| # | Problem | Link |
|---|---|---|
| 1 | [Second Largest](https://www.geeksforgeeks.org/problems/second-largest3735/1) | [`02. Second Largest/`](02.%20Second%20Largest/) |
| 2 | [Roof Top](https://www.geeksforgeeks.org/problems/roof-top-1587115621/1) | [`16. Roof Top/`](16.%20Roof%20Top/) |
| 3 | [Search in a K-Step Array](https://www.geeksforgeeks.org/problems/searching-in-an-array-where-adjacent-differ-by-at-most-k0456/1) | [`19. Search in a K-Step Array/`](19.%20Search%20in%20a%20K-Step%20Array/) |
| 4 | [Operating an array](https://www.geeksforgeeks.org/problems/operating-an-array/1) | [`20. Operating an array/`](20.%20Operating%20an%20array/) |

## Pattern 2: Lower / Upper Bound Binary Search

Sorted input makes `a[i] >= x` a false-then-true sequence, so binary search finds where it flips. That flip is the lower bound. The upper bound uses `a[i] > x`. Together they give the first and last occurrence and the count `upper - lower`. A sorted binary array is the same problem: the first 1, the transition point, the count of 1s or 0s. Sorted insert position is the lower bound itself. Counting elements of one array that are `<=` each element of another sorts the second array and takes an upper bound per query.

| # | Problem | Link |
|---|---|---|
| 1 | [First Occurrence in Sorted](https://www.geeksforgeeks.org/problems/binary-search-1587115620/1) | [`03. First Occurrence in Sorted/`](03.%20First%20Occurrence%20in%20Sorted/) |
| 2 | [Number of Occurrence](https://www.geeksforgeeks.org/problems/number-of-occurrence2259/1) | [`05. Number of Occurrence/`](05.%20Number%20of%20Occurrence/) |
| 3 | [Transition Point in Sorted Binary](https://www.geeksforgeeks.org/problems/find-transition-point-1587115620/1) | [`08. Transition Point in Sorted Binary/`](08.%20Transition%20Point%20in%20Sorted%20Binary/) |
| 4 | [Count Zeros in Sorted](https://www.geeksforgeeks.org/problems/count-the-zeros2550/1) | [`14. Count Zeros in Sorted/`](14.%20Count%20Zeros%20in%20Sorted/) |
| 5 | [Sorted Insert Position](https://www.geeksforgeeks.org/problems/search-insert-position-of-k-in-a-sorted-array/1) | [`15. Sorted Insert Position/`](15.%20Sorted%20Insert%20Position/) |
| 6 | [Count 1's in binary array](https://www.geeksforgeeks.org/problems/count-1s-in-binary-array-1587115620/1) | [`18. Count 1's in binary array/`](18.%20Count%201's%20in%20binary%20array/) |
| 7 | [Zeros Count in Sorted Binary](https://www.geeksforgeeks.org/problems/count-the-zeros2550--141153/1) | [`24. Zeros Count in Sorted Binary/`](24.%20Zeros%20Count%20in%20Sorted%20Binary/) |

## Pattern 3: Modified Binary Search (Rotated / Bitonic / Peak)

The array is not fully sorted, but one half is always predictable. In a rotated array, compare `a[mid]` with `a[high]`: the minimum (and the rotation count) lies in the unsorted half. To search for a target, find the sorted half and check whether the target falls inside it. For a bitonic array or a peak, compare `a[mid]` with `a[mid + 1]` and move toward the larger side. Ternary search splits a unimodal range into three parts and drops one third per step.

| # | Problem | Link |
|---|---|---|
| 1 | [Find Kth Rotation](https://www.geeksforgeeks.org/problems/rotation4723/1) | [`07. Find Kth Rotation/`](07.%20Find%20Kth%20Rotation/) |
| 2 | [Bitonic Point](https://www.geeksforgeeks.org/problems/maximum-value-in-a-bitonic-array3001/1) | [`09. Bitonic Point/`](09.%20Bitonic%20Point/) |
| 3 | [Sorted and Rotated Minimum](https://www.geeksforgeeks.org/problems/minimum-element-in-a-sorted-and-rotated-array3611/1) | [`11. Sorted and Rotated Minimum/`](11.%20Sorted%20and%20Rotated%20Minimum/) |

## Pattern 4: Binary Search on the Answer

When the answer is a number and 'is answer <= v feasible' is monotone in v, binary search on v. Square root finds the largest x with `x * x <= n`. Allocate Minimum Pages checks whether students can be given at most v pages each by a greedy pass. Maximum Teams checks `sum(min(a_i, t)) >= t * k`. The smallest n with at least k trailing zeros in n! counts factors of 5 with Legendre's formula. Number and the Digit Sum counts values where `x - digitsum(x)` reaches the threshold.

| # | Problem | Link |
|---|---|---|
| 1 | [Square Root](https://www.geeksforgeeks.org/problems/square-root/1) | [`06. Square Root/`](06.%20Square%20Root/) |
| 2 | [Number and the Digit Sum](https://www.geeksforgeeks.org/problems/number-and-the-digit-sum4021/1) | [`23. Number and the Digit Sum/`](23.%20Number%20and%20the%20Digit%20Sum/) |

## Pattern 5: Missing / Repeated via Hashing, Math or Index Marking

Values come from a known range such as `1..n`, so the indices can stand in for the values. The missing number is `n(n+1)/2 - sum` or an XOR of indices and values. Two repeated elements, or the smallest positive missing, mark `a[|x| - 1]` negative or cyclic-sort each value to its home index. Checking that a whole range is present, or counting elements that occur more than a threshold, uses a hash set or a frequency map.

| # | Problem | Link |
|---|---|---|
| 1 | [Missing in Array](https://www.geeksforgeeks.org/problems/missing-number-in-array1416/1) | [`01. Missing in Array/`](01.%20Missing%20in%20Array/) |
| 2 | [Count Frequent Elements](https://www.geeksforgeeks.org/problems/count-element-occurences/1) | [`13. Count Frequent Elements/`](13.%20Count%20Frequent%20Elements/) |

## Pattern 6: Search in Sorted Matrix

If rows and columns are each sorted, start at the top-right. Step left when the value is too large and step down when it is too small. Each step removes a row or a column. Counting zeros in a sorted binary matrix uses the same walk. If the matrix is sorted row after row, treat it as a single array and map index `k` to `(k / m, k % m)`.

| # | Problem | Link |
|---|---|---|
| 1 | [Search in a Row-Column Sorted](https://www.geeksforgeeks.org/problems/search-in-a-matrix17201720/1) | [`10. Search in a Row-Column Sorted/`](10.%20Search%20in%20a%20Row-Column%20Sorted/) |
| 2 | [Search in a  Matrix](https://www.geeksforgeeks.org/problems/search-in-a-matrix--021840/1) | [`22. Search in a Matrix/`](22.%20Search%20in%20a%20Matrix/) |

## Pattern 7: Number Theory & Digit Manipulation

Some searching problems are really arithmetic. A number has exactly 9 divisors when it is `p^8` or `p^2 · q^2`, so sieve primes up to `sqrt(n)` and count the forms. Super primes are primes p where `p - 2` is also prime, counted from one sieve. The next greater number with the same digits is the next permutation: find the rightmost ascent, swap with the next larger digit to its right, and reverse the suffix. Repeated removal of the k-th element follows a direct arithmetic pattern.

| # | Problem | Link |
|---|---|---|
| 1 | [Next greater number set digits](https://www.geeksforgeeks.org/problems/next-greater-number-set-digits3503/1) | [`21. Next greater number set digits/`](21.%20Next%20greater%20number%20set%20digits/) |

## Pattern 8: Binary Search on an Index Invariant

A single anomaly shifts the positions of everything after it. Before a single element among doubles, pairs start at even indices, and after it they start at odd ones. Before the extra element in the longer array, `a[i] == b[i]`, and after it they differ. In a sorted run of consecutive numbers with one repeat, `a[i] - i` changes at the repeat. Binary search for the first index where the invariant breaks.

| # | Problem | Link |
|---|---|---|
| 1 | [Extra in One of the Two Arrays](https://www.geeksforgeeks.org/problems/index-of-an-extra-element/1) | [`12. Extra in One of the Two Arrays/`](12.%20Extra%20in%20One%20of%20the%20Two%20Arrays/) |

## Pattern 9: Two / Three Pointers on Sorted Arrays

Sorted order lets pointers replace nested loops. Common elements in three sorted arrays advance the pointer at the smallest value until all three match. The closest pair across two arrays starts at the start of one and the end of the other. Pair sum closest to 0 sorts and moves the end pointers inward, tracking the smallest absolute sum.

| # | Problem | Link |
|---|---|---|
| 1 | [Common in 3 Sorted Arrays](https://www.geeksforgeeks.org/problems/common-elements1132/1) | [`04. Common in 3 Sorted Arrays/`](04.%20Common%20in%203%20Sorted%20Arrays/) |
| 2 | [Closest Sum Pair Across Two Arrays](https://www.geeksforgeeks.org/problems/find-the-closest-pair-from-two-arrays4215/1) | [`17. Closest Sum Pair Across Two Arrays/`](17.%20Closest%20Sum%20Pair%20Across%20Two%20Arrays/) |
