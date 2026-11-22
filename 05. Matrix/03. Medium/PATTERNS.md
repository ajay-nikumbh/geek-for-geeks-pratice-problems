# Matrix — Medium: Patterns

Medium-level Matrix problems (36) add structure: spiral traversal by layers, rotation in place, binary search on sorted matrices, 2D prefix sums for sub-matrix queries, row/column bookkeeping for validation, and DFS on the grid.

## Pattern 1: In-Place Transform (Transpose / Reverse / Rotate / Reshape)

Most layout changes are a fixed mapping from old to new coordinates. Transpose swaps `a[i][j]` with `a[j][i]` above the diagonal. Reversing each row, or the order of rows, mirrors the matrix. A 90-degree rotation is a transpose followed by a reverse, and a 180-degree rotation is a reverse of rows plus a reverse of columns. Rotating each row by k uses `k mod m`. Swapping triangles, diagonals, or middle blocks is a swap of mirrored indices. Sorting a matrix flattens it, sorts, and refills row by row. When many row and column swaps arrive as queries, keep row and column permutation arrays instead of moving data.

| # | Problem | Link |
|---|---|---|
| 1 | [Rotate by 90 degree](https://www.geeksforgeeks.org/problems/rotate-by-90-degree-1587115621/1) | [`03. Rotate by 90 degree/`](03.%20Rotate%20by%2090%20degree/) |
| 2 | [Rotate Each Row of Matrix K Times](https://www.geeksforgeeks.org/problems/left-rotate-matrix-k-times2351/1) | [`11. Rotate Each Row of Matrix K Times/`](11.%20Rotate%20Each%20Row%20of%20Matrix%20K%20Times/) |
| 3 | [Rotate a Matrix by 180 Counterclockwise](https://www.geeksforgeeks.org/problems/c-matrix-rotation-by-180-degree0745/1) | [`20. Rotate a Matrix by 180 Counterclockwise/`](20.%20Rotate%20a%20Matrix%20by%20180%20Counterclockwise/) |
| 4 | [Matrix Row-Column Swaps](https://www.geeksforgeeks.org/problems/matrix-row-column-swaps/1) | [`35. Matrix Row-Column Swaps/`](35.%20Matrix%20Row-Column%20Swaps/) |

## Pattern 2: Matrix Multiplication, Determinant & Fast Power

Product `C[i][j] = sum(A[i][k] * B[k][j])` needs the inner dimensions to match. The Kronecker product places a scaled copy of B at each cell of A. A determinant comes from cofactor expansion on small inputs or Gaussian elimination on larger ones. Powers of a matrix use binary exponentiation: square the base and multiply it in when the current bit of the exponent is set. Linear recurrences such as a generalised Fibonacci are solved by raising a small transition matrix to the n-th power under a modulus.

| # | Problem | Link |
|---|---|---|
| 1 | [Determinant of a Matrix](https://www.geeksforgeeks.org/problems/determinant-of-a-matrix-1587115620/1) | [`10. Determinant of a Matrix/`](10.%20Determinant%20of%20a%20Matrix/) |
| 2 | [Power of a 2 x 2 Binary Matrix](https://www.geeksforgeeks.org/problems/rohans-love-for-matrix4723/1) | [`13. Power of a 2 x 2 Binary Matrix/`](13.%20Power%20of%20a%202%20x%202%20Binary%20Matrix/) |
| 3 | [Multiply 2 Matrices](https://www.geeksforgeeks.org/problems/multiply-2-matrices4144/1) | [`18. Multiply 2 Matrices/`](18.%20Multiply%202%20Matrices/) |

## Pattern 3: Layer-by-Layer Traversal (Boundary / Spiral)

Spiral and boundary problems peel the matrix like an onion. Walk the top row left to right, the right column top to bottom, the bottom row right to left, and the left column bottom to top. Then move each bound one step inward. Guard the last row or column so it is not visited twice. The same loop prints the boundary only, gives the k-th spiral element, builds a spiral matrix from an array, reverses the spiral order, splits the matrix into coils, or shifts each ring one step to rotate clockwise by one.

| # | Problem | Link |
|---|---|---|
| 1 | [Spirally Traversing a Matrix](https://www.geeksforgeeks.org/problems/spirally-traversing-a-matrix-1587115621/1) | [`02. Spirally Traversing a Matrix/`](02.%20Spirally%20Traversing%20a%20Matrix/) |
| 2 | [Kth of spiral matrix](https://www.geeksforgeeks.org/problems/find-nth-element-of-spiral-matrix/1) | [`09. Kth of spiral matrix/`](09.%20Kth%20of%20spiral%20matrix/) |
| 3 | [Reverse Spiral Form of Matrix](https://www.geeksforgeeks.org/problems/reverse-spiral-form-of-matrix4033/1) | [`24. Reverse Spiral Form of Matrix/`](24.%20Reverse%20Spiral%20Form%20of%20Matrix/) |
| 4 | [Rotate Matrix Clockwise by One](https://www.geeksforgeeks.org/problems/rotate-matrix-elements-clockwise2336/1) | [`28. Rotate Matrix Clockwise by One/`](28.%20Rotate%20Matrix%20Clockwise%20by%20One/) |
| 5 | [Coils in a Matrix](https://www.geeksforgeeks.org/problems/form-coils-in-a-matrix4726/1) | [`31. Coils in a Matrix/`](31.%20Coils%20in%20a%20Matrix/) |
| 6 | [Create a spiral matrix of N*M size from given array](https://www.geeksforgeeks.org/problems/create-a-spiral-matrix-of-nm-size-from-given-array/1) | [`32. Create a spiral matrix of NM size from given array/`](32.%20Create%20a%20spiral%20matrix%20of%20NM%20size%20from%20given%20array/) |

## Pattern 4: Neighbour Scan with Direction Arrays

Many grid rules depend only on the cells next to the current one. Store the offsets in `dr` and `dc` arrays and skip any neighbour outside the grid. Count zeros around each 1, count 1s next to each 0, add exposed sides to get a perimeter, or sum the cells at distance 1 or 2 from a query point (including the hex-grid neighbours in 2D Hopscotch). When updates must use the old state, as in Game of Life or zero-processing, write to a copy or encode the old and new state in the same cell.

| # | Problem | Link |
|---|---|---|
| 1 | [2D Hopscotch](https://www.geeksforgeeks.org/problems/hopscotch4857/1) | [`27. 2D Hopscotch/`](27.%202D%20Hopscotch/) |
| 2 | [Conway's Game Of Life](https://www.geeksforgeeks.org/problems/game-of-life/1) | [`36. Conway's Game Of Life/`](36.%20Conway's%20Game%20Of%20Life/) |

## Pattern 5: Binary Search on Sorted Matrix

If every row is sorted, binary search each row. If the whole matrix is sorted row after row, map a flat index `k` to `(k / m, k % m)` and run one binary search, including the rotated version and counting occurrences with two bounds. In a sorted binary matrix, start at the top-right and step left or down to find the row with the most 1s. For the median, binary search on the value and count elements `<= mid` with upper bound in each row. A 2D peak picks the middle column, takes its maximum, and moves toward a larger neighbour.

| # | Problem | Link |
|---|---|---|
| 1 | [Row with Max 1s in Rowwise Sorted](https://www.geeksforgeeks.org/problems/row-with-max-1s0023/1) | [`01. Row with Max 1s in Rowwise Sorted/`](01.%20Row%20with%20Max%201s%20in%20Rowwise%20Sorted/) |
| 2 | [Median in a Row-Wise Sorted Matrix](https://www.geeksforgeeks.org/problems/median-in-a-row-wise-sorted-matrix1527/1) | [`04. Median in a Row-Wise Sorted Matrix/`](04.%20Median%20in%20a%20Row-Wise%20Sorted%20Matrix/) |
| 3 | [Find the Peak Element in a 2D Matrix](https://www.geeksforgeeks.org/problems/find-the-peak-element-in-a-2d-matrix/1) | [`23. Find the Peak Element in a 2D Matrix/`](23.%20Find%20the%20Peak%20Element%20in%20a%202D%20Matrix/) |
| 4 | [Search in Fully Rotated Sorted 2D Matrix](https://www.geeksforgeeks.org/problems/search-in-fully-rotated-sorted-2d-matrix/1) | [`25. Search in Fully Rotated Sorted 2D Matrix/`](25.%20Search%20in%20Fully%20Rotated%20Sorted%202D%20Matrix/) |
| 5 | [Count Occurrences in a Fully Sorted Matrix](https://www.geeksforgeeks.org/problems/count-occurrences-in-a-fully-sorted-matrix/1) | [`33. Count Occurrences in a Fully Sorted Matrix/`](33.%20Count%20Occurrences%20in%20a%20Fully%20Sorted%20Matrix/) |

## Pattern 6: Precomputed Sums & Runs for Sub-Matrices

Sub-matrix questions become fast once the right table exists. A 2D prefix sum `P[i][j]` gives any rectangle sum by inclusion-exclusion, which solves the max k×k square sum. The hourglass is a fixed shape summed at every centre. For the largest square bordered by X, store the length of the run of X to the left and above each cell, then test each candidate size. Rectangle with 1-corners records each pair of columns that are both 1 in a row and stops at the first repeat. Largest rectangle with column swaps builds heights of consecutive 1s and sorts each row of heights in descending order.

| # | Problem | Link |
|---|---|---|
| 1 | [Largest Subsquare Surrounded by X](https://www.geeksforgeeks.org/problems/largest-subsquare-surrounded-by-x0558/1) | [`14. Largest Subsquare Surrounded by X/`](14.%20Largest%20Subsquare%20Surrounded%20by%20X/) |
| 2 | [Maximum Hourglass Sum](https://www.geeksforgeeks.org/problems/maximum-sum-of-hour-glass3842/1) | [`15. Maximum Hourglass Sum/`](15.%20Maximum%20Hourglass%20Sum/) |
| 3 | [Rectangle with Corners as 1 in Binary Matrix](https://www.geeksforgeeks.org/problems/find-rectangle-with-corners-as-1--141631/1) | [`19. Rectangle with Corners as 1 in Binary Matrix/`](19.%20Rectangle%20with%20Corners%20as%201%20in%20Binary%20Matrix/) |
| 4 | [Max Sum Square Sub-Matrix of Size k](https://www.geeksforgeeks.org/problems/coins-of-geekland--141631/1) | [`22. Max Sum Square Sub-Matrix of Size k/`](22.%20Max%20Sum%20Square%20Sub-Matrix%20of%20Size%20k/) |
| 5 | [Prefix Sum of Matrix (Or 2D Array)](https://www.geeksforgeeks.org/problems/prefix-sum-of-matrix-or-2d-array/1) | [`34. Prefix Sum of Matrix (Or 2D Array)/`](34.%20Prefix%20Sum%20of%20Matrix%20(Or%202D%20Array)/) |

## Pattern 7: Row / Column Bookkeeping & Validation

Some problems need a summary of each row and column before they can act. Boolean Matrix records which rows and columns contain a 1, then sets those lines. Sudoku validity keeps a seen-set for each row, column, and 3×3 box. A magic square compares every row, column, and diagonal sum to one target. Make Matrix Beautiful raises every line to the largest sum and counts the increments. Fill the Missing Cell derives the value from a complete row's sum and then checks all lines.

| # | Problem | Link |
|---|---|---|
| 1 | [Boolean Matrix](https://www.geeksforgeeks.org/problems/boolean-matrix-problem-1587115620/1) | [`05. Boolean Matrix/`](05.%20Boolean%20Matrix/) |
| 2 | [Make Matrix Beautiful](https://www.geeksforgeeks.org/problems/make-matrix-beautiful-1587115620/1) | [`07. Make Matrix Beautiful/`](07.%20Make%20Matrix%20Beautiful/) |
| 3 | [Is Sudoku Valid](https://www.geeksforgeeks.org/problems/is-sudoku-valid4820/1) | [`17. Is Sudoku Valid/`](17.%20Is%20Sudoku%20Valid/) |
| 4 | [Fill the Missing Cell to Balance](https://www.geeksforgeeks.org/problems/missing-number-in-matrix5316/1) | [`21. Fill the Missing Cell to Balance/`](21.%20Fill%20the%20Missing%20Cell%20to%20Balance/) |
| 5 | [Magic Square](https://www.geeksforgeeks.org/problems/magic-square/1) | [`29. Magic Square/`](29.%20Magic%20Square/) |

## Pattern 8: Graph Search on Grid (DFS / BFS)

When the answer depends on paths, not just neighbours, run a graph search. Word search starts DFS from every cell that matches the first letter and backtracks in all directions. Towers Reaching Both Stations runs DFS inward from each border and keeps cells reached by both. Palindromic paths explore right/down paths and check or count palindromes. Shortest path with up to k wall removals is BFS where the state is `(row, col, removals used)`.

| # | Problem | Link |
|---|---|---|
| 1 | [Word in Grid - All Occurrences](https://www.geeksforgeeks.org/problems/find-the-string-in-grid0111/1) | [`06. Word in Grid - All Occurrences/`](06.%20Word%20in%20Grid%20-%20All%20Occurrences/) |
| 2 | [Towers Reaching Both Stations](https://www.geeksforgeeks.org/problems/geeks-island--170646/1) | [`16. Towers Reaching Both Stations/`](16.%20Towers%20Reaching%20Both%20Stations/) |
| 3 | [Palindromic Paths in a Matrix](https://www.geeksforgeeks.org/problems/number-of-palindromic-paths-in-a-matrix0819/1) | [`30. Palindromic Paths in a Matrix/`](30.%20Palindromic%20Paths%20in%20a%20Matrix/) |

## Pattern 9: Index Formulas & Counting

The matrix is implied, not stored. Squares in an n×m grid sum `(n - k + 1)(m - k + 1)` over each size k. Summed Matrix counts cells with `i + j = q` in an n×n grid by reasoning about the range of valid i. Grid colouring and tiling questions compare against the two checkerboard patterns or reduce to modular arithmetic over the dimensions.

| # | Problem | Link |
|---|---|---|
| 1 | [Geek and Tiles](https://www.geeksforgeeks.org/problems/matrix-exponentiation2711/1) | [`26. Geek and Tiles/`](26.%20Geek%20and%20Tiles/) |

## Pattern 10: Snake / Diagonal / Zigzag Order

Cells on the same anti-diagonal share `i + j`, and cells on the same diagonal share `i - j`. Print diagonally by looping over each sum and stepping down-left. Zigzag diagonal traversal flips the direction on alternate diagonals. Toeplitz checks that every cell equals its upper-left neighbour. The snake pattern prints even rows left to right and odd rows right to left.

| # | Problem | Link |
|---|---|---|
| 1 | [Matrix Zig Zag Diagonal Traversal](https://www.geeksforgeeks.org/problems/print-matrix-in-diagonal-pattern/1) | [`12. Matrix Zig Zag Diagonal Traversal/`](12.%20Matrix%20Zig%20Zag%20Diagonal%20Traversal/) |

## Pattern 11: Direction / Path Simulation

Simulate the walk exactly. Exit Point moves in the current direction, turns right on a 1 and clears it, and stops when the next step leaves the grid. Trace Path applies each move and checks that some start cell keeps the robot inside. Minimum moves to type a string maps each letter to its keypad coordinates and adds the row and column distance between consecutive letters.

| # | Problem | Link |
|---|---|---|
| 1 | [Exit Point in a Matrix](https://www.geeksforgeeks.org/problems/exit-point-in-a-matrix0905/1) | [`08. Exit Point in a Matrix/`](08.%20Exit%20Point%20in%20a%20Matrix/) |
