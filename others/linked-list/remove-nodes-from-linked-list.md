# Question

You are given the `head` of a linked list.

Remove every node which has a node with a greater value anywhere to the right side of it.

Return `the `head` of the modified linked list.`

## Leetcode Link

[2487. Remove Nodes from Linked List](https://leetcode.com/problems/remove-nodes-from-linked-list/)

## Approaches

1. **Reverse and Iterate**: It first reverses the list, then iterates through it, keeping track of the maximum value seen. Nodes with values less than the maximum are removed. Finally, the list is reversed back to its original order and returned. The time complexity is O(N) and the space complexity is O(1).

2. **Monotonic Stack**: It uses a stack to keep track of the nodes with values greater than the current node. The stack is maintained in decreasing order of values. The time complexity is O(N) and the space complexity is O(N).

## Solutions

### Java Approach 1

```java
class Solution {
    public ListNode removeNodes(ListNode head) {
        ListNode reversed = reverse(head);
        ListNode dummy = new ListNode(0,reversed);
        ListNode cur = reversed;
        ListNode prev = dummy;
        int max = 0;

        while(cur != null) {
            max = Math.max(max,cur.val);
            if(max > cur.val) {
                prev.next = cur.next;
            } else {
                prev = cur;
            }
            cur = cur.next;
        }
        return reverse(dummy.next);
    }

    private ListNode reverse(ListNode head) {
        ListNode cur = head;
        ListNode prev = null;
        while(cur != null) {
            ListNode temp = cur.next;
            cur.next = prev;
            prev = cur;
            cur = temp;
        }
        return prev;
    }
}
```

### Java Approach 2

```java
class Solution {
    public ListNode removeNodes(ListNode head) {
        ListNode cur = head;
        Stack<ListNode> stack = new Stack<>();

        while (cur != null) {
            while (!stack.isEmpty() && stack.peek().val < cur.val) {
                stack.pop();
            }
            stack.push(cur);
            cur = cur.next;
        }

        ListNode nxt = null;
        while (!stack.isEmpty()) {
            cur = stack.pop();
            cur.next = nxt;
            nxt = cur;
        }

        return cur;
    }
}
```
