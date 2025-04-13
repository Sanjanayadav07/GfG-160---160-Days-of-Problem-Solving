---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Dynamic Programming
  - Arrays
---

#  _Day 18. Stickler Thief_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/stickler-theif-1587115621)

## 💡 **Problem Description:**

Stickler the thief wants to loot money from houses arranged in a line. However, he **cannot loot two consecutive houses** to avoid being caught. His goal is to **maximize** the total amount looted.

Given an array **arr[]**, where `arr[i]` represents the amount of money in the `i`-th house, determine the **maximum amount** he can loot.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```cpp
arr[] = [6, 5, 5, 7, 4]
```

#### **Output:**

```cpp
15
```

#### **Explanation:**

Maximum loot can be obtained by robbing the **1st, 3rd, and 5th houses**:  
**6 + 5 + 4 = 15**

### **Example 2:**

#### **Input:**

```cpp
arr[] = [1, 5, 3]
```

#### **Output:**

```cpp
5
```

#### **Explanation:**

Best choice is to **loot only the 2nd house**, obtaining **5**.

### **Example 3:**

#### **Input:**

```cpp
arr[] = [4, 4, 4, 4]
```

#### **Output:**

```cpp
8
```

#### **Explanation:**

Stickler can loot **either** the **1st & 3rd houses** or **2nd & 4th houses** for a total of **4 + 4 = 8**.

### **Constraints:**

- $1 \leq \text{arr.size()} \leq 10^5$
- $1 \leq \text{arr}[i] \leq 10^4$

## 🎯 **My Approach:**

## **Optimized Dynamic Programming**

### **Algorithm Steps:**

1. Maintain **two variables**:
   - `prev2` → Stores the **loot obtained up to the house before the previous one**.
   - `prev1` → Stores the **loot obtained up to the previous house**.
2. Iterate through the array:
   - For each house `arr[i]`, decide whether to **loot it** or **skip it**.
   - If looted, the total becomes `prev2 + arr[i]`.
   - If skipped, the total remains `prev1`.
   - Update `prev2` and `prev1` accordingly.
3. Return `prev1` as the final answer.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** **O(N)**, since we iterate over the array once.
- **Expected Auxiliary Space Complexity:** **O(1)**, as we use only a few variables.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public int findMaxSum(int[] arr) {
        int prev2 = 0, prev1 = 0;
        for (int num : arr) {
            int temp = Math.max(prev1, prev2 + num);
            prev2 = prev1;
            prev1 = temp;
        }
        return prev1;
    }
}
```


## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
