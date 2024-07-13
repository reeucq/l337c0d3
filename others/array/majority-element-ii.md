# Question

Given an integer array of size `n`, find all elements that appear more than `⌊ n/3 ⌋` times.

## Leetcode Link

[229. Majority Element II](https://leetcode.com/problems/majority-element-ii/)

## Approaches

1. **Hashing**: Count the frequency of each element using a hash map. Return all elements with frequency greater than `n/3`.

2. **Moore's Voting Algorithm**: Find the two most frequent elements using Moore's Voting Algorithm. Check if they appear more than `n/3` times.

## Solutions

### Java Approach 1

```java
class Solution {
    public List<Integer> majorityElement(int[] nums) {
        ArrayList<Integer> res = new ArrayList<>();
        HashMap<Integer,Integer> hm = new HashMap<>();

        for(int num : nums) {
            hm.put(num, hm.getOrDefault(num,0)+1);
            if(hm.get(num) == Math.floor(nums.length/3)+1) {
                res.add(num);
            }
            if(res.size() == 2) break;
        }

        return res;
    }
}
```

### Java Approach 2

```java
class Solution {
    public List<Integer> majorityElement(int[] nums) {
        List<Integer> res = new ArrayList<>();

        if (nums == null || nums.length == 0)
            return res;

        int c1 = 0, c2 = 0;
        int e1 = Integer.MIN_VALUE, e2 = Integer.MIN_VALUE;

        for (int num : nums) {
            if (c1 == 0 && num != e2) {
                c1 = 1;
                e1 = num;
            } else if (c2 == 0 && num != e1) {
                c2 = 1;
                e2 = num;
            } else if (e1 == num) {
                c1++;
            } else if (e2 == num) {
                c2++;
            } else {
                c1--;
                c2--;
            }
        }

        c1 = 0;
        c2 = 0;
        for (int num : nums) {
            if (num == e1)
                c1++;
            if (num == e2)
                c2++;
        }

        if (c1 > nums.length / 3)
            res.add(e1);
        if (c2 > nums.length / 3)
            res.add(e2);

        return res;
    }
}
```
