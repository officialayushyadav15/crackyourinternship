## Problem

You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the i-th line are `(i, 0)` and `(i, height[i])`.

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

Notice that you may not slant the container.

For more details on the problem, visit the [LeetCode Problem Link](https://leetcode.com/problems/container-with-most-water/description/).

## Approach

### Two-Pointer Approach

1. **Initialize Two Pointers:**
   - Place one pointer at the beginning of the array (`left`).
   - Place the other pointer at the end of the array (`right`).

2. **Calculate Area:**
   - Compute the width of the container as the difference between the `right` and `left` pointers.
   - Determine the height of the container as the minimum of the heights at the `left` and `right` pointers.
   - Calculate the area of the container using the formula:
     \[
     \text{Area} = \text{width} \times \text{current\_height}
     \]

3. **Update Maximum Area:**
   - Compare the computed area with the maximum area found so far and update if the current area is larger.

4. **Move Pointers:**
   - Move the pointer that points to the shorter line towards the other pointer. This is because the shorter line is the limiting factor for the height of the container.

5. **Repeat:**
   - Continue this process until the two pointers meet.

###Loop

```cpp


        while (left < right) {
            int width = right - left;
            int current_height = std::min(height[left], height[right]);
            int current_area = width * current_height;
            max_area = std::max(max_area, current_area);

            // Move the pointer of the shorter line towards the center
            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }

```

### Time and Space Complexity

- **Time Complexity:** O(n)  
- **Space Complexity:** O(1)  
 
