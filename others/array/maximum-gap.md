# Question

Given an integer array `nums`, return _the maximum difference between two successive elements in its sorted form_. If the array contains less than two elements, return `0`.

## Leetcode Link

[164. Maximum Gap](https://leetcode.com/problems/maximum-gap/)

## Approaches

1. **Radix Sort**: We can use radix sort to sort the array and then in a single pass, we can find the maximum difference between two successive elements. The time complexity of this approach is O(n\*k) and the space complexity is O(n).

2. **Bucket Sort**: Read more on [here](https://web.eecs.utk.edu/~jplank/topcoder-writeups/Leetcode/Maximum-Gap/index.html). I don't understand this, just yet, maybe sometime else.

## Solutions

### Java Approach 1

```java
class Solution {
    public int maximumGap(int[] nums) {
        int maxGap = 0;
        radixSort(nums,nums.length);
        for(int i = 1; i < nums.length; i++) {
            if((nums[i]-nums[i-1])>maxGap) maxGap = nums[i]-nums[i-1];
        }
        return maxGap;
    }

    private void radixSort(int[] nums, int n) {
        int max = nums[0];
        for(int i = 1; i < n; i++) if(nums[i] > max) max = nums[i];
        int d = (int) Math.floor(Math.log10(max))+1;
        LinkedList[] L = new LinkedList[10];
        for(int i = 0; i < 10; i++) L[i] = new LinkedList<>();

        for(int i = 1; i <= d; i++) {
            for(int j = 0; j < n; j++) {
                L[(nums[j]/(int)Math.pow(10,i-1))%10].addFirst(nums[j]);
            }
            int k = 0;
            for(int j = 0; j < 10; j++) {
                while(!L[j].isEmpty()) {
                    nums[k++] = (int) L[j].pollLast();
                }
            }
        }
    }
}
```
