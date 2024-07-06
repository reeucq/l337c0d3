# Question
Given an array of strings `strs`, group **the anagrams** together. You can return the answer in **any order**.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

## Leetcode Link
[49. Group Anagrams](https://leetcode.com/problems/group-anagrams/)

## Approaches
1. **Brute Force**: This method iterates over each string and compares it with every other string to check if they are anagrams using the `isAnagram` method. If two strings are anagrams, they are grouped together, and the matched string is marked to avoid reprocessing. This approach has a time complexity of $O(n^2 \cdot k)$, where `n` is the number of strings and `k` is the length of the strings.

2. **Sorting**: In this approach, each string is sorted, and the sorted string is used as a key in a hashmap. Strings that are anagrams will have the same sorted string key, allowing them to be grouped together efficiently. This method has a time complexity of $O(n \cdot k \log k)$ due to the sorting operation.

3. **Character Count as Key**: This method uses a character count array as a key in the hashmap instead of sorting. For each string, a count of each character is computed and converted to a string or tuple to use as a hashmap key. Anagrams will have identical character count arrays, allowing them to be grouped together. This approach has a time complexity of $O(n \cdot k)$ and is more efficient than the previous methods.

## Solutions
### Java Approach 1
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        List<List<String>> result = new ArrayList<>();
       
        if(strs.length == 0) {
            return result;
        }

        for(int i = 0; i < strs.length; i++) {
            ArrayList<String> temp = new ArrayList<>();
            if(strs[i].equals("0")) continue;
            temp.add(strs[i]);
            for(int j = i+1; j < strs.length; j++) {
                if(isAnagram(temp.get(0),strs[j])) {
                    temp.add(strs[j]);
                    strs[j] = "0";
                }
            }
            result.add(temp);
        }
        return result;
    }


    public boolean isAnagram(String str1, String str2) {
        if(str1.length() != str2.length()) return false;
        int[] store = new int[256];
        for(int i = 0; i < str1.length(); i++) {
            store[str1.charAt(i)]++;
            store[str2.charAt(i)]--;
        }
        for(int n : store) if(n != 0) return false;
        return true;
    }
}

```

### Java Approach 2
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();
        
        for (String word : strs) {
            char[] chars = word.toCharArray();
            Arrays.sort(chars);
            String sortedWord = new String(chars);
            
            if (!map.containsKey(sortedWord)) {
                map.put(sortedWord, new ArrayList<>());
            }
            
            map.get(sortedWord).add(word);
        }
        
        return new ArrayList<>(map.values());
    }
}
```

### Java Approach 3
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();
        
        for (String word : strs) {
            int[] count = new int[26];
            for (char c : word.toCharArray()) {
                count[c - 'a']++;
            }
            String key = Arrays.toString(count);
            
            if (!map.containsKey(key)) {
                map.put(key, new ArrayList<>());
            }
            
            map.get(key).add(word);
        }
        
        return new ArrayList<>(map.values());
    }
}
```