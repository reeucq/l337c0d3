# Question

The Leetcode file system keeps a log each time some user performs a _change folder_ operation.

The operations are described below:

`"../"` : Move to the parent folder of the current folder. (If you are already in the main folder, **remain in the same folder**).
`"./"` : Remain in the same folder.
`"x/"` : Move to the child folder named x (This folder is **guaranteed to always exist**).
You are given a list of strings `logs` where `logs[i]` is the operation performed by the user at the `ith` step.

The file system starts in the main folder, then the operations in `logs` are performed.

_Return the minimum number of operations needed to go back to the main folder after the change folder operations._

## Leetcode Link

[1598. Crawler Log Folder](https://leetcode.com/problems/crawler-log-folder/)

## Approaches

1. **Simulation**: We can simulate the process of changing the folder and keep track of the current folder. If the current folder is the main folder, we do not need to do anything. Otherwise, we need to move to the parent folder. The time complexity of this approach is $O(n)$, where n is the number of operations in the logs.

2. **Stack**: We can use a stack to keep track of the current folder. If the current folder is the main folder, we do not need to do anything. Otherwise, we need to move to the parent folder. The time complexity of this approach is $O(n)$, where n is the number of operations in the logs.

## Solutions

### Java Approach 1

```java
    public int minOperations(String[] logs) {
        int res = 0;
        for (String s : logs) {
            if (s.equals("../")) res = Math.max(0, --res);
            else if (s.equals("./")) continue;
            else res++;
        }
        return res;
    }
```

### Java Approach 2

```java
class Solution {
    public int minOperations(String[] logs) {
        Stack<String> paths_stack = new Stack<>();

        for (String log : logs) {
            if (log.equals("../")) {
                if (!paths_stack.isEmpty()) {
                    paths_stack.pop();
                }
            } else if (!log.equals("./")) {
                paths_stack.push(log);
            }
        }

        return paths_stack.size();
    }
}
```
