---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - sliding-window
  - Arrays
  - Queue
---

#  _Day 1. K Sized Subarray Maximum_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/queue-and-deque-gfg-160/problem/maximum-of-all-subarrays-of-size-k3101)

## 💡 **Problem Description:**

Given an **array arr[]** of integers and an integer **k**, your task is to find the **maximum value for each contiguous subarray of size k**. The output should be an array of maximum values corresponding to each contiguous subarray.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

`arr[] = [1, 2, 3, 1, 4, 5, 2, 3, 6]`  
`k = 3`

#### **Output:**

`[3, 3, 4, 5, 5, 5, 6]`

#### **Explanation:**

1st window: [1, 2, 3], max = 3  
2nd window: [2, 3, 1], max = 3  
3rd window: [3, 1, 4], max = 4  
4th window: [1, 4, 5], max = 5  
5th window: [4, 5, 2], max = 5  
6th window: [5, 2, 3], max = 5  
7th window: [2, 3, 6], max = 6

### **Example 2:**

#### **Input:**

`arr[] = [8, 5, 10, 7, 9, 4, 15, 12, 90, 13]`  
`k = 4`

#### **Output:**

`[10, 10, 10, 15, 15, 90, 90]`

#### **Explanation:**

1st window: [8, 5, 10, 7], max = 10  
2nd window: [5, 10, 7, 9], max = 10  
3rd window: [10, 7, 9, 4], max = 10  
4th window: [7, 9, 4, 15], max = 15  
5th window: [9, 4, 15, 12], max = 15  
6th window: [4, 15, 12, 90], max = 90  
7th window: [15, 12, 90, 13], max = 90

### **Constraints**

- $\(1 \leq \text{arr.size()} \leq 10^6\)$
- $\(1 \leq k \leq \text{arr.size()}\)$
- $\(0 \leq arr[i] \leq 10^9\)$

## 🎯 **My Approach:**

### **Sliding Window Maximum using Deque**

- We maintain a **deque** where each element is an **index**, and the values at those indices are in decreasing order.
- As we iterate through the array, we **add new elements** to the deque and **remove elements that fall out of the current window.**
- The **maximum element of the current window** will always be at the front of the deque.
- This allows us to efficiently compute the maximum for each window in constant time on average.

### **Algorithm Steps:**

1. Initialize a **deque** to store indices.
2. Loop through the array.
3. **Remove elements from the front** of the deque if they are outside the window.
4. **Remove elements from the back** of the deque if they are smaller than the current element (ensuring decreasing order).
5. **Add the current index** to the deque.
6. Once the first window is complete, **append the front element (maximum)** to the result.
7. Continue until all windows are processed.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(N)`, because each element is added and removed from the deque at most once.
- **Expected Auxiliary Space Complexity:** `O(K)`, the size of the deque.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public ArrayList<Integer> maxOfSubarrays(int[] arr, int k) {
        ArrayList<Integer> res = new ArrayList<>();
        Deque<Integer> dq = new ArrayDeque<>();
        for (int i = 0; i < arr.length; i++) {
            if (!dq.isEmpty() && dq.peekFirst() <= i - k) dq.pollFirst();
            while (!dq.isEmpty() && arr[dq.peekLast()] < arr[i]) dq.pollLast();
            dq.offerLast(i);
            if (i >= k - 1) res.add(arr[dq.peekFirst()]);
        }
        return res;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yada007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---
