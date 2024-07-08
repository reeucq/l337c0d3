# Question

Given two integer arrays `nums1` and `nums2`, _return an array of their intersection_. Each element in the result must appear as many times as it shows in both arrays and you may return the result in **any order**.

## Leetcode Link

[350. Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/)

## Approaches

1. **HashMap**: We can use a hashmap to store the frequency of each element in the first array. Then, we can iterate over the second array and check if the element is present in the hashmap. If it is, we can add it to the result and decrement the frequency in the hashmap. This approach has a time complexity of $O(n + m)$ and a space complexity of $O(n)$, where n is the size of the smaller array.

2. **Sorting with Two Pointers**: We can sort both arrays and then use two pointers to find the common elements. This approach has a time complexity of $O(n \log n + m \log m)$ and a space complexity of $O(1)$.

## Solutions

### Java Approcah 1

```java
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        if(nums1.length > nums2.length) return intersect(nums2, nums1);

        HashMap<Integer,Integer> hm1 = new HashMap<>();
        for(int num: nums1) hm1.put(num,hm1.getOrDefault(num,0)+1);

        ArrayList<Integer> res = new ArrayList<>();
        for(int num: nums2) {
            if(hm1.containsKey(num) && hm1.get(num) > 0) {
                res.add(num);
                hm1.put(num,hm1.get(num)-1);
            }
        }

        int[] result = new int[res.size()];
        for (int i = 0; i < res.size(); i++) {
            result[i] = res.get(i);
        }

        return result;
    }
}
```

### Java Approcah 2

```java
public int[] intersect(int[] nums1, int[] nums2) {
        Arrays.sort(nums1);
        Arrays.sort(nums2);
        int n = nums1.length, m = nums2.length;
        int i = 0, j = 0;
        List<Integer> list = new ArrayList<>();
        while(i < n && j < m){
            int a = nums1[i], b= nums2[j];
            if(a == b){
                list.add(a);
                i++;
                j++;
            }else if(a < b){
                i++;
            }else{
                j++;
            }
        }
        int[] ret = new int[list.size()];
        for(int k = 0; k < list.size();k++) ret[k] = list.get(k);
        return ret;
    }
```
