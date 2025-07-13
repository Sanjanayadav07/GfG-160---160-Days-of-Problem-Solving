---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Stack
  - Recursion
  - Backtracking
---

# 🚀 _Day 9. Decode the string_ 🧠

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/stack-gfg-160/problem/decode-the-string2444)

## 💡 **Problem Description:**

Given an encoded string `s`, the task is to decode it.  
The encoding rule is:

- `k[encoded_string]`, where the encoded string inside the square brackets is repeated exactly `k` times.
- Note: `k` is guaranteed to be a positive integer.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

s = "1[b]"

#### **Output:**

b

#### **Explanation:**

The string "b" is present only once.

### **Example 2:**

#### **Input:**

s = "3[b2[ca]]"

#### **Output:**

bcacabcacabcaca

#### **Explanation:**

- First, `2[ca]` expands to `caca`
- Then, `3[bcaca]` expands to `bcacabcacabcaca` which is the final output.

### **Constraints:**

- $\(1 \leq |s| \leq 10^5\)$

## 🎯 **My Approach:**

### **Stack-Based Iterative Approach (O(N) Time, O(N) Space)**

The goal is to parse and decode nested patterns like `k[encoded_string]` using a **stack-based simulation**.

### **Algorithm Steps:**

1. **Use two stacks**:
   - One for tracking the string built so far.
   - One for tracking the repetition counts (`k`).
2. **Iterate over the string**:
   - If you see a digit, accumulate it into `k`.
   - If you see `[`, push the current string and current `k` to the stacks, then reset them.
   - If you see `]`, pop the previous string and `k`, and append the current string repeated `k` times.
   - Otherwise, append the character to the current string.
3. The final decoded string will be the result.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(N), since each character is processed at most twice (once when pushed, once when popped).
- **Expected Auxiliary Space Complexity:** O(N), as the worst case (deeply nested or large repeated sections) can push every character onto the stack.

## 📝 **Solution Code**


## **Code (Java)**

```java
class Solution {
    static String decodeString(String s) {
        Stack<String> str = new Stack<>();
        Stack<Integer> num = new Stack<>();
        String cur = "";
        int n = 0;

        for (char c : s.toCharArray()) {
            if (Character.isDigit(c)) n = n * 10 + (c - '0');
            else if (c == '[') { str.push(cur); num.push(n); cur = ""; n = 0; }
            else if (c == ']') {
                String temp = cur;
                cur = str.pop();
                cur += temp.repeat(num.pop());
            } else cur += c;
        }
        return cur;
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---
