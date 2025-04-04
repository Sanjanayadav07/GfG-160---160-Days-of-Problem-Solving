---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Dynamic Programming
---

#  _Day 9. Min Cost Climbing Stairs_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/min-cost-climbing-stairs)  

## 💡 **Problem Description:**

Given an array of integers `cost[]`, where `cost[i]` represents the cost of the `i-th` step on a staircase, you can either:  
- Pay the cost at `i-th` step and move **one step** forward.  
- Pay the cost at `i-th` step and move **two steps** forward.  

Return the **minimum cost** required to reach the top of the floor.  

📌 **Assumptions:**  
- **0-based indexing**  
- You can start either from **step 0** or **step 1**  

## 🔍 **Example Walkthrough:**

### **Example 1:**  
#### **Input:**  
```cpp
cost[] = [10, 15, 20]
```
#### **Output:**  
```cpp
15
```
#### **Explanation:**  
The cheapest way is:  
- Start at `cost[1] = 15`  
- Jump **2 steps** to the top (no cost at the top)  

<img src="https://github.com/user-attachments/assets/70112a65-01f8-4b37-9d6e-b9740c45049a" width="30%">



### **Example 2:**  
#### **Input:**  
```cpp
cost[] = [1, 100, 1, 1, 1, 100, 1, 1, 100, 1]
```
#### **Output:**  
```cpp
6
```
#### **Explanation:**  
The cheapest way is:  
1 → 3 → 4 → 6 → 7 → 9 (Total cost = `1 + 1 + 1 + 1 + 1 + 1 = 6`)  

<img src="https://github.com/user-attachments/assets/4cc857d1-2e6e-44df-ad87-35521adaff27" width="30%">



## **Constraints:**  
- $\(2 \leq \text{cost.length} \leq 1000\)$
- $2 ≤ cost.size() ≤ 10^5$
- $\(0 \leq \text{cost[i]} \leq 999\)$  


## 🎯 **My Approach:**

### **Algorithm Steps:**  
1. **Use two variables** `a` and `b` to keep track of the **minimum cost** of the last two steps.  
2. **Iterate through the cost array**, updating `b` using the recurrence relation:  
   - `b = cost[i] + min(a, b)`  
   - `a = previous b` (before update)  
3. **Return** `min(a, b)`, representing the minimum cost to reach the top.
    
## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** `O(N)`, as we iterate through the `cost` array once.  
- **Expected Auxiliary Space Complexity:** `O(1)`, as we use only a constant amount of extra space (`a` and `b`).
  
## 📝 **Solution Code**

## **Code (Java)**  
```java
class Solution {
    public int minCostClimbingStairs(int[] cost) {
        int a = cost[0], b = cost[1];
        for (int i = 2; i < cost.length; i++) {
            int temp = b;
            b = cost[i] + Math.min(a, b);
            a = temp;
        }
        return Math.min(a, b);
    }
}
```


## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐
