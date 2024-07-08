# Question

Given an integer array `nums`, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

## Leetcode Link

[283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)

## Approaches

1. **Using Extra Array**: We can use an extra array to store the non-zero elements and then fill the remaining elements with 0. This approach requires $O(n)$ extra space and $O(n)$ time complexity.

2. **Two Pointer Approach**: We can use two pointers to keep track of the position of the next non-zero element. We can swap the elements at the two pointers and move the pointers accordingly. This approach requires $O(1)$ extra space and $O(n)$ time complexity.

3. **Snowball Approach**: [Link to Understand](https://leetcode.com/problems/move-zeroes/solutions/172432/the-easiest-but-unusual-snowball-java-solution-beats-100-o-n-clear-explanation) It is a variation of the two-pointer approach where we keep track of the size of the snowball (number of non-zero elements) and swap the elements at the snowball index and the current index. This approach requires $O(1)$ extra space and $O(n)$ time complexity.

## Solutions

### Java Approach 1

```java
class Solution {
    public void moveZeroes(int[] nums) {
        int zeroIdx = -1;
        for(int i = 0; i < nums.length; i++) {
            if(nums[i] == 0) {
                zeroIdx = i;
                break;
            }
        }

        if(zeroIdx == -1) return;

        for(int i = zeroIdx+1; i < nums.length; i++) {
            if(nums[i] != 0) {
                nums[zeroIdx] = nums[i];
                nums[i] = 0;
                zeroIdx++;
            }
        }
    }
}
```

### Java Approach 2

```java
class Solution {
    public void moveZeroes(int[] nums) {
        int zeroIdx = -1;
        for(int i = 0; i < nums.length; i++) {
            if(nums[i] == 0) {
                zeroIdx = i;
                break;
            }
        }

        if(zeroIdx == -1) return;

        for(int i = zeroIdx+1; i < nums.length; i++) {
            if(nums[i] != 0) {
                nums[zeroIdx] = nums[i];
                nums[i] = 0;
                zeroIdx++;
            }
        }
    }
}
```

### Java Approach 3

```java
class Solution {
     public void moveZeroes(int[] nums) {
        int snowBallSize = 0;
        for (int i=0;i<nums.length;i++){
	        if (nums[i]==0){
                snowBallSize++;
            }
            else if (snowBallSize > 0) {
	            int t = nums[i];
	            nums[i]=0;
	            nums[i-snowBallSize]=t;
            }
        }
    }
}
```
