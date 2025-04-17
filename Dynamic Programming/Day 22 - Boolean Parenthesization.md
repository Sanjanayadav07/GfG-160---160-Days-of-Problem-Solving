---
Difficulty: Hard
Source: 160 Days of Problem Solving
Tags:
  - Dynamic Programming
---

#  _Day 22. Boolean Parenthesization_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/boolean-parenthesization5610)

## 💡 **Problem Description:**

Given a **boolean expression** `s` consisting of:

- **Operands**:
  - `'T'` → **True**
  - `'F'` → **False**
- **Operators**:
  - `'&'` → **Boolean AND**
  - `'|'` → **Boolean OR**
  - `'^'` → **Boolean XOR**

Count the **number of ways** we can parenthesize the expression such that it evaluates to **True**.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```cpp
s = "T|T&F^T"
```

#### **Output:**

```cpp
4
```

#### **Explanation:**

The expression evaluates to **True** in **4 ways**:

1. `((T | T) & (F ^ T)) → (T | T) → T, (F ^ T) → T, T & T = T ✅`
2. `(T | (T & (F ^ T))) → (F ^ T) → T, (T & T) → T, T | T = T ✅`
3. `(((T | T) & F) ^ T) → (T | T) → T, (T & F) → F, F ^ T = T ✅`
4. `(T | ((T & F) ^ T)) → (T & F) → F, (F ^ T) → T, T | T = T ✅`

### **Example 2:**

#### **Input:**

```cpp
s = "T^F|F"
```

#### **Output:**

```cpp
2
```

#### **Explanation:**

The expression evaluates to **True** in **2 ways**:

1. `((T^F)|F)`
2. `(T^(F|F))`

## **Constraints:**

- $\(1 \leq |s| \leq 100\)$

## 🎯 **My Approach:**

The problem follows **optimal substructure** and **overlapping subproblems**, making **Dynamic Programming (DP)** the most efficient approach.

We use a **bottom-up DP approach** where we maintain two **2D DP tables**:

- `T[i][j]` → Number of ways to parenthesize `s[i:j]` to get **True**.
- `F[i][j]` → Number of ways to parenthesize `s[i:j]` to get **False**.

### **Algorithm Steps:**

1. **Initialize the DP tables**:

   - If `s[i] == 'T'`, set `T[i][i] = 1` (since a single `T` is always `True`).
   - If `s[i] == 'F'`, set `F[i][i] = 1` (since a single `F` is always `False`).

2. **Fill the DP tables using a bottom-up approach**:

   - Iterate over **subexpressions of increasing length (`l`)**, from **2 to n**.
   - For each subexpression `s[i:j]`, check **each operator `s[k]`** (where `k` is an odd index).
   - Compute `T[i][j]` and `F[i][j]` using **previously computed DP values**.

3. **Update DP values based on the operator `s[k]`**:

   - If `s[k] == '&'` (**AND operator**):
     - `T[i][j] += lt * rt` (both left and right must be True).
     - `F[i][j] += lt * rf + lf * rt + lf * rf` (any case where at least one is False).
   - If `s[k] == '|'` (**OR operator**):
     - `T[i][j] += lt * rt + lt * rf + lf * rt` (only both False make it False).
     - `F[i][j] += lf * rf`.
   - If `s[k] == '^'` (**XOR operator**):
     - `T[i][j] += lt * rf + lf * rt` (one True, one False).
     - `F[i][j] += lt * rt + lf * rf` (both True or both False).

4. **Return `T[0][n-1]`**, which gives the total ways to evaluate `s` to `True`.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(N³), as we process all partitions `(i, k, j)` for each segment of `s`.
- **Expected Auxiliary Space Complexity:** O(N²), for storing `T` and `F` DP tables.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    static int countWays(String s) {
        int n = s.length();
        int[][] T = new int[n][n], F = new int[n][n];
        for (int i = 0; i < n; i += 2) T[i][i] = s.charAt(i) == 'T' ? 1 : 0;
        for (int i = 0; i < n; i += 2) F[i][i] = s.charAt(i) == 'F' ? 1 : 0;
        for (int l = 2; l < n; l += 2)
            for (int i = 0; i < n - l; i += 2)
                for (int k = i + 1, j = i + l; k < j; k += 2) {
                    int lt = T[i][k - 1], lf = F[i][k - 1], rt = T[k + 1][j], rf = F[k + 1][j];
                    if (s.charAt(k) == '&') {
                        T[i][j] += lt * rt;
                        F[i][j] += lt * rf + lf * rt + lf * rf;
                    } else if (s.charAt(k) == '|') {
                        T[i][j] += lt * rt + lt * rf + lf * rt;
                        F[i][j] += lf * rf;
                    } else {
                        T[i][j] += lt * rf + lf * rt;
                        F[i][j] += lt * rt + lf * rf;
                    }
                }
        return T[0][n - 1];
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
