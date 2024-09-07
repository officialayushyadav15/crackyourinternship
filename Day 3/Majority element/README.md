## Problem

Given an array `nums` of size `n`, return the majority element.

The **majority element** is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

For more details on the problem, visit the [LeetCode Problem Link](https://leetcode.com/problems/majority-element/).

## Description

**Iterate Through the Array:**
   - Loop through each element in `nums`.
   - If `c` is `0`, set the current element `nums[i]` as the new candidate `el` and increment `c`.
   - If `nums[i]` is equal to the current candidate `el`, increment `c`.
   - If `nums[i]` is not equal to `el`, decrement `c`.
   - This approach works because if there is a majority element, it will be the last remaining candidate after the loop.

**Code:**

   ```cpp
   for (int i = 0; i < n; i++) {  // Iterate through the array
               if (c == 0) {  
                   el = nums[i];
                   c++;
               } else if (nums[i] == el) { 
                   c++;
               } else {  
                   c--;
               }
           }
 ```

**Time Complexity:** O(n)  
**Space Complexity:** O(1) 
