# Question

You are given the head of a linked list, which contains a series of integers **separated** by `0's`. The **beginning** and **end** of the linked list will have `Node.val == 0`.

For **every** two consecutive `0's`, **merge** all the nodes lying in between them into a single node whose value is the **sum** of all the merged nodes. The modified list should not contain any `0's`.

Return the `head` of the modified linked list.

## Leetcode Link

[2181. Merge Nodes in Between Zeroes](https://leetcode.com/problems/merge-nodes-in-between-zeros/)

## Intuition

- The algorithm uses a dummy node to simplify the merging process.
- It iterates over the linked list and merges all the nodes between two consecutive zeros.
- The algorithm updates the pointers of the previous and next nodes to skip the merged nodes.
- The algorithm returns the head of the modified linked list.

## Solutions

```java
class Solution {
    public ListNode mergeNodes(ListNode head) {
        ListNode dummy = new ListNode(-1,head);
        ListNode prev = dummy;
        ListNode cur = head;
        while(cur != null && cur.next != null) {
            if(cur.val == 0) {
                prev = cur;
                int sum = 0;
                cur = cur.next;
                while(cur != null && cur.val != 0) {
                    sum += cur.val;
                    cur = cur.next;
                }
                prev.val = sum;
                prev.next = cur;
            } else {
                prev = cur;
                cur = cur.next;
            }
        }
        prev.next = null;
        return dummy.next;
    }
}
```
