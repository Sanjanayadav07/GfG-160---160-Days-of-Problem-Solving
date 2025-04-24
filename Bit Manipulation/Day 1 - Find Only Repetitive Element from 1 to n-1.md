---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - Bit Manipulation
  - two-pointer-algorithm
  - Arrays
---

#  _Day 1. Find Only Repetitive Element from 1 to n-1_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/bit-manipulation-gfg-160/problem/find-repetitive-element-from-1-to-n-1)  

## 💡 **Problem Description:**

Given an array `arr[]` of size `n`, filled with numbers from `1` to `n-1` in random order. The array has **only one repetitive element**. Your task is to find this **repeating element**.

> It is guaranteed that **there is exactly one repeating element**.


## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**
```
arr[] = [1, 3, 2, 3, 4]
```

#### **Output:**
```
3
```

#### **Explanation:**
The number `3` is repeated in the array.


### **Example 2:**

#### **Input:**
```
arr[] = [1, 5, 1, 2, 3, 4]
```

#### **Output:**
```
1
```

#### **Explanation:**
The number `1` appears twice.


### **Example 3:**

#### **Input:**
```
arr[] = [1, 1]
```

#### **Output:**
```
1
```

#### **Explanation:**
The only possible value `1` is repeated.


## **Constraints:**

- $\(2 \leq \text{arr.size()} \leq 10^5\)$
- $\(1 \leq \text{arr}[i] \leq n - 1\)$


## 🎯 **My Approach:**

### **Algorithm Steps:**

1. -Initialize an empty HashSet.

- Loop through each number in the array.

- Check if the number exists in the HashSet:

- If yes, return that number (it's the first duplicate).

- If no, add the number to the HashSet.

- After the loop, return -1 (no duplicates found).


## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public int findDuplicate(int[] arr) {
        // code here
        HashSet<Integer> set = new HashSet<>();
        
        for(int x : arr) {
            if(set.contains(x)) {
                return x;
            }
            set.add(x);
        }
        return -1;
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007/). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---


