---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Dynamic Programming
  - Subset
---

#  _Day 15. Partition Equal Subset Sum_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/subset-sum-problem2014)

## 💡 **Problem Description:**

Given an array `arr[]`, determine if it can be **partitioned into two subsets** such that the sum of elements in both parts is the same.

Each element must be in exactly **one subset**.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
arr = [1, 5, 11, 5]
```

#### **Output:**

```
True
```

#### **Explanation:**

The array can be partitioned into **[1, 5, 5]** and **[11]**, both having the sum **11**.

### **Example 2:**

#### **Input:**

```
arr = [1, 3, 5]
```

#### **Output:**

```
False
```

#### **Explanation:**

There is no way to split the array into two subsets with equal sum.

## **Constraints:**

- $\(1 \leq arr.size \leq 100\)$
- $\(1 \leq arr[i] \leq 200\)$

## 🎯 **My Approach:**

## **Optimized 1D Dynamic Programming**

### **Algorithm Steps:**

1. **Calculate the total sum** of the array. If it's **odd**, return false (cannot be evenly split).
2. **Use a DP table (`dp[j]`)**, where `dp[j]` tells if we can form sum `j`.
3. **Initialize** `dp[0] = true`, since a sum of **0** is always possible.
4. **Iterate through each element** in the array:
   - Update `dp[j] = dp[j] OR dp[j - num]` for `j = target` down to `num`.
5. If `dp[target]` is **true**, we can partition the array into two subsets with equal sum.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** $O(N \times sum)$, as we iterate over the elements and process sums up to `sum/2`.
- **Expected Auxiliary Space Complexity:** $O(sum)$, as we use a 1D DP array of size `sum/2 + 1`.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    static boolean equalPartition(int[] arr) {
        int sum = Arrays.stream(arr).sum();
        if (sum % 2 != 0) return false;
        int target = sum / 2;
        boolean[] dp = new boolean[target + 1];
        dp[0] = true;
        for (int num : arr)
            for (int j = target; j >= num; --j)
                dp[j] |= dp[j - num];
        return dp[target];
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
