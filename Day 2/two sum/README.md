## Problem

Given an array of integers `nums` and an integer `target`, return the indices of the two numbers such that they add up to `target`.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

For more details on the problem, visit the [LeetCode Problem Link](https://leetcode.com/problems/two-sum/description/).

## Description

### Approach: Brute Force

1. **Iterate Over All Pairs:**
   - Use two nested loops to check all possible pairs of elements in the array.
   
   ```cpp
   for (int i = 0; i < nums.size(); i++) {
       for (int j = i + 1; j < nums.size(); j++) {
           if ((nums[i] + nums[j]) == target) {
               a.push_back(i);
               a.push_back(j);
           }
       }
   }
   ```

   - **Time Complexity:** O(N^2) 
   - **Space Complexity:** O(1) 

