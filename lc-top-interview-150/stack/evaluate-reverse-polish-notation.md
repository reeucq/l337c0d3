# Question

You are given an array of strings `tokens` that represents an arithmetic expression in a Reverse Polish Notation.

Evaluate the expression. Return _an integer that represents the value of the expression._

## Leetcode Link

[150. Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

## Approaches

1. Using a stack: This approach uses a stack to evaluate the Reverse Polish Notation (RPN) expression. The stack is used to store the operands and intermediate results while processing the tokens. When an operator is encountered, the top two elements from the stack are popped, the operation is performed, and the result is pushed back onto the stack. This process continues until all tokens are processed, and the final result is obtained from the stack.
   - Time complexity: O(n) where n is the number of tokens
   - Space complexity: O(n) for the stack

## Solutions

### Java Approach 1

```java
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> s = new Stack<>();

        for(String t : tokens) {
            if(t.equals("+") || t.equals("-") || t.equals("*") || t.equals("/")) {
                int num1 = s.pop();
                int num2 = s.pop();
                int res = 0;
                switch(t) {
                    case "+":
                        res = num2 + num1;
                        break;
                    case "-":
                        res = num2 - num1;
                        break;
                    case "*":
                        res = num2 * num1;
                        break;
                    case "/":
                        res = num2 / num1;
                        break;
                }
                s.push(res);
            } else {
                s.push(Integer.parseInt(t));
            }
        }

        return s.peek();
    }
}
```
