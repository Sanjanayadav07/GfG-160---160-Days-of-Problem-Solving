---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Dynamic Programming
  - Greedy
  - Arrays
---

#  _Day 13. Minimum Jumps_ 

The problem can be found at the following link: [Question Link](http://geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/minimum-number-of-jumps-1587115620)

## 💡 **Problem Description:**

Given an array `arr[]` of non-negative integers, each element represents the **maximum number of steps** that can be taken forward from that index.

Find the **minimum number of jumps** required to reach the last index.  
If the last index is not reachable, return `-1`.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
arr = [1, 3, 5, 8, 9, 2, 6, 7, 6, 8, 9]
```

#### **Output:**

```
3
```

#### **Explanation:**

- Jump from `arr[0] = 1` → `arr[1] = 3`.
- Jump from `arr[1] = 3` → `arr[4] = 9`.
- Jump from `arr[4] = 9` → last index.

### **Example 2:**

#### **Input:**

```
arr = [1, 4, 3, 2, 6, 7]
```

#### **Output:**

```
2
```

#### **Explanation:**

- Jump from `arr[0] = 1` → `arr[1] = 4`.
- Jump from `arr[1] = 4` → last index.

### **Example 3:**

#### **Input:**

```
arr = [0, 10, 20]
```

#### **Output:**

```
-1
```

#### **Explanation:**

Since `arr[0] = 0`, we cannot move forward.

### **Constraints:**

- $2 \leq \text{arr.size()} \leq 10^4$
- $0 \leq \text{arr[i]} \leq 10^4$

## 🎯 **My Approach:**
1. **Initialize three variables:**
   - `jumps = 0` → Tracks the number of jumps.
   - `farthest = 0` → Tracks the farthest reachable index.
   - `end = 0` → Marks the end of the current jump.
2. **Iterate through the array (except the last element):**
   - Update `farthest = max(farthest, i + arr[i])`.
   - If `i == end`:
     - Increase `jumps`.
     - Update `end = farthest`.
     - If `end >= n-1`, return `jumps`.
3. **If the last index is never reached, return `-1`.**

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(N)`, as we iterate through the array only once.
- **Expected Auxiliary Space Complexity:** `O(1)`, as we use only a few variables for tracking jumps and indices.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    static int minJumps(int[] arr) {
        int n = arr.length, jumps = 0, farthest = 0, end = 0;
        if (n == 1) return 0;
        for (int i = 0; i < n - 1; i++) {
            farthest = Math.max(farthest, i + arr[i]);
            if (i == end) {
                jumps++;
                end = farthest;
                if (end >= n - 1) return jumps;
            }
        }
        return -1;
    }
}
```


## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐
