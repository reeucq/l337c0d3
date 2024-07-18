# Question

Given an unsorted array `Arr[]` of `N` integers and an integer `X`, find **floor** and **ceiling** of `X` in `Arr[0..N-1].`

**Floor** of `X` is the **largest element** which is **smaller than or equal to** `X`. **Floor** of `X` doesn’t exist if `X` is **smaller than smallest element of** `Arr[]`.

**Ceil** of `X` is the **smallest element** which is **greater than or equal to** `X`. **Ceil** of `X` doesn’t exist if `X` is **greater than greatest element of** `Arr[]`.

## GFG Link

[Ceil The Floor](https://www.geeksforgeeks.org/problems/ceil-the-floor2802/1)

## Approaches

1. **Binary Search**: We can first sort the array and then use binary search to find the floor and ceiling of `X`.

## Solutions

### Java Approach 1

```java
class Solve {
    Pair getFloorAndCeil(int[] arr, int n, int x) {
        Arrays.sort(arr);
        int floor = getFloor(arr,n,x);
        int ceiling = getCeiling(arr,n,x);

        return new Pair(floor,ceiling);
    }

    private int getFloor(int[] arr, int n, int x) {
        int l = 0;
        int r = n-1;
        int ans = -1;

        while(l <= r) {
            int m = l + (r-l)/2;

            if(arr[m] <= x) {
                ans = m;
                l = m + 1;
            } else {
                r = m - 1;
            }
        }

        return ans != -1 ? arr[ans] : ans;
    }

    private int getCeiling(int[] arr, int n, int x) {
        int l = 0;
        int r = n-1;
        int ans = -1;

        while(l <= r) {
            int m = l + (r-l)/2;

            if(arr[m] >= x) {
                ans = m;
                r = m - 1;
            } else {
                l = m + 1;
            }
        }

        return ans != -1 ? arr[ans] : ans;
    }
}
```
