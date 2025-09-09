---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - sliding-window
  - Heap
  - Arrays
  - Queue
---

#  _Day 2. Longest Bounded-Difference Subarray_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/queue-and-deque-gfg-160/problem/longest-bounded-difference-subarray)

## 💡 **Problem Description:**

Given an array of positive integers `arr[]` and a non-negative integer `x`, the task is to find the **longest sub-array** where the absolute difference between any two elements is not greater than `x`.

If multiple such subarrays exist, return the one that **starts at the smallest index**.

## 🔍 **Example Walkthrough:**

### Example 1

#### Input

```
arr[] = [8, 4, 2, 6, 7]
x = 4
```

#### Output

```
[4, 2, 6]
```

#### Explanation

- The sub-array [4, 2, 6] has no pair of elements with absolute difference greater than 4.
- Other subarrays either don't meet the condition or are shorter.

### Example 2

#### Input

```
arr[] = [15, 10, 1, 2, 4, 7, 2]
x = 5
```

#### Output

```
[2, 4, 7, 2]
```

#### Explanation

- The sub-array described by indexes [3..6], i.e. [2, 4, 7, 2] contains no such difference of two elements which is greater than 5.

### **Constraints**

- $1 \leq N \leq 10^5$
- $1 \leq arr[i] \leq 10^9$
- $0 \leq x \leq 10^9$

## 🎯 **My Approach:**

### **Sliding Window with Deque**

This approach uses **two deques** to dynamically maintain the **minimum and maximum elements** within the sliding window.

- **minQ** tracks the **minimum values** in the current window.
- **maxQ** tracks the **maximum values** in the current window.
- If `maxQ.front() - minQ.front()` exceeds `x`, we shrink the window from the left.
- At every step, we check if the current window length is the longest valid window seen so far.

### **Steps:**

1. Initialize `start` pointer and two deques: `minQ` (for minimum) and `maxQ` (for maximum).
2. Expand the window by adding the current element to both deques.
3. If the difference between max and min exceeds `x`, shrink the window by incrementing `start`.
4. Track the **longest valid window** and its starting position.
5. Return the subarray corresponding to the longest valid window.

## 🕒 **Time and Auxiliary Space Complexity**

| Complexity           | Analysis                                                                |
| -------------------- | ----------------------------------------------------------------------- |
| **Time Complexity**  | `O(N)` - Each element is pushed and popped from the deque at most once. |
| **Space Complexity** | `O(N)` - In the worst case, both deques can hold all indices.           |

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public ArrayList<Integer> longestSubarray(int[] arr, int x) {
        Deque<Integer> minQ = new ArrayDeque<>(), maxQ = new ArrayDeque<>();
        int n = arr.length, start = 0, resStart = 0, resLen = 0;
        for (int end = 0; end < n; end++) {
            while (!minQ.isEmpty() && arr[minQ.peekLast()] > arr[end]) minQ.pollLast();
            while (!maxQ.isEmpty() && arr[maxQ.peekLast()] < arr[end]) maxQ.pollLast();
            minQ.addLast(end);
            maxQ.addLast(end);
            while (arr[maxQ.peekFirst()] - arr[minQ.peekFirst()] > x) {
                if (minQ.peekFirst() == start) minQ.pollFirst();
                if (maxQ.peekFirst() == start) maxQ.pollFirst();
                start++;
            }
            if (end - start + 1 > resLen) {
                resStart = start;
                resLen = end - start + 1;
            }
        }
        ArrayList<Integer> res = new ArrayList<>();
        for (int i = resStart; i < resStart + resLen; i++) res.add(arr[i]);
        return res;
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---
