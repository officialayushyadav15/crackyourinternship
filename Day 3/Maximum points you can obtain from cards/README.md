## Problem

You are given several cards arranged in a row, and each card has an associated number of points. The points are given in the integer array `cardPoints`.

In one step, you can take one card from either the beginning or the end of the row. You must take exactly `k` cards.

Your score is the sum of the points of the cards you have taken.

Given the integer array `cardPoints` and the integer `k`, return the maximum score you can obtain.

For more details on the problem, visit the [LeetCode Problem Link](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/).

## Explanation

**LOOP:**

   ```cpp
   for(int i = 0; i < k; i++) {
       sum = sum + cp[i];  // Calculate the sum of the first k elements from the start
   }
   max = sum;  // Initialize max with the initial sum

   for(int i = 0; i < k; i++) {
       sum = sum + cp[cp.size() - 1 - i] - cp[k - i - 1];  // Update sum by adding element from the end and removing from the start
       if(max < sum) {  // Check if the new sum is greater than the current max
           max = sum;  // Update max if a greater sum is found
       }
   }
   ```
   - **First Loop:**
     - `for(int i = 0; i < k; i++)`: This loop calculates the sum of the first `k` cards from the beginning of the array (`cp`).
     - `sum = sum + cp[i]`: Adds the `i-th` element to `sum` to compute the initial sum.
     - `max = sum`: Initializes the `max` value with the computed sum.

   - **Second Loop:**
     - `for(int i = 0; i < k; i++)`: This loop slides the window from the end of the array to include elements from the back while excluding elements from the front.
     - `sum = sum + cp[cp.size() - 1 - i] - cp[k - i - 1]`: This line updates `sum`:
       - `cp[cp.size() - 1 - i]`: Adds the `i-th` element from the end of the array.
       - `cp[k - i - 1]`: Subtracts the `k-i-1` element from the beginning.
     - `if(max < sum)`: Checks if the newly computed `sum` is greater than the current `max`.
     - `max = sum`: Updates `max` if a new maximum sum is found.

5. **Time Complexity:** O(k)
6. **Space Complexity:** O(1) 
