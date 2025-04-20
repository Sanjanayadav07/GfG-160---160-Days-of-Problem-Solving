---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Sorting
  - Heap
  - Mathematical
  - priority-queue
  - Divide and Conquer
  - Geometric
  - Arrays
---

#  _Day 2. K Closest Points to Origin_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/heap-gfg-160/problem/k-closest-points-to-origin--172242)

## 💡 **Problem Description:**

Given an array of points where each point is represented as **points[i] = [xi, yi]** on the **X-Y plane** and an integer **k**, return the **k closest points** to the origin **(0, 0)**.

The distance between two points on the **X-Y plane** is defined as:  
$\text{distance} = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$  
You may return the **k closest points in any order**. The driver code will sort them before printing.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

k = 2, points[] = **[[1, 3], [-2, 2], [5, 8], [0, 1]]**

#### **Output:**

**[[-2, 2], [0, 1]]**

#### **Explanation:**

The Euclidean distances from the origin **(0,0)** are:

- Point (1,3) = **√10**
- Point (-2,2) = **√8**
- Point (5,8) = **√89**
- Point (0,1) = **√1**

The **two closest points** to the origin are **[-2,2]** and **[0,1]**.

### **Example 2:**

#### **Input:**

k = 1, points = **[[2, 4], [-1, -1], [0, 0]]**

#### **Output:**

**[[0, 0]]**

#### **Explanation:**

The Euclidean distances from the origin **(0,0)** are:

- Point (2,4) = **√20**
- Point (-1,-1) = **√2**
- Point (0,0) = **√0**

The **closest point** to the origin is **(0,0)**.

### **Constraints:**

- $\( 1 \leq k \leq \text{points.size()} \leq 10^5 \)$
- $\( -10^4 \leq x_i, y_i \leq 10^4 \)$

## 🎯 **My Approach:**

### **Partial Sort using `nth_element` (O(N + K log K) Time, O(1) Space)**

1. We need to **find the k closest points** to the origin based on their **Euclidean distance**.
2. Instead of sorting the entire array (which takes **O(N log N)**), we can use **`nth_element`** which partially sorts the array in **O(N + K log K)** time.
3. The **first k elements** in the sorted range will be the k closest points.
4. Since **we don’t need exact sorting**, `nth_element` is much more efficient than a full sort.

### **Algorithm Steps:**

1. **Use `nth_element`** to place the k closest points at the beginning of the array.
2. **Extract the first k points** and return them as the result.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** **O(N + K log K)**, since `nth_element` partially sorts the array.
- **Expected Auxiliary Space Complexity:** **O(1)**, as sorting is done in place without extra memory.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public int[][] kClosest(int[][] p, int k) {
        Arrays.sort(p, Comparator.comparingInt(a -> a[0] * a[0] + a[1] * a[1]));
        return Arrays.copyOfRange(p, 0, k);
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐
