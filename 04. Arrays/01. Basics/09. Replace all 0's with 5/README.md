# Replace All 0's With 5

**GfG Link:** https://www.geeksforgeeks.org/problems/replace-all-0s-with-5/1

## 1. Problem Statement

You are given a single non-negative integer `N`. Replace every occurrence of the digit `0` in `N` with the digit `5`, and return the resulting number.

Despite being filed under the "Arrays" topic on GfG, this problem does **not** operate on an array — it operates on the **digits of a single number**. There is no array of elements to traverse; instead you traverse the decimal digits of `N` one at a time (either by converting to a string, or by repeated `% 10` / `/ 10` arithmetic).

### Examples

**Example 1**
```
Input:  N = 1004
Output: 1554
Explanation: The two '0' digits are replaced with '5', giving 1554.
```

**Example 2**
```
Input:  N = 0
Output: 5
Explanation: The single digit 0 is replaced by 5.
```

---

## 2. Constraints — Deep Dive

Typical GfG constraint for this problem:

```
0 <= N <= 10^9   (sometimes stated up to 10^18 in variants)
```

**Why the range matters:**

- **Data type selection.** If `N` can be as large as `10^9`, it still fits comfortably in a 32-bit signed integer (`int` in C++/Java, max ~2.1 × 10^9). But if the constraint is pushed to `10^18` (common in "large number" variants of this problem), you **must** use a 64-bit type — `long long` in C++, `long` in Java, or Python's arbitrary-precision `int` (which needs no special handling). Using a 32-bit type with an 18-digit input silently overflows and produces wrong answers with no runtime error in C++ (undefined behavior) — a classic interview trap.

- **Digit-count preservation implies same-magnitude output.** A crucial observation: replacing digits does **not** change the number of digits. `1004` (4 digits) becomes `1554` (4 digits). `999999999` (9 nines, no zeros) stays 9 digits. Since replacing `0` with `5` never changes digit count, and `5 > 0`, the output is always `>=` the input numerically, but it never gains an extra digit. This means: **whatever integer type safely holds N also safely holds the answer** — you never need to "upgrade" type between input and output. This is worth stating explicitly in an interview because it removes a common overflow worry ("could the result overflow beyond N's type?" — no, because digit count is invariant).

- **String vs. number representation affects which approaches are even eligible.** If the problem is phrased as "given N as a string" (some variants do this to sidestep type-limit issues entirely, allowing arbitrarily large N), then string-based approaches are natural and the "optimal" arithmetic approach doesn't apply (there's no numeric type large enough, nor is one needed). If N is genuinely given as an **integer type**, you are bounded by that type's range, and a pure-arithmetic (mod/div) approach becomes viable and is the most space-efficient. Recognizing which flavor of the problem you've been given determines which of the three approaches below is realistic — you cannot do mod-10 arithmetic on a string-only representation of a 10^100-digit number using fixed-width integer types.

- **Sign.** The constraint says `N >= 0`, so negative numbers are explicitly out of scope for the base problem — but interviewers often probe this as a follow-up (see Section 8).

---

## 3. Visualization / Diagram

Take `N = 1004`. Laid out digit by digit (most significant to least significant):

```
Index:      0     1     2     3
Digit:      1     0     0     4
             |     |     |     |
             |   [0->5] [0->5] |
             v     v     v     v
Result:     1     5     5     4

Final number: 1 5 5 4  =>  1554
```

A second trace for `N = 0`:

```
Index:      0
Digit:      0
             |
           [0->5]
             v
Result:     5

Final number: 5
```

A trace showing digits that are untouched (`N = 5029`):

```
Digit:      5     0     2     9
             |     |     |     |
          (keep) [0->5] (keep)(keep)
             v     v     v     v
Result:     5     5     2     9

Final number: 5529
```

The transformation is purely a **per-position digit map**: `f(d) = 5 if d == 0 else d`, applied independently to every digit, left to right, with position/place-value otherwise unchanged.

---

## 4. Brute Force Approach — String Convert + Replace

### Idea

1. Convert the integer `N` to its string representation.
2. Use the language's built-in string-replace to swap every `'0'` character with `'5'`.
3. Convert the resulting string back to an integer.

This is the most direct translation of "replace digit 0 with digit 5" into code, leaning entirely on library string operations.

### Python Code

```python
class Solution:
    def replaceZerosBrute(self, n: int) -> int:
        # Convert integer n to its string representation
        s = str(n)

        # Replace every '0' character with '5' in the string
        s = s.replace('0', '5')

        # Convert the resulting string back to an integer and return it
        return int(s)
```

