# Question

Given `head`, the head of a linked list, determine if the linked list has a cycle in it. Return `true` _if there is a cycle in the linked list_. Otherwise, return `false`.

## Leetcode Link

[141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)

## Intuition & Approaches

To detect a cycle in a linked list, we can use the **Floyd's Cycle Detection Algorithm**. This algorithm uses two pointers, `slow` and `fast`, to traverse the linked list. The `slow` pointer moves one step at a time, while the `fast` pointer moves two steps at a time. If there is a cycle in the linked list, the `slow` and `fast` pointers will eventually meet at some point, since the `fast` pointer will catch up to the `slow` pointer. This has a time complexity of `O(n)` and a space complexity of `O(1)`. Another approach is to add each node to a set and check if the node is already present in the set. If it is, then there is a cycle in the linked list. This approach has a time complexity of `O(n)` and a space complexity of `O(n)`.

## Solutions

```java
public class Solution {
    public boolean hasCycle(ListNode head) {
        if(head == null) return false;

        ListNode slow = head;
        ListNode fast = head;

        while(fast != null && fast.next != null) {
            fast = fast.next.next;
            slow = slow.next;

            if(fast == slow) return true;
        }

        return false;
    }
}
```
