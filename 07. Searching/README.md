# 7. Searching

[← Back to root](../README.md) · [GfG topic problems](https://www.geeksforgeeks.org/explore?category%5B%5D=Searching)

## Patterns (merged across all difficulty levels)

Same core technique shows up at every difficulty — this view merges those occurrences into one pattern, with problems ordered Basics → Easy → Medium → Hard. Logic/Time/Space are filled in as each problem's full article is written.

| # | Pattern | Logic | Typical Time | Typical Space | Total | Basics | Easy | Medium | Hard |
|---|---|---|---|---|---|---|---|---|---|
| 1 | [Linear Scan with Running State](#linear-scan-with-running-state-11) | Walk the array once (or jump ahead when a bound allows it), keeping a small running state — target found, best so far, streak, prefix sum. | O(n) | O(1) | 11 | 5 | 4 | 2 | 0 |
| 2 | [Lower / Upper Bound Binary Search](#lower--upper-bound-binary-search-10) | Binary search for the first index where a monotone condition becomes true — first/last occurrence, count = upper - lower, insert position, transition point. | O(log n) | O(1) | 10 | 2 | 7 | 1 | 0 |
| 3 | [Modified Binary Search (Rotated / Bitonic / Peak)](#modified-binary-search-rotated--bitonic--peak-6) | Compare `mid` with an end or its neighbour to decide which half is sorted or which side rises, then discard the other half. | O(log n) | O(1) | 6 | 0 | 3 | 3 | 0 |
| 4 | [Binary Search on the Answer](#binary-search-on-the-answer-5) | Binary search over the answer value, with a monotone feasibility check — `x*x <= n`, pages per student, teams of size k, trailing zeros, `x - digitsum(x) >= s`. | O(log range · check) | O(1) | 5 | 0 | 2 | 3 | 0 |
| 5 | [Missing / Repeated via Hashing, Math or Index Marking](#missing--repeated-via-hashing-math-or-index-marking-5) | Find missing, extra, or repeated values in a known range with a sum/XOR identity, a frequency map, or by marking `a[abs(x) - 1]` negative. | O(n) | O(1) marking / O(n) hash | 5 | 1 | 2 | 2 | 0 |
| 6 | [Search in Sorted Matrix](#search-in-sorted-matrix-4) | Staircase walk from the top-right corner (row-column sorted), or one binary search over the flattened index (fully sorted). | O(n + m) / O(log(n · m)) | O(1) | 4 | 1 | 2 | 1 | 0 |
| 7 | [Number Theory & Digit Manipulation](#number-theory--digit-manipulation-4) | Precompute primes with a sieve, or reason about digits and arithmetic directly — count numbers with exactly 9 divisors, super primes, next permutation of digits. | O(n log log n) sieve / O(digits) | O(n) sieve / O(1) | 4 | 1 | 1 | 2 | 0 |
| 8 | [Binary Search on an Index Invariant](#binary-search-on-an-index-invariant-3) | Binary search on a property that holds before the anomaly and breaks after it — pair parity, `a[i] == b[i]`, `a[i] - i` offset. | O(log n) | O(1) | 3 | 0 | 1 | 2 | 0 |
| 9 | [Two / Three Pointers on Sorted Arrays](#two--three-pointers-on-sorted-arrays-3) | Sort (or use sorted input) and move one pointer per array, or one at each end, toward the target — common elements, closest pair, sum closest to 0. | O(n log n) with sort / O(n + m) | O(1) | 3 | 0 | 2 | 1 | 0 |
| 10 | [String Repetition + Pattern Match](#string-repetition--pattern-match-1) | Repeat the base string until it is at least as long as the pattern, then test one more repetition with substring search (KMP/Z or built-in find). | O(n + m) per check | O(n + m) | 1 | 0 | 0 | 1 | 0 |
| | **Total (10 patterns)** | | | | **52** | **10** | **24** | **18** | **0** |

### Linear Scan with Running State (11)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Array Search](https://www.geeksforgeeks.org/problems/search-an-element-in-an-array-1587115621/1) | — | — | — | Basics | — | Arrays, Searching | [`01. Basics/01. Array Search/`](01.%20Basics/01.%20Array%20Search/) |
| 2 | [Value Equal to Position](https://www.geeksforgeeks.org/problems/value-equal-to-index-value1330/1) | — | — | — | Basics | Flipkart, Amazon, FactSet, Hike | Arrays, Searching | [`01. Basics/03. Value Equal to Position/`](01.%20Basics/03.%20Value%20Equal%20to%20Position/) |
| 3 | [Last index of One](https://www.geeksforgeeks.org/problems/last-index-of-15847/1) | — | — | — | Basics | InMobi | Searching, Strings | [`01. Basics/04. Last index of One/`](01.%20Basics/04.%20Last%20index%20of%20One/) |
| 4 | [Remove Consonants](https://www.geeksforgeeks.org/problems/c-program-to-remove-consonants-from-a-string1945/1) | — | — | — | Basics | — | Searching, Strings | [`01. Basics/07. Remove Consonants/`](01.%20Basics/07.%20Remove%20Consonants/) |
| 5 | [Doubling the Value](https://www.geeksforgeeks.org/problems/doubling-the-value4859/1) | — | — | — | Basics | Flipkart | Searching | [`01. Basics/09. Doubling the Value/`](01.%20Basics/09.%20Doubling%20the%20Value/) |
| 6 | [Second Largest](https://www.geeksforgeeks.org/problems/second-largest3735/1) | — | — | — | Easy | SAP Labs, Rockstand | Arrays, Searching | [`02. Easy/02. Second Largest/`](02.%20Easy/02.%20Second%20Largest/) |
| 7 | [Roof Top](https://www.geeksforgeeks.org/problems/roof-top-1587115621/1) | — | — | — | Easy | — | Arrays, Searching | [`02. Easy/16. Roof Top/`](02.%20Easy/16.%20Roof%20Top/) |
| 8 | [Search in a K-Step Array](https://www.geeksforgeeks.org/problems/searching-in-an-array-where-adjacent-differ-by-at-most-k0456/1) | — | — | — | Easy | — | Arrays, Searching, CPP | [`02. Easy/19. Search in a K-Step Array/`](02.%20Easy/19.%20Search%20in%20a%20K-Step%20Array/) |
| 9 | [Operating an array](https://www.geeksforgeeks.org/problems/operating-an-array/1) | — | — | — | Easy | — | Arrays, Searching | [`02. Easy/20. Operating an array/`](02.%20Easy/20.%20Operating%20an%20array/) |
| 10 | [Marks from Ranks](https://www.geeksforgeeks.org/problems/find-marks-from-ranks/1) | — | — | — | Medium | — | Arrays, Searching | [`03. Medium/16. Marks from Ranks/`](03.%20Medium/16.%20Marks%20from%20Ranks/) |
| 11 | [Equilibrium Points](https://www.geeksforgeeks.org/problems/magnet-array-problem3743/1) | — | — | — | Medium | D-E-Shaw | Arrays, Searching, Mathematics, Binary Search | [`03. Medium/17. Equilibrium Points/`](03.%20Medium/17.%20Equilibrium%20Points/) |

### Lower / Upper Bound Binary Search (10)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Binary Search](https://www.geeksforgeeks.org/problems/who-will-win-1587115621/1) | — | — | — | Basics | Paytm | Searching, Binary Search | [`01. Basics/02. Binary Search/`](01.%20Basics/02.%20Binary%20Search/) |
| 2 | [First 1 in a Sorted Binary Array](https://www.geeksforgeeks.org/problems/index-of-first-1-in-a-sorted-array-of-0s-and-1s4048/1) | — | — | — | Basics | Amazon, MakeMyTrip | Arrays, Binary Search, Searching | [`01. Basics/06. First 1 in a Sorted Binary Array/`](01.%20Basics/06.%20First%201%20in%20a%20Sorted%20Binary%20Array/) |
| 3 | [First Occurrence in Sorted](https://www.geeksforgeeks.org/problems/binary-search-1587115620/1) | — | — | — | Easy | Infosys, Oracle, Wipro, Linkedin, Qualcomm, TCS, Cognizant, Accenture | Arrays, Searching, Divide and Conquer | [`02. Easy/03. First Occurrence in Sorted/`](02.%20Easy/03.%20First%20Occurrence%20in%20Sorted/) |
| 4 | [Number of Occurrence](https://www.geeksforgeeks.org/problems/number-of-occurrence2259/1) | — | — | — | Easy | Zoho, Amazon, MakeMyTrip | Arrays, Searching | [`02. Easy/05. Number of Occurrence/`](02.%20Easy/05.%20Number%20of%20Occurrence/) |
| 5 | [Transition Point in Sorted Binary](https://www.geeksforgeeks.org/problems/find-transition-point-1587115620/1) | — | — | — | Easy | Amazon | Arrays, Searching | [`02. Easy/08. Transition Point in Sorted Binary/`](02.%20Easy/08.%20Transition%20Point%20in%20Sorted%20Binary/) |
| 6 | [Count Zeros in Sorted](https://www.geeksforgeeks.org/problems/count-the-zeros2550/1) | — | — | — | Easy | Amazon, Yahoo | Arrays, Searching | [`02. Easy/14. Count Zeros in Sorted/`](02.%20Easy/14.%20Count%20Zeros%20in%20Sorted/) |
| 7 | [Sorted Insert Position](https://www.geeksforgeeks.org/problems/search-insert-position-of-k-in-a-sorted-array/1) | — | — | — | Easy | Microsoft | Searching | [`02. Easy/15. Sorted Insert Position/`](02.%20Easy/15.%20Sorted%20Insert%20Position/) |
| 8 | [Count 1's in binary array](https://www.geeksforgeeks.org/problems/count-1s-in-binary-array-1587115620/1) | — | — | — | Easy | — | Searching | [`02. Easy/18. Count 1's in binary array/`](02.%20Easy/18.%20Count%201's%20in%20binary%20array/) |
| 9 | [Zeros Count in Sorted Binary](https://www.geeksforgeeks.org/problems/count-the-zeros2550--141153/1) | — | — | — | Easy | Amazon, Yahoo | Arrays, Searching | [`02. Easy/24. Zeros Count in Sorted Binary/`](02.%20Easy/24.%20Zeros%20Count%20in%20Sorted%20Binary/) |
| 10 | [Counting elements in two arrays](https://www.geeksforgeeks.org/problems/counting-elements-in-two-arrays/1) | — | — | — | Medium | Amazon | Arrays, Searching, Binary Search | [`03. Medium/08. Counting elements in two arrays/`](03.%20Medium/08.%20Counting%20elements%20in%20two%20arrays/) |

### Modified Binary Search (Rotated / Bitonic / Peak) (6)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Find Kth Rotation](https://www.geeksforgeeks.org/problems/rotation4723/1) | — | — | — | Easy | Flipkart, Amazon, ABCO | Arrays, Searching | [`02. Easy/07. Find Kth Rotation/`](02.%20Easy/07.%20Find%20Kth%20Rotation/) |
| 2 | [Bitonic Point](https://www.geeksforgeeks.org/problems/maximum-value-in-a-bitonic-array3001/1) | — | — | — | Easy | Flipkart, Amazon, Microsoft | Arrays, Searching, Binary Search | [`02. Easy/09. Bitonic Point/`](02.%20Easy/09.%20Bitonic%20Point/) |
| 3 | [Sorted and Rotated Minimum](https://www.geeksforgeeks.org/problems/minimum-element-in-a-sorted-and-rotated-array3611/1) | — | — | — | Easy | Morgan Stanley, Amazon, Microsoft, Samsung, Snapdeal, Adobe, Times Internet | Searching | [`02. Easy/11. Sorted and Rotated Minimum/`](02.%20Easy/11.%20Sorted%20and%20Rotated%20Minimum/) |
| 4 | [Peak element](https://www.geeksforgeeks.org/problems/peak-element/1) | — | — | — | Medium | Accolite, Amazon, Visa, Adobe, Google | Arrays, Searching, Binary Search | [`03. Medium/01. Peak element/`](03.%20Medium/01.%20Peak%20element/) |
| 5 | [Search in Rotated Sorted Array](https://www.geeksforgeeks.org/problems/search-in-a-rotated-array4618/1) | — | — | — | Medium | Paytm, Flipkart, Amazon, Microsoft, Snapdeal, D-E-Shaw, FactSet, Hike, MakeMyTrip, Intuit, Adobe, Google, BankBazaar, Times Internet, NPCI | Searching, Divide and Conquer | [`03. Medium/04. Search in Rotated Sorted Array/`](03.%20Medium/04.%20Search%20in%20Rotated%20Sorted%20Array/) |
| 6 | [Ternary Search](https://www.geeksforgeeks.org/problems/searching-an-element-in-a-sorted-array-ternary-search--141631/1) | — | — | — | Medium | Paytm, Microsoft | Searching, Divide and Conquer, Design-Pattern | [`03. Medium/15. Ternary Search/`](03.%20Medium/15.%20Ternary%20Search/) |

### Binary Search on the Answer (5)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Square Root](https://www.geeksforgeeks.org/problems/square-root/1) | — | — | — | Easy | VMWare, Flipkart, Accolite, Amazon, Microsoft | Searching, Mathematics, Binary Search | [`02. Easy/06. Square Root/`](02.%20Easy/06.%20Square%20Root/) |
| 2 | [Number and the Digit Sum](https://www.geeksforgeeks.org/problems/number-and-the-digit-sum4021/1) | — | — | — | Easy | — | Searching, Mathematics, Binary Search | [`02. Easy/23. Number and the Digit Sum/`](02.%20Easy/23.%20Number%20and%20the%20Digit%20Sum/) |
| 3 | [Allocate Minimum Pages](https://www.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1) | — | — | — | Medium | Infosys, Amazon, Microsoft, Google, Codenation, Uber, NPCI | Searching, Divide and Conquer | [`03. Medium/03. Allocate Minimum Pages/`](03.%20Medium/03.%20Allocate%20Minimum%20Pages/) |
| 4 | [Smallest number with at least n trailing zeroes in factorial](https://www.geeksforgeeks.org/problems/smallest-factorial-number5929/1) | — | — | — | Medium | NPCI | Searching, Mathematics, factorial, Binary Search | [`03. Medium/11. Smallest number with at least n trailing zeroes in factorial/`](03.%20Medium/11.%20Smallest%20number%20with%20at%20least%20n%20trailing%20zeroes%20in%20factorial/) |
| 5 | [Maximum Teams of Size K](https://www.geeksforgeeks.org/problems/maximum-team-of-k-player/1) | — | — | — | Medium | Google | Arrays, Searching, Mathematics, Binary Search | [`03. Medium/18. Maximum Teams of Size K/`](03.%20Medium/18.%20Maximum%20Teams%20of%20Size%20K/) |

### Missing / Repeated via Hashing, Math or Index Marking (5)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Elements in the Range](https://www.geeksforgeeks.org/problems/elements-in-the-range2834/1) | — | — | — | Basics | Amazon | Arrays, Searching | [`01. Basics/05. Elements in the Range/`](01.%20Basics/05.%20Elements%20in%20the%20Range/) |
| 2 | [Missing in Array](https://www.geeksforgeeks.org/problems/missing-number-in-array1416/1) | — | — | — | Easy | Flipkart, Morgan Stanley, Accolite, Amazon, Microsoft, D-E-Shaw, Ola Cabs, Payu, Visa, Intuit, Adobe, Cisco, Qualcomm, TCS, NPCI | Arrays, Searching, Bit Magic | [`02. Easy/01. Missing in Array/`](02.%20Easy/01.%20Missing%20in%20Array/) |
| 3 | [Count Frequent Elements](https://www.geeksforgeeks.org/problems/count-element-occurences/1) | — | — | — | Easy | Amazon | Arrays, Searching | [`02. Easy/13. Count Frequent Elements/`](02.%20Easy/13.%20Count%20Frequent%20Elements/) |
| 4 | [Smallest Positive Missing](https://www.geeksforgeeks.org/problems/smallest-positive-missing-number-1587115621/1) | — | — | — | Medium | Accolite, Amazon, Samsung, Snapdeal, NPCI | Arrays, Searching | [`03. Medium/02. Smallest Positive Missing/`](03.%20Medium/02.%20Smallest%20Positive%20Missing/) |
| 5 | [Two Repeated Elements](https://www.geeksforgeeks.org/problems/two-repeated-elements-1587115621/1) | — | — | — | Medium | — | Arrays, Searching | [`03. Medium/06. Two Repeated Elements/`](03.%20Medium/06.%20Two%20Repeated%20Elements/) |

### Search in Sorted Matrix (4)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Count Zeros in a Sorted Matrix](https://www.geeksforgeeks.org/problems/count-zeros-in-a-sorted-matrix/1) | — | — | — | Basics | — | Searching, Matrix | [`01. Basics/08. Count Zeros in a Sorted Matrix/`](01.%20Basics/08.%20Count%20Zeros%20in%20a%20Sorted%20Matrix/) |
| 2 | [Search in a Row-Column Sorted](https://www.geeksforgeeks.org/problems/search-in-a-matrix17201720/1) | — | — | — | Easy | Paytm, Accolite, Amazon, Microsoft, Snapdeal, MakeMyTrip, Ola Cabs, Oracle, Visa, Goldman Sachs, Directi, Adobe, SAP Labs, Groupon, InMobi, One97, Polycom, TinyOwl | Searching, Matrix | [`02. Easy/10. Search in a Row-Column Sorted/`](02.%20Easy/10.%20Search%20in%20a%20Row-Column%20Sorted/) |
| 3 | [Search in a  Matrix](https://www.geeksforgeeks.org/problems/search-in-a-matrix--021840/1) | — | — | — | Easy | — | Searching, Matrix | [`02. Easy/22. Search in a Matrix/`](02.%20Easy/22.%20Search%20in%20a%20Matrix/) |
| 4 | [Search in a sorted Matrix](https://www.geeksforgeeks.org/problems/search-in-a-matrix-1587115621/1) | — | — | — | Medium | Paytm, Accolite, MakeMyTrip, Ola Cabs, Oracle, Visa, Goldman Sachs, Directi, Groupon, InMobi, One97, Polycom, TinyOwl | Searching, Matrix | [`03. Medium/05. Search in a sorted Matrix/`](03.%20Medium/05.%20Search%20in%20a%20sorted%20Matrix/) |

### Number Theory & Digit Manipulation (4)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Repeated Removal of Kth](https://www.geeksforgeeks.org/problems/ishaans-internship4400/1) | — | — | — | Basics | — | Searching, Mathematics | [`01. Basics/10. Repeated Removal of Kth/`](01.%20Basics/10.%20Repeated%20Removal%20of%20Kth/) |
| 2 | [Next greater number set digits](https://www.geeksforgeeks.org/problems/next-greater-number-set-digits3503/1) | — | — | — | Easy | Morgan Stanley, Amazon, Microsoft, Samsung, Snapdeal, Hike, Adobe, Zillious, Oxigen Wallet, Vizury Interactive Solutions | Searching | [`02. Easy/21. Next greater number set digits/`](02.%20Easy/21.%20Next%20greater%20number%20set%20digits/) |
| 3 | [Nine Divisors](https://www.geeksforgeeks.org/problems/nine-divisors3751/1) | — | — | — | Medium | — | Searching, Prime Number, sieve, Binary Search | [`03. Medium/13. Nine Divisors/`](03.%20Medium/13.%20Nine%20Divisors/) |
| 4 | [Super Primes](https://www.geeksforgeeks.org/problems/super-primes2443/1) | — | — | — | Medium | — | Searching | [`03. Medium/14. Super Primes/`](03.%20Medium/14.%20Super%20Primes/) |

### Binary Search on an Index Invariant (3)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Extra in One of the Two Arrays](https://www.geeksforgeeks.org/problems/index-of-an-extra-element/1) | — | — | — | Easy | Zoho, Amazon | Arrays, Searching | [`02. Easy/12. Extra in One of the Two Arrays/`](02.%20Easy/12.%20Extra%20in%20One%20of%20the%20Two%20Arrays/) |
| 2 | [Single Among Doubles in a Sorted](https://www.geeksforgeeks.org/problems/find-the-element-that-appears-once-in-sorted-array0624/1) | — | — | — | Medium | Amazon, D-E-Shaw, Ola Cabs | Searching, Divide and Conquer | [`03. Medium/07. Single Among Doubles in a Sorted/`](03.%20Medium/07.%20Single%20Among%20Doubles%20in%20a%20Sorted/) |
| 3 | [Count Only Repeated](https://www.geeksforgeeks.org/problems/count-only-repeated2047/1) | — | — | — | Medium | — | Arrays, Searching | [`03. Medium/12. Count Only Repeated/`](03.%20Medium/12.%20Count%20Only%20Repeated/) |

### Two / Three Pointers on Sorted Arrays (3)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Common in 3 Sorted Arrays](https://www.geeksforgeeks.org/problems/common-elements1132/1) | — | — | — | Easy | VMWare, Microsoft, MAQ Software | Searching | [`02. Easy/04. Common in 3 Sorted Arrays/`](02.%20Easy/04.%20Common%20in%203%20Sorted%20Arrays/) |
| 2 | [Closest Sum Pair Across Two Arrays](https://www.geeksforgeeks.org/problems/find-the-closest-pair-from-two-arrays4215/1) | — | — | — | Easy | — | Arrays, Searching | [`02. Easy/17. Closest Sum Pair Across Two Arrays/`](02.%20Easy/17.%20Closest%20Sum%20Pair%20Across%20Two%20Arrays/) |
| 3 | [Pair Sum Closest to 0](https://www.geeksforgeeks.org/problems/two-numbers-with-sum-closest-to-zero1737/1) | — | — | — | Medium | Accolite, Amazon, Microsoft, Snapdeal | Arrays, Searching | [`03. Medium/10. Pair Sum Closest to 0/`](03.%20Medium/10.%20Pair%20Sum%20Closest%20to%200/) |

### String Repetition + Pattern Match (1)

| # | Problem | Logic | Time | Space | Difficulty | Companies | Related Tags | Folder |
|---|---|---|---|---|---|---|---|---|
| 1 | [Minimum repeat to make substring](https://www.geeksforgeeks.org/problems/minimum-times-a-has-to-be-repeated-such-that-b-is-a-substring-of-it--170645/1) | — | — | — | Medium | Google, NPCI | Searching, Strings, Pattern Searching | [`03. Medium/09. Minimum repeat to make substring/`](03.%20Medium/09.%20Minimum%20repeat%20to%20make%20substring/) |
