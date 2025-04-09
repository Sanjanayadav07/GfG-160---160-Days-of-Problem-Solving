---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Dynamic Programming
---

#  _Day 14. Subset Sum Problem_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/subset-sum-problem-1611555638)

## 💡 **Problem Description:**

Given an array of positive integers **arr[]** and a target value **sum**, determine if there exists a **subset** of `arr[]` whose sum is exactly equal to the given sum.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**
```cpp
arr[] = {3, 34, 4, 12, 5, 2}
sum = 9
```

#### **Output:**

```cpp
true
```

#### **Explanation:**

A subset `{4, 3, 2}` exists with sum = **9**.

### **Example 2:**

#### **Input:**

```cpp
arr[] = {3, 34, 4, 12, 5, 2}
sum = 30
```

#### **Output:**

```cpp
false
```

#### **Explanation:**

There is no subset with sum = **30**.

### **Example 3:**

#### **Input:**

```cpp
arr[] = {1, 2, 3}
sum = 6
```

#### **Output:**

```cpp
true
```

#### **Explanation:**

The entire array `{1, 2, 3}` forms the subset with sum = **6**.

## **Constraints:**

- $1 \leq \text{size of arr} \leq 200$
- $1 \leq arr[i] \leq 200$
- $1 \leq sum \leq 10^4$

## 🎯 **My Approach:**

### **Dynamic Programming (Optimized 1D DP) – O(N × sum) Time, O(sum) Space**

1. **Define a boolean DP array** `dp[sum + 1]`, where `dp[j]` tells whether sum `j` is possible.
2. **Base Case:** `dp[0] = true` (sum 0 is always achievable).
3. **Iterate through each number in the array** and update `dp[j]` for all `j` from `sum` down to `num`.
4. **Transition Formula:**  
   $\[
   \text{dp}[j] = \text{dp}[j] \ OR\ \text{dp}[j - \text{num}]
   $\]
   - If `dp[j - num]` was `true`, then `dp[j]` can also become `true` by including `num`.
5. **Return `dp[sum]` as the final answer**.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(N × sum), since we iterate through all elements and update the DP table.
- **Expected Auxiliary Space Complexity:** O(sum), as we use a 1D array of size `sum + 1`.

## 📝 **Solution Code**
## **Code (Java)**

```java
class Solution {
    static boolean isSubsetSum(int[] arr, int sum) {
        boolean[] dp = new boolean[sum + 1];
        dp[0] = true;
        for (int num : arr)
            for (int j = sum; j >= num; --j)
                dp[j] |= dp[j - num];
        return dp[sum];
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
