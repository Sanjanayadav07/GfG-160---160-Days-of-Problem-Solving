---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Dynamic Programming
---

#  _Day 3. Longest Common Subsequence_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/longest-common-subsequence-1587115620)

## 💡 **Problem Description:**

Given **two strings** `s1` and `s2`, **return the length of their longest common subsequence (LCS)**. If there is no common subsequence, return `0`.  

A **subsequence** is a sequence that can be derived from the given string by deleting some or no elements without changing the order of the remaining elements. For example, `"ABE"` is a subsequence of `"ABCDE"`.  

## 🔍 **Example Walkthrough:**

### **Example 1:**  

#### **Input:**  
```
s1 = "ABCDGH", s2 = "AEDFHR"
```

#### **Output:**  
```
3
```

#### **Explanation:**  
The longest common subsequence of `"ABCDGH"` and `"AEDFHR"` is **"ADH"**, which has a length of 3.  


### **Example 2:**  

#### **Input:**  
```
s1 = "ABC", s2 = "AC"
```

#### **Output:**  
```
2
```

#### **Explanation:**  
The longest common subsequence of `"ABC"` and `"AC"` is **"AC"**, which has a length of 2.  


### **Example 3:**  

#### **Input:**  
```
s1 = "XYZW", s2 = "XYWZ"
```

#### **Output:**  
```
3
```

#### **Explanation:**  
The longest common subsequences of `"XYZW"` and `"XYWZ"` are **"XYZ"** and **"XYW"**, both of length 3.  


### **Constraints:**  
- $\(1 \leq \text{length}(s1), \text{length}(s2) \leq 10^3\)$  
- Both `s1` and `s2` contain only **uppercase English letters**.  


## 🎯 **My Approach:**

### **Space-Optimized 1D DP**

### **Key Idea**  
- Use **only two arrays (current and previous rows)** to store LCS lengths for substrings.
- The value at `dp[j]` represents the **LCS length of `s1[0..i-1]` and `s2[0..j-1]`**.
- Only **the previous row is needed** to compute the current row, so space is reduced to **O(M)**, where M is the length of the second string.

### **Algorithm Steps**  
1. Use two **rolling 1D arrays** (or one array with a few variables) to store only the previous row and current row.  
2. **Traverse** the strings from `i = 1..n` and `j = 1..m`:  
   - If `s1[i - 1] == s2[j - 1]`, we do `curr[j] = prev[j - 1] + 1`.  
   - Else, `curr[j] = max(prev[j], curr[j - 1])`.  
3. **Swap** `prev` and `curr` at the end of each `i` iteration.  
4. The result is `prev[m]`, which is the **length of LCS**.  

This approach is more **space-efficient** than the standard `O(N * M)` DP table because it only keeps **two rows** (or one row with updates).  

## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** `O(N * M)`, where `N` is the length of `s1` and `M` is the length of `s2`.  
- **Expected Auxiliary Space Complexity:** `O(N)`, using the space-optimized approach (storing only one dimension).  



## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    static int lcs(String s1, String s2) {
        int n = s1.length(), m = s2.length();
        int[] prev = new int[m + 1], curr = new int[m + 1];
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= m; j++) {
                curr[j] = s1.charAt(i - 1) == s2.charAt(j - 1) ? prev[j - 1] + 1 : Math.max(prev[j], curr[j - 1]);
            }
            int[] temp = prev; prev = curr; curr = temp;
        }
        return prev[m];
    }
}
```


## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007) Let’s make this learning journey more collaborative! 

⭐ **If you find this helpful, please give this repository a star!** ⭐  
