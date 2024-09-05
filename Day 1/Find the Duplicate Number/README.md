## Problem

Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive, there is only one repeated number in `nums`. Your task is to return this repeated number. You must solve the problem without modifying the array `nums` and using only constant extra space.

## Approaches

### First Approach: Sorting

1. **Sort the Array:**
   - First, sort the array.
   
2. **Iterate and Find Duplicate:**
   - Use a for loop to iterate through the sorted array and check if the current element is equal to the next element.
   
   ```cpp
   for(int i = 0; i < nums.size() - 1; i++) {
       if (nums[i] == nums[i + 1]) {
           return nums[i];
       }
   }
   ```

   - **Time Complexity:** O(n log n) due to sorting + O(n) for the iteration.
   - **Space Complexity:** O(1) as no extra space is used except for the sorting algorithm.

### Second Approach: Counting Occurrences

1. **Initialize Count Vector:**
   - Create a vector `v2` to count occurrences of each number.
   
   ```cpp
   vector<int> v2(n + 1, 0);
   ```

2. **Count Frequencies:**
   - Iterate through the `nums` array and increment the count in the vector `v2` for each number.
   
   ```cpp
   for (int i = 0; i < nums.size(); i++) {
       v2[nums[i]]++;
   }
   ```

3. **Find the Repeated Number:**
   - Iterate through the `v2` vector to find the index with a count greater than 1.
   
   ```cpp
   for (int i = 1; i < v2.size(); i++) {
       if (v2[i] > 1) {
           return i;
       }
   }
   ```

   - **Time Complexity:** O(n) for counting + O(n) for finding the duplicate.
   - **Space Complexity:** O(n) due to the extra vector used for counting.
 
