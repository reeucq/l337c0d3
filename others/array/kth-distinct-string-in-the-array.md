# Question

A **distinct string** is a string that is present only **once** in an array.

Given an array of strings `arr`, and an integer `k`, return _the `kth` **distinct string** present in `arr`. If there are **fewer** than `k` distinct strings, return an **empty string** `""`._

## Leetcode Link

[2053. Kth Distinct String in an Array](https://leetcode.com/problems/kth-distinct-string-in-an-array/)

## Approach

1. Create a hashmap to store the frequency of each string in the array.
2. Iterate through the array and store the frequency of each string in the hashmap.
3. Iterate through the hashmap and check if the frequency of the string is equal to 1.
4. If the frequency of the string is equal to 1, decrement `k` by 1.
5. If `k` is equal to 0 , return the string.

## Solution

```java
class Solution {
    public String kthDistinct(String[] arr, int k) {
        Map<String, Integer> hm = new HashMap<>();
        for(String s : arr) hm.put(s, hm.getOrDefault(s,0)+1);

        for(String s : arr) {
            if(hm.get(s) == 1) {
                k--;
                if(k == 0) return s;
            }
        }

        return "";
    }
}
```
