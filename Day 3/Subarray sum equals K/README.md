## Problem

Given an array of integers `nums` and an integer `k`, return the total number of subarrays whose sum equals `k`.

A subarray is a contiguous non-empty sequence of elements within an array.

For more details on the problem, visit the [LeetCode Problem Link](https://leetcode.com/problems/subarray-sum-equals-k/).

## Explanation

To solve this problem, we can use a **prefix sum** approach combined with a **hash map** to keep track of the cumulative sum frequencies. This allows us to efficiently calculate the number of subarrays with a given sum `k`.

### Algorithm

1. **Initialize Hash Map:**
   - Use an `unordered_map<int, int>` to store the frequency of each prefix sum encountered. Initialize it with `{0: 1}` to handle the case where a subarray itself sums to `k`.

2. **Iterate Through the Array:**
   - Maintain a running sum, `prefixSum`, which keeps track of the cumulative sum of elements from the start to the current position.
   - For each element in `nums`, compute the prefix sum by adding the current element to `prefixSum`.
   - Calculate `remove = prefixSum - k`. This value represents the prefix sum that, when removed from `prefixSum`, would leave a subarray summing to `k`.
   - If `remove` is found in the hash map, it indicates that there are `map[remove]` subarrays ending at the current index that sum to `k`. Add this count to the total `count`.
   - Update the frequency of `prefixSum` in the hash map.
**LOOP:**

   ```cpp
   for (int i = 0; i < nums.size(); i++) {
            prefixSum += nums[i];
            int remove = prefixSum - k;
            if (map.find(remove) != map.end()) {
                count += map[remove];
            }
            map[prefixSum]++;
        }
   ```

**Time Complexity:** O(n)

**Space Complexity:** O(n) 
