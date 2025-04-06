---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Dynamic Programming
  - Arrays
---

#  _Day 11. Coin Change (Count Ways)_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/coin-change2448)

## 💡 **Problem Description:**

Given an integer array **coins[]** representing different denominations of currency and an integer **sum**, find the **number of ways** to make `sum` using any number of coins.  
🔹 **Note:** You have an **infinite** supply of each type of coin.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```plaintext
coins = [1, 2, 3], sum = 4
```

#### **Output:**

```plaintext
4
```

#### **Explanation:**

There are **4 ways** to make `4` using given coins:

1. `[1, 1, 1, 1]`
2. `[1, 1, 2]`
3. `[2, 2]`
4. `[1, 3]`

### **Example 2:**

#### **Input:**

```plaintext
coins = [2, 5, 3, 6], sum = 10
```

#### **Output:**

```plaintext
5
```

#### **Explanation:**

There are **5 ways** to make `10`:

1. `[2, 2, 2, 2, 2]`
2. `[2, 2, 3, 3]`
3. `[2, 2, 6]`
4. `[2, 3, 5]`
5. `[5, 5]`

### **Constraints:**

- $1 \leq \text{Number of Coins} \leq 10^3$
- $1 \leq \text{sum} \leq 10^6$
- $1 \leq \text{coins}[i] \leq 10^3$

## 🎯 **My Approach:**

## **Optimized Dynamic Programming**

### **Algorithm Steps:**

1. Use a **1D DP array** `dp[]`, where `dp[i]` stores the **number of ways** to make sum `i`.
2. **Base Case:**
   - `dp[0] = 1` (There is **one way** to make sum `0`: choose nothing).
3. **Transition:**
   - For each `coin`, update all sums from `coin` to `sum`.
   - `dp[j] += dp[j - coin]` (Include current coin).

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(N × sum)`, where `N` is the number of coins.
- **Expected Auxiliary Space Complexity:** `O(sum)`, as we only store a 1D DP array.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public int count(int[] coins, int sum) {
        int[] dp = new int[sum + 1];
        dp[0] = 1;
        for (int coin : coins)
            for (int j = coin; j <= sum; j++)
                dp[j] += dp[j - coin];
        return dp[sum];
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
