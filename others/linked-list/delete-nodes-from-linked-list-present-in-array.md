# Question

You are given an array of integers `nums` and the `head` of a linked list. Return the `head` of the modified linked list after **removing** all nodes from the linked list that have a value that exists in `nums`.

## Leetcode Link

[3217. Delete Nodes From Linked List Present in Array](https://leetcode.com/problems/delete-nodes-from-linked-list-present-in-array/)

## Approaches

1. **Brute Force**: Add all the nodes to a set and then iterate over the linked list and remove the nodes that are present in the set. The time complexity of this approach is O(n) and the space complexity is O(n).

## Solutions

### Java Approach 1

```java
class Solution {
    public ListNode modifiedList(int[] nums, ListNode head) {
        if(head == null || nums.length == 0) return head;
        HashSet<Integer> set = new HashSet<>();
        for(int num : nums) set.add(num);
        ListNode dummy = new ListNode(0,head);
        ListNode prev = dummy;
        ListNode cur = head;
        while(cur != null) {
            if(set.contains(cur.val)) {
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
