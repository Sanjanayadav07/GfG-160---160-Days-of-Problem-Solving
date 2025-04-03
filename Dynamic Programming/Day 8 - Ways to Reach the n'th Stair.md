---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Dynamic Programming
  - sliding-window
  - Mathematical
---

#  _Day 8. Ways to Reach the n'th Stair_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/count-ways-to-reach-the-nth-stair-1587115620)  

## 💡 **Problem Description:**

There are `n` stairs, and a person standing at the bottom wants to reach the top. The person can climb either **1 stair** or **2 stairs** at a time. Your task is to **count the number of ways** the person can reach the top (order matters).  

## 🔍 **Example Walkthrough:**

### **Example 1:**  

#### **Input:**  
```
n = 1
```
#### **Output:**  
```
1
```

#### **Explanation:**  
There is only one way to climb 1 stair — just **one step** of size 1.  


### **Example 2:**  

#### **Input:**  
```
n = 2
```
#### **Output:**  
```
2
```

#### **Explanation:**  
There are two ways to reach the 2nd stair:  
1. (1, 1)  
2. (2)  


### **Example 3:**  

#### **Input:**  
```
n = 4
```
#### **Output:**  
```
5
```

#### **Explanation:**  
There are five ways to climb 4 stairs:  
1. (1, 1, 1, 1)  
2. (1, 1, 2)  
3. (1, 2, 1)  
4. (2, 1, 1)  
5. (2, 2)  


### **Constraints:**  
- $\(1 \le n \le 44\)$  

  

## 🎯 **My Approach:**

### **Iterative (Space-Optimized DP)**
1. We know this is essentially the **Fibonacci sequence** shifted by one index.  
2. Use **two variables** `a` and `b` to track the ways to climb `(n-1)` and `n` stairs.  
3. Initially, `a = 1` and `b = 1`, representing ways to climb `0` or `1` stairs.  
4. Update in a loop from `2` to `n`, computing `b = a + b` (the sum of ways to climb `(n-1)` and `(n-2)`), then shift `a` to the old `b`.  

This approach eliminates the need for an entire DP array and uses only **constant space**.  

  

## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** `O(n)`, as we iterate from 2 to n once.  
- **Expected Auxiliary Space Complexity:** `O(1)`, since we only use a constant amount of extra space (two variables).  

  
## 📝 **Solution Code**

## **Code (Java)**
```java
class Solution {
    public long countWays(int n) {
        long a = 1, b = 1;
        while (n-- > 1) {
            b += a;
            a = b - a;
        }
        return b;
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
