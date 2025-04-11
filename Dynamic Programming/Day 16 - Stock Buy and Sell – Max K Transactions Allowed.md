---
Difficulty: Hard
Source: 160 Days of Problem Solving
Tags:
  - Dynamic Programming
---

#  _Day 16. Stock Buy and Sell – Max K Transactions Allowed_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/maximum-profit4657)

## 💡 **Problem Description:**

In the stock market, a person can buy a stock and sell it on a future date. You are given an array **prices[]** representing stock prices on different days and a positive integer **k**.

Find out the **maximum profit** a person can make with **at most k transactions**.

A **transaction** consists of **buying** and subsequently **selling** a stock. A new transaction can only start after completing the previous one.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
prices = [10, 22, 5, 80]
k = 2
```

#### **Output:**

```
87
```

#### **Explanation:**

1. **Buy at 10, Sell at 22** → Profit = **12**
2. **Buy at 5, Sell at 80** → Profit = **75**  
   **Total Profit = 12 + 75 = 87**

### **Example 2:**

#### **Input:**

```
prices = [20, 580, 420, 900]
k = 3
```

#### **Output:**

```
1040
```

#### **Explanation:**

1. **Buy at 20, Sell at 580** → Profit = **560**
2. **Buy at 420, Sell at 900** → Profit = **480**  
   **Total Profit = 560 + 480 = 1040**

### **Example 3:**

#### **Input:**

```
prices = [100, 90, 80, 50, 25]
k = 1
```

#### **Output:**

```
0
```

#### **Explanation:**

- The stock price is **continuously decreasing**, so there is **no profit possible**.

### **Constraints:**

- $\(1 \leq \text{prices.size()} \leq 10^3\)$
- $\(1 \leq k \leq 200\)$
- $\(1 \leq \text{prices}[i] \leq 10^3\)$

## 🎯 **My Approach:**

## **Optimized Dynamic Programming**

1. If **2 \* k >= n**, it's optimal to perform **all profitable transactions**, similar to an **unlimited transactions problem**.
2. Otherwise, we use a **1D DP table** (`dp[2*k+1]`) to store the **best profit for different transaction states**:
   - **Odd indices** → Buying states
   - **Even indices** → Selling states
3. **Iterate through the stock prices** and update `dp[]` based on previous values:
   - If **buying**, maximize profit by either **holding** or **buying today**.
   - If **selling**, maximize profit by either **selling today** or **holding**.

### **Algorithm Steps:**

1. If `k == 0`, return **0** (no transactions allowed).
2. If **2 \* k >= n**, return the **sum of all upward price differences**.
3. Initialize `dp[2*k+1]` with `-∞` for buy states and `0` for the rest.
4. **Iterate through prices** and update `dp[j]` for **all transactions**.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(K × N), since we iterate over `prices[]` for each transaction.
- **Expected Auxiliary Space Complexity:** O(2K), since we only use a `dp[]` array of size `2K + 1`.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public static int maxProfit(int[] prices, int k) {
        int n = prices.length;
        if (n == 0 || k == 0) return 0;
        if (2 * k >= n) {
            int profit = 0;
            for (int i = 1; i < n; i++)
                profit += Math.max(0, prices[i] - prices[i - 1]);
            return profit;
        }
        int[] dp = new int[2 * k + 1];
        Arrays.fill(dp, Integer.MIN_VALUE);
        dp[0] = 0;
        for (int price : prices)
            for (int j = 1; j <= 2 * k; j++)
                dp[j] = (j % 2 == 1) ? Math.max(dp[j], dp[j - 1] - price) : Math.max(dp[j], dp[j - 1] + price);
        return dp[2 * k];
    }
}
```


## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐
