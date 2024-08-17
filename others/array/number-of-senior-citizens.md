# Question

You are given a **0-indexed** array of strings `details`. Each element of `details` provides information about a given passenger compressed into a string of length `15`. The system is such that:

- The first ten characters consist of the phone number of passengers.
- The next character denotes the gender of the person.
- The following two characters are used to indicate the age of the person.
- The last two characters determine the seat allotted to that person.

Return _the number of passengers who are **strictly more than 60 years old**._

## Leetcode Link

[2678. Number of Senior Citizens](https://leetcode.com/problems/number-of-senior-citizens/)

## Intuition

- The algorithm uses a linear scan to find the number of senior citizens in the given array.
- It iterates over the array and extracts the age of each passenger.
- If the age of the passenger is strictly greater than 60, the algorithm increments the count of senior citizens.
- The algorithm returns the count of senior citizens in the given array.

## Solution

```java
class Solution {
    public int countSeniors(String[] details) {
        int count = 0;
        for(String person : details) {
            if(Integer.parseInt(person.substring(11,13)) > 60) count++;
        }
        return count;
    }
}
```
