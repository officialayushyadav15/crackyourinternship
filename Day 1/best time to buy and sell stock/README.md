## Problem

You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0

For more details on the problem, visit the [LeetCode Problem Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/).

## Explanation

The goal is to determine the maximum profit from buying and selling a stock on different days. The solution efficiently computes this by keeping track of the minimum price seen so far and the maximum profit achievable with that minimum price.

### Approach

1. **Initialization:**
   - `minPrice` is initialized to `INT_MAX` to ensure that any price encountered will be lower.
   - `maxProfit` is initialized to `0` to track the maximum profit.

2. **Iterate Through Prices:**
   - Traverse the `prices` array to update `minPrice` and `maxProfit`.
   - For each price, check if it is lower than `minPrice`. If so, update `minPrice` to this new lower price.
   - Otherwise, compute the potential profit by subtracting `minPrice` from the current price. If this profit is greater than `maxProfit`, update `maxProfit`.

3. **Return Result:**
   - After iterating through all prices, return `maxProfit`, which represents the maximum profit that can be achieved.

### Code

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int minPrice = INT_MAX;
        int maxProfit = 0;
        int n = prices.size();

        for (int i = 0; i < n; i++) {
            if (prices[i] < minPrice) {
                minPrice = prices[i]; 
            }
            else if (prices[i] - minPrice > maxProfit) {
                maxProfit = prices[i] - minPrice; 
            }
        }

        return maxProfit;
    }
};
```

- **Time Complexity:** O(n) – Each element in the array is processed once.
- **Space Complexity:** O(1) – The solution uses constant extra space.
