---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Dynamic Programming
  - Arrays
---

#  _Day 19. Stickler Thief II_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/house-robber-ii)

## 💡 **Problem Description:**

You are given an array `arr[]` representing houses arranged in a **circular** fashion. Each house contains a certain value, and a thief aims to **maximize** the stolen amount while ensuring that **no two adjacent houses are robbed**.

Since the houses form a **circle**, the first and last house are also considered adjacent.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
arr[] = [2, 3, 2]
```

#### **Output:**

```
3
```

#### **Explanation:**

The houses at index **0 and 2** are adjacent, so they **cannot** be robbed together. The maximum amount that can be stolen is **3** (robbing the house at index `1`).

### **Example 2:**

#### **Input:**

```
arr[] = [1, 2, 3, 1]
```

#### **Output:**

```
4
```

#### **Explanation:**

The optimal strategy is to rob houses at index **0 and 2**, which gives **1 + 3 = 4**.

### **Example 3:**

#### **Input:**

```
arr[] = [2, 2, 3, 1, 2]
```

#### **Output:**

```
5
```

#### **Explanation:**

Possible choices:

1. **Rob house at index 0 and 2** → `2 + 3 = 5`
2. **Rob house at index 2 and 4** → `3 + 2 = 5`  
   The maximum amount that can be stolen is **5**.

### **Constraints:**

- $\(2 \leq \text{arr.size()} \leq 10^5\)$
- $\(0 \leq \text{arr}[i] \leq 10^4\)$

## 🎯 **My Approach:**

### **Optimized Dynamic Programming**

1. Since the houses are arranged **in a circle**, the **first and last houses cannot be robbed together**.
2. The problem reduces to **two linear House Robber problems**:
   - Robbing **from house 0 to n-2** (excluding the last house).
   - Robbing **from house 1 to n-1** (excluding the first house).
3. We solve the **House Robber problem** for both cases using **Dynamic Programming** with space optimization.
4. The final answer is the **maximum of both cases**.

### **Algorithm Steps:**

1. **Define a helper function** `robRange(l, r)`:
   - Use **two variables (prev1, prev2)** to track maximum money stolen up to the previous two houses.
   - Iterate through the houses from `l` to `r`, updating the maximum amount stolen.
   - Return `prev1` (max stolen amount).
2. **Compute the result** by taking the maximum of:
   - `robRange(0, n-2)` (excluding last house).
   - `robRange(1, n-1)` (excluding first house).
3. **Edge case:** If there's only **one house**, return its value.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(N), since we iterate through the houses twice.
- **Expected Auxiliary Space Complexity:** O(1), since we use only a few variables (constant space).

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public int maxValue(int[] nums) {
        int n = nums.length;
        if (n == 1) return nums[0];

        return Math.max(rob(nums, 0, n - 2), rob(nums, 1, n - 1));
    }

    private int rob(int[] nums, int l, int r) {
        int prev2 = 0, prev1 = 0;
        for (int i = l; i <= r; i++) {
            int curr = Math.max(prev1, prev2 + nums[i]);
            prev2 = prev1;
            prev1 = curr;
        }
        return prev1;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on **LinkedIn**: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository star.

---
