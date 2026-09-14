# Count Odd and Even

**Problem Link:** [GfG - Count Odd and Even](https://www.geeksforgeeks.org/problems/count-odd-even/1)

## Problem Statement

Given an array of integers, count how many elements are odd and how many elements are even.

Formally, given `arr[]` of size `n`, return the count of elements `x` in `arr` such that `x % 2 == 0` (even), and the count of elements such that `x % 2 != 0` (odd).

### Example 1

```
Input:  arr[] = [1, 2, 3, 4, 5]
Output: Even = 2, Odd = 3
Explanation: 2 and 4 are even; 1, 3, 5 are odd.
```

### Example 2

```
Input:  arr[] = [-3, -2, 0, 7, 10, 15]
Output: Even = 3, Odd = 3
Explanation: -2, 0, 10 are even; -3, 7, 15 are odd.
```

---

## Constraints

```
1 <= n <= 10^6
-10^9 <= arr[i] <= 10^9
```

At first glance this problem looks trivial — check `arr[i] % 2` and bucket the element. The real depth is in the **constraint on the value range including negative numbers**, which is exactly where naive parity checks break in some languages.

### The negative-number modulo pitfall

In mathematics, the modulo operation is defined to always return a non-negative remainder. But in most programming languages, `%` is not "modulo" — it is the **remainder operator**, and its sign follows the **dividend** (the left operand), not a mathematical convention. This differs by language:

| Language | `-3 % 2` | Sign convention |
|---|---|---|
| C, C++ (C99+), Java, JavaScript, Rust | `-1` | Result takes sign of dividend (truncated division) |
| Python | `1` | Result takes sign of divisor (floored division) |
| Some older/other languages | varies | Implementation-defined pre-C99 |

So for `-3`:
- In **C++/Java/JS**: `-3 % 2 == -1`
- In **Python**: `-3 % 2 == 1`

This means a naive **odd check** written as:

```python
# WRONG for negative odd numbers in truncating-division languages (illustrative, not Python-safe reasoning)
if arr[i] % 2 == 1:
    ...
```

will **fail to detect `-3` as odd**, because `-3 % 2` evaluates to `-1`, not `1`. The condition `== 1` is false, so `-3` silently gets skipped or miscounted.

However, the **even check** `arr[i] % 2 == 0` is safe in every language, because zero has no sign — whether the language returns `+0` or `-0` conceptually, `0 == 0` is always true. Only the odd check (`== 1`) is fragile.

**The fix for the odd check** is one of:
1. `arr[i] % 2 != 0` — correct in every language, since if it's not even, it's odd (this is what we use below).
2. `abs(arr[i]) % 2 == 1` — force the dividend positive first.
3. `arr[i] & 1` — bitwise AND, which is immune to this issue entirely (explained in depth in the Optimal Approach).

This subtlety is exactly why the problem constraints explicitly allow negative `arr[i]` — it's testing whether you reach for `% 2 == 1` blindly (a common but broken habit carried over from unsigned-only thinking) or you reason about remainder semantics correctly.

**Scale (`n` up to 10^6):** With a single pass being the theoretical minimum (you must look at every element at least once to classify it), performance differences at this scale come entirely from constant factors — number of passes, and cost per operation (modulo/division vs. bitwise AND). This is exactly what the Brute → Better → Optimal progression below demonstrates.

---

## Visualization / Diagram

Single-pass scan with two counters updated together:

```
arr   = [ -3,   -2,    0,    7,   10,   15 ]
         Odd,  Even, Even,  Odd, Even,  Odd

index:      0      1      2      3      4      5
value:     -3     -2      0      7     10     15
check:   %2!=0  %2==0  %2==0  %2!=0  %2==0  %2!=0
tag:      ODD   EVEN   EVEN    ODD   EVEN    ODD

even_count:  0 -> 0 -> 1 -> 2 -> 2 -> 3 -> 3
odd_count:   0 -> 1 -> 1 -> 1 -> 2 -> 2 -> 3

Final: Even = 3, Odd = 3
```

Bitwise view for the same elements (two's complement, last bit decides parity):

```
 -3  -> ...11111101  -> last bit 1 -> ODD
 -2  -> ...11111110  -> last bit 0 -> EVEN
  0  -> ...00000000  -> last bit 0 -> EVEN
  7  -> ...00000111  -> last bit 1 -> ODD
 10  -> ...00001010  -> last bit 0 -> EVEN
 15  -> ...00001111  -> last bit 1 -> ODD
```

---

## Brute Force Approach

### Idea

Use two **separate loops** over the array — one loop dedicated to counting evens, another separate loop dedicated to counting odds. This is the most naive decomposition: solve "count evens" and "count odds" as two independent problems, each scanning the whole array.

### Code

```python
class Solution:
    def countOddEvenBrute(self, arr):
        # Store length of array
        n = len(arr)

        # Initialize even counter to zero
        even_count = 0
        # Loop over all indices for the first pass (evens)
        for i in range(n):
            # Check if current element is even
            if arr[i] % 2 == 0:
                # Increment even counter
                even_count += 1

        # Initialize odd counter to zero
        odd_count = 0
        # Loop over all indices again for the second pass (odds)
        for i in range(n):
            # Check if current element is odd
            if arr[i] % 2 != 0:
                # Increment odd counter
                odd_count += 1

        # Return both counts as a tuple
        return even_count, odd_count
```

### Worked Trace

`arr = [-3, -2, 0, 7, 10, 15]`

**Pass 1 (evens):**
```
i=0: -3 % 2 = -1 (Python: 1) -> not even
i=1: -2 % 2 = 0  -> even, even_count=1
i=2:  0 % 2 = 0  -> even, even_count=2
i=3:  7 % 2 = 1  -> not even
i=4: 10 % 2 = 0  -> even, even_count=3
i=5: 15 % 2 = 1  -> not even
Result: even_count = 3
```

**Pass 2 (odds):**
```
i=0: -3 % 2 != 0 -> odd, odd_count=1
i=1: -2 % 2 != 0? -2%2=0 -> not odd
i=2:  0 % 2 != 0?  0%2=0 -> not odd
i=3:  7 % 2 != 0 -> odd, odd_count=2
i=4: 10 % 2 != 0? -> not odd
i=5: 15 % 2 != 0 -> odd, odd_count=3
Result: odd_count = 3
```

Final: `Even = 3, Odd = 3` — matches expected output.

### Complexity

- **Time:** `O(n)` asymptotically, but the array is traversed **twice**, so the actual work is `2n` element visits plus `2n` modulo operations. Big-O notation hides this constant factor (`O(2n)` collapses to `O(n)`), but at `n = 10^6`, doing 2 million modulo operations instead of 1 million is a real, measurable difference in wall-clock time and cache behavior (the array is read into cache twice).
- **Space:** `O(1)` — only two integer counters.

---

## Better Approach

### Idea

Merge the two loops into **one single pass**. For each element, check its parity once and increment the appropriate counter — both counters are maintained together in the same iteration instead of two independent scans.

### Code

```python
class Solution:
    def countOddEvenBetter(self, arr):
        # Initialize even counter to zero
        even_count = 0
        # Initialize odd counter to zero
        odd_count = 0

        # Loop through array once, visiting every element
        for x in arr:
            # Check if current element is even
            if x % 2 == 0:
                # Increment even counter
                even_count += 1
            else:
                # Otherwise it must be odd, increment odd counter
                odd_count += 1

        # Return both counts as a tuple
        return even_count, odd_count
```

Note the use of `else` rather than a second `if x % 2 != 0` check — since every integer is exactly one of odd or even, we don't need to re-evaluate the modulo; if it wasn't even, it must be odd. This also sidesteps the `% 2 == 1` pitfall automatically, since we never explicitly test for `== 1`.

### Worked Trace

`arr = [-3, -2, 0, 7, 10, 15]`

```
x=-3:  -3 % 2 = -1 (nonzero) -> else branch -> odd_count=1   | even=0 odd=1
x=-2:  -2 % 2 = 0            -> even_count=1                  | even=1 odd=1
x=0:    0 % 2 = 0            -> even_count=2                  | even=2 odd=1
x=7:    7 % 2 = 1            -> else branch -> odd_count=2   | even=2 odd=2
x=10:  10 % 2 = 0            -> even_count=3                  | even=3 odd=2
x=15:  15 % 2 = 1            -> else branch -> odd_count=3   | even=3 odd=3
```

Final: `Even = 3, Odd = 3` — one pass, correct result.

### Complexity

- **Time:** `O(n)` — exactly `n` element visits and `n` modulo operations, half the raw work of the brute force (`n` vs `2n`). This is **not an asymptotic improvement** (both are `O(n)`) — it's a **constant-factor improvement** (2x fewer operations and half the memory traffic since the array is only streamed through cache once). In competitive/production settings at `n` up to 10^6, this constant factor is genuinely significant for throughput and cache locality.
- **Space:** `O(1)`.

---

## Optimal Approach

### Idea

Replace the modulo check `x % 2` with the **bitwise AND** check `x & 1`. Since binary numbers store parity entirely in their least-significant bit (LSB), `x & 1` isolates that bit directly: it evaluates to `1` if `x` is odd and `0` if `x` is even — **regardless of sign**.

**Why `x & 1` works correctly for negative numbers when `%` can be unsafe:**

Integers are stored in **two's complement** representation. In two's complement, the least-significant bit follows the same rule for negative and positive numbers alike: it is `1` exactly when the number is odd. For example, on a typical 8-bit representation:

```
 3 = 00000011   -> LSB = 1 -> odd
-3 = 11111101   -> LSB = 1 -> odd
 2 = 00000010   -> LSB = 0 -> even
-2 = 11111110   -> LSB = 0 -> even
```

Two's complement negation is computed as `~x + 1` (invert all bits, add 1). Flipping bits and adding 1 does not change whether the final bit ends up as `0` or `1` in a way that breaks the odd/even pattern — the encoding is specifically constructed so that arithmetic (including bit-level parity) stays consistent across positive and negative values. `x & 1` reads that bit directly with a single hardware AND instruction — there is no "remainder sign convention" involved at all, because we're not performing division; we're doing a direct bit inspection. This is why the language-specific `%` sign ambiguity (truncated vs. floored division) simply does not exist for `&`.

**Why this is faster, not just safer:** Modulo/division (`%`) is implemented in hardware as an integer division instruction, which on most CPUs takes multiple clock cycles (division is one of the more expensive primitive ALU operations, often 10-40+ cycles depending on architecture). Bitwise AND is a single-cycle operation on essentially every architecture. At `n = 10^6` or `10^7`, replacing a division-class instruction with a single-cycle bitwise op per element is a meaningful throughput win, especially in tight loops the compiler can vectorize (SIMD bitwise AND is cheap; SIMD integer division is not, and compilers are far more willing to auto-vectorize a loop that only uses `&`).

### Code

```python
class Solution:
    def countOddEvenOptimal(self, arr):
        # Initialize even counter to zero
        even_count = 0
        # Initialize odd counter to zero
        odd_count = 0

        # Loop through array once, visiting every element
        for x in arr:
            # Check least-significant bit: 1 => odd, 0 => even, correct for all signs
            if x & 1:
                # Increment odd counter
                odd_count += 1
            else:
                # Increment even counter
                even_count += 1

        # Return both counts as a tuple
        return even_count, odd_count
```

### Worked Trace

`arr = [-3, -2, 0, 7, 10, 15]`

```
x=-3:  -3 & 1 = 1 -> odd_count=1     | even=0 odd=1
x=-2:  -2 & 1 = 0 -> even_count=1    | even=1 odd=1
x=0:    0 & 1 = 0 -> even_count=2    | even=2 odd=1
x=7:    7 & 1 = 1 -> odd_count=2     | even=2 odd=2
x=10:  10 & 1 = 0 -> even_count=3    | even=3 odd=2
x=15:  15 & 1 = 1 -> odd_count=3     | even=3 odd=3
```

Final: `Even = 3, Odd = 3` — same correct result, computed with cheaper per-element work.

### Complexity

- **Time:** `O(n)` — same asymptotic class as the Better approach (one pass, `n` operations). The improvement over Better is again a **constant-factor** one (bitwise AND vs. modulo instruction cost), not a change in the growth rate. However, this approach is **optimal in the true lower-bound sense** for this problem: any correct algorithm must inspect every one of the `n` elements at least once (an unseen element's parity is unknown), so `Ω(n)` is an unavoidable lower bound, and a single pass with O(1) work per element achieves it — you cannot do asymptotically better than `O(n)` for this problem. What separates "optimal" here from "correct-and-linear" is: (a) it hits the single-pass, O(1)-space lower bound, and (b) it uses the cheapest correct per-element operation (bitwise AND) and is immune to the modulo sign pitfall by construction.
- **Space:** `O(1)` — two counters only.

---

## Edge Cases

1. **Empty array (`n = 0`):** No elements to classify. Return `Even = 0, Odd = 0`. Guard against this if the language/framework doesn't handle an empty iteration gracefully (most loops naturally handle it fine).
2. **Single element:** `arr = [4]` → `Even = 1, Odd = 0`. `arr = [-7]` → `Even = 0, Odd = 1`.
3. **All even:** `arr = [2, 4, 6, 8]` → `Even = 4, Odd = 0`.
4. **All odd:** `arr = [1, 3, 5, 7]` → `Even = 0, Odd = 4`.
5. **Negative odd numbers (the modulo pitfall, concretely):** `arr = [-3]` in C++/Java/JS:
   - `-3 % 2` evaluates to `-1`.
   - A naive check `arr[i] % 2 == 1` evaluates `-1 == 1` → **false** → `-3` is wrongly excluded from the odd count.
   - Correct checks: `arr[i] % 2 != 0` (`-1 != 0` → true → correctly odd), or `arr[i] & 1` (`-3 & 1 = 1` → true → correctly odd).
   - This is the single most important edge case in this problem — it's specifically why the constraints allow negative values.
6. **Zero:** `0` is even (`0 % 2 == 0` and `0 & 1 == 0` in every language, no ambiguity). A common misconception is treating `0` as neither odd nor even, or as a special case — it needs no special handling; it falls out correctly as even.
7. **Very large numbers (`arr[i]` near `10^9`):** No overflow risk in standard 32-bit or 64-bit integer types since `10^9` fits comfortably in a 32-bit signed int (`max ~2.1 * 10^9`). Parity check itself is unaffected by magnitude — both `%` and `&` operate correctly at this scale, and the extremes worth testing are `INT_MIN`-adjacent values only if the language's specific integer type is a concern (not an issue in Python; matters more in fixed-width C++/Java if constraints were pushed further).

---

## Interview Follow-ups

1. **Why use bitwise AND instead of modulo — what's the actual performance difference?**
   Modulo (`%`) compiles to an integer division instruction, which is a multi-cycle operation on most CPUs (division is markedly more expensive than addition, subtraction, or bitwise ops). Bitwise AND (`&`) is a single-cycle ALU operation. For parity checking specifically, `x & 1` extracts the least-significant bit directly — no division semantics needed at all. Compilers may already optimize `x % 2` into a bitwise op for *unsigned* types, but for *signed* types they generally cannot make this substitution silently, because `%`'s truncating sign behavior on negative operands differs from what `& 1` gives — so writing `& 1` explicitly is both faster and removes ambiguity.

2. **Handle negative number parity correctly — explain the two's complement reasoning.**
   Negative integers are stored in two's complement: `-x` is `~x + 1` (bitwise NOT of `x`, plus one). This representation preserves the least-significant bit as a reliable parity indicator for both positive and negative numbers — the bit pattern's last bit is `1` iff the integer is odd, full stop, independent of sign. This is different from `%`, which is a *division remainder* operation whose sign convention (does the remainder follow the dividend's sign, truncated division, or is it always non-negative, floored/Euclidean division) is a language design choice, not a hardware/representation fact. That's why `& 1` is representation-native and sign-safe, while `% 2 == 1` is a language-dependent trap.

3. **Separate odds and evens into two arrays instead of just counting — how does that change the approach?**
   Same single pass, same parity check, but instead of incrementing counters you append to two output lists/arrays: `if x & 1: odds.append(x) else: evens.append(x)`. Time stays `O(n)`; space becomes `O(n)` total across both output arrays (still O(1) *extra* space if the two output arrays together are considered the required output rather than auxiliary space). Worth mentioning: if order doesn't matter and in-place partitioning is desired, this becomes exactly the partition step of a Dutch National Flag / quicksort-style partition, doable in `O(n)` time and `O(1)` extra space using two pointers swapping elements in place.

4. **Count odd/even without any conditional branching — branchless technique?**
   Since `x & 1` yields exactly `0` or `1`, you can accumulate directly without an `if`:
   ```python
   odd_count += (x & 1)
   even_count += 1 - (x & 1)
   ```
   or equivalently track only `odd_count` via branchless accumulation and derive `even_count = n - odd_count` in `O(1)` at the end (see follow-up 5). This avoids branch mispredictions in tight loops on data with unpredictable parity patterns, which matters for SIMD/vectorized execution where branches are costly or impossible to vectorize cleanly, but arithmetic accumulation vectorizes well.

5. **Do you even need two counters?**
   No — since every element is either odd or even, `even_count = n - odd_count` (or vice versa). You only need to count one category in the pass and derive the other by subtraction in `O(1)`, saving one increment operation per iteration (a minor but real constant-factor win, and a good "did you notice the redundancy" signal in an interview).

---

## Interview Explanation Tips

- **Start with the naive version out loud**, but immediately flag the negative-number trap before being asked — this signals depth rather than looking like an oversight caught later. Say something like: *"A common mistake here is checking `arr[i] % 2 == 1` for odd — that fails for negative odd numbers in C++, Java, or JavaScript, because `%` in those languages returns a result with the sign of the dividend, so `-3 % 2` is `-1`, not `1`. I'll use `!= 0` or bitwise AND instead to avoid that."**
- **Walk through the concrete counterexample**: `-3 % 2 == -1` in C++/Java, but `1` in Python — show you know this is language-dependent, not a universal fact, which demonstrates you understand remainder semantics rather than having memorized a rule.
- **Explain `x & 1` as a representation-level fact, not a trick**: tie it to two's complement — the LSB directly encodes parity regardless of sign, because two's complement is constructed so bit-level parity is sign-invariant. Contrast this clearly against `%`, which is a division operation with a sign convention that varies by language — that's the crux of why AND is both faster and safer.
- **Narrate the progression explicitly as constant-factor, not asymptotic**: two loops (2n operations) → one loop (n operations, still O(n)) → one loop with bitwise AND (n operations, cheaper per-op, still O(n)). Say plainly: *"All three are O(n) — the improvements are constant-factor: fewer passes, then cheaper per-element work. The true lower bound is Ω(n) since every element must be inspected at least once, so O(n) with O(1) space is optimal for this problem."*
- **Preempt the "why not just count one and subtract" question** by mentioning it yourself if time allows — it shows you look for redundant work even after arriving at a working solution.
- **Common mistake to explicitly call out**: using `% 2 == 1` as the odd check is the single most frequent bug in this exact problem when negative numbers are in scope — mentioning this unprompted, correctly, and with the right example (`-3`) is a strong signal in this specific interview question.
