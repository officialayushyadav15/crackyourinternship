## Problem

You are given an integer array `prices` where `prices[i]` represents the price of a given stock on the `i-th` day.

On each day, you may decide to buy and/or sell the stock. You can only hold at most one share of the stock at any time. However, you can buy it and immediately sell it on the same day.

Find and return the maximum profit you can achieve.

For more details on the problem, visit the [LeetCode Problem Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/).

## Explanation

### Approach: Greedy

1. **Iterate Through the Array:**
   - Traverse through the array of stock prices, and whenever you find a day where the price is higher than the previous day, add the difference to the total profit. This is because buying on a lower price day and selling on a higher price day will yield profit.

2. **Calculate Profit:**
   - Add up all the positive differences between consecutive days. This is equivalent to summing up all upward slopes in the price curve, which represents buying on the dips and selling on the peaks.

   ```cpp
   class Solution {
   public:
       int maxProfit(vector<int>& prices) {
           int n = prices.size();
           if (n == 0) return 0;

           int totalProfit = 0;
           for (int i = 1; i < n; i++) {
               if (prices[i] > prices[i - 1]) {
                   totalProfit += prices[i] - prices[i - 1];
               }
           }

           return totalProfit;
       }
   };
   ```

   - **Time Complexity:** O(N)
   - **Space Complexity:** O(1)

