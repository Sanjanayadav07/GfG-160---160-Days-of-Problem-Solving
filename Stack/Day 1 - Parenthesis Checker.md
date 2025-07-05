---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - Strings
  - Stack
  - STL
---

#  _Day 1. Parenthesis Checker_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/stack-gfg-160/problem/parenthesis-checker2744)

## 💡 **Problem Description:**

Given a string `s`, composed of different combinations of `(`, `)`, `{`, `}`, `[`, `]`, verify the **validity of the arrangement**.

A string is **valid** if:

1. **Open brackets** must be closed by the **same type** of brackets.
2. **Open brackets** must be closed in the **correct order**.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```plaintext
s = "[{()}]"
```

#### **Output:**

```plaintext
true
```

#### **Explanation:**

All brackets are correctly paired and well-formed.

### **Example 2:**

#### **Input:**

```plaintext
s = "[()()]{}"
```

#### **Output:**

```plaintext
true
```

#### **Explanation:**

All brackets are well-formed.

### **Example 3:**

#### **Input:**

```plaintext
s = "([]"
```

#### **Output:**

```plaintext
false
```

#### **Explanation:**

The expression is **not balanced** as there is a missing `')'` at the end.

### **Example 4:**

#### **Input:**

```plaintext
s = "([{]})"
```

#### **Output:**

```plaintext
false
```

#### **Explanation:**

The expression is **not balanced** as there is a **closing `]` before the closing `}`**.

### **Constraints:**

- $1 \leq |s| \leq 10^6$
- `s[i]` ∈ `{ '(', ')', '{', '}', '[', ']' }`

## 🎯 **My Approach:**

### **Stack-Based Validation (O(N) Time, O(N) Space)**

1. **Iterate over the string** and use a **stack** to track opening brackets.
2. **When encountering a closing bracket**:
   - If the stack is empty, return `false`.
   - Check whether the **top of the stack matches** the expected opening bracket.
   - If matched, pop the stack. Otherwise, return `false`.
3. **After iterating the string**, the stack should be **empty** for a valid expression.

### **Algorithm Steps:**

1. **Use a stack** to store open brackets `{[(`.
2. **Iterate through the string**:
   - If `s[i]` is an **opening bracket**, push it onto the stack.
   - If `s[i]` is a **closing bracket**:
     - Check if the **stack is empty** (invalid case).
     - **Compare the top element** of the stack with `s[i]`.
     - If it **matches**, pop the stack. Otherwise, return `false`.
3. **After the loop**, return **true** if the stack is empty, else **false**.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(N)`, since each character is processed once in the loop.
- **Expected Auxiliary Space Complexity:** `O(N)`, in the worst case, all characters are pushed onto the stack.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    static boolean isBalanced(String s) {
        Stack<Character> st = new Stack<>();
        for (char c : s.toCharArray())
            if ("({[".indexOf(c) >= 0) st.push(c);
            else if (st.isEmpty() || Math.abs(st.peek() - c) > 2) return false;
            else st.pop();
        return st.isEmpty();
    }
}
```


## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐
