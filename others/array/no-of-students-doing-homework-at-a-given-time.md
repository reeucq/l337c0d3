# Question

Given two integer arrays `startTime` and `endTime` and given an integer `queryTime`.

The `ith` student started doing their homework at the time `startTime[i]` and finished it at time `endTime[i]`.

Return _the number of students doing their homework at time `queryTime`_. More formally, return the number of students where `queryTime` lays in the interval `[startTime[i], endTime[i]]` inclusive.

## Leetcode Link

[1450. Number of Students Doing Homework at a Given Time](https://leetcode.com/problems/number-of-students-doing-homework-at-a-given-time/)

## Approach

The problem is simple. We just need to iterate over the `startTime` and `endTime` arrays and check if the `queryTime` lies between the `startTime` and `endTime` of the `ith` student. If it does, we increment the count of students doing homework at that time. This works because the `queryTime` is inclusive of the `startTime` and `endTime` of the `ith` student.

## Solutions

### Java

```java
class Solution {
    public int busyStudent(int[] startTime, int[] endTime, int queryTime) {
        int cnt = 0;
        int n = startTime.length;
        for(int i = 0; i < n; i++) {
            if(startTime[i] <= queryTime && queryTime <= endTime[i]) cnt++;
        }
        return cnt;
    }
}
```
