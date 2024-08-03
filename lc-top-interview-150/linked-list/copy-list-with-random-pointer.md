# Question

A linked list of length `n` is given such that each node contains an additional random pointer, which could point to any node in the list, or `null`.

Construct a **deep copy** of the list. The deep copy should consist of exactly `n` **brand new** nodes, where each new node has its value set to the value of its corresponding original node. Both the next and random pointer of the new nodes should point to new nodes in the copied list such that the pointers in the original list and copied list represent the same list state. **None of the pointers in the new list should point to nodes in the original list.**

Return _the head of the copied linked list._

## Leetcode Link

[138. Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)

## Approaches

1. **Using Hash Map**: We can solve this problem using a hash map. We will iterate over the original linked list and create a new node for each node in the original linked list. We will store the mapping of the original node to the new node in a hash map. We will then iterate over the original linked list again and update the next and random pointers of the new nodes using the hash map.

   **Time Complexity:** O(N), where N is the number of nodes in the linked list.

   **Space Complexity:** O(N), where N is the number of nodes in the linked list.

2. **Optimized Approach**: We can solve this problem without using extra space. We will create a new node for each node in the original linked list and insert it between the original node and its next node. We will then iterate over the original linked list and update the random pointers of the new nodes. Finally, we will separate the original and copied linked lists.

## Solutions

### Java Approach 1

```java
class Solution {
    public Node copyRandomList(Node head) {
        if(head == null) return null;

        HashMap<Node,Node> hm = new HashMap<>();

        Node cur = head;
        while(cur != null) {
            hm.put(cur,new Node(cur.val));
            cur = cur.next;
        }

        cur = head;
        while(cur != null) {
            hm.get(cur).next = hm.get(cur.next);
            hm.get(cur).random = hm.get(cur.random);
            cur = cur.next;
        }

        return hm.get(head);
    }
}
```

### Java Approach 2

```java
public RandomListNode copyRandomList(RandomListNode head) {
  RandomListNode iter = head, next;

  // First round: make copy of each node,
  // and link them together side-by-side in a single list.
  while (iter != null) {
    next = iter.next;

    RandomListNode copy = new RandomListNode(iter.label);
    iter.next = copy;
    copy.next = next;

    iter = next;
  }

  // Second round: assign random pointers for the copy nodes.
  iter = head;
  while (iter != null) {
    if (iter.random != null) {
      iter.next.random = iter.random.next;
    }
    iter = iter.next.next;
  }

  // Third round: restore the original list, and extract the copy list.
  iter = head;
  RandomListNode pseudoHead = new RandomListNode(0);
  RandomListNode copy, copyIter = pseudoHead;

  while (iter != null) {
    next = iter.next.next;

    // extract the copy
    copy = iter.next;
    copyIter.next = copy;
    copyIter = copy;

    // restore the original list
    iter.next = next;

    iter = next;
  }

  return pseudoHead.next;
}
```
