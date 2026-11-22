# Matrix — Hard: Patterns

Hard-level Matrix problems (3) each push one Medium pattern further: matrix fast power for linear recurrences, BFS with an extra state dimension, and column-height tables sorted per row for the largest rectangle.

## Pattern 1: Matrix Multiplication, Determinant & Fast Power

Product `C[i][j] = sum(A[i][k] * B[k][j])` needs the inner dimensions to match. The Kronecker product places a scaled copy of B at each cell of A. A determinant comes from cofactor expansion on small inputs or Gaussian elimination on larger ones. Powers of a matrix use binary exponentiation: square the base and multiply it in when the current bit of the exponent is set. Linear recurrences such as a generalised Fibonacci are solved by raising a small transition matrix to the n-th power under a modulus.

| # | Problem | Link |
|---|---|---|
| 1 | [Generalised Fibonacci Nnumbers](https://www.geeksforgeeks.org/problems/generalised-fibonacci-numbers1820/1) | [`01. Generalised Fibonacci Nnumbers/`](01.%20Generalised%20Fibonacci%20Nnumbers/) |

## Pattern 2: Precomputed Sums & Runs for Sub-Matrices

Sub-matrix questions become fast once the right table exists. A 2D prefix sum `P[i][j]` gives any rectangle sum by inclusion-exclusion, which solves the max k×k square sum. The hourglass is a fixed shape summed at every centre. For the largest square bordered by X, store the length of the run of X to the left and above each cell, then test each candidate size. Rectangle with 1-corners records each pair of columns that are both 1 in a row and stops at the first repeat. Largest rectangle with column swaps builds heights of consecutive 1s and sorts each row of heights in descending order.

| # | Problem | Link |
|---|---|---|
| 1 | [Largest Rectangle with Column Swaps](https://www.geeksforgeeks.org/problems/find-the-largest-rectangle-of-1s-with-swapping-of-columns-allowed0243/1) | [`03. Largest Rectangle with Column Swaps/`](03.%20Largest%20Rectangle%20with%20Column%20Swaps/) |

## Pattern 3: Graph Search on Grid (DFS / BFS)

When the answer depends on paths, not just neighbours, run a graph search. Word search starts DFS from every cell that matches the first letter and backtracks in all directions. Towers Reaching Both Stations runs DFS inward from each border and keeps cells reached by both. Palindromic paths explore right/down paths and check or count palindromes. Shortest path with up to k wall removals is BFS where the state is `(row, col, removals used)`.

| # | Problem | Link |
|---|---|---|
| 1 | [Shortest Path by Removing K walls](https://www.geeksforgeeks.org/problems/shortest-path-by-removing-k-walls/1) | [`02. Shortest Path by Removing K walls/`](02.%20Shortest%20Path%20by%20Removing%20K%20walls/) |
