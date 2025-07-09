---
Difficulty: Hard
Source: 160 Days of Problem Solving
Tags:
  - Stack
---

#  _Day 5. Histogram Max Rectangular Area_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/stack-gfg-160/problem/maximum-rectangular-area-in-a-histogram-1587115620)

## 💡 **Problem Description:**

You are given a **histogram** represented by an array `arr`, where each element denotes the **height** of the bars.  
Each bar has a width of **1 unit**.

Your task is to **find the largest rectangular area** possible in the given histogram, where the rectangle is formed using **contiguous bars**.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```plaintext
arr[] = [60, 20, 50, 40, 10, 50, 60]
```

<img src="https://github.com/user-attachments/assets/ad3da9cf-b355-49c7-b525-189c0c82b128" width="50%">

#### **Output:**

```plaintext
100
```

#### **Explanation:**

The maximum area is achieved by picking bars **50 and 60**.  
The area is computed as:  
$\[
\text{(smallest height)} \times \text{(number of picked bars)} = 50 \times 2 = 100
$\]

### **Example 2:**

#### **Input:**

```plaintext
arr[] = [3, 5, 1, 7, 5, 9]
```

#### **Output:**

```plaintext
15
```

#### **Explanation:**

The maximum area is achieved by picking bars **7, 5, and 9**.  
$\[
5 \times 3 = 15
$\]

### **Example 3:**

#### **Input:**

```plaintext
arr[] = [3]
```

#### **Output:**

```plaintext
3
```

#### **Explanation:**

The largest area is simply **3** (height `3`, width `1`).

### **Constraints:**

- $\(1 \leq \text{arr.size()} \leq 10^5\)$
- $\(0 \leq \text{arr[i]} \leq 10^4\)$

## 🎯 **My Approach:**

### **Optimized Monotonic Stack (O(N) Time, O(N) Space)**

1. **Use a stack** to keep track of indices of increasing heights.
2. **Process each bar once**, ensuring an **O(N) complexity**.
3. **Calculate maximum width dynamically** by maintaining left and right boundaries.

## **Algorithm Steps:**

1. Traverse each element in `arr[]` and use a **monotonic increasing stack** to store indices.
2. If `arr[i]` is **smaller** than the top of the stack, compute the largest area with the popped height.
3. The **width** is determined by checking the previous elements stored in the stack.
4. Repeat the process until all elements are processed.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** **O(N)**, as each bar is processed only once.
- **Expected Auxiliary Space Complexity:** **O(N)**, due to stack storage.

## 📝 **Solution Code**


## **Code (Java)**

```java
class Solution {
    public int getMaxArea(int[] arr) {
        Stack<Integer> s = new Stack<>();
        int n = arr.length, res = 0;
        for (int i = 0; i <= n; i++) {
            while (!s.isEmpty() && (i == n || arr[s.peek()] >= arr[i])) {
                int h = arr[s.pop()];
                int w = s.isEmpty() ? i : i - s.peek() - 1;
                res = Math.max(res, h * w);
            }
            s.push(i);
        }
        return res;
    }
}
```


## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
