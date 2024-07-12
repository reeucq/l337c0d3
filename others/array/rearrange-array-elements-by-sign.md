# Question

You are given a **0-indexed** integer array `nums` of **even** length consisting of an **equal** number of positive and negative integers.

You should return the array of nums such that the the array follows the given conditions:

1. Every **consecutive pair** of integers have **opposite signs**.
2. For all integers with the same sign, the **order** in which they were present in `nums` is **preserved**.
3. The rearranged array begins with a positive integer.

Return _the modified array after rearranging the elements to satisfy the aforementioned conditions._

## Leetcode Link

[2149. Rearrange Array Elements by Sign](https://leetcode.com/problems/rearrange-array-elements-by-sign/)

## Approaches

1. **Brute Force**: We can use a brute force approach to solve this problem by storing all the positive and negative integers in separate lists. Then, we can add numbers from those lists one by one in the result array. This approach has a time complexity of $O(n)$ and a space complexity of $O(n)$.

2. **Optimized**: We don't have to store the numbers in separate lists, We can just use two pointers to update the return array. This approach has a time complexity of $O(n)$ and a space complexity of $O(1)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public int[] rearrangeArray(int[] nums) {
        int[] temp1 = new int[nums.length/2];
        int[] temp2 = new int[nums.length/2];
        int[] res = new int[nums.length];
        int i = 0, j = 0;

        for(int k = 0; k < nums.length; k++) {
            if(nums[k] > 0) temp1[i++] = nums[k];
            else temp2[j++] = nums[k];
        }

        int count = 0;
        int n = 0;
        while(n != nums.length) {
            res[n++] = temp1[count];
            res[n++] = temp2[count];
            count++;
        }
        return res;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int[] rearrangeArray(int[] nums) {
        int[] res = new int[nums.length];
        int pos = 0;
        int neg = 1;

        for(int i = 0; i < nums.length; i++) {
            if(nums[i] > 0) {
                res[pos] = nums[i];
                pos+=2;
            } else {
                res[neg] = nums[i];
                neg+=2;
            }
        }

        return res;
    }
}
```

### Follow Up - What if Positive and Negative Numbers aren't equal?

```java
public class Solution {
    public static void rearrange(int[] arr) {
        List<Integer> pos = new ArrayList<>();
        List<Integer> neg = new ArrayList<>();

        for(int i = 0; i < arr.length; i++) {
            if(arr[i] > 0) pos.add(arr[i]);
            else neg.add(arr[i]);
        }

        if(pos.size() > neg.size()) {
            for(int i = 0; i < neg.size(); i++) {
                arr[2*i] = pos.get(i);
                arr[2*i+1] = neg.get(i);
            }

            int index = neg.size()*2;
            for(int i = neg.size(); i < pos.size(); i++) {
                arr[index++] = pos.get(i);
            }
        } else {
            for(int i = 0; i < pos.size(); i++) {
                arr[2*i] = pos.get(i);
                arr[2*i+1] = neg.get(i);
            }

            int index = pos.size()*2;
            for(int i = pos.size(); i < neg.size(); i++) {
                arr[index++] = neg.get(i);
            }
        }
    }

}
```
