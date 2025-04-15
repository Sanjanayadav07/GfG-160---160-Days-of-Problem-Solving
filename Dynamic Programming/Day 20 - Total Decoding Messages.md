---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Dynamic Programming
---

#  _Day 20. Total Decoding Messages_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/total-decoding-messages1235)

## **Problem Description**

A message containing letters **A-Z** is encoded using the following mapping:

```
'A' -> "1"
'B' -> "2"
...
'Z' -> "26"
```

Given a **numeric string `digits`**, return the total number of ways the message can be decoded.

## **Examples**

### **Example 1:**

#### **Input:**

```
digits = "123"
```

#### **Output:**

```
3
```

#### **Explanation:**

"123" can be decoded as:

- `"ABC"` (1, 2, 3)
- `"LC"` (12, 3)
- `"AW"` (1, 23)

### **Example 2:**

#### **Input:**

```
digits = "90"
```

#### **Output:**

```
0
```

#### **Explanation:**

"90" is not a valid encoding because '0' cannot be decoded.

### **Example 3:**

#### **Input:**

```
digits = "05"
```

#### **Output:**

```
0
```

#### **Explanation:**

"05" is not valid because leading zero makes it an invalid encoding.

### **Constraints:**

- $\(1 \leq \text{digits.length} \leq 10^3\)$

## 🎯 **My Approach:**

## **Optimized Space Dynamic Programming**

### **Algorithm Steps:**

1. **Edge Case Handling**: If `digits[0] == '0'`, return 0 because it cannot be decoded.
2. **Use Two Variables (`prev2` and `prev1`)**:
   - `prev1`: Stores the number of ways to decode up to index `i-1`.
   - `prev2`: Stores the number of ways to decode up to index `i-2`.
3. **Iterate Over the String**:
   - If `digits[i]` is not `'0'`, add `prev1` to the current count.
   - If `digits[i-1]digits[i]` forms a valid number (10-26), add `prev2`.
4. **Update `prev2` and `prev1` for the next iteration**.

## **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(N), as we iterate through the string once.
- **Expected Auxiliary Space Complexity:** O(1), since we use only two variables.

## **Code (Java)**

```java
class Solution {
    public int countWays(String s) {
        if (s.charAt(0) == '0') return 0;
        int prev2 = 1, prev1 = 1;
        for (int i = 1; i < s.length(); i++) {
            int curr = (s.charAt(i) != '0') ? prev1 : 0;
            if (s.charAt(i - 1) != '0' && Integer.parseInt(s.substring(i - 1, i + 1)) <= 26)
                curr += prev2;
            prev2 = prev1;
            prev1 = curr;
        }
        return prev1;
    }
}
```

##**Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on **LinkedIn**: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a **star**! ⭐