### Worked Trace (N = 1004)

```
str(1004)          -> "1004"
"1004".replace('0','5') -> "1554"
int("1554")         -> 1554
```

### Complexity

- **Time: O(d)**, where `d` = number of digits in `N` (`d = O(log10 N)`).
  - `str(n)` scans/produces `d` characters — O(d).
  - `.replace('0','5')` is a single linear scan over the string producing a new string — O(d). Python's `str.replace` is implemented as one pass that builds a fresh string buffer; it is **not** O(d²) because it doesn't shift-and-rebuild per match, it constructs the output once.
  - `int(s)` parses `d` characters — O(d).
  - Total: O(d) + O(d) + O(d) = O(d).

- **Space: O(d)**.
  - Python strings are **immutable**. Each of the three steps (`str(n)`, `.replace(...)`, and internally re-materializing digits for `int(...)`) allocates a **new** string/buffer of length O(d) rather than mutating in place. So although asymptotically we only pay O(d) space (not more), we pay it **multiple times over** — once per intermediate string — which matters for constant factors even though it doesn't change the Big-O class.
  - This immutability point is the seed for why the "Better" and "Optimal" approaches try to reduce the number of separate allocations / avoid strings altogether.

---

## 5. Better Approach — Manual Digit-by-Digit Construction (String-Based)

### Idea

Rather than relying on the black-box `.replace()`, manually iterate over each character of the string form of `N`, decide digit-by-digit whether to keep it or substitute `'5'`, and **assemble the result using a mutable/linear-time-friendly structure** (a list of characters), joining only once at the end.

This section's real teaching point is a classic interview trap: **naive string concatenation inside a loop is O(d²)**, not O(d), because strings are immutable — each `+=` creates an entirely new string of growing length. Building a list and joining once avoids this.

### Code — Inefficient Version (concatenation in a loop, O(d²))

```python
class Solution:
    def replaceZerosNaiveConcat(self, n: int) -> int:
        # Convert integer n to its string representation
        s = str(n)

        # Start with an empty result string
        result = ""

        # Loop through every character in the string
        for ch in s:
            # Check if the current character is '0'
            if ch == '0':
                # Append '5' by concatenation (this copies the entire string so far)
                result += '5'
            else:
                # Append the original character unchanged (same copy cost)
                result += ch

        # Convert the assembled string back to an integer and return it
        return int(result)
```

