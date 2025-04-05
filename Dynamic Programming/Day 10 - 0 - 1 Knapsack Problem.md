---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Dynamic Programming
---

#  _Day 10. 0 - 1 Knapsack Problem_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/0-1-knapsack-problem0945)  

## 💡 **Problem Description:**

Given `n` items, each with a **weight** and **value**, and a knapsack with a capacity of `W`, the task is to determine the maximum total value that can be obtained by placing items in the knapsack **without exceeding its weight capacity**.  

🔹 **Note:**  
- Each item can be either **included** or **excluded** (hence, 0-1 Knapsack).  
- **Each item is available only once**.  


## 🔍 **Example Walkthrough:**

### **Example 1:**  
#### **Input:**  
```
W = 4  
val[] = [1, 2, 3]  
wt[] = [4, 5, 1]  
```
#### **Output:**  
```
3
```
#### **Explanation:**  
Choose the last item (value = 3, weight = 1), as it **fits within the weight limit** and maximizes the value.  


### **Example 2:**  
#### **Input:**  
```
W = 3  
val[] = [1, 2, 3]  
wt[] = [4, 5, 6]  
```
#### **Output:**  
```
0
```
#### **Explanation:**  
No item fits within the weight limit **W = 3**, so the maximum value obtained is **0**.  


### **Example 3:**  
#### **Input:**  
```
W = 5  
val[] = [10, 40, 30, 50]  
wt[] = [5, 4, 2, 3]  
```
#### **Output:**  
```
80
```
#### **Explanation:**  
- Select the **third item** (value = 30, weight = 2).  
- Select the **fourth item** (value = 50, weight = 3).  
- Total weight = **2 + 3 = 5** (within limit).  
- Total value = **30 + 50 = 80**.  


## **Constraints:**  
- $2 \leq \text{val.size()} = \text{wt.size()} \leq 10^3$  
- $1 \leq W \leq 10^3$  
- $1 \leq \text{val}[i] \leq 10^3$  
- $1 \leq \text{wt}[i] \leq 10^3$  


## 🎯 **My Approach:**
## **Optimized Space Dynamic Programming** 

### **Algorithm Steps:**  
1. **Use a 1D DP array (`dp[W+1]`)** to track the maximum value at each capacity from `0` to `W`.  
2. **Iterate over each item** and update the DP array **backwards** (from `W` to `wt[i]`), ensuring each item is used only once.  
3. **For each weight `j`**, decide whether to:  
   - **Include** the current item: `dp[j] = max(dp[j], val[i] + dp[j - wt[i]])`.  
   - **Exclude** the current item (keep previous value).  
4. **Return `dp[W]`**, which contains the maximum value achievable with capacity `W`.  


## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** `O(N * W)`, as we process `N` items and iterate over `W` capacities.  
- **Expected Auxiliary Space Complexity:** `O(W)`, as we use a **1D DP array** of size `W+1`.  

## 📝 **Solution Code**


## **Code (Java)**  
```java
class Solution {
    static int knapsack(int W, int[] val, int[] wt) {
        int[] dp = new int[W + 1];
        for (int i = 0; i < wt.length; i++) 
            for (int j = W; j >= wt[i]; j--) 
                dp[j] = Math.max(dp[j], val[i] + dp[j - wt[i]]);
        return dp[W];
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
