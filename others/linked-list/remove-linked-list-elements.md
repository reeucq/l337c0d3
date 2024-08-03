# Question

Given the `head` of a linked list and an integer `val`, remove all the nodes of the linked list that has `Node.val == val`, and return _the new head_.

## Leetcode Link

[203. Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/)

## Approaches

1. **Iterative**: We can iterate over the linked list and remove the nodes that have the value `val`. We'll keep track of the previous node to remove the current node. This approach has a time complexity of `O(n)` and a space complexity of `O(1)`.

## Solutions

### Java Approach 1

```java
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        ListNode dummy = new ListNode(0,head);
        ListNode prev = dummy, cur = head;

        while(cur != null) {
            if(cur.val == val) {
                prev.next = cur.next;
            } else {
                prev = cur;
            }
            cur = cur.next;
        }

        return dummy.next;
    }
}
```

### Java Approach 1 - Recursive

```java
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        if(head==null){
            return head;
        }
        head.next=removeElements(head.next,val);
            return head.val==val?head.next:head;
    }
}
```
