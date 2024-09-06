### Problem

Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive, there is only one repeated number in `nums`. Your task is to return this repeated number. You must solve the problem without modifying the array `nums` and using only constant extra space.

For more details on the problem, visit the [LeetCode Problem Link](https://leetcode.com/problems/find-the-duplicate-number/description/).

### explanation

#### First Approach: Sorting

1. **Sort the Array:**
   - First, sort the array to bring duplicate elements next to each other.

2. **Iterate and Find Duplicate:**
   - Use a for loop to iterate through the sorted array and check if the current element is equal to the next element.
   
   ```cpp
   for(int i = 0; i < nums.size() - 1; i++) {
       if (nums[i] == nums[i + 1]) {
           return nums[i];
       }
   }
   ```

   - **Time Complexity:** O(n log n) + O(n)
   - **Space Complexity:** O(1)

