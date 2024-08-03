# Question

Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (`push`, `peek`, `pop`, and `empty`).

Implement the MyQueue class:

- `void push(int x)` Pushes element x to the back of the queue.
- `int pop()` Removes the element from the front of the queue and returns it.
- `int peek()` Returns the element at the front of the queue.
- `boolean empty()` Returns true if the queue is empty, false otherwise.

## Leetcode Link

[232. Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)

## Approaches

1. Using two stacks: This approach uses two stacks to implement a queue. s1 is used to store elements on push operations, and s2 is used to reverse the order when popping or peeking. By transferring elements from s1 to s2 only when s2 is empty, the queue maintains the correct order for FIFO (First-In-First-Out) operations. This ensures efficient handling of push, pop, and peek operations.
   - Time complexity: O(1) for push, O(n) for pop, O(1) for peek, O(1) for empty
   - Space complexity: O(n)

## Solutions

### Java Approach 1

```java
class MyQueue {
    Stack<Integer> s1, s2;

    public MyQueue() {
        s1 = new Stack<>();
        s2 = new Stack<>();
    }

    public void push(int x) {
        s1.push(x);
    }

    public int pop() {
        if(s2.isEmpty()) {
            while(!s1.isEmpty()) s2.push(s1.pop());
        }
        return s2.pop();
    }

    public int peek() {
        if(s2.isEmpty()) {
            while(!s1.isEmpty()) s2.push(s1.pop());
        }
        return s2.peek();
    }

    public boolean empty() {
        return s1.isEmpty() && s2.isEmpty();
    }
}
```
