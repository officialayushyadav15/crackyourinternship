## Problem

Given an integer array `nums`, move all `0`s to the end of it while maintaining the relative order of the non-zero elements. Note that you must do this in-place without making a copy of the array.

For more details on the problem, visit the [LeetCode Problem Link](https://leetcode.com/problems/move-zeroes/).

## Explanation

In this approach, we use a variable `j` to track the position where the next non-zero element should be placed. 

Here’s a step-by-step explanation:

1. **Initialization:**
   - Start with `j` initialized to `0`, which will be used to track the position of the next non-zero element.

2. **Iteration:**
   - Traverse the array. When a non-zero element is encountered, swap it with the element at index `j` and increment `j`.
   - If a zero is encountered, simply continue to the next element.

3. **Swapping:**
   - When a non-zero element is found, swap it with the element at index `j` (the current position for the next non-zero element).
   - After the swap, increment `j` to move to the next position for any subsequent non-zero elements.

### Code

```cpp
for(int i = 0; i < n; i++) {
    if (j == 0) {
        if (nums[i] != 0) {
            j++;
            continue;
        } else {
            j = i;
        }
    }
    if (nums[i] != 0) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
        j++;
    }
}
```

- **Time Complexity:** O(n) – Each element is processed once.
- **Space Complexity:** O(1) – The solution uses constant extra space.
