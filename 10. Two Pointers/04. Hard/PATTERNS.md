# Two Pointers — Hard: Patterns

The Hard-level Two Pointers problem (1) combines prefix sums with several pointers that each move only forward, so a multi-way split stays linear.

## Pattern 1: Multiple Split Pointers with Prefix Sums

Split an array into several contiguous parts with balanced sums. Build prefix sums, loop over the middle cut, and keep one pointer for the best cut in the left half and one for the right half. Both pointers only move forward as the middle moves, so the total work stays linear.

| # | Problem | Link |
|---|---|---|
| 1 | [Partition Into 4 with Min Sum Diff](https://www.geeksforgeeks.org/problems/partition-the-array--170647/1) | [`01. Partition Into 4 with Min Sum Diff/`](01.%20Partition%20Into%204%20with%20Min%20Sum%20Diff/) |
