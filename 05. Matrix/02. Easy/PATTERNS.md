# Matrix — Easy: Patterns

These are the recurring patterns across the 30 Easy-level Matrix problems. Most are per-line aggregation or a fixed index transform (transpose, reverse, swap), with neighbour scans, diagonal orders, and the first spiral and simulation problems as the other families.

## Pattern 1: Row / Column / Diagonal Aggregation

The base matrix move: two nested loops, with an accumulator per row, per column, or per diagonal. Sum all cells, sum the main and anti diagonals (`i == j`, `i + j == n - 1`), or sum the upper and lower triangles (`j >= i`, `j <= i`). Add or compare two matrices cell by cell. Per-line checks fit the same frame: count rows that are sorted, find the row with the fewest 1s or the column with the most 0s, or test whether some row or column is a palindrome. No extra memory is needed beyond a few counters.

| # | Problem | Link |
|---|---|---|
| 1 | [Row with Minimum 1s](https://www.geeksforgeeks.org/problems/row-with-minimum-number-of-1s5430/1) | [`04. Row with Minimum 1s/`](04.%20Row%20with%20Minimum%201s/) |
| 2 | [Column with Max 0s](https://www.geeksforgeeks.org/problems/predict-the-column/1) | [`06. Column with Max 0s/`](06.%20Column%20with%20Max%200s/) |
| 3 | [Sum of upper and lower triangles](https://www.geeksforgeeks.org/problems/sum-of-upper-and-lower-triangles-1587115621/1) | [`07. Sum of upper and lower triangles/`](07.%20Sum%20of%20upper%20and%20lower%20triangles/) |
| 4 | [Row or Column Palindrome](https://www.geeksforgeeks.org/problems/the-palindrome-pattern3900/1) | [`15. Row or Column Palindrome/`](15.%20Row%20or%20Column%20Palindrome/) |
| 5 | [Row Sum in a Matrix](https://www.geeksforgeeks.org/problems/row-sum-in-a-matrix/1) | [`20. Row Sum in a Matrix/`](20.%20Row%20Sum%20in%20a%20Matrix/) |
| 6 | [Column Sum in a Matrix](https://www.geeksforgeeks.org/problems/column-sum-in-a-matrix/1) | [`21. Column Sum in a Matrix/`](21.%20Column%20Sum%20in%20a%20Matrix/) |
| 7 | [Diagonal in a 2D Numpy Array](https://www.geeksforgeeks.org/problems/find-diagonal-elements-in-a-2d-numpy-array/1) | [`29. Diagonal in a 2D Numpy Array/`](29.%20Diagonal%20in%20a%202D%20Numpy%20Array/) |

## Pattern 2: In-Place Transform (Transpose / Reverse / Rotate / Reshape)

Most layout changes are a fixed mapping from old to new coordinates. Transpose swaps `a[i][j]` with `a[j][i]` above the diagonal. Reversing each row, or the order of rows, mirrors the matrix. A 90-degree rotation is a transpose followed by a reverse, and a 180-degree rotation is a reverse of rows plus a reverse of columns. Rotating each row by k uses `k mod m`. Swapping triangles, diagonals, or middle blocks is a swap of mirrored indices. Sorting a matrix flattens it, sorts, and refills row by row. When many row and column swaps arrive as queries, keep row and column permutation arrays instead of moving data.

| # | Problem | Link |
|---|---|---|
| 1 | [Transpose of Matrix](https://www.geeksforgeeks.org/problems/transpose-of-matrix-1587115621/1) | [`01. Transpose of Matrix/`](01.%20Transpose%20of%20Matrix/) |
| 2 | [Reversing the columns of a Matrix](https://www.geeksforgeeks.org/problems/reversing-the-columns-of-a-matrix-1587115621/1) | [`17. Reversing the columns of a Matrix/`](17.%20Reversing%20the%20columns%20of%20a%20Matrix/) |
| 3 | [Reverse Order of Rows of a Matrix](https://www.geeksforgeeks.org/problems/reversing-the-rows-of-a-matrix-1587115621/1) | [`18. Reverse Order of Rows of a Matrix/`](18.%20Reverse%20Order%20of%20Rows%20of%20a%20Matrix/) |
| 4 | [Swap  diagonals](https://www.geeksforgeeks.org/problems/swap-major-and-minor-diagonals-of-a-square-matrix/1) | [`22. Swap diagonals/`](22.%20Swap%20diagonals/) |
| 5 | [Middle Swap in 4x4 Grid](https://www.geeksforgeeks.org/problems/middle-swap/1) | [`24. Middle Swap in 4x4 Grid/`](24.%20Middle%20Swap%20in%204x4%20Grid/) |
| 6 | [Create a 3D Array from a List of Lists](https://www.geeksforgeeks.org/problems/create-a-3d-array-from-a-list-of-lists/1) | [`26. Create a 3D Array from a List of Lists/`](26.%20Create%20a%203D%20Array%20from%20a%20List%20of%20Lists/) |
| 7 | [Matrix Transpose in NumPy](https://www.geeksforgeeks.org/problems/transpose-of-a-matrix/1) | [`28. Matrix Transpose in NumPy/`](28.%20Matrix%20Transpose%20in%20NumPy/) |

## Pattern 3: Matrix Multiplication, Determinant & Fast Power

Product `C[i][j] = sum(A[i][k] * B[k][j])` needs the inner dimensions to match. The Kronecker product places a scaled copy of B at each cell of A. A determinant comes from cofactor expansion on small inputs or Gaussian elimination on larger ones. Powers of a matrix use binary exponentiation: square the base and multiply it in when the current bit of the exponent is set. Linear recurrences such as a generalised Fibonacci are solved by raising a small transition matrix to the n-th power under a modulus.

| # | Problem | Link |
|---|---|---|
| 1 | [Kronecker Product](https://www.geeksforgeeks.org/problems/kronecker-product0918/1) | [`27. Kronecker Product/`](27.%20Kronecker%20Product/) |
| 2 | [Matrix Multiplication](https://www.geeksforgeeks.org/problems/matrix-multiplication--132654/1) | [`30. Matrix Multiplication/`](30.%20Matrix%20Multiplication/) |

## Pattern 4: Layer-by-Layer Traversal (Boundary / Spiral)

Spiral and boundary problems peel the matrix like an onion. Walk the top row left to right, the right column top to bottom, the bottom row right to left, and the left column bottom to top. Then move each bound one step inward. Guard the last row or column so it is not visited twice. The same loop prints the boundary only, gives the k-th spiral element, builds a spiral matrix from an array, reverses the spiral order, splits the matrix into coils, or shifts each ring one step to rotate clockwise by one.

| # | Problem | Link |
|---|---|---|
| 1 | [Matrix Boundary Traversal](https://www.geeksforgeeks.org/problems/boundary-traversal-of-matrix-1587115620/1) | [`02. Matrix Boundary Traversal/`](02.%20Matrix%20Boundary%20Traversal/) |

## Pattern 5: Neighbour Scan with Direction Arrays

Many grid rules depend only on the cells next to the current one. Store the offsets in `dr` and `dc` arrays and skip any neighbour outside the grid. Count zeros around each 1, count 1s next to each 0, add exposed sides to get a perimeter, or sum the cells at distance 1 or 2 from a query point (including the hex-grid neighbours in 2D Hopscotch). When updates must use the old state, as in Game of Life or zero-processing, write to a copy or encode the old and new state in the same cell.

| # | Problem | Link |
|---|---|---|
| 1 | [Count 1s Surrounded by Even  0s](https://www.geeksforgeeks.org/problems/surround-the-1s2505/1) | [`11. Count 1s Surrounded by Even 0s/`](11.%20Count%201s%20Surrounded%20by%20Even%200s/) |
| 2 | [Coverage of all Zeros in a Binary Matrix](https://www.geeksforgeeks.org/problems/coverage-of-all-zeros-in-a-binary-matrix4024/1) | [`12. Coverage of all Zeros in a Binary Matrix/`](12.%20Coverage%20of%20all%20Zeros%20in%20a%20Binary%20Matrix/) |
| 3 | [Letters Collection](https://www.geeksforgeeks.org/problems/c-letters-collection4552/1) | [`13. Letters Collection/`](13.%20Letters%20Collection/) |
| 4 | [Process Zeros and Neighbors in Grid](https://www.geeksforgeeks.org/problems/make-zeroes4042/1) | [`16. Process Zeros and Neighbors in Grid/`](16.%20Process%20Zeros%20and%20Neighbors%20in%20Grid/) |
| 5 | [Perimeter of Shapes in Binary Matrix](https://www.geeksforgeeks.org/problems/find-perimeter-of-shapes/1) | [`25. Perimeter of Shapes in Binary Matrix/`](25.%20Perimeter%20of%20Shapes%20in%20Binary%20Matrix/) |

## Pattern 6: Binary Search on Sorted Matrix

If every row is sorted, binary search each row. If the whole matrix is sorted row after row, map a flat index `k` to `(k / m, k % m)` and run one binary search, including the rotated version and counting occurrences with two bounds. In a sorted binary matrix, start at the top-right and step left or down to find the row with the most 1s. For the median, binary search on the value and count elements `<= mid` with upper bound in each row. A 2D peak picks the middle column, takes its maximum, and moves toward a larger neighbour.

| # | Problem | Link |
|---|---|---|
| 1 | [Search in a row-wise sorted matrix](https://www.geeksforgeeks.org/problems/search-in-a-row-wise-sorted-matrix/1) | [`10. Search in a row-wise sorted matrix/`](10.%20Search%20in%20a%20row-wise%20sorted%20matrix/) |

## Pattern 7: Index Formulas & Counting

The matrix is implied, not stored. Squares in an n×m grid sum `(n - k + 1)(m - k + 1)` over each size k. Summed Matrix counts cells with `i + j = q` in an n×n grid by reasoning about the range of valid i. Grid colouring and tiling questions compare against the two checkerboard patterns or reduce to modular arithmetic over the dimensions.

| # | Problem | Link |
|---|---|---|
| 1 | [Summed Matrix](https://www.geeksforgeeks.org/problems/summed-matrix5834/1) | [`08. Summed Matrix/`](08.%20Summed%20Matrix/) |
| 2 | [Min Swaps in a Grid to Make Adjacent Different](https://www.geeksforgeeks.org/problems/distributing-question-papers2513/1) | [`19. Min Swaps in a Grid to Make Adjacent Different/`](19.%20Min%20Swaps%20in%20a%20Grid%20to%20Make%20Adjacent%20Different/) |

## Pattern 8: Snake / Diagonal / Zigzag Order

Cells on the same anti-diagonal share `i + j`, and cells on the same diagonal share `i - j`. Print diagonally by looping over each sum and stepping down-left. Zigzag diagonal traversal flips the direction on alternate diagonals. Toeplitz checks that every cell equals its upper-left neighbour. The snake pattern prints even rows left to right and odd rows right to left.

| # | Problem | Link |
|---|---|---|
| 1 | [Matrix Snake Pattern](https://www.geeksforgeeks.org/problems/print-matrix-in-snake-pattern-1587115621/1) | [`03. Matrix Snake Pattern/`](03.%20Matrix%20Snake%20Pattern/) |
| 2 | [Print Diagonally](https://www.geeksforgeeks.org/problems/print-diagonally4331/1) | [`05. Print Diagonally/`](05.%20Print%20Diagonally/) |
| 3 | [Toeplitz Matrix](https://www.geeksforgeeks.org/problems/toeplitz-matrix/1) | [`09. Toeplitz Matrix/`](09.%20Toeplitz%20Matrix/) |

## Pattern 9: Direction / Path Simulation

Simulate the walk exactly. Exit Point moves in the current direction, turns right on a 1 and clears it, and stops when the next step leaves the grid. Trace Path applies each move and checks that some start cell keeps the robot inside. Minimum moves to type a string maps each letter to its keypad coordinates and adds the row and column distance between consecutive letters.

| # | Problem | Link |
|---|---|---|
| 1 | [Trace Path](https://www.geeksforgeeks.org/problems/trace-path3840/1) | [`14. Trace Path/`](14.%20Trace%20Path/) |
| 2 | [Minimum Moves to Type a String](https://www.geeksforgeeks.org/problems/primitive-typing5427/1) | [`23. Minimum Moves to Type a String/`](23.%20Minimum%20Moves%20to%20Type%20a%20String/) |
