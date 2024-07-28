# Question

Given a string `s`, return _the string after replacing every uppercase letter with the same lowercase letter._

## Leetcode Link

[709. To Lower Case](https://leetcode.com/problems/to-lower-case/)

## Approaches

1. **In Place Solution**: We can convert the string to a character array and iterate through the array. For each character, we can check if it is an uppercase letter. If it is, we can convert it to lowercase by adding 32 to its ASCII value. This approach has a time complexity of `O(n)` and a space complexity of `O(1)`.

2. **Using String Builder**: We can use a `StringBuilder` to build the lowercase string. We can iterate through the string and append the lowercase version of each character to the `StringBuilder`. This approach has a time complexity of `O(n)` and a space complexity of `O(n)`.

## Solutions

### Java In Place Solution

```java
public String toLowerCase(String str) {
    char[] res = str.toCharArray();
    for(int i = 0; i < res.length; i++)
        if(res[i] >= 'A' && res[i] <= 'Z') res[i] += 32;
    return new String(res);
}
```

### Java Using String Builder

```java
class Solution {
    public String toLowerCase(String s) {
        StringBuilder sb = new StringBuilder(100);
        for(char c : s.toCharArray()) {
            if('A' <= c && c <= 'Z') sb.append((char)(c+32));
            else sb.append(c);
        }
        return sb.toString();
    }
}
```
