---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - Bit Manipulation
  - Bit Magic
---

#  _Day 3. Unique Number I_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/bit-manipulation-gfg-160/problem/find-unique-number)


## 💡 **Problem Description:**

You are given an **unsorted array** of positive integers in which **every element occurs exactly twice**, except for **one element that appears only once**. Your task is to **find that unique number**.


## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**
```
arr[] = [1, 2, 1, 5, 5]
```

#### **Output:**
```
2
```

#### **Explanation:**
All elements except **2** occur twice. Hence, the unique number is **2**.


### **Example 2:**

#### **Input:**
```
arr[] = [2, 30, 2, 15, 20, 30, 15]
```

#### **Output:**
```
20
```

#### **Explanation:**
Only **20** appears once. All other elements occur twice.


### **Constraints:**
- $\(1 \leq \text{arr.size()} \leq 10^6\)$  
- $\(0 \leq \text{arr}[i] \leq 10^9\)$


## 🎯 **My Approach:**

### **Bit Manipulation (XOR Method)**

- The **XOR** of two equal numbers is 0.  
- XOR of a number with 0 is the number itself.  
- Thus, XOR-ing all numbers will cancel out the duplicates and leave the unique one.

### **Algorithm Steps:**
1. Initialize result as 0.
2. Iterate over the array and XOR each number with the result.
3. Final result is the unique number.


## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(n)`, as we traverse the array once.  
- **Expected Auxiliary Space Complexity:** `O(1)`, as we only use a constant amount of extra space.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public int findUnique(int[] arr) {
        int r = 0;
        for (int x : arr) r ^= x;
        return r;
    }
}
```

## **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐
