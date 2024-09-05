## Problem

Given an `m x n` integer matrix `matrix`, if an element is `0`, set its entire row and column to `0`s. You must do this in-place.

For more details on the problem, visit the [LeetCode Problem Link](https://leetcode.com/problems/set-matrix-zeroes/).

## Explanation

In this approach, we use the first row and first column of the matrix as markers to represent which rows and columns should be set to zero. We also use a variable `col0` to keep track of whether the first column itself needs to be set to zero.

Here’s a step-by-step breakdown:

1. **Mark Rows and Columns:**
   - Traverse the matrix. Whenever a `0` is found, mark the corresponding row and column in the first row and first column.
   - Specifically, set `matrix[i][0]` to `0` for rows, and `matrix[0][j]` to `0` for columns. 
   - Special handling is done for the first column to keep track if it needs to be zeroed.

2. **Set Zeroes for Internal Elements:**
   - Iterate through the matrix (excluding the first row and first column).
   - For each element, check if its corresponding row or column is marked to be zero. If so, set the element to `0`.

3. **Zero Out First Row and Column:**
   - If `matrix[0][0]` is `0`, zero out the entire first row.
   - If `col0` indicates that the first column needs to be zeroed, zero out the entire first column.

### Code

```cpp
for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        if (matrix[i][j] == 0) {
            matrix[i][0] = 0;
            if (j != 0)
                matrix[0][j] = 0;
            else
                col0 = 0;
        }
    }
}

for (int i = 1; i < n; i++) {
    for (int j = 1; j < m; j++) {
        if (matrix[i][j] != 0) {
            if (matrix[i][0] == 0 || matrix[0][j] == 0) {
                matrix[i][j] = 0;
            }
        }
    }
}

if (matrix[0][0] == 0) {
    for (int j = 0; j < m; j++) {
        matrix[0][j] = 0;
    }
}
if (col0 == 0) {
    for (int i = 0; i < n; i++) {
        matrix[i][0] = 0;
    }
}
```

- **Time Complexity:** O(m * n) – Each element is processed a constant number of times.
- **Space Complexity:** O(1) – The solution uses constant extra space.
