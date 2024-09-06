
## Problem

Given an array `nums` of `n` integers, return an array of all the unique quadruplets `[nums[a], nums[b], nums[c], nums[d]]` such that:

- `0 <= a, b, c, d < n`
- `a, b, c, and d` are distinct.
- `nums[a] + nums[b] + nums[c] + nums[d] == target`

You may return the answer in any order.

For more details on the problem, visit the [LeetCode Problem Link](https://leetcode.com/problems/4sum/description/).

## Approach

### Explanation of the Code

1. **Sorting:**
   - The array is sorted to help in managing duplicates and to efficiently apply the two-pointer technique.

2. **Iterating with Nested Loops:**
   - The outer loops (`i` and `j`) iterate over pairs of indices. For each pair, the two-pointer technique (`k` and `l`) is used to find the remaining two elements.

3. **Avoiding Duplicates:**
   - The code ensures that no duplicate quadruplets are added by skipping over duplicate values for each index.

4. **Two-Pointer Technique:**
   - The pointers `k` and `l` adjust based on whether the current sum is less than or greater than the target to find the required quadruplets.



###Loop
```cpp
sort(nums.begin(), nums.end());
        
        for(int i = 0; i < nums.size() - 3; i++) {
            if(i > 0 && nums[i] == nums[i - 1]) continue; // Avoid duplicates for i
            for(int j = i + 1; j < nums.size() - 2; j++) {
                if(j > i + 1 && nums[j] == nums[j - 1]) continue; // Avoid duplicates for j
                int k = j + 1;
                int l = nums.size() - 1;
                while(k < l) {
                    long long sum = (long long)nums[i] + nums[j] + nums[k] + nums[l];
                    if(sum == target) {
                        result.push_back({nums[i], nums[j], nums[k], nums[l]});
                        k++;
                        l--;
                        while(k < l && nums[k] == nums[k - 1]) k++; // Avoid duplicates for k
                        while(k < l && nums[l] == nums[l + 1]) l--; // Avoid duplicates for l
                    } else if(sum < target) {
                        k++;
                    } else {
                        l--;
                    }
                }
            }
        }
```



### Loop Explanation

1. **Outer Loops (i and j):**
   - **First Loop (i):** Iterates over each element of the array up to the third last element.
   - **Second Loop (j):** For each `i`, iterates from `i + 1` to the second last element.

2. **Two-Pointer Technique (k and l):**
   - **Pointers Initialization:** `k` starts from `j + 1`, and `l` starts from the end of the array.
   - **Calculate Sum:** Compute the sum of the four elements `nums[i]`, `nums[j]`, `nums[k]`, and `nums[l]`.
   - **Adjust Pointers:**
     - If the sum is equal to the target, add the quadruplet to the result and move both pointers while skipping over duplicates.
     - If the sum is less than the target, increment `k` to increase the sum.
     - If the sum is greater than the target, decrement `l` to decrease the sum.

### Time and Space Complexity

- **Time Complexity:** O(n^3) 
- **Space Complexity:** O(1)  
