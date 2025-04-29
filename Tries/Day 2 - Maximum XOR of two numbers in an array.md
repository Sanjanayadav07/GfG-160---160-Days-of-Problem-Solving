---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Bit Magic
  - Tries
---

#  _Day 2. Maximum XOR of two numbers in an array_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/tries-gfg-160/problem/maximum-xor-of-two-numbers-in-an-array)  

## 💡 **Problem Description:**

Given an array `arr[]` of **non-negative integers**, your task is to find the **maximum XOR** value that can be obtained by XORing any two distinct elements of the array.


## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**
`arr[] = [25, 10, 2, 8, 5, 3]`

#### **Output:**  
`28`

#### **Explanation:**  
The pair `(25 ^ 5)` gives the maximum XOR value which is `28`.


### **Example 2:**

#### **Input:**
`arr[] = [1, 2, 3, 4, 5, 6, 7]`

#### **Output:**  
`7`

#### **Explanation:**  
The pair `(1 ^ 6)` gives the maximum XOR value which is `7`.


### **Constraints:**  
- $\(2 \leq \text{arr.size()} \leq 5 \times 10^4\)$  
- $\(1 \leq \text{arr[i]} \leq 10^6\)$  


## 🎯 **My Approach:**

### **Greedy Bitmasking with HashSet**
1. Iterate from **MSB to LSB** (31 to 0).
2. At each bit position:
   - Mask numbers to keep the current prefix.
   - Try setting the current bit in the result.
   - Use a set to check if there's a pair that can form this potential result.
3. This way, we **greedily try to set each bit** from left to right, ensuring it's possible.


### **Algorithm Steps:**
1. Initialize `max_xor = 0` and `mask = 0`.
2. Loop over 31 bits from high to low.
3. For each bit:
   - Add the bit to the `mask`.
   - Store all prefixes using the current mask.
   - Try setting the bit in `max_xor`, and see if two prefixes exist that form it.
4. If yes, update `max_xor`.


## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(32 × N), where N is the size of the array. We iterate through 32 bits and for each bit, we traverse the entire array once.
- **Expected Auxiliary Space Complexity:** O(N), used to store prefixes in a hash set at each bit position.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public int maxXor(int[] arr) {
        int maxXor = 0, mask = 0;
        HashSet<Integer> set = new HashSet<>();
        for (int i = 30; i >= 0; i--) {
            mask |= (1 << i);
            set.clear();
            int temp = maxXor | (1 << i);
            boolean found = false;
            for (int num : arr) {
                int prefix = num & mask;
                if (set.contains(temp ^ prefix)) {
                    found = true;
                    break;
                }
                set.add(prefix);
            }
            if (found) maxXor = temp;
        }
        return maxXor;
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐
