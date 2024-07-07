# Question

There are `numBottles` water bottles that are initially full of water. You can exchange `numExchange` empty water bottles from the market with one full water bottle.

The operation of drinking a full water bottle turns it into an empty bottle.

Given the two integers `numBottles` and `numExchange`, return _the **maximum** number of water bottles you can drink._

## Leetcode Link

[1518. Water Bottles](https://leetcode.com/problems/water-bottles/)

## Approaches

1. **Simulation**: We can simulate the process of drinking water bottles. We can keep track of the number of bottles we have drunk and the number of empty bottles we have. We can keep drinking water bottles until we don't have enough empty bottles to exchange for a full bottle. We can return the number of bottles we have drunk. This approach has a time complexity of $O(n)$ where n is the number of bottles we have drunk.

2. **Mathematical**: Every time you trade in numExchange bottles, you get one bottle back. Therefore you decrease your number of bottles by (numExchange - 1) and increase your answer by 1. This suggests a simple division, where you can just divide numBottles by (numExchange - 1). The reason this doesn't work, is that you can't end up with zero bottles. For example if you have 4 bottles and numExchange is 5, you can't trade and wind up with 0 bottles; you can't trade at all. So, you subtract one from each of the numbers you're given, and then divide. That says how many full bottles you can get by trading. Add to that the number of bottles you started with, and you have the answer. This has the time complexity of $O(1)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public int numWaterBottles(int numBottles, int numExchange) {
        int ans = numBottles;

        while(numBottles >= numExchange) {
            int newBottles = numBottles / numExchange;
            int remBottles = numBottles % numExchange;
            ans = ans + newBottles;
            numBottles = newBottles + remBottles;
        }

        return ans;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int numWaterBottles(int numBottles, int numExchange) {
        return numBottles + (numBottles - 1) / (numExchange - 1);
    }
}
```
