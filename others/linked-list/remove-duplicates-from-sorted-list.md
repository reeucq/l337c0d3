# Question

Given the `head` of a sorted linked list, _delete all duplicates such that each element appears only once_. Return _the linked list **sorted** as well_.

## Leetcode Link

[83. Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)

## Approaches

1. **Two Pointers**: Keep track of two pointers, `prev` and `cur`. If the value of `prev` and `cur` are equal, then we can remove the current node. Otherwise, we can move the `prev` pointer to the `cur` pointer. The time complexity of this approach is O(n) and the space complexity is O(1).

## Solutions

### Java Approach 1 - Iterative

```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if(head == null || head.next == null) return head;

        ListNode dummy = new ListNode(Integer.MIN_VALUE);
        dummy.next = head;
        ListNode prev = dummy;
        ListNode cur = head;
        while(cur != null) {
            if(prev.val == cur.val) {
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

[Thought Process](https://yyc-images.oss-cn-beijing.aliyuncs.com/leetcode_83_recursion.png)

```java
public ListNode deleteDuplicates(ListNode head) {
        if(head == null || head.next == null)return head;
        head.next = deleteDuplicates(head.next);
        return head.val == head.next.val ? head.next : head;
}
```
