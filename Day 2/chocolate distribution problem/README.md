## Problem

Given an array of positive integers `A[]` of size `N`, where each value represents the number of chocolates in a packet, and `M` students, your task is to distribute exactly one packet to each student such that:

1. Each student gets exactly one packet.
2. The difference between the maximum number of chocolates given to a student and the minimum number of chocolates given to a student is minimized.

For more details on the problem, visit the [GeeksforGeeks Problem Link](https://www.geeksforgeeks.org/problems/chocolate-distribution-problem3825/1).

## Explanation

### Approach: Sorting and Sliding Window

1. **Sort the Array:**
   - First, sort the array `A[]` which allows us to easily find the smallest range of `M` consecutive packets.
   
   ```cpp
   sort(A.begin(), A.end());
   ```

2. **Find Minimum Difference:**
   - Initialize a variable to track the minimum difference between the maximum and minimum chocolates given to the students.
   
   ```cpp
   int min_diff = A[M - 1] - A[0];  // Initial difference
   ```

   - Iterate through the sorted array and check each subset of `M` consecutive packets to find the smallest difference.
   
   ```cpp
   for (int i = M; i < N; i++) {
       if (min_diff > (A[i] - A[i - M + 1])) {
           min_diff = A[i] - A[i - M + 1];
       }
   }
   ```

   - **Time Complexity:** O(N log N) for sorting + O(N) for finding the minimum difference. Overall, O(N log N).
   - **Space Complexity:** O(1) additional space for tracking the minimum difference, not counting the space required for sorting.

