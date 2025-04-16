---
Difficulty: Hard
Source: 160 Days of Problem Solving
Tags:
  - Dynamic Programming
  - Matrix
---

#  _Day 21. Matrix Chain Multiplication_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/matrix-chain-multiplication0303)

## 💡 **Problem Description:**

Given an array `arr[]` where the `i`th matrix has the dimensions **(arr[i-1] × arr[i])** for `i ≥ 1`, find the most efficient way to multiply these matrices together. The efficient way is the one that involves the least number of scalar multiplications.

You need to find the **minimum number of multiplications** required to multiply the matrices.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```plaintext
arr[] = [2, 1, 3, 4]
```

#### **Output:**

```plaintext
20
```

#### **Explanation:**

We have three matrices:

- `M1 (2×1)`, `M2 (1×3)`, and `M3 (3×4)`.
- There are two ways to multiply them:

  1. **((M1 × M2) × M3)**

     - Cost = `(2 × 1 × 3) + (2 × 3 × 4) = 30`

  2. **(M1 × (M2 × M3))**
     - Cost = `(1 × 3 × 4) + (2 × 1 × 4) = 20`

The minimum cost is **20**.

### **Example 2:**

#### **Input:**

```plaintext
arr[] = [1, 2, 3, 4, 3]
```

#### **Output:**

```plaintext
30
```

#### **Explanation:**

We have four matrices:

- `M1 (1×2)`, `M2 (2×3)`, `M3 (3×4)`, and `M4 (4×3)`.
- The minimum multiplication cost is **30**.

### **Example 3:**

#### **Input:**

```plaintext
arr[] = [3, 4]
```

#### **Output:**

```plaintext
0
```

#### **Explanation:**

There is only **one** matrix, so no multiplication is required.

## **Constraints:**

- $\(2 \leq \text{arr.size()} \leq 100\)$
- $\(1 \leq \text{arr}[i] \leq 200\)$

## 🎯 **My Approach:**

## **Bottom-Up Dynamic Programming**

### **Key Idea:**

We define **`dp[i][j]`** as the minimum number of scalar multiplications required to multiply matrices **from index `i` to `j`**.

### **Algorithm Steps:**

1. **Create a DP table** `dp[i][j]`, initialized to 0.
2. Iterate over **chain lengths** (`len = 2` to `n-1`).
3. Iterate over **starting indices** (`i = 1` to `n-len`), setting `j = i + len - 1`.
4. Compute the **minimum cost** for multiplying matrices from `i` to `j` by iterating over possible partition points `k`.
5. **Return `dp[1][n-1]`**, which contains the minimum multiplication cost.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(N³), since we iterate over `O(N²)` subproblems, and each subproblem requires `O(N)` operations.
- **Expected Auxiliary Space Complexity:** O(N²), for storing the DP table.

## 📝 **Solution Code**


## **Code (Java)**

```java
class Solution {
    static int matrixMultiplication(int[] arr) {
        int n = arr.length;
        int[][] dp = new int[n][n];

        for (int len = 2; len < n; len++)
            for (int i = 1, j = len; j < n; i++, j++) {
                dp[i][j] = Integer.MAX_VALUE;
                for (int k = i; k < j; k++)
                    dp[i][j] = Math.min(dp[i][j], arr[i - 1] * arr[k] * arr[j] + dp[i][k] + dp[k + 1][j]);
            }
        return dp[1][n - 1];
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
