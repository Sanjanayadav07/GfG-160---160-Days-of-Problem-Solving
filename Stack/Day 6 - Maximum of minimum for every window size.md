---
Difficulty: Hard
Source: 160 Days of Problem Solving
Tags:
  - Stack
  - sliding-window
---

#  _Day 6. Maximum of minimum for every window size_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/stack-gfg-160/problem/maximum-of-minimum-for-every-window-size3453)

## 💡 **Problem Description:**

Given an array of integers **arr[]**, find the **maximum of the minimum element** for every window size **w** from **1 to N**.

## 🔍 **Example Walkthrough:**

### **Example 1**

### **Input:**

```
arr[] = {10, 20, 30, 50, 10, 70, 30}
```

### **Output:**

```
70 30 20 10 10 10 10
```

### **Explanation:**

| **Window Size (k)** | **Subarrays of size k**                                                | **Minimum in each subarray** | **Maximum among these minimums** |
| ------------------- | ---------------------------------------------------------------------- | ---------------------------- | -------------------------------- |
| 1                   | {10}, {20}, {30}, {50}, {10}, {70}, {30}                               | 10, 20, 30, 50, 10, 70, 30   | 70                               |
| 2                   | {10, 20}, {20, 30}, {30, 50}, {50, 10}, {10, 70}, {70, 30}             | 10, 20, 30, 10, 10, 30       | 30                               |
| 3                   | {10, 20, 30}, {20, 30, 50}, {30, 50, 10}, {50, 10, 70}, {10, 70, 30}   | 10, 20, 10, 10, 10           | 20                               |
| 4                   | {10, 20, 30, 50}, {20, 30, 50, 10}, {30, 50, 10, 70}, {50, 10, 70, 30} | 10, 10, 10, 10               | 10                               |
| 5                   | {10, 20, 30, 50, 10}, {20, 30, 50, 10, 70}, {30, 50, 10, 70, 30}       | 10, 10, 10                   | 10                               |
| 6                   | {10, 20, 30, 50, 10, 70}, {20, 30, 50, 10, 70, 30}                     | 10, 10                       | 10                               |
| 7                   | {10, 20, 30, 50, 10, 70, 30}                                           | 10                           | 10                               |

## **Example 2**

### **Input:**

```
arr[] = {1, 3, 2, 4, 5}
```

### **Output:**

```
5 3 2 1 1
```

### **Explanation:**

| **Window Size (k)** | **Subarrays of size k**         | **Minimum in each subarray** | **Maximum among these minimums** |
| ------------------- | ------------------------------- | ---------------------------- | -------------------------------- |
| 1                   | {1}, {3}, {2}, {4}, {5}         | 1, 3, 2, 4, 5                | 5                                |
| 2                   | {1, 3}, {3, 2}, {2, 4}, {4, 5}  | 1, 2, 2, 4                   | 3                                |
| 3                   | {1, 3, 2}, {3, 2, 4}, {2, 4, 5} | 1, 2, 2                      | 2                                |
| 4                   | {1, 3, 2, 4}, {3, 2, 4, 5}      | 1, 2                         | 1                                |
| 5                   | {1, 3, 2, 4, 5}                 | 1                            | 1                                |

## **Constraints:**

- $\( 1 \leq N \leq 10^5 \)$
- $\( 1 \leq arr[i] \leq 10^6 \)$

## 🎯 **My Approach:**

### **Optimized Stack-Based Approach (O(N) Time, O(N) Space)**

To efficiently find the **maximum of the minimum for every window size**, we use a **monotonic stack** to determine the **window size for which each element is the minimum**.

### **Algorithm Steps:**

1. **Find the nearest smaller elements on both left and right sides**

   - Store the **left boundary** (`prevSmaller[i]`) where `arr[i]` is the minimum.
   - Store the **right boundary** (`nextSmaller[i]`) where `arr[i]` is the minimum.
   - Use **stacks** to efficiently compute these values.

2. **Calculate the window size where each element is the minimum**

   - The window size for `arr[i]` is `nextSmaller[i] - prevSmaller[i] - 1`.

3. **Store maximum values for each window size**

   - Use an array `res[]` to store the maximum of the minimums for each window size.

4. **Propagate the maximum values**
   - Ensure `res[i]` contains the maximum for all larger windows using **backward propagation**.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(N), since each element is processed once.
- **Expected Auxiliary Space Complexity:** O(N), for storing index boundaries and stack operations.

## 📝 **Solution Code**
## **Code (Java)**

```java
class Solution {
    public ArrayList<Integer> maxOfMins(int[] arr) {
        int n = arr.length;
        int[] res = new int[n], len = new int[n];
        Stack<Integer> s = new Stack<>();
        for (int i = 0; i <= n; i++) {
            while (!s.isEmpty() && (i == n || arr[s.peek()] >= arr[i])) {
                int j = s.pop();
                len[j] = s.isEmpty() ? i : i - s.peek() - 1;
            }
            if (i < n) s.push(i);
        }
        for (int i = 0; i < n; i++) res[len[i] - 1] = Math.max(res[len[i] - 1], arr[i]);
        for (int i = n - 2; i >= 0; i--) res[i] = Math.max(res[i], res[i + 1]);
        ArrayList<Integer> ans = new ArrayList<>();
        for (int r : res) ans.add(r);
        return ans;
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
