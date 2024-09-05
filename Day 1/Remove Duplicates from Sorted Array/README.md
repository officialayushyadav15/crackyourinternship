## Problem

Given an integer array `nums` sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Then return the number of unique elements in `nums`.

Consider the number of unique elements of `nums` to be `k`. To get accepted, you need to do the following:

- Modify the array `nums` such that the first `k` elements contain the unique elements in the order they were present in `nums` initially. The remaining elements of `nums` are not important, as well as the size of `nums`.
- Return `k`.

## Description

To solve this problem, you can use a single loop to iterate through the array. The approach involves using a variable `k` to track the index where the next unique element should be placed.

### Algorithm

1. **Initialize Variables:**
   - Start with `k` set to `1` (since the first element is always unique by itself).
   
2. **Iterate Through the Array:**
   - Use a for loop to iterate from the second element to the end of the array.
   
   ```cpp
   for(int i = 1; i < nums.size(); i++) {
       if (nums[i] != nums[i - 1]) {
           nums[k] = nums[i];
           k++;
       }
   }
   ```

   - **Explanation:**
     - Compare the current element `nums[i]` with the previous element `nums[i - 1]`.
     - If they are different, it means the current element is unique. Replace the element at index `k` with `nums[i]` and increment `k`.
     - Continue to the next element in the array.

   - **Time Complexity:** O(n) – Each element is processed once.
   - **Space Complexity:** O(1) – The solution uses constant extra space.

### Note

- The array `nums` is modified in place to contain the unique elements at the beginning.
- The final number of unique elements is given by `k`.
