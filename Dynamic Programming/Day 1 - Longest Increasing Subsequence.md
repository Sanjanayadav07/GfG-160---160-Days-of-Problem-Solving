---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Dynamic Programming
  - Binary Search
---

#  _Day 1. Longest Increasing Subsequence_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/longest-increasing-subsequence-1587115620)  


## 💡 **Problem Description:**

Given an array **arr[]** of non-negative integers, the task is to find the length of the **Longest Strictly Increasing Subsequence (LIS)**.

A **subsequence** is strictly increasing if each element in the subsequence is strictly less than the next element.


## 🔍 **Example Walkthrough:**

### **Example 1:**  
#### **Input:**  
`arr[] = [5, 8, 3, 7, 9, 1]`

#### **Output:**  
`3`

#### **Explanation:**  
The longest strictly increasing subsequence could be `[5, 7, 9]`, which has a length of `3`.


### **Example 2:**  
#### **Input:**  
`arr[] = [0, 8, 4, 12, 2, 10, 6, 14, 1, 9, 5, 13, 3, 11, 7, 15]`

#### **Output:**  
`6`

#### **Explanation:**  
One of the possible longest strictly increasing subsequences is `[0, 2, 6, 9, 13, 15]`, which has a length of `6`.


### **Example 3:**  
#### **Input:**  
`arr[] = [3, 10, 2, 1, 20]`

#### **Output:**  
`3`

#### **Explanation:**  
The longest strictly increasing subsequence could be `[3, 10, 20]`, which has a length of `3`.


### **Constraints:**  
- $\(1 \leq arr.size() \leq 10^3\)$  
- $\(0 \leq arr[i] \leq 10^6\)$  



## 🎯 **My Approach:**

### **1️⃣ Optimized Binary Search Approach**

### **Algorithm Steps:**  
1. Iterate through each element of the array.
2. Maintain a **list `ans` which tracks the smallest possible tail for increasing subsequences of different lengths.**
3. For each element, **find its correct position in `ans` using `lower_bound` (binary search)**.
4. If the element can extend the current LIS, append it to `ans`, else replace the element at the correct position in `ans` to keep `ans` optimized.
5. The size of `ans` at the end represents the **length of the longest increasing subsequence**.

### **Step-by-step Process**  
1. Initialize an empty list `lis`.
2. For each element `num` in the array:
    - Use **binary search (`lower_bound`) to find the position where `num` can replace or extend the `lis` list.**
    - If `num` is larger than all elements in `lis`, append it.
    - Otherwise, replace the existing element at the correct position with `num`, maintaining the smallest possible value for subsequences of that length.
3. Return the **size of `lis`**, which is the length of the **Longest Increasing Subsequence**.


## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** O(N log N), where `N` is the size of the array, as we perform binary search for each element.  
- **Expected Auxiliary Space Complexity:** O(N), for storing the `ans` array.

## 📝 **Solution Code**

## **Code (Java)**  

```java
class Solution {
    public int lis(int[] arr) {
        ArrayList<Integer> ans = new ArrayList<>();
        for (int num : arr) {
            int idx = Collections.binarySearch(ans, num);
            if (idx < 0) idx = -idx - 1;
            if (idx == ans.size()) ans.add(num);
            else ans.set(idx, num);
        }
        return ans.size();
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!  

⭐ **If you find this helpful, please give this repository a star!** ⭐  

--- 
