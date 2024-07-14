# Question

Pascal's triangle is a triangular array of the binomial coefficients that arises in probability theory, combinatorics, and algebra.

## Variation 1

Given row number r and column number c. Print the element at position (r, c) in Pascal's triangle.

## Variation 2

Print the nth row of Pascal's triangle.

## Variation 3

Print the first n rows of Pascal's triangle.

## Approaches - Variation 1

1. **Using Binomial Coefficients**: The kth element in the nth row of Pascal's triangle is given by the binomial coefficient C(n, k) = n! / (k! \* (n - k)!). We can calculate this using the formula. Where n is row - 1 and k is col - 1. This has a time complexity of O(k).

## Solutions - Variation 1

### Java Approach 1

```java
public static long elementAt(int r, int c) {
    if (c < 0 || c > r) {
        return 0;
    }
    long res = 1;
    for (int i = 0; i < Math.min(c, r - c); i++) {
        res = res * (r - i) / (i + 1);
    }
    return res;
}
```

## Approaches - Variation 2

1. **Using Binomial Coefficients**: The key insight here is that we can calculate each element of the row based on the previous element. This can be done by multiplying the previous element by (n - k + 1) / k. We can use this formula to calculate the nth row of Pascal's triangle. This has a time complexity of O(n) as there are n elements in the row. The space complexity is also O(n) to store the row.

## Solutions - Variation 2

### Java Approach 1

```java
public static List<Long> nthRow(int n) {
    List<Long> row = new ArrayList<>();
    row.add(1L);
    for (int k = 1; k <= n; k++) {
        long element = row.get(k - 1) * (n - k + 1) / k;
        row.add(element);
    }
    return row;
}
```

## Approaches - Variation 3

1. We generate each row based on the previous row. Each element (except the first and last) is the sum of two elements from the previous row. Time complexity: O(n^2), Space complexity: O(n^2) to store all rows.

## Solutions - Variation 3

### Java Approach 1

```java
public static List<List<Integer>> generateTriangle(int n) {
    List<List<Integer>> triangle = new ArrayList<>();
    if (n <= 0) return triangle;

    triangle.add(List.of(1));
    for (int i = 1; i < n; i++) {
        List<Integer> row = new ArrayList<>();
        row.add(1);
        for (int j = 1; j < i; j++) {
            row.add(triangle.get(i-1).get(j-1) + triangle.get(i-1).get(j));
        }
        row.add(1);
        triangle.add(row);
    }
    return triangle;
}
```

Note: In this variation, we use `Integer` instead of `Long` as the triangle size is limited and `Integer` should be sufficient for most practical cases. If larger values are expected, `Long` can be used instead.
