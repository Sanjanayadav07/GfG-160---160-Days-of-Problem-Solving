---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Arrays
  - Sorting
  - Heap
---

#  _Day 1. K Largest Elements_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/heap-gfg-160/problem/k-largest-elements4206)

## 💡 **Problem Description:**

Given an array `arr[]` of **positive integers** and an integer `k`, your task is to return the **k largest elements** in **decreasing order**.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```plaintext
arr = [12, 5, 787, 1, 23]
k = 2
```

#### **Output:**

```plaintext
[787, 23]
```

#### **Explanation:**

- The **1st largest element** is **787**.
- The **2nd largest element** is **23**.

### **Example 2:**

#### **Input:**

```plaintext
arr = [1, 23, 12, 9, 30, 2, 50]
k = 3
```

#### **Output:**

```plaintext
[50, 30, 23]
```

#### **Explanation:**

- The **3 largest elements** in descending order are **50, 30, and 23**.

### **Example 3:**

#### **Input:**

```plaintext
arr = [12, 23]
k = 1
```

#### **Output:**

```plaintext
[23]
```

#### **Explanation:**

- The **1st largest element** is **23**.

### **Constraints:**

- $\(1 \leq k \leq arr.size() \leq 10^6\)$
- $\(1 \leq arr[i] \leq 10^6\)$

## 🎯 **My Approach:**

### **Optimized Partial Sort (O(N + K log K) Time, O(1) Space)**

1. **Use `nth_element()`** to partition the `k` largest elements in `O(N)`.
2. **Use `partial_sort()`** to sort the top `k` elements in `O(K log K)`.
3. **Extract and return the `k` largest elements** in descending order.

### **Algorithm Steps:**

1. Use `nth_element()` to place the **k-th largest element** at `arr.end() - k`.
2. Use `partial_sort()` to sort only the **k largest elements** in descending order.
3. Return the last `k` elements in `arr`.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(N + K log K)`, due to partitioning and sorting.
- **Expected Auxiliary Space Complexity:** `O(1)`, since sorting is done in-place.

## 📝 **Solution Code**
## **Code (Java)**

```java
class Solution {
    public ArrayList<Integer> kLargest(int[] arr, int k) {
        Arrays.sort(arr);
        ArrayList<Integer> res = new ArrayList<>();
        for (int i = arr.length - 1; i >= arr.length - k; i--) res.add(arr[i]);
        return res;
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav07). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---
