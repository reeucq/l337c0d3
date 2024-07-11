# Question

You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.

You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

Return the _maximum profit you can achieve from this transaction_. If you cannot achieve any profit, return `0`.

## Leetcode Link

[121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

## Approaches

1. **Brute Force**: We can find all possible pairs of buying and selling days and calculate the profit. The pair with the maximum profit will be our answer. This approach will take $O(n^2)$ time.

2. **One Pass**: We can solve this problem in $O(n)$ time using a single pass by keeping track of the minimum price and the maximum profit.

## Solutions

### Java Approach 1

```java
class Solution {
    public int maxProfit(int[] prices) {
        int maxProfit = 0;
        for (int i = 0; i < prices.length; i++) {
            for (int j = i + 1; j < prices.length; j++) {
                maxProfit = Math.max(maxProfit, prices[j] - prices[i]);
            }
        }
        return maxProfit;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = Integer.MAX_VALUE;
        int maxProfit = 0;
        for (int price : prices) {
            minPrice = Math.min(minPrice, price);
            maxProfit = Math.max(maxProfit, price - minPrice);
        }
        return maxProfit;
    }
}
```
