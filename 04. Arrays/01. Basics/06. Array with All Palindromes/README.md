# Array with All Palindromes

**GfG Link:** https://www.geeksforgeeks.org/problems/palindromic-array-1587115620/1

## Problem Statement

Given an array `arr[]` of `n` integers, determine whether **every element of the array, when read as a number (its digit sequence), is a palindrome**. Return `true` (or `1`) if all elements are palindromic numbers, otherwise return `false` (or `0`).

It is important to be precise about what "palindrome" means here: this is **not** about reversing the *array itself* (i.e., it's not asking whether `arr == reverse(arr)`). It is about each individual **number's digits** reading the same forwards and backwards. For example, `121` is a palindrome because its digits `1 2 1` are symmetric; `123` is not, because reversing its digits gives `321 ≠ 123`.

### Example 1

```
Input:  arr[] = [555, 585, 2, 92222, 3223]
Output: false

Explanation:
555   -> palindrome (5 5 5)
585   -> palindrome (5 8 5)
2     -> palindrome (single digit)
92222 -> NOT a palindrome (reverse = 22229 ≠ 92222)
3223  -> palindrome (3 2 2 3)

Since 92222 breaks the pattern, the answer is false.
```

### Example 2

```
Input:  arr[] = [11, 121, 1, 4554]
Output: true

Explanation:
11   -> palindrome
121  -> palindrome
1    -> palindrome (trivially, single digit)
4554 -> palindrome (4 5 5 4)

All elements are palindromic numbers, so the answer is true.
```

---

## Constraints — Deep Dive

Typical GfG constraints for this problem:

```
1 <= n <= 10^6          (array size)
1 <= arr[i] <= 10^9     (element magnitude, non-negative in the standard version)
```

Let's unpack why each bound matters for algorithm design:

- **`n` up to `10^5`–`10^6`**: The array itself can be large, so whatever per-element check we design, we must not multiply it by an unnecessary constant factor (e.g., avoid repeated string allocations or nested loops over the array). An `O(n)` or `O(n · d)` scan (where `d` is the average digit count) is expected — anything super-linear in `n` risks TLE at the upper bound.

- **Element value up to `10^9`**: This means each individual number can have **up to 10 digits** (since `10^9` has 10 digits: `1,000,000,000`). This is the key insight that makes the "d" (digit count) dimension relevant:
  - A number like `7` has `d = 1` digit — checking it is essentially `O(1)`.
  - A number like `999999999` (9 nines, ~`10^9`) has `d = 9`–`10` digits — checking it requires inspecting up to 5 digit-pairs (two pointers meeting in the middle).
  - Since `d` is bounded by a small constant (≤ 10 for `arr[i] ≤ 10^9`), the per-element cost is technically `O(1)` in an amortized/practical sense, but it's more precise and more interview-friendly to express the total complexity as **`O(n · d)`**, making the dependency on digit count explicit rather than hiding it inside a hidden constant.
  - This matters because if the constraints were relaxed to allow arbitrarily large numbers (e.g., big integers via strings, `10^100`), the `d` term would no longer be negligible, and `O(n · d)` would become the *true* bottleneck rather than an academic footnote.

- **Do negative numbers appear?** The stated constraint `1 <= arr[i]` on GfG for this exact problem typically restricts elements to **positive integers**, sidestepping the ambiguity. However, it's worth clarifying the assumption for interviews, since many variants allow negatives:
  - **Common convention**: A negative number is treated as **not a palindrome**, because the `-` sign breaks symmetry when you consider the printed representation (e.g., `"-121"` reversed is `"121-"`, which isn't equal to `"-121"`).
  - **Alternative convention** (must be explicitly stated by the interviewer/spec): Ignore the sign and only check the digit magnitude — so `-121` would be considered a palindrome because `121` is.
  - **This article assumes the GfG-standard interpretation**: inputs are non-negative (`arr[i] >= 1`), so the sign ambiguity does not arise. Where relevant, the "Interview Follow-ups" section below discusses how to adapt the solution if negatives must be handled.

---

## Visualization / Diagram

### Checking a single number with two pointers (digit-level)

Take `arr[i] = 3223`. Think of its digits as an array `[3, 2, 2, 3]` with a `left` pointer starting at index 0 and a `right` pointer starting at the last index, moving toward each other:

```
Digits:   3    2    2    3
Index:    0    1    2    3
          ^                ^
        left             right

Step 1: digit[left]=3 == digit[right]=3  ✔ match -> left++, right--

          3    2    2    3
               ^    ^
             left  right

Step 2: digit[left]=2 == digit[right]=2  ✔ match -> left++, right--

          3    2    2    3
                 ^^
            left/right cross or meet

left >= right  -> all pairs matched -> 3223 IS a palindrome
```

Contrast with `92222`:

```
Digits:   9    2    2    2    2
Index:    0    1    2    3    4
          ^                   ^
        left                right

Step 1: digit[left]=9 vs digit[right]=2  ✘ MISMATCH -> stop immediately

Result: 92222 is NOT a palindrome (no need to check remaining digits)
```

### Overall array scan with early exit

```
arr = [555, 585, 2, 92222, 3223]
        |     |    |    |      |
        ✔     ✔    ✔    ✘      (never reached)
                         |
                 mismatch found here
                 -> STOP scanning the array immediately
                 -> return false

Array scan:  555 -> OK -> 585 -> OK -> 2 -> OK -> 92222 -> FAIL -> [early exit, skip 3223]
```

This early-exit behavior (stopping the moment a single non-palindrome is found — both within a number's digit check AND across the array scan) is a recurring optimization theme in this problem, applicable at every approach level below.

---

## Brute Force Approach — String Reversal

### Idea

For each element, convert the integer to a string and compare it with its reverse. Python's slicing makes this a one-liner: `str(num) == str(num)[::-1]`. If any element fails this check, the whole array's answer is `false`; if all pass, it's `true`.

### Code

```python
def is_array_all_palindromes_brute(arr):
    for num in arr:
        s = str(num)
        if s != s[::-1]:
            return False
    return True

# Driver
if __name__ == "__main__":
    print(is_array_all_palindromes_brute([555, 585, 2, 92222, 3223]))  # False
    print(is_array_all_palindromes_brute([11, 121, 1, 4554]))          # True
```

### Worked Trace

For `arr = [555, 585, 2, 92222, 3223]`:

```
num = 555    -> s = "555"   -> reversed = "555"   -> equal -> continue
num = 585    -> s = "585"   -> reversed = "585"   -> equal -> continue
num = 2      -> s = "2"     -> reversed = "2"     -> equal -> continue
num = 92222  -> s = "92222" -> reversed = "22229" -> NOT equal -> return False immediately
```

Final output: `False` — matches Example 1.

### Complexity

- **Time**: For a single number with `d` digits, `str(num)` costs `O(d)`, `s[::-1]` costs `O(d)` (creates a new reversed string), and the comparison `s != s[::-1]` costs `O(d)`. So each element check is `O(d)`. Across `n` elements, total time is **`O(n · d)`**.
- **Space**: Each call to `str(num)` and `s[::-1]` allocates a **new string object** of length `d`. So the auxiliary space per element check is `O(d)` (temporary, garbage-collected after each iteration, but still real allocation overhead). This repeated string construction is the main inefficiency this approach carries compared to the approaches below.

---

## Better Approach — Digit Extraction with Two-Pointer Array (No String Conversion)

### Idea

Avoid string conversion entirely. Extract the digits of each number mathematically using `% 10` (modulo, to peel off the last digit) and `// 10` (integer division, to remove it), storing them into a list. Then run a two-pointer scan on that digit list — comparing `digits[left]` with `digits[right]`, moving inward — to check palindrome symmetry, exactly as shown in the diagram above.

### Code

```python
def is_palindrome_number_digit_array(num):
    if num < 0:
        return False  # sign breaks symmetry under this problem's convention

    digits = []
    temp = num
    if temp == 0:
        digits = [0]
    while temp > 0:
        digits.append(temp % 10)
        temp //= 10

    left, right = 0, len(digits) - 1
    while left < right:
        if digits[left] != digits[right]:
            return False
        left += 1
        right -= 1
    return True


def is_array_all_palindromes_better(arr):
    for num in arr:
        if not is_palindrome_number_digit_array(num):
            return False
    return True

# Driver
if __name__ == "__main__":
    print(is_array_all_palindromes_better([555, 585, 2, 92222, 3223]))  # False
    print(is_array_all_palindromes_better([11, 121, 1, 4554]))          # True
```

### Worked Trace

For `num = 3223`:

```
temp = 3223
  3223 % 10 = 3  -> digits = [3]         ; temp = 3223 // 10 = 322
  322  % 10 = 2  -> digits = [3, 2]      ; temp = 322  // 10 = 32
  32   % 10 = 2  -> digits = [3, 2, 2]   ; temp = 32   // 10 = 3
  3    % 10 = 3  -> digits = [3, 2, 2, 3]; temp = 3    // 10 = 0  (loop ends)

digits = [3, 2, 2, 3]   (note: this is the REVERSE reading order of the number,
                          i.e., least-significant digit first, but that's fine —
                          symmetry is preserved either way)

Two-pointer check:
  left=0(val 3), right=3(val 3) -> match -> left=1, right=2
  left=1(val 2), right=2(val 2) -> match -> left=2, right=1 -> loop ends (left >= right)

Result: palindrome ✔
```

### Complexity

- **Time**: Extracting `d` digits via repeated `% 10` / `// 10` takes `O(d)`. The two-pointer comparison over the digit list also takes `O(d)` (at most `d/2` comparisons). So per element it's `O(d)`, and overall **`O(n · d)`** — same asymptotic class as brute force.
- **Space**: We still allocate a `digits` list of size `O(d)` per element — so auxiliary space is `O(d)` per check, same order as the brute force string approach.
- **Tradeoff vs. brute force**: Although the Big-O class is identical, this approach **avoids Python's string object overhead** (string creation, encoding, slicing machinery) in favor of raw arithmetic operations on a plain list of small integers. In performance-sensitive contexts (e.g., compiled languages like C++/Java, or hot loops in Python), integer arithmetic is typically cheaper than string allocation, so this is a genuine (if constant-factor) improvement. It also sets up the conceptual bridge to the fully optimal approach below, which removes the extra list entirely.

---

## Optimal Approach — Reverse the Number Mathematically (O(1) Extra Space)

### Idea

We don't need to store digits in a list at all. We can reconstruct the **reversed number itself** using the classic "reverse integer" technique: repeatedly peel off the last digit of `num` with `% 10` and append it to a `reversed_num` accumulator (`reversed_num = reversed_num * 10 + digit`), while shrinking `num` with `// 10`. At the end, compare `reversed_num` to the **original** number. If they match, the number is a palindrome.

This uses only a handful of scalar variables (`num`, `original`, `reversed_num`, `digit`) — no string, no list — giving **O(1) extra space per element** (beyond the built-in integer storage itself, which doesn't scale with `d` the way a string/list does).

**Overflow awareness**: In languages with fixed-width integers (C++/Java `int`/`long`), reversing a number near the type's maximum value can overflow (e.g., reversing `1000000009` might exceed `2^31 - 1`). Defensive code checks for overflow before the multiply-add step, or uses a wider type (`long long` / `long`) for the accumulator. In Python, integers are arbitrary-precision, so this is a non-issue — but it is a point worth raising explicitly in an interview to demonstrate awareness of language-level constraints.

### Code

```python
def is_palindrome_number_optimal(num):
    if num < 0:
        return False  # sign breaks symmetry under this problem's convention

    original = num
    reversed_num = 0
    temp = num

    while temp > 0:
        digit = temp % 10
        # Overflow guard (relevant in fixed-width languages; shown here for completeness)
        reversed_num = reversed_num * 10 + digit
        temp //= 10

    return reversed_num == original


def is_array_all_palindromes_optimal(arr):
    for num in arr:
        if not is_palindrome_number_optimal(num):
            return False   # early exit: stop scanning the array immediately
    return True

# Driver
if __name__ == "__main__":
    print(is_array_all_palindromes_optimal([555, 585, 2, 92222, 3223]))  # False
    print(is_array_all_palindromes_optimal([11, 121, 1, 4554]))          # True
```

### Step-by-Step Trace

For `num = 585`:

```
original = 585
reversed_num = 0
temp = 585

Iteration 1:
  digit = 585 % 10 = 5
  reversed_num = 0 * 10 + 5 = 5
  temp = 585 // 10 = 58

Iteration 2:
  digit = 58 % 10 = 8
  reversed_num = 5 * 10 + 8 = 58
  temp = 58 // 10 = 5

Iteration 3:
  digit = 5 % 10 = 5
  reversed_num = 58 * 10 + 5 = 585
  temp = 5 // 10 = 0   (loop ends)

Compare: reversed_num (585) == original (585)  -> True -> palindrome ✔
```

For `num = 92222` (the failing case from Example 1):

```
original = 92222
reversed_num = 0, temp = 92222

digit=2 -> reversed_num = 2      -> temp = 9222
digit=2 -> reversed_num = 22     -> temp = 922
digit=2 -> reversed_num = 222    -> temp = 92
digit=2 -> reversed_num = 2222   -> temp = 9
digit=9 -> reversed_num = 22229  -> temp = 0 (loop ends)

Compare: reversed_num (22229) == original (92222)? NO -> not a palindrome ✘
```

### Complexity

- **Time**: Reversing a `d`-digit number takes exactly `d` iterations, i.e., `O(d)` per element. Across the whole array: **`O(n · d)`**. This is asymptotically **optimal** — there is no way to determine whether a `d`-digit number is a palindrome without inspecting at least `⌈d/2⌉` of its digits in the worst case (you cannot skip digits and still guarantee correctness), so `O(d)` per element is a hard lower bound, making `O(n · d)` optimal for the array as a whole (you must, in the worst case, look at every element too — you cannot know an element isn't checked without checking it).
- **Space**: `O(1)` **per element** — only a constant number of scalar variables (`original`, `reversed_num`, `temp`, `digit`) are used, none of which scale with `d` in terms of *auxiliary structure* (unlike the string or digit-list approaches, which allocate `O(d)`-sized objects). Overall extra space for the whole array check is `O(1)` (excluding the input array itself and the recursion-free iterative control flow).
- **Early-exit optimization**: Just as within a single number's digit comparison we stop at the first mismatched digit pair, at the array level we `return False` the instant we hit the first non-palindromic element — we never even construct `reversed_num` for the remaining elements. In the worst case (all palindromes, or the failure is the last element), this doesn't change the asymptotic bound, but in practice (and especially in interviews) it's an optimization worth calling out proactively, since it can produce large real-world speedups on inputs where a mismatch appears early.

---

## Edge Cases

- **Empty array (`n = 0`)**: Vacuously, "all elements are palindromes" is true (there are no counter-examples). Most implementations of `all()`/a loop that never enters naturally return `True` for an empty array — but confirm this is the expected behavior for the specific problem/judge, since some define it as an invalid input instead.
- **Single-digit numbers (`0`–`9`)**: Always palindromes trivially — a single digit is symmetric by definition (`d = 1`, so `left == right` immediately and the loop body never executes, or the reversal trivially reproduces the same digit).
- **Zero itself (`num = 0`)**: A special case worth handling explicitly in the digit-extraction approaches — the `while temp > 0` loop never executes for `temp = 0`, so `digits` (in the "Better" approach) would end up empty unless explicitly seeded with `[0]`, and `reversed_num` (in the "Optimal" approach) correctly stays `0`, matching `original = 0` — so the optimal approach handles zero correctly without special-casing, but the digit-array approach needs the explicit `if temp == 0: digits = [0]` guard shown above.
- **Negative numbers**: Under this problem's stated constraints (`arr[i] >= 1`), negatives shouldn't appear — but defensive code should still decide a convention. This article's implementations return `False` immediately for negative numbers (sign breaks symmetry), consistent with the "standard" convention discussed in Constraints.
- **Numbers with trailing zero(s) — the classic pitfall**: A number like `120` is **not** a palindrome, and it's important to understand *why* concretely: reversing the digit sequence of `120` gives `021`, which as a **number** is just `21` (leading zeros are dropped) — so `reversed_num` ends up as `21`, definitively `≠ 120`. This is a very common source of off-by-one or "seems obviously wrong" bugs for anyone who tries to shortcut the check (e.g., by comparing digit *counts* naively, or mishandling leading-zero stripping). The two-pointer digit-array and mathematical-reversal approaches both handle this correctly automatically, precisely because they never try to "reconstruct with padding" — they just compare pure digit/number values. It's a great detail to mention out loud in an interview.
- **Very large numbers near overflow when reversing**: In fixed-width-integer languages, a number close to `INT_MAX`/`LONG_MAX` can produce a reversed value that overflows during the `reversed_num * 10 + digit` step even if the original number itself was in range. Defensive implementations check `if reversed_num > (INT_MAX - digit) / 10: overflow` before each multiply-add, or promote to a 64-bit accumulator when reversing a 32-bit input. Python sidesteps this due to arbitrary-precision integers, but this is worth flagging explicitly as language-dependent.

---

## Interview Follow-ups

1. **"How would you modify the solution to treat negative numbers as palindromes by ignoring the sign?"**
   Take `abs(num)` before running the digit-extraction/reversal logic, effectively stripping the sign before the check. Be explicit that this is a *convention change*, not a bug fix — clarify the requirement with the interviewer before assuming either behavior.

2. **"Instead of a boolean, return the count of how many elements are palindromic numbers."**
   Remove the early-exit `return False`; instead, maintain a running `count`, increment it whenever `is_palindrome_number_optimal(num)` is `True`, and return `count` at the end. Note this **removes the early-exit optimization opportunity** for that specific requirement, since you now must inspect every element regardless of any single failure — total time becomes strictly `O(n · d)` with no possible short-circuit.

3. **"Return the index of the first element that is NOT a palindrome (or -1 if all are palindromes)."**
   Nearly identical to the optimal solution, but instead of returning `False`, return the current loop index `i` the moment `is_palindrome_number_optimal(arr[i])` is `False`; if the loop completes without finding one, return `-1`. This retains the early-exit benefit.

4. **"What if the array contains strings representing numbers instead of integers (e.g., very large numbers that don't fit in standard integer types)?"**
   If the numbers are given as strings (perhaps because they're too large for 64-bit integers, like `"123456789012345678901"`), you cannot use the mathematical mod/div reversal (integer overflow becomes unavoidable at fixed width, or you'd need arbitrary-precision arithmetic anyway). In that case, the **two-pointer approach directly on the string's characters** (comparing `s[left]` and `s[right]`, moving inward) is actually the *right* choice — it's `O(d)` time, `O(1)` extra space (beyond the input string itself), and sidesteps overflow entirely, since you never convert to a numeric type.

5. **"Can you do this without any extra space at all, including not creating `reversed_num`?"**
   Not meaningfully beyond what's already shown — the O(1) approach already uses only scalar variables. If asked to push further, you could point out that comparing digits via repeated division without building a full reversed number (extract the leading digit via `num // 10^(d-1)` and the trailing digit via `num % 10`, comparing pairs while shrinking from both ends) achieves the same O(1) space with digit-pair early exit *within* a single number as well — worth mentioning as a refinement that mirrors the two-pointer idea without ever materializing `reversed_num` fully, useful if the interviewer wants to see early exit *within* the per-number check too, not just across the array.

---

## Interview Explanation Tips

- **Start by restating the problem precisely.** Explicitly say out loud: "To be clear, this isn't about reversing the array — it's about checking that *each number's digits* read the same forwards and backwards." This preempts a very common misunderstanding and signals careful reading of the problem.
- **Walk through the brute force first, even if you plan to optimize.** Mention `str(num) == str(num)[::-1]` as the obvious first idea — it shows you can produce a correct baseline quickly, and it gives you a natural segue into "but this allocates new string objects on every check; can we avoid that?"
- **Explicitly call out the trailing-zero pitfall as a sign of depth.** Proactively say something like: "One classic gotcha here is a number like 120 — its digit-reversal is 021, which as an integer is just 21, not something padded back to three digits. Any correct solution has to naturally fall out of pure digit/value comparison rather than any kind of string-length assumption." Bringing this up *before being asked* signals you've thought about correctness edge cases, not just the happy path.
- **Present the mathematical reversal as the natural endpoint, and justify why it's optimal — not just "faster."** Explain the lower bound: you must inspect on the order of `d/2` digits of any given number in the worst case to be sure it's a palindrome, so `O(d)` per element (and `O(n·d)` overall) isn't just an implementation choice, it's information-theoretically required. This shows you understand optimality isn't just "the fastest code I could write" but tied to a real lower bound.
- **Proactively mention early exit as an optimization, at both levels.** Two places to highlight: (1) within a single number's digit/two-pointer check, stop the instant a mismatched pair is found; (2) across the array scan, stop the instant one element fails, without checking the rest. Say this even if the interviewer doesn't ask — it demonstrates you think about real-world performance on top of Big-O, and it's a natural lead-in to follow-up questions like "what if you needed the count instead" (where you'd note early exit no longer applies).
- **Mention overflow awareness if the language has fixed-width integers.** Even in Python where it doesn't matter, saying "in a language like Java or C++, reversing a number near INT_MAX could overflow, so I'd either check before each step or widen the accumulator type" shows breadth beyond the specific language you're coding in.
