---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Dynamic Programming
---

#  _Day 12. Coin Change (Minimum Coins)_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/number-of-coins1824)

## 💡 **Problem Description:**

Given an array `coins[]` of distinct denominations and an integer `sum`, determine the **minimum number of coins** required to make up the given sum.  
You have **an infinite supply** of each type of coin.  
If the sum **cannot be formed**, return `-1`.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
coins[] = [25, 10, 5]
sum = 30
```

#### **Output:**

```
2
```

#### **Explanation:**

The minimum number of coins required is **2** (25 + 5).

### **Example 2:**

#### **Input:**

```
coins[] = [9, 6, 5, 1]
sum = 19
```

#### **Output:**

```
3
```

#### **Explanation:**

The minimum number of coins required is **3** (9 + 9 + 1).

### **Example 3:**

#### **Input:**

```
coins[] = [5, 1]
sum = 0
```

#### **Output:**

```
0
```

#### **Explanation:**

For a target sum of **0**, no coins are needed.

### **Example 4:**

#### **Input:**

```
coins[] = [4, 6, 2]
sum = 5
```

#### **Output:**

```
-1
```

#### **Explanation:**

It's **not possible** to obtain a sum of `5` using the given coins.

### **Constraints:**

- $\(1 \leq \text{sum} \times \text{coins.size()} \leq 10^6\)$
- $\(0 \leq \text{sum} \leq 10^4\)$
- $\(1 \leq \text{coins}[i] \leq 10^4\)$
- $\(1 \leq \text{coins.size()} \leq 10^3\)$

## 🎯 **My Approach:**

## **Optimized Dynamic Programming**

### **Algorithm Steps:**

1. **Define `dp[j]`** as the minimum number of coins needed to obtain `sum = j`.
2. **Base Case:** `dp[0] = 0` (zero sum requires zero coins).
3. **Transition:**
   - For each `coin`, update `dp[j]` for all `j >= coin` using:  
     $\[
     dp[j] = \min(dp[j], dp[j - coin] + 1)
     $\]
4. **Final Check:** If `dp[sum] == ∞`, return `-1` (sum cannot be formed).

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(N × sum), as we iterate over each coin and process all sums up to `sum`.
- **Expected Auxiliary Space Complexity:** O(sum), as we maintain a 1D DP array of size `sum + 1`.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public int minCoins(int[] coins, int sum) {
        int[] dp = new int[sum + 1];
        Arrays.fill(dp, Integer.MAX_VALUE);
        dp[0] = 0;
        for (int c : coins)
            for (int j = c; j <= sum; j++)
                if (dp[j - c] != Integer.MAX_VALUE)
                    dp[j] = Math.min(dp[j], dp[j - c] + 1);
        return dp[sum] == Integer.MAX_VALUE ? -1 : dp[sum];
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
