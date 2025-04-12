---
Difficulty: Hard
Source: 160 Days of Problem Solving
Tags:
  - Dynamic Programming
  - Arrays
---

#  _Day 17. Stock Buy and Sell – Max 2 Transactions Allowed_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/buy-and-sell-a-share-at-most-twice)

## 💡 **Problem Description:**

In daily share trading, a trader buys shares and sells them on the same day. Given an array **prices[]** representing stock prices throughout the day, find the **maximum profit** a trader could have made with at most **2 transactions**.

⚠ **Note:** The second transaction can only start after the first one is complete (**buy → sell → buy → sell**).

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```cpp
prices[] = [10, 22, 5, 75, 65, 80]
```

#### **Output:**

```cpp
87
```

#### **Explanation:**

- Buy at **10**, sell at **22** → **Profit = 12**
- Buy at **5**, sell at **80** → **Profit = 75**
- **Total Profit = 12 + 75 = 87**

### **Example 2:**

#### **Input:**

```cpp
prices[] = [2, 30, 15, 10, 8, 25, 80]
```

#### **Output:**

```cpp
100
```

#### **Explanation:**

- Buy at **2**, sell at **30** → **Profit = 28**
- Buy at **8**, sell at **80** → **Profit = 72**
- **Total Profit = 28 + 72 = 100**

### **Constraints:**

- $1 \leq \text{prices.size()} \leq 10^5$
- $1 \leq \text{prices[i]} \leq 10^5$

## 🎯 **My Approach:**

### **Optimized Greedy Approach**

1. Use **four variables**:
   - `b1` (Best price to buy first stock)
   - `s1` (Best profit after first sale)
   - `b2` (Best price to buy second stock after first sale)
   - `s2` (Best profit after second sale)
2. Iterate through prices and update these variables accordingly.
3. Return `s2` (Maximum profit with at most two transactions).

### **Algorithm Steps:**

1. Initialize `b1 = ∞`, `s1 = 0`, `b2 = ∞`, `s2 = 0`.
2. **For each price `p` in the array:**
   - Update `b1` (Minimum price to buy first stock).
   - Update `s1` (Best profit after first sale).
   - Update `b2` (Best price to buy second stock).
   - Update `s2` (Best profit after second sale).
3. Return `s2`.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(N), as we traverse the array once and perform a constant number of operations.
- **Expected Auxiliary Space Complexity:** O(1), as we use only four variables.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public int maxProfit(int[] a) {
        int b1 = Integer.MAX_VALUE, s1 = 0, b2 = Integer.MAX_VALUE, s2 = 0;
        for (int p : a) {
            b1 = Math.min(b1, p);
            s1 = Math.max(s1, p - b1);
            b2 = Math.min(b2, p - s1);
            s2 = Math.max(s2, p - b2);
        }
        return s2;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
