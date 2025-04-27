---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - Bit Manipulation
  - Bit Magic
---

#  _Day 4. Unique Number II_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/bit-manipulation-gfg-160/problem/finding-the-numbers0215)  

## 💡 **Problem Description:**

Given an array `arr[]` of size **2*N + 2**, where **2*N** elements appear in pairs and **two elements appear only once**, your task is to find those two **distinct unique numbers** and return them in **increasing order**.  

## 🔍 **Example Walkthrough:**

### **Example 1:**  

#### **Input:**  
`arr[] = [1, 2, 3, 2, 1, 4]`  

#### **Output:**  
`[3, 4]`

#### **Explanation:**  
3 and 4 occur exactly once in the array. All other elements appear in pairs.


### **Example 2:**  

#### **Input:**  
`arr[] = [2, 1, 3, 2]`  

#### **Output:**  
`[1, 3]`  

#### **Explanation:**  
1 and 3 occur only once. 2 appears twice.


### **Example 3:**  

#### **Input:**  
`arr[] = [2, 1, 3, 3]`  

#### **Output:**  
`[1, 2]`  

#### **Explanation:**  
1 and 2 occur once. 3 appears twice.


### **Constraints:**  
- $\(2 \leq \text{arr.size()} \leq 10^6\)$  
- $\(1 \leq \text{arr}[i] \leq 5 \times 10^6\)$  
- `arr.size()` is even  


## 🎯 **My Approach:**

### **XOR Partition Method**

This is the most efficient and clever approach using **bit manipulation**.

### **Algorithm Steps:**  
1. XOR all elements → result is XOR of the two unique numbers: `x = a ^ b`.  
2. Find the **rightmost set bit** in `x`.  
3. Partition the array into **two groups** based on this bit.  
4. XOR each group → you get `a` and `b` separately.  
5. Return the numbers in increasing order.


## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(n)`, as we iterate through the array a constant number of times.  
- **Expected Auxiliary Space Complexity:** `O(1)`, as we only use a constant number of variables.

## 📝 **Solution Code**
## **Code (Java)**

```java
class Solution {
    public int[] singleNum(int[] arr) {
       // Get the XOR of the two numbers we need to find
        int xorVal = 0;
        for (int i : arr) {
            xorVal ^= i;
        }

        // Get its last set bit
        xorVal &= -xorVal;

        int[] res = new int[2];

        for (int num : arr) {

            // If bit is not set, it belongs to the first set
            if ((num & xorVal) == 0) {
                res[0] ^= num;
            }

            // If bit is set, it belongs to the second set
            else {
                res[1] ^= num;
            }
        }

        // Ensure the order of the returned numbers is consistent
        if (res[0] > res[1]) {
            int temp = res[0];
            res[0] = res[1];
            res[1] = temp;
        }

        return res; 
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---
