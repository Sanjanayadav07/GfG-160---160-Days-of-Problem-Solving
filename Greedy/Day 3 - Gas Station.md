---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Greedy
---

#  _Day 3. Gas Station_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/greedy-gfg-160/problem/circular-tour-1587115620)

## 💡 **Problem Description:**

There are some gas stations along a **circular route**. You are given two integer arrays **gas[]** (the amount of gas at each station) and **cost[]** (the cost to travel to the next station).

You have a car with an **unlimited gas tank** and you start the journey with an **empty tank** from one of the gas stations.

Return the **index** of the starting gas station if it's possible to travel around the circuit without running out of gas at any station in a **clockwise direction**.  
If **no such starting station exists**, return **-1**.  
**Note:** If a solution exists, it is **guaranteed to be unique**.

> Note: Sorry for uploading late, my exam is going on.

## 🔍 **Example Walkthrough:**

### **Example 1:**

**Input:**

```cpp
gas[] = [4, 5, 7, 4]
cost[] = [6, 6, 3, 5]
```

**Output:**

```cpp
2
```

**Explanation:**

- Start at **index 2** (gas = 7).
- Travel to index 3: **7 - 3 + 4 = 8** (gas left).
- Travel to index 0: **8 - 5 + 4 = 7** (gas left).
- Travel to index 1: **7 - 6 + 5 = 6** (gas left).
- Return to index 2: **6 - 6 = 0** (gas left).  
  Hence, starting from **index 2** allows a complete circuit.

### **Example 2:**

**Input:**

```cpp
gas[] = [1, 2, 3, 4, 5]
cost[] = [3, 4, 5, 1, 2]
```

**Output:**

```cpp
3
```

**Explanation:**

- Start at **index 3** (gas = 4).
- Travel to index 4: **4 - 1 + 5 = 8** (gas left).
- Travel to index 0: **8 - 2 + 1 = 7** (gas left).
- Travel to index 1: **7 - 3 + 2 = 6** (gas left).
- Travel to index 2: **6 - 4 + 3 = 5** (gas left).
- Return to index 3: **5 - 5 = 0** (gas left).  
  Hence, starting from **index 3** allows a complete circuit.

### **Example 3:**

**Input:**

```cpp
gas[] = [3, 9]
cost[] = [7, 6]
```

**Output:**

```cpp
-1
```

**Explanation:**  
There is **no gas station** to start such that you can complete the circuit.

### **Constraints:**

- $\(1 \leq \text{gas.size()}, \text{cost.size()} \leq 10^6\)$
- $\(1 \leq \text{gas}[i], \text{cost}[i] \leq 10^3\)$

## 🎯 **My Approach:**

### **Greedy (Optimized)**

#### **Algorithm Steps:**

1. Traverse the gas stations and maintain:
   - **total:** Total difference between gas and cost.
   - **curr:** Current gas balance.
   - **start:** Starting index.
2. For each station:
   - Calculate the difference: **diff = gas[i] - cost[i]**.
   - Add **diff** to **total** and **curr**.
   - If **curr < 0**, it means that starting from the current start is not possible, so:
     - Update **start = i + 1**.
     - Reset **curr = 0**.
3. After traversing all stations:
   - If **total >= 0**, return **start**.
   - Otherwise, return **-1**.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** \(O(N)\), as we traverse the gas stations once.
- **Expected Auxiliary Space Complexity:** \(O(1)\), since we use only a few variables for calculation.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public int startStation(int[] gas, int[] cost) {
        int total = 0, curr = 0, start = 0;
        for (int i = 0; i < gas.length; i++) {
            int diff = gas[i] - cost[i];
            total += diff;
            curr += diff;
            if (curr < 0) { start = i + 1; curr = 0; }
        }
        return total >= 0 ? start : -1;
    }
}
```



## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/patel-hetkumar-sandipbhai-8b110525a/). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

