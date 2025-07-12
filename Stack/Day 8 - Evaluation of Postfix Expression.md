----
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Stack
---

#  _Day 8. Evaluation of Postfix Expression_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/stack-gfg-160/problem/evaluation-of-postfix-expression1735)

## 💡 **Problem Description:**

You are given an array of strings `arr` that represents a valid arithmetic expression written in **Reverse Polish Notation (Postfix Notation)**.

Your task is to evaluate the expression and return an integer representing its value.

### **Operators Supported**

- `+` Addition
- `-` Subtraction
- `*` Multiplication
- `/` Integer Division (rounds towards zero)

### **Key Points**

- All numbers are valid integers.
- No division by zero.
- Result and intermediate values fit in **32-bit signed integer**.

## 🔍 **Example Walkthrough:**

### **Example 1**

#### **Input:**

arr = ["2", "3", "1", "*", "+", "9", "-"]

#### **Output:**

`-4`

#### **Explanation:**

Expression equivalent to:  
$\(2 + (3 \times 1) - 9 = 5 - 9 = -4\)$

### **Example 2**

#### **Input:**

arr = ["100", "200", "+", "2", "/", "5", "*", "7", "+"]

#### **Output:**

`757`

#### **Explanation:**

Expression equivalent to:  
$\(\frac{100 + 200}{2} \times 5 + 7 = 150 \times 5 + 7 = 757\)$

### **Constraints**

- $\(1 \leq arr.size() \leq 10^5\)$
- $\(arr[i]\)$ is either an **operator**: "+", "-", "\*", "/" or an **integer** in the range $\([-10^4, 10^4]\)$

## 🎯 **My Approach:**

### **Stack-Based Evaluation (O(N) Time, O(N) Space)**

This approach processes each element in the postfix expression in a **single pass** and uses a **stack** to store operands. Operators pop the top two operands, evaluate them, and push the result back onto the stack.

### **Algorithm Steps:**

1. **Initialize an empty stack.**
2. **Iterate through each token in the array:**
   - If the token is an **operator**, pop the top two operands, apply the operation, and push the result back.
   - If the token is a **number**, convert it to integer and push it onto the stack.
3. **At the end, the stack will contain exactly one value — the final result.**

This method guarantees all operations happen in **O(1)** time, and we iterate over the array exactly once.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(N), where N = length of `arr`, as each token is processed exactly once.
- **Expected Auxiliary Space Complexity:** O(N), for storing the operands in the stack.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public int evaluate(String[] arr) {
        Stack<Integer> st = new Stack<>();
        for (String s : arr) {
            if ("+-*/".contains(s)) {
                int b = st.pop(), a = st.pop();
                if (s.equals("+")) st.push(a + b);
                else if (s.equals("-")) st.push(a - b);
                else if (s.equals("*")) st.push(a * b);
                else st.push(a / b);
            } else {
                st.push(Integer.parseInt(s));
            }
        }
        return st.peek();
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---
