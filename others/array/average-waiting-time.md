# Question

There is a restaurant with a single chef. You are given an array `customers`, where `customers[i] = [arrival_i, time_i]`:

- `arrival_i` is the arrival time of the `ith` customer. The arrival times are sorted in **non-decreasing** order.
- `time_i` is the time needed to prepare the order of the `ith` customer.

When a customer arrives, he gives the chef his order, and the chef starts preparing it once he is idle. The customer waits till the chef finishes preparing his order. The chef does not prepare food for more than one customer at a time. The chef prepares food for customers **in the order they were given in the input**.

_Return the **average** waiting time of all customers._

## Leetcode Link

[1701. Average Waiting Time](https://leetcode.com/problems/average-waiting-time/)

## Approaches

1. **Simulation**: We can simulate the process of preparing the food for each customer and calculate the waiting time for each customer. The average waiting time can be calculated by summing up the waiting time of each customer and dividing it by the total number of customers. The time complexity of this approach is $O(n)$ where n is the number of customers.

## Solutions

### Java Approach 1

```java
class Solution {
    public double averageWaitingTime(int[][] customers) {
        int n = customers.length;
        long totalWaitingTime = 0;
        int currentTime = 0;

        for (int[] customer : customers) {
            int arrivalTime = customer[0];
            int cookingTime = customer[1];

            // Update current time to at least the arrival time
            currentTime = Math.max(currentTime, arrivalTime);

            // Calculate finish time and waiting time
            int finishTime = currentTime + cookingTime;
            int waitingTime = finishTime - arrivalTime;

            totalWaitingTime += waitingTime;
            currentTime = finishTime;
        }

        return (double) totalWaitingTime / n;
    }
}
```
