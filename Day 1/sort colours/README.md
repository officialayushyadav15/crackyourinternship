## Problem

Given an array `nums` with `n` objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue. We will use the integers `0`, `1`, and `2` to represent the colors red, white, and blue, respectively. You must solve this problem without using the library's sort function.

## Description

To solve this problem, we can use a three-pointer approach, often referred to as the Dutch National Flag problem. 

### Algorithm

1. **Initialize Pointers:**
   - Set `low` to the start of the array.
   - Set `mid` to the start of the array.
   - Set `high` to the end of the array.

2. **Iterate and Sort:**
   - Use a while loop to iterate through the array until `mid` exceeds `high`.
   
   ```cpp
   while (mid <= high) {
       if (nums[mid] == 0) {
           // Swap nums[low] and nums[mid]
           int temp = nums[low];
           nums[low] = nums[mid];
           nums[mid] = temp;
           low++;
           mid++;
       } 
       else if (nums[mid] == 1) {
           mid++;
       } 
       else if (nums[mid] == 2) {
           // Swap nums[mid] and nums[high]
           int temp = nums[mid];
           nums[mid] = nums[high];
           nums[high] = temp;
           high--;
       }
   }
   ```

   - **Explanation:**
     - If the element at the `mid` position is `0`, swap it with the element at the `low` position. Increment both `low` and `mid`.
     - If the element at `mid` is `1`, it is already in the correct position, so just increment `mid`.
     - If the element at `mid` is `2`, swap it with the element at `high` and decrement `high`. Do not increment `mid` in this case because the swapped element from `high` needs to be processed.

   - **Time Complexity:** O(n) – Each element is processed exactly once.
   - **Space Complexity:** O(1) – No additional space is used beyond a few pointers.
