# Question

Given two strings `ransomNote` and `magazine`, return `true` if `ransomNote` can be constructed by using the letters from `magazine` and `false` otherwise.

Each letter in `magazine` can only be used once in `ransomNote`.

## Leetcode Link

[383. Ransom Note](https://leetcode.com/problems/ransom-note/)

## Approaches

1. **HashMap**: We can use a HashMap to store the frequency of each character in the `magazine` string. Then, we can iterate over the `ransomNote` string and decrement the frequency of each character in the HashMap. If the frequency becomes negative or the character is not present in the HashMap, we return `false`. Otherwise, we return `true`. This approach has a time complexity of $O(n)$ and a space complexity of $O(1)$, where `n` is the length of the `ransomNote` string.

2. **Array**: We can use an array of size 26 to store the frequency of each character in the `magazine` string. Then, we can iterate over the `ransomNote` string and decrement the frequency of each character in the array. If the frequency becomes negative or the character is not present in the array, we return `false`. Otherwise, we return `true`. This approach has a time complexity of $O(n)$ and a space complexity of $O(1)$, where `n` is the length of the `ransomNote` string.

## Solutions

### Java Approach 1

```java
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        if (ransomNote.length() > magazine.length()) return false;
        HashMap<Character,Integer> hm = new HashMap<>();
        for(char c : magazine.toCharArray())
            hm.put(c,hm.getOrDefault(c,0)+1);

        for(char c : ransomNote.toCharArray()) {
            if(!hm.containsKey(c) || hm.get(c) < 1) return false;
            hm.put(c, hm.get(c) - 1);
        }

        return true;
    }
}
```

### Java Approach 2

```java
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        if(ransomNote.length() > magazine.length()) return false;
        int[] a = new int[26];

        for(char c: magazine.toCharArray()) a[c-'a']++;
        for(char c: ransomNote.toCharArray()) {
            if(a[c-'a'] == 0) return false;
            a[c-'a']--;
        }

        return true;
    }
}
```
