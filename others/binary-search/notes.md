# Important Notes Regarding Binary Search

## Basic Template

```java
public int search(int[] nums, int target) {
    int l = 0;
    int r = nums.length - 1;

    while(l <= r) {
        int m = l + (r-l)/2;

        if(nums[m] == target) {
            return m;
        } else if(nums[m] < target) {
            l = m+1;
        } else {
            r = m-1;
        }
    }

    return -1;
}
```

## Definitions

### Lower Bound

- The smallest element in the array that is greater than or equal to the target element.
- If the target exists, it returns the first occurrence of the target element.
- IF the target doesn't exist, it returns the first element that is greater than the target element.

### Upper Bound

- The smallest element in the array that is strictly greater than the target value.
- If the target exists, it returns the element just after the last occurrence of the target.
- If the target doesn't exist, it behaves the same as lower bound.

### Floor

- The largest element in the array that is less than or equal to the target value.
- If the target exists, it returns the last occurrence of the target.
- If the target doesn't exist, it returns the largest element smaller than the target.

### Ceiling

- The smallest element in the array that is greater than or equal to the target value.
- This is essentially the same as Lower Bound.

## Code

```python
def binary_search(arr, target, find_type):
    left, right = 0, len(arr) - 1
    # in case of upper bound, always initialize result to nums.length, altho it usually depends on the problem
    result = -1

    while left <= right:
        mid = (left + right) // 2

        if find_type == "lower_bound" or find_type == "ceiling":
            if arr[mid] >= target:
                result = mid
                right = mid - 1
            else:
                left = mid + 1

        elif find_type == "upper_bound":
            if arr[mid] > target:
                result = mid
                right = mid - 1
            else:
                left = mid + 1

        elif find_type == "floor":
            if arr[mid] <= target:
                result = mid
                left = mid + 1
            else:
                right = mid - 1

    return result
```
