# Question

Given two strings `s` and `p`, return _an array of all the start indices of `p`'s anagrams in `s`. You may return the answer in any order._

## Leetcode Link

[438. Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)

## Approach

1. **Brute Force**: Generate all possible substrings of length `len(p)` and check if they are anagrams of `p`. This approach has a time complexity of $O(n*k)$ and is not efficient.

2. **Sliding Window**: Maintain a window of length `len(p)` and keep track of the frequency of characters in the window. If the frequency of characters in the window matches the frequency of characters in `p`, then we have found an anagram. This approach has a time complexity of $O(n)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        List<Integer> res = new ArrayList<>();
        for(int i = 0; i <= s.length() - p.length(); i++) {
            String sub = s.substring(i,i+p.length());
            if(isAnagram(sub,p)) res.add(i);
        }
        return res;
    }

    private boolean isAnagram(String s, String t) {
        if(s.length() != t.length()) return false;
        int[] store = new int[26];

        for(int i = 0; i < s.length(); i++) {
            store[s.charAt(i) - 'a']++;
            store[t.charAt(i) - 'a']--;
        }

        for(int n : store) if(n != 0) return false;

        return true;
    }
}
```

### Java Approach 2

```java
class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        List<Integer> res = new ArrayList<>();
        if(s == null || p == null || s.length() < p.length()) return res;

        int[] sCount = new int[26];
        int[] pCount = new int[26];

        for(char c : p.toCharArray()) pCount[c-'a']++;

        for(int i = 0; i < s.length(); i++) {
            sCount[s.charAt(i) - 'a']++;
            if(i >= p.length()) sCount[s.charAt(i - p.length()) - 'a']--;
            if(Arrays.equals(pCount, sCount)) res.add(i - p.length() + 1);
        }

        return res;
    }
}
```

### Java Approach 2 - Hashmap Solution

```java
class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        int startIndex = 0;
        Map<Character, Integer> pMap = new HashMap<>(), sMap = new HashMap<>();
        List<Integer> res = new ArrayList<>();

        for(char c: p.toCharArray())
            pMap.put(c, 1 + pMap.getOrDefault(c, 0));

        for(int i = 0; i < s.length(); i++) {
            sMap.put(s.charAt(i), 1 + sMap.getOrDefault(s.charAt(i), 0));

            if(i >= p.length() - 1) {
                if(sMap.equals(pMap))
                    res.add(startIndex);

                //if current character is in sMap, remove it and re-update the map.
                if(sMap.containsKey(s.charAt(startIndex))) {
                    sMap.put(s.charAt(startIndex), sMap.get(s.charAt(startIndex)) - 1);
                    if(sMap.get(s.charAt(startIndex)) == 0)
                        sMap.remove(s.charAt(startIndex));
                }
                startIndex += 1;
            }
        }

        return res;
    }
}

```
