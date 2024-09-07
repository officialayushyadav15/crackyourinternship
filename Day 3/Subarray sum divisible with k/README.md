## Problem

Given an integer array `nums` and an integer `k`, return the number of non-empty subarrays whose sum is divisible by `k`.

A subarray is a contiguous part of an array.

For more details on the problem, visit the [LeetCode Problem Link](https://leetcode.com/problems/subarray-sums-divisible-by-k/).

## Explanation 

1. **Initialize Variables and Hash Map:**
   - Use an `unordered_map<int, int>` to store the frequency of each prefix sum modulo `k` encountered. Initialize it with `{0: 1}` to handle cases where the cumulative sum itself is divisible by `k`.
   - Initialize `Sum` to store the cumulative sum and `count` to keep track of the number of valid subarrays.

2. **Iterate Through the Array:**
   - Maintain a running sum, `Sum`, which keeps track of the cumulative sum of elements from the start to the current position.
   - For each element in `nums`, compute the cumulative sum by adding the current element to `Sum`.
   - Calculate `prefixSum = Sum % k`. This value represents the remainder when the cumulative sum is divided by `k`.
   - If `prefixSum` is negative (this can happen in languages where the modulus operator retains the sign), adjust it by adding `k` to ensure it is positive.
   - If `prefixSum` is found in the hash map, it indicates that there are `map[prefixSum]` subarrays ending at the current index whose sum is divisible by `k`. Add this count to the total `count`.
   - Update the frequency of `prefixSum` in the hash map.

  **LOOP:**

   ```cpp
   for (int i = 0; i < nums.size(); i++) {  // Iterate through the array
       Sum += nums[i];  // Update the cumulative sum with the current element
       prefixSum = Sum % k;  // Calculate the prefix sum modulo k

       if (prefixSum < 0) {  // Adjust negative prefix sum to be within the range [0, k-1]
           prefixSum += k;
       }

       if (map.find(prefixSum) != map.end()) {  // Check if this prefix sum exists in the map
           count += map[prefixSum];  // If it exists, add the number of times it appears to the count
       }

       map[prefixSum]++;  // Update the frequency of the current prefix sum in the map
   }
   ```
 
**Time Complexity:** O(n)
**Space Complexity:** O(n) 
