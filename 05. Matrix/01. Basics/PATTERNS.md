# Matrix — Basics: Patterns

Basics-level Matrix problems (10) are nested-loop warm-ups: sum or compare cells, add and multiply matrices, and swap mirrored triangles. They build the habit of thinking in `(i, j)` coordinates before the traversal problems.

## Pattern 1: Row / Column / Diagonal Aggregation

The base matrix move: two nested loops, with an accumulator per row, per column, or per diagonal. Sum all cells, sum the main and anti diagonals (`i == j`, `i + j == n - 1`), or sum the upper and lower triangles (`j >= i`, `j <= i`). Add or compare two matrices cell by cell. Per-line checks fit the same frame: count rows that are sorted, find the row with the fewest 1s or the column with the most 0s, or test whether some row or column is a palindrome. No extra memory is needed beyond a few counters.

| # | Problem | Link |
|---|---|---|
| 1 | [Sum of Matrix](https://www.geeksforgeeks.org/problems/sum-of-elements-in-a-matrix2000/1) | [`02. Sum of Matrix/`](02.%20Sum%20of%20Matrix/) |
| 2 | [Diagonal Sum in Matrix](https://www.geeksforgeeks.org/problems/diagonal-sum0158/1) | [`03. Diagonal Sum in Matrix/`](03.%20Diagonal%20Sum%20in%20Matrix/) |
| 3 | [Add of 2 Square Matrices](https://www.geeksforgeeks.org/problems/addition-of-two-square-matrices4916/1) | [`05. Add of 2 Square Matrices/`](05.%20Add%20of%202%20Square%20Matrices/) |
| 4 | [Sums of i-th row and i-th column](https://www.geeksforgeeks.org/problems/sums-of-i-th-row-and-i-th-column3054/1) | [`06. Sums of i-th row and i-th column/`](06.%20Sums%20of%20i-th%20row%20and%20i-th%20column/) |
| 5 | [Check Identical Matrices](https://www.geeksforgeeks.org/problems/identical-matrices1042/1) | [`07. Check Identical Matrices/`](07.%20Check%20Identical%20Matrices/) |
| 6 | [Count Sorted Rows](https://www.geeksforgeeks.org/problems/count-sorted-rows2702/1) | [`09. Count Sorted Rows/`](09.%20Count%20Sorted%20Rows/) |

## Pattern 2: In-Place Transform (Transpose / Reverse / Rotate / Reshape)

Most layout changes are a fixed mapping from old to new coordinates. Transpose swaps `a[i][j]` with `a[j][i]` above the diagonal. Reversing each row, or the order of rows, mirrors the matrix. A 90-degree rotation is a transpose followed by a reverse, and a 180-degree rotation is a reverse of rows plus a reverse of columns. Rotating each row by k uses `k mod m`. Swapping triangles, diagonals, or middle blocks is a swap of mirrored indices. Sorting a matrix flattens it, sorts, and refills row by row. When many row and column swaps arrive as queries, keep row and column permutation arrays instead of moving data.

| # | Problem | Link |
|---|---|---|
| 1 | [Sort a Matrix](https://www.geeksforgeeks.org/problems/sorted-matrix2333/1) | [`01. Sort a Matrix/`](01.%20Sort%20a%20Matrix/) |
| 2 | [Swapping Triangles in Matrix](https://www.geeksforgeeks.org/problems/swapping-triangles5209/1) | [`10. Swapping Triangles in Matrix/`](10.%20Swapping%20Triangles%20in%20Matrix/) |

## Pattern 3: Matrix Multiplication, Determinant & Fast Power

Product `C[i][j] = sum(A[i][k] * B[k][j])` needs the inner dimensions to match. The Kronecker product places a scaled copy of B at each cell of A. A determinant comes from cofactor expansion on small inputs or Gaussian elimination on larger ones. Powers of a matrix use binary exponentiation: square the base and multiply it in when the current bit of the exponent is set. Linear recurrences such as a generalised Fibonacci are solved by raising a small transition matrix to the n-th power under a modulus.

| # | Problem | Link |
|---|---|---|
| 1 | [Multiply Two Matrices](https://www.geeksforgeeks.org/problems/multiply-matrices/1) | [`04. Multiply Two Matrices/`](04.%20Multiply%20Two%20Matrices/) |

## Pattern 4: Index Formulas & Counting

The matrix is implied, not stored. Squares in an n×m grid sum `(n - k + 1)(m - k + 1)` over each size k. Summed Matrix counts cells with `i + j = q` in an n×n grid by reasoning about the range of valid i. Grid colouring and tiling questions compare against the two checkerboard patterns or reduce to modular arithmetic over the dimensions.

| # | Problem | Link |
|---|---|---|
| 1 | [Squares in Matrix](https://www.geeksforgeeks.org/problems/squares-in-a-matrix5716/1) | [`08. Squares in Matrix/`](08.%20Squares%20in%20Matrix/) |
