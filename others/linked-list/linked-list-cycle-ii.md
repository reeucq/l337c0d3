# Question

Given the `head` of a linked list, return _the node where the cycle begins. If there is no cycle, return `null`._

## Leetcode Link

[142. Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)

## Approaches

1. Hash Table

   - Store the nodes in a hash table and check if the node is already present in the hash table.
   - Time complexity: O(n)
   - Space complexity: O(n)

2. Floyd's Tortoise and Hare
   - Use two pointers, slow and fast, to detect the cycle.
   - Time complexity: O(n)
   - Space complexity: O(1)

## Solutions

### Java Approach 1

```java
public class Solution {
    public ListNode detectCycle(ListNode head) {
        HashMap<ListNode, Integer> linkedList = new HashMap<>();
        ListNode temp = head;
        while(temp != null) {
            if(linkedList.containsKey(temp)) {
                return temp;
            } else {
                linkedList.put(temp, 1);
                temp = temp.next;
            }
        }
        return null;
    }
}
```

### Java Approach 2

```java
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;

        while(fast != null && fast.next != null) {
            fast = fast.next.next;
            slow = slow.next;

            if(fast == slow) break;
        }

        if (fast == null || fast.next == null) return null;

        ListNode slowtwo = head;
        while(slow != slowtwo) {
            slow = slow.next;
            slowtwo = slowtwo.next;
        }

        return slowtwo;
    }
}
```
