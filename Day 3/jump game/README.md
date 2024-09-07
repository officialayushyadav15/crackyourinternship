## Problem

You are given an integer array `nums` where you are initially positioned at the array's first index. Each element in the array represents your maximum jump length at that position.

Your task is to determine if you can reach the last index starting from the first index. Return `true` if you can reach the last index, or `false` otherwise.

For more details on the problem, visit the [LeetCode Problem Link](https://leetcode.com/problems/jump-game/).

## Description

1. **Iterate from Right to Left:**
   - Use a loop to iterate from the second-last index (`n-2`) to the first index (`0`).
   - For each position `i`, check if you can jump to or beyond the current reachable position `c`.
   - If `i + nums[i] >= c`, update `c` to `i` because we can now reach the last index starting from this position `i`.

2. **Check Reachability:**
   - After the loop, if `c` is `0`, it means we can jump from the first index to the last index. Return `true`.
   - Otherwise, return `false`.

**LOOP:**

   ```cpp
           for (int i = n - 2; i >= 0; i--) {  
               if (c <= i + nums[i]) {  
                   c = i; 
               }
           }
   ```
**Time Complexity:** O(n)**Space Complexity:** O(1) 