**Why this is O(d²):** on iteration `i`, `result` already has length `i`, and `result += ch` must allocate a new string of length `i+1` and copy all `i` existing characters into it (because strings are immutable in Python, Java, C#, etc.). Summing `1 + 2 + 3 + ... + d = O(d²)` total character copies.

### Code — Efficient Version (list + single join, O(d))

```python
class Solution:
    def replaceZerosBetter(self, n: int) -> int:
        # Convert integer n to its string representation
        s = str(n)

        # Initialize a mutable buffer (list) to collect characters
        chars = []

        # Loop through every character in the string
        for ch in s:
            # Append '5' if the character is '0', otherwise append it unchanged
            chars.append('5' if ch == '0' else ch)

        # Join all characters into the final string in a single pass
        result = ''.join(chars)

        # Convert the joined string back to an integer and return it
        return int(result)
```

**Why this is O(d):** `list.append` is O(1) amortized (dynamic array doubling), so the loop costs O(d) total. `''.join(chars)` builds the final string exactly once, in one O(d) pass, instead of rebuilding it after every character.

### Worked Trace (N = 1004, efficient version)

```
s = "1004"
chars = []
ch='1' -> not '0' -> chars = ['1']
ch='0' -> is '0'  -> chars = ['1','5']
ch='0' -> is '0'  -> chars = ['1','5','5']
ch='4' -> not '0' -> chars = ['1','5','5','4']
''.join(chars) = "1554"
int("1554") = 1554
```

### Complexity

- **Time: O(d)** — one pass to build the char list, one pass (internally) to join.
- **Space: O(d)** — the `chars` list and the final joined string, both proportional to digit count. Strictly better in *constant factor* than the brute force's `.replace()` version only in the sense that we now control exactly one buffer growth pattern (amortized doubling) instead of depending on an opaque library call — pedagogically this section exists to demonstrate the O(d) vs O(d²) trap, not to beat brute force's asymptotic class (they're the same, O(d)).

---

## 6. Optimal Approach — Pure Arithmetic (No String Conversion)

### Idea

Avoid string conversion entirely. Extract digits from `N` using repeated `% 10` (get last digit) and `/ 10` (drop last digit), replacing `0` with `5` as each digit is extracted, and rebuild the result number using place-value accumulation.

Because `% 10` / `/ 10` extraction yields digits in **reverse order** (least significant digit first), we must rebuild carefully. Two clean ways to do this:

**Method A — build reversed, then re-reverse the digit sequence at the end.**
**Method B — build using increasing place value (multiply the extracted digit by the correct power of 10) — avoids needing a second reversal pass.**

Below is Method B, which needs only one pass plus a final combine, and is the more elegant "pure arithmetic" solution.

### Python Code

```python
class Solution:
    def replaceZerosOptimal(self, n: int) -> int:
        # Handle the edge case where n is a single digit 0
        if n == 0:
            # Directly return 5 since the while loop below would never execute
            return 5

        # Initialize place value (10^0, 10^1, ...) for the digit currently extracted
        place = 1

        # Initialize the accumulator for the rebuilt result
        result = 0

        # Copy n into temp so we can destroy it during extraction
        temp = n

        # Loop until all digits have been extracted from temp
        while temp > 0:
            # Extract the least-significant digit of temp
            digit = temp % 10

            # Check if the extracted digit is zero
            if digit == 0:
                # Replace the zero digit with five
                digit = 5

            # Place the digit at its correct position in the result
            result += digit * place

            # Move the place value up by one power of ten for the next digit
            place *= 10

            # Drop the least-significant digit from temp
            temp //= 10

        # Return the fully rebuilt number
        return result
```

### Step-by-Step Trace (N = 1004)

```
Initial: temp=1004, place=1, result=0

Iter 1: digit = 1004 % 10 = 4   (not 0, keep 4)
        result = 0 + 4*1   = 4
        place = 10
        temp  = 1004 // 10 = 100

Iter 2: digit = 100 % 10 = 0    (is 0 -> becomes 5)
        result = 4 + 5*10  = 54
        place = 100
        temp  = 100 // 10 = 10

Iter 3: digit = 10 % 10 = 0     (is 0 -> becomes 5)
        result = 54 + 5*100 = 554
        place = 1000
        temp  = 10 // 10 = 1

Iter 4: digit = 1 % 10 = 1      (not 0, keep 1)
        result = 554 + 1*1000 = 1554
        place = 10000
        temp  = 1 // 10 = 0     -> loop ends

Final result = 1554
```

This matches the brute-force output, confirming correctness, with **zero string allocation**.

### Complexity

- **Time: O(d)**, where `d` = number of digits = `O(log10 N)`. Each loop iteration strips one digit via integer division, so the loop runs exactly `d` times. Since `d = floor(log10 N) + 1`, we commonly state this as **O(log N)** — the number of digits grows logarithmically with the magnitude of N.

- **Space: O(1) extra**, excluding the output itself. We only maintain a constant number of scalar variables (`place`, `result`, `temp`, `digit`) regardless of how many digits `N` has — no string buffer, no character list, no intermediate array. This is a genuine space improvement over both prior approaches (O(d) → O(1) auxiliary space), even though the **time complexity class is identical (O(d) in all three approaches)**.

- **Why this matters beyond the whiteboard:** in memory-constrained or embedded environments (microcontrollers, firmware, high-frequency systems where allocations trigger GC pauses or heap fragmentation), avoiding any heap allocation — as this approach does — is a meaningful practical win even when Big-O doesn't distinguish the approaches. It also avoids the overhead of string<->int conversion routines (locale handling, buffer allocation, parsing) that real string libraries carry, which are not "free" even though we abstract them as O(d).

---

## 7. Edge Cases

| Case | Input | Output | Notes |
|---|---|---|---|
| Single digit zero | `N = 0` | `5` | Must be special-cased in the arithmetic approach since the `while temp > 0` loop never executes for `temp = 0`; string approach handles it naturally via `str(0) = "0"`. |
| All digits are zero | `N = 1000` | `1555` | Only the leading `1` is non-zero; the three trailing zeros all become `5`. (Note: `1000 -> 1555`, not `1555...` — exactly one digit per position, no digit count change.) |
| No zero digits | `N = 5529` | `5529` | Unchanged — no zeros to replace. |
| Single non-zero digit | `N = 7` | `7` | Loop runs once, digit stays 7. |
| Large N near type limit | `N = 999999999` (near `int32` max region) | `999999999` | No zeros, but demonstrates the type must hold `N` itself comfortably; for constraints up to `10^18`, use 64-bit (`long long`/`long`) or Python's native big int. |
| "Leading zero" concern | N/A | N/A | Since `N` is supplied as an integer (not a string with formatting), it cannot have a leading zero by definition (`007` is not a valid integer literal/value — it's just `7`). Leading-zero handling only becomes a real concern if the problem instead supplies `N` as a **string** (e.g., preserving a fixed-width serial number); the arithmetic approach implicitly cannot represent or preserve leading zeros, which is a good reason to ask the interviewer whether input is numeric or string-formatted. |

---

## 8. Interview Follow-ups

1. **"Replace 0 with 5 across an array of numbers instead of a single number?"**
   Apply the single-number transformation to each element independently: `O(n * d_avg)` total, where `n` is array length and `d_avg` is average digit count per element. This is the natural "Arrays" framing the problem's topic tag suggests — worth raising proactively since the given problem is really scalar.

2. **"Generalize to replace an arbitrary digit X with digit Y."**
   Trivial parameterization: in the arithmetic approach, change the condition `if digit == 0: digit = 5` to `if digit == X: digit = Y`. Works identically for any `0 <= X, Y <= 9`. Ask whether `X == Y` should short-circuit (no-op) as a micro-optimization.

3. **"Do it without converting to string at all — pure arithmetic — how?"**
   This is exactly Section 6's Optimal Approach — extract via `% 10` / `// 10`, rebuild via place-value accumulation (`result += digit * place; place *= 10`). Be ready to also present the "build reversed then reverse the digit list" alternative (Method A) and explain the tradeoff: Method A needs an explicit reversal step (or a list to hold digits before combining), Method B avoids that by tracking increasing place value directly — Method B is preferable when no intermediate storage is desired.

4. **"Handle negative numbers — where does the sign go?"**
   The base problem states `N >= 0`, but if negatives are allowed: extract and remember the sign first (`sign = -1 if n < 0 else 1`), take `abs(n)` for digit processing, run the same digit-replacement logic on the magnitude, and reapply the sign to the final result (`return sign * result`). The sign character itself is never a "digit" and must never be scanned for `'0'`/replaced.

5. **"What if N is given as a string to support arbitrarily large numbers beyond 64-bit range?"**
   Then the string-based approaches (Sections 4 and 5) become the *only* viable options — the arithmetic approach depends on `N` fitting in a fixed-width (or big-int-native) numeric type to do `% 10` / `// 10`. In that case, prefer the list-and-join "Better" approach over `.replace()` if you want to demonstrate manual control, but functionally `.replace('0','5')` on the string is both correct and optimal at O(d) time / O(d) space in that regime — there's no way around O(d) space when the answer itself must be materialized as a string of length d.

---

## 9. Interview Explanation Tips

- **Open by immediately flagging the mislabel.** State clearly: "Although this is filed under Arrays, it's actually a digit-manipulation problem on a single integer — I'll treat it as iterating over digits, not array elements." This shows you read the problem carefully rather than pattern-matching on the topic tag.

- **Narrate the three-tier progression out loud**, the way this document is structured: start with the honest brute force (string convert + replace) to show you can produce a correct answer immediately, then flag the O(d²) trap of naive string concatenation as a *deliberate teaching detour* ("if I did this character-by-character with `+=` in a loop, that would silently degrade to O(d²) — here's why, and here's the list+join fix"), then arrive at the arithmetic-only optimal solution.

- **Explicitly state the space tradeoff**, because time complexity is identical (O(d)) across all three approaches — the differentiator is **space and constant factors**, not asymptotic time:
  - String-based: more readable, leans on well-tested library functions, costs O(d) auxiliary space (possibly several intermediate string allocations).
  - Arithmetic-based: O(1) auxiliary space, no allocation, but marginally less readable and requires careful handling of digit order (place-value reconstruction) and the `N == 0` edge case.

- **Connect this pattern to the broader family of digit-manipulation problems** — reversing a number, checking palindromic numbers, summing digits, counting digits, checking Armstrong numbers, converting a number to its digit array, digit DP problems — all share the same `% 10` / `// 10` extraction skeleton. Mentioning this shows the interviewer you recognize this as a **template**, not a one-off trick, which is exactly the kind of transferable insight interviewers are listening for.

- **Close by proactively raising the negative-number and array-of-numbers follow-ups yourself** if time allows — it demonstrates you're already thinking about how the core technique generalizes, rather than waiting to be asked.
