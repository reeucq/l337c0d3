# Question

You are given the `head` of a linked list. **Delete** the **middle node**, and return _the head of the modified linked list._

## Leetcode Link

[2095. Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)

## Approaches

1. **Using Two Pointer**: This approach uses two pointers to find the middle node of the linked list. The first pointer moves one node at a time, while the second pointer moves two nodes at a time. When the second pointer reaches the end of the linked list, the first pointer will be at the middle node. The middle node is then deleted by updating the next pointer of the previous node to skip the middle node.
   - Time complexity: O(n)
   - Space complexity: O(1)

## Solutions

### Java Approach 1

```java
class Solution {
    public ListNode deleteMiddle(ListNode head) {
        if(head == null || head.next == null) return null;

        ListNode dummy = new ListNode(0,head);
        ListNode preSlow = dummy;
        ListNode slow = head;
        ListNode fast = head;

        while(fast != null && fast.next != null) {
            preSlow = preSlow.next;
            slow = slow.next;
            fast = fast.next.next;
        }

        preSlow.next = slow.next;
        return head;
    }
}
```
