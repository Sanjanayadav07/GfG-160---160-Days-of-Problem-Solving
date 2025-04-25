---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - Bit Manipulation
  - Arrays
  - Searching
  - Bit Magic
---

#  _Day 2. Missing in Array_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/bit-manipulation-gfg-160/problem/missing-number-in-array1416)  

## 💡 **Problem Description:**

You are given an array `arr[]` of size **n - 1** that contains distinct integers in the range from **1 to n** (inclusive).  
The array represents a permutation of numbers from `1` to `n` with **one number missing**. Your task is to **find the missing number**.  

## 🔍 **Example Walkthrough:**

### **Example 1:**  

#### **Input:**  
arr[] = [1, 2, 3, 5]  

#### **Output:**  
4  

#### **Explanation:**  
All numbers from 1 to 5 should be present. The number **4** is missing.  


### **Example 2:**  

#### **Input:**  
arr[] = [8, 2, 4, 5, 3, 7, 1]  

#### **Output:**  
6  

#### **Explanation:**  
All numbers from 1 to 8 should be present. The number **6** is missing.  


### **Example 3:**  

#### **Input:**  
arr[] = [1]  

#### **Output:**  
2  

#### **Explanation:**  
Only 1 is present, hence the missing number is **2**.  


### **Constraints:**  
- $\(1 \leq \text{arr.size()} \leq 10^6\)$  
- $\(1 \leq \text{arr[i]} \leq \text{arr.size()} + 1\)$  


## 🎯 **My Approach:**

### **Optimal XOR Approach**

This approach relies on properties of XOR:
- **a ⊕ a = 0** and **a ⊕ 0 = a**
- If you XOR all numbers from `1 to n` and all elements in the array, the duplicate numbers cancel each other out, leaving only the missing number.

### **Algorithm Steps:**  
1. Initialize `x = 0`.  
2. XOR all elements of the array with `x`.  
3. XOR all numbers from `1` to `n` with `x`.  
4. The result is the missing number.  


## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(n)`, as we make two passes over the array (XOR and loop from 1 to n).  
- **Expected Auxiliary Space Complexity:** `O(1)`, as we use only a constant amount of additional space.  

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    int missingNum(int[] a) {
        int x = 0;
        for (int i = 0; i < a.length; ++i) x ^= a[i] ^ (i + 1);
        return x ^ (a.length + 1);
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---
