# Question

There is a singly-linked list `head` and we want to delete a node `node` in it.

You are given the node to be deleted `node`. You will **not be given access** to the first node of `head`.

All the values of the linked list are **unique**, and it is guaranteed that the given node `node` is not the last node in the linked list.

Delete the given node.

## Leetcode Link

[237. Delete Node in a Linked List](https://leetcode.com/problems/delete-node-in-a-linked-list/)

## Intuition

The problem is asking us to delete a node in a linked list. We are not given the head of the linked list, but we are given the node to be deleted. We can solve this problem by copying the value of the next node to the current node and then deleting the next node.

## Solution

### Java

```java
class Solution {
    public void deleteNode(ListNode node) {
        node.val = node.next.val;
        node.next = node.next.next;
    }
}
```
