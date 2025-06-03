---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Greedy
  - Binary Search
---

#  _Day 2. Activity Selection_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/greedy-gfg-160/problem/activity-selection-1587115620)

## 💡 **Problem Description:**

You are given a set of activities, each with a **start time** and a **finish time**, represented by the arrays `start[]` and `finish[]`, respectively. A single person can perform only **one activity at a time**, meaning no two activities can overlap.

Your task is to determine the **maximum number of activities** that a person can complete in a day.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
start[] = [1, 3, 0, 5, 8, 5]
finish[] = [2, 4, 6, 7, 9, 9]
```

#### **Output:**

```
4
```

#### **Explanation:**

A person can perform **at most four activities**. The maximum set of activities that can be executed is `{0, 1, 3, 4}`.

### **Example 2:**

#### **Input:**

```
start[] = [10, 12, 20]
finish[] = [20, 25, 30]
```

#### **Output:**

```
1
```

#### **Explanation:**

A person can perform **at most one activity**.

### **Example 3:**

#### **Input:**

```
start[] = [1, 3, 2, 5]
finish[] = [2, 4, 3, 6]
```

#### **Output:**

```
3
```

#### **Explanation:**

A person can perform **activities 0, 1, and 3**.

### **Constraints:**

- $\(1 \leq \text{start.size()} = \text{finish.size()} \leq 2 \times 10^5\)$
- $\(1 \leq \text{start[i]} \leq \text{finish[i]} \leq 10^9\)$

## 🎯 **My Approach:**

### **Greedy Approach**

1. **Sort Activities by Finish Time:**

   - Pair up each start and finish time as a pair `(finish[i], start[i])` to easily sort them by finish time.
   - Sorting ensures that we always consider the earliest finishing activity first.

2. **Select Non-Overlapping Activities:**
   - Initialize `finishtime` to -1 and `ans` to 0.
   - Iterate through the sorted list:
     - If the **current start time** is greater than the `finishtime`, select the activity and update `finishtime` to the **current finish time**.
     - Increment the count of activities.

#### **Why Greedy Works:**

Since we are sorting by finish time, we ensure that we select the **earliest finishing non-overlapping activity**, leaving maximum room for subsequent activities.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(N log N), due to sorting of the activities based on finish time.
- **Expected Auxiliary Space Complexity:** O(1), as no extra space is used except for variables.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public int activitySelection(int[] start, int[] finish) {
        int n = start.length, ans = 0, finishtime = -1;
        Integer[] indices = new Integer[n];
        for (int i = 0; i < n; i++) indices[i] = i;
        Arrays.sort(indices, Comparator.comparingInt(i -> finish[i]));
        for (int i : indices) {
            if (start[i] > finishtime) {
                finishtime = finish[i];
                ans++;
            }
        }
        return ans;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
