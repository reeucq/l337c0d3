# Question

You have `n` coins and you want to build a staircase with these coins. The staircase consists of `k` rows where the `ith` row has exactly `i` coins. The last row of the staircase may be incomplete.

Given the integer `n`, return _the number of complete rows of the staircase you will build._

## Leetcode Link

[441. Arranging Coins](https://leetcode.com/problems/arranging-coins/)

## Approaches

1. **Iterative**: We build the staircase row by row, subtracting the coins used in each row from the total. We continue until we can't complete the next row. Time Complexity: $O(k)$, where `k` is the number of complete rows, Space Complexity: $O(1)$

2. **Binary Search**: We can use binary search to find the largest `k` where `k(k+1)/2 <= n`. This is because the sum of the first `k` natural numbers is `k(k+1)/2`. Time Complexity: $O(log n)$, Space Complexity: $O(1)$

3. **Mathematical Approach**: We can solve the equation `k(k+1)/2 = n` for `k`. Time Complexity: $O(1)$, Space Complexity: $O(1)$, Derivation Below:

   ```
   (K * (K+1))/2 <= N

   (K * (K+1)) <= 2N

   K^2 + K <= 2N

   Complete the square:

   K^2 + K + 1/4 - 1/4 <= 2N

   (K + 1/2)^2 - 1/4 <= 2N

   (K + 1/2)^2 <= 2N + 1/4

   K + 1/2 <= sqrt(2N + 1/4)

   Our final equation:

   K <= sqrt(2N + 1/4) - 1/2
   ```

## Solutions

### Java Approach 1

```java
class Solution {
    public int arrangeCoins(int n) {
        int k = 0;
        while (n >= k + 1) {
            k++;
            n -= k;
        }
        return k;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int arrangeCoins(int n) {

        int completedRows = 0;
        long left = 1;
        long right = n;
        while (left <= right) {

            int mid = (int) ((left + right) / 2);
            long coins = (long) ((mid / 2.0) * (mid + 1));
            if (coins > n) {
                right = mid - 1;
            } else {
                completedRows = Math.max(completedRows, mid);
                left = mid + 1;
            }

        }

        return completedRows;
    }
}
```

### Java Approach 3

```java
class Solution {
    public int arrangeCoins(int n) {
        return (int)(Math.sqrt(2 * (long)n + 0.25) - 0.5);
    }
}
```
