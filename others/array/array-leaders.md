# Question

Given an array `arr` of `n` positive integers, your task is to find all the leaders in the array. An element of the array is considered a leader if it is greater than all the elements on its right side or if it is equal to the maximum element on its right side. The rightmost element is always a leader.

## GFG Link

[Array Leaders](https://www.geeksforgeeks.org/problems/leaders-in-an-array-1587115620/)

## Approaches

1. **Brute Force**: For each element, check if it is a leader or not. Time complexity is $O(n^2)$.

2. **Optimal**: Traverse from the back, keeping track of the maximum element found so far. If the current element is greater than the maximum element found so far, it is a leader. Time complexity is $O(n)$.

## Solutions

### Java Approach 1

```java
class Solution {
    static ArrayList<Integer> leaders(int n, int arr[]) {
        ArrayList<Integer> res = new ArrayList<>();

        for(int i = 0; i < n; i++) {
            int num = arr[i];
            boolean flag = true;
            for(int j = i+1; j < n; j++) {
                if(arr[j] > num) {
                    flag = false;
                    break;
                }
            }
            if(flag) res.add(num);
        }

        return res;
    }
}
```

### Java Approach 2

```java
class Solution {
    static ArrayList<Integer> leaders(int n, int arr[]) {
        ArrayList<Integer> ans = new ArrayList<>();
        ans.add(arr[n-1]);
        int max=arr[n-1];
        for(int i=n-2;i>=0;i--)
        {
            if(arr[i]>=max)
            {
                max=arr[i];
                ans.add(0,arr[i]);
            }
        }
        return ans;
    }
}
```
