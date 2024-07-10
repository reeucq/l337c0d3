# Question

There are `n` kids with candies. You are given an integer array `candies`, where each `candies[i]` represents the number of candies the `ith` kid has, and an integer `extraCandies`, denoting the number of extra candies that you have.

Return _a boolean array `result` of length `n`, where `result[i]` is `true` if, after giving the `ith` kid all the `extraCandies`, they will have the **greatest** number of candies among all the kids, or `false` otherwise._

Note that **multiple** kids can have the **greatest** number of candies.

## Leetcode Link

[1431. Kids With the Greatest Number of Candies](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/)

## Approaches

1. **Brute Force**: Find the maximum number of candies among all kids and then check if the `ith` kid has the greatest number of candies after adding `extraCandies`. Time complexity is $O(n)$ and space complexity is $O(1)$.

## Solutions

1. Java Approach 1

```java
class Solution {
    public List<Boolean> kidsWithCandies(int[] candies, int extraCandies) {
        int max = 0;
        for (int candy : candies) {
            max = Math.max(max, candy);
        }

        List<Boolean> result = new ArrayList<>(candies.length);
        for (int candy : candies) {
            result.add(candy + extraCandies >= max);
        }

        return result;
    }
}
```

## Java Approach 1 - Functional

```java
class Solution {
    public List<Boolean> kidsWithCandies(int[] candies, int extraCandies) {
        int max = Arrays.stream(candies).max().orElse(0);

        return Arrays.stream(candies)
                     .mapToObj(candy -> candy + extraCandies >= max)
                     .collect(Collectors.toList());
    }
}
```
