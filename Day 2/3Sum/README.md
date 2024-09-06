## Problem

Given an integer array `nums`, return all the triplets `[nums[i], nums[j], nums[k]]` such that:

- `i != j`
- `i != k`
- `j != k`
- `nums[i] + nums[j] + nums[k] == 0`

Notice that the solution set must not contain duplicate triplets.

For more details on the problem, visit the [LeetCode Problem Link](https://leetcode.com/problems/3sum/description/).


### Loop

```cpp
sort(nums.begin(),nums.end());
        for (int i=0;i<nums.size();i++){
            if (i>0 && nums[i]==nums[i-1]){continue;}
            int j= i+1;
            int k= nums.size()-1;
            while(j<k){
                int sum = nums[i]+nums[j]+nums[k];
                if (sum<0){
                    j++;
                }
                else if (sum>0){
                    k--;
                }
                else{
                    vector <int> temp = {nums[i],nums[j],nums[k]};
                    a.push_back(temp);
                    j++;
                    k--;
                    while(j<k && nums[j]==nums[j-1]){j++;}
                    while(j<k && nums[k]==nums[k+1]){k--;}
                }
            }
        }
```

### Explanation of the Code

1. **Sorting:**
   - The array is sorted to facilitate the two-pointer approach and to help in skipping duplicates.

2. **Iterating with a For Loop:**
   - Loop through each element of the sorted array. For each element, use two pointers to find pairs that sum up to zero with the current element.

3. **Two-Pointer Technique:**
   - Calculate the sum of the current element and the values pointed by `j` and `k`.
   - Adjust the pointers based on the sum to find the correct triplets and avoid duplicates.

4. **Skipping Duplicates:**
   - After finding a valid triplet, move the pointers while skipping duplicate values to avoid adding duplicate triplets to the result.

### Time and Space Complexity

- **Time Complexity:** O(n^2)
- **Space Complexity:** O(1)
