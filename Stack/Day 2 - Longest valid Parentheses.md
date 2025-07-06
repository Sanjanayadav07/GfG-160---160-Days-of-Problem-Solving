---
Difficulty: Hard
Source: 160 Days of Problem Solving
Tags:
  - Strings
  - Dynamic Programming
  - Stack
---

#  _Day 2. Longest valid Parentheses_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/stack-gfg-160/problem/longest-valid-parentheses5657)

## 💡 **Problem Description:**

Given a string **s** consisting of only **'('** and **')'**, find the **length of the longest valid parentheses substring**.

A parenthesis string is **valid** if:

1. Every opening parenthesis **'('** has a corresponding closing **')'**.
2. The closing parenthesis appears **after** its matching opening parenthesis.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
s = "((()"
```

#### **Output:**

```
2
```

#### **Explanation:**

The longest valid parentheses substring is `"()"`.

### **Example 2:**

#### **Input:**

```
s = ")()())"
```

#### **Output:**

```
4
```

#### **Explanation:**

The longest valid parentheses substring is `"()()"`.

### **Example 3:**

#### **Input:**

```
s = "())()"
```

#### **Output:**

```
2
```

#### **Explanation:**

The longest valid parentheses substring is `"()"`.

### **Constraints:**

- $1 \leq s.length \leq 10^6$
- **s** consists of **'('** and **')'** only.

## 🎯 **My Approach:**

### **Stack-Based Approach (O(N) Time, O(N) Space)**

1. **Use a stack to track indices** of parentheses.
2. **Push opening parentheses ('(') indices** onto the stack.
3. **For closing parentheses (')')**:
   - If the stack is not empty, pop the top element.
   - If the stack is empty, push the current index as a new base.
   - Maintain the **maximum valid length** by subtracting indices.

### **Algorithm Steps:**

1. Initialize a **stack** and push `-1` as a base index.
2. Traverse **s** character by character:
   - If `'('`, push its index onto the stack.
   - If `')'`, pop from the stack.
     - If the stack becomes empty, push the current index.
     - Otherwise, update `max_length = max(max_length, i - st.top())`.
3. Return `max_length`.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** **O(N)**, as we traverse the string once.
- **Expected Auxiliary Space Complexity:** **O(N)**, for storing indices in the stack.

## 📝 **Solution Code**
## **Code (Java)**

```java
class Solution {
    static int maxLength(String s) {
        java.util.Stack<Integer> st = new java.util.Stack<>();
        st.push(-1);
        int m = 0;
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '(') st.push(i);
            else {
                st.pop();
                if (st.empty()) st.push(i);
                else m = Math.max(m, i - st.peek());
            }
        }
        return m;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---
