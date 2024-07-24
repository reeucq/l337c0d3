# Question

Alice has `n` candies, where the `ith` candy is of type `candyType[i]`. Alice noticed that she started to gain weight, so she visited a doctor.

The doctor advised Alice to only eat `n / 2` of the candies she has (`n` is always even). Alice likes her candies very much, and she wants to eat the maximum number of different types of candies while still following the doctor's advice.

Given the integer array `candyType` of length `n`, return _the maximum number of different types of candies she can eat if she only eats n / 2 of them._

## Leetcode Link

[575. Distribute Candies](https://leetcode.com/problems/distribute-candies/)

## Approach

We can use a HashSet to store the types of candies Alice has. Since the number of candies Alice can eat is `n / 2`, we can return the minimum of the number of unique candies Alice has and `n / 2`.

## Solution

```java
class Solution {
    public int distributeCandies(int[] candyType) {
        int maxAllowed = candyType.length / 2;
        Set<Integer> uniqueTypes = new HashSet<>();
        for(int candy : candyType) {
            uniqueTypes.add(candy);
            if(uniqueTypes.size() == maxAllowed) return maxAllowed;
        }
        return uniqueTypes.size();
    }
}
```
