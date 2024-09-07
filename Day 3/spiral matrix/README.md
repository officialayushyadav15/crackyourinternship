## Problem

Given an `m x n` matrix, return all elements of the matrix in **spiral order**.

For more details on the problem, visit the [LeetCode Problem Link](https://leetcode.com/problems/spiral-matrix/).

## Description
 **Iterate Until All Elements are Traversed:**
   - Use a `while` loop that continues until `top` exceeds `bottom` or `left` exceeds `right`.
   - **Traverse from Left to Right:**
     - Iterate from `left` to `right` using a `for` loop and add elements in the `top` row to `ans`.
     - Increment `top` since the `top` row is completely processed.
   - **Traverse from Top to Bottom:**
     - Iterate from `top` to `bottom` using a `for` loop and add elements in the `right` column to `ans`.
     - Decrement `right` since the `right` column is completely processed.
   - **Traverse from Right to Left (if applicable):**
     - Check if `top` is still less than or equal to `bottom`. If true, iterate from `right` to `left` using a `for` loop and add elements in the `bottom` row to `ans`.
     - Decrement `bottom` since the `bottom` row is completely processed.
   - **Traverse from Bottom to Top (if applicable):**
     - Check if `left` is still less than or equal to `right`. If true, iterate from `bottom` to `top` using a `for` loop and add elements in the `left` column to `ans`.
     - Increment `left` since the `left` column is completely processed.
 **LOOP:**

   ```cpp
   

           while (top <= bottom && left <= right) {  / 
               for (int i = left; i <= right; i++)
                   ans.push_back(mat[top][i]);
               top++;   
               for (int i = top; i <= bottom; i++)
                   ans.push_back(mat[i][right]);
               right--;   
               if (top <= bottom) {
                   for (int i = right; i >= left; i--)
                       ans.push_back(mat[bottom][i]);
                   bottom--;   
               }

                
               if (left <= right) {
                   for (int i = bottom; i >= top; i--)
                       ans.push_back(mat[i][left]);
                   left++;   
               }
           }
           
   ```

**Time Complexity:** O(m * n) 
**Space Complexity:** O(1) 
