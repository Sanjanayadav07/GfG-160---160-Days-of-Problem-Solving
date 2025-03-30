---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Dynamic Programming
  - Strings
---

#  _Day 4. Longest Palindromic Subsequence_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/longest-palindromic-subsequence-1612327878/1)  

## 💡 **Problem Description:**

Given a string `s`, return the length of the **longest palindromic subsequence**.

A **subsequence** is a sequence derived from the given sequence by deleting some or no elements without changing the order of the remaining elements.  
A **palindromic subsequence** reads the same forwards and backwards.

## 🔍 **Example Walkthrough:**

### **Example 1:**  
#### **Input:**  
`s = "bbabcbcab"`

#### **Output:**  
`7`

#### **Explanation:**  
The longest palindromic subsequence is `"babcbab"`, which has a length of **7**.


### **Example 2:**  
#### **Input:**  
`s = "abcd"`

#### **Output:**  
`1`

#### **Explanation:**  
The longest palindromic subsequence is any single character, which has a length of **1**.


### **Example 3:**  
#### **Input:**  
`s = "agbdba"`

#### **Output:**  
`5`

#### **Explanation:**  
The longest palindromic subsequence is `"abdba"`, which has a length of **5**.


### **Constraints:**  
- $1 \leq s.size() \leq 1000$
- The string contains only lowercase letters.


## 🎯 **My Approach:**

### **DP - Bottom-Up 2D Table**

### **Algorithm Steps:**

- Initialize a DP table t[n][n] to store LPS lengths.
- Set t[i][i] = 1 for all single characters.
- For substring lengths L from 2 to n:
- For each substring s[i...j]:
- If s[i] == s[j]:
- If L == 2, t[i][j] = 2.
- Else, t[i][j] = 2 + t[i+1][j-1].
- Else, t[i][j] = max(t[i+1][j], t[i][j-1]).
- Return t[0][n-1] as the length of the longest palindromic subsequence.

  ## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** $O(N^2)$, 

- **Expected Auxiliary Space Complexity:** $O(N^2)$

  ## 📝 **Solution Code**

  ## **Code (Java)**

```java
  class Solution {
    
    public int longestPalinSubseq(String s) {
        
        int n = s.length();
        
        int [][] t = new int[n][n];
        
        for(int i = 0; i < n; i++) {
            
            t[i][i] = 1;
        }
        
        for(int L = 2; L <= n; L++) {
            
            for(int i = 0; i < n - L + 1; i++) {
                
                int j = i + L - 1;
                
                if(s.charAt(i) == s.charAt(j) && L == 2) 
                    
                    t[i][j] = 2;
                    
                else if( s.charAt(i) == s.charAt(j)) {
                    
                    t[i][j] = 2 + t[i + 1][j - 1];
                    
                } else {
                    
                    t[i][j] = Math.max(t[i + 1][j],t[i][j - 1]);
                }
            }
        }
        
        return t[0][n - 1];
        
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007) Let’s make this learning journey more collaborative!  

⭐ **If you find this helpful, please give this repository a star!** ⭐  

--- 
