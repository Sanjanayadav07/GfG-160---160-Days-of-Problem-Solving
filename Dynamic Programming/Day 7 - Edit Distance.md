---
Difficulty: Hard  
Source: 160 Days of Problem Solving  
Tags:
  - Dynamic Programming
  - Strings
---

# 🚀 _Day 7. Edit Distance_ 🧠


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/edit-distance3702)  

## 💡 **Problem Description:**

Given two strings **s1** and **s2**, you need to find the minimum number of operations required to convert **s1** into **s2**. The valid operations are:  
1. **Insert** a character at any position.  
2. **Delete** any character from the string.  
3. **Replace** any character with another character.  

## 🔍 **Example Walkthrough:**

### **Example 1:**  

#### **Input:**  
```
s1 = "geek"
s2 = "gesek"
```
#### **Output:**  
```
1
```
#### **Explanation:**  
We can insert `'s'` between the two `'e'` in **"geek"** to form **"gesek"**.  

### **Example 2:**  

#### **Input:**  
```
s1 = "gfg"
s2 = "gfg"
```
#### **Output:**  
```
0
```
#### **Explanation:**  
The strings are already the same, so **0** operations are required.  

### **Example 3:**  

#### **Input:**  
```
s1 = "abcd"
s2 = "bcfe"
```
#### **Output:**  
```
3
```
#### **Explanation:**  
- Remove `'a'` from **"abcd"** → **"bcd"**  
- Replace `'d'` with `'f'` → **"bcf"**  
- Insert `'e'` at the end → **"bcfe"**  

### **Constraints:**  
- $\(1 \leq s1.length(), s2.length() \leq 10^3\)$  
- Both strings are in lowercase.  


## 🎯 **My Approach:**

### **Dynamic Programming**  
- Base Case:
  - If m == 0, return n (insert all characters of s2).
  - If n == 0, return m (delete all characters of s1).
- Memoization Check:
   -If t[m][n] != -1, return t[m][n].
- Recursive Cases:
  - If characters match: Move diagonally → solve(s1, s2, m-1, n-1).
  - If they don’t match:
- Insert: solve(s1, s2, m, n-1) + 1
- Delete: solve(s1, s2, m-1, n) + 1
- Replace: solve(s1, s2, m-1, n-1) + 1
  -Store minimum in t[m][n].
  -Initialize DP table (t[][]) with -1 and call solve(s1, s2, m, n).

## 📝 **Solution Code**

## **Code (Java)**

```java
  class Solution {
    
    int[][] t;
    
    public int solve(String s1, String s2, int m, int n) {
        if(m == 0) return n;
        
        if(n == 0) return m;
           
        if(t[m][n] != - 1) return t[m][n];
        
        if(s1.charAt(m - 1) == s2.charAt(n - 1))
        
          return t[m][n] = solve(s1,s2, m-1, n-1);
          
        else {
            int insertC = 1 + solve(s1,s2, m, n-1);
            
            int deleteC = 1 + solve(s1,s2,m-1,n);
            
            int replaceC = 1 + solve(s1,s2, m-1,n-1);
            
            return t[m][n] = Math.min(insertC, Math.min(deleteC, replaceC));
        }
            
    }
    public int editDistance(String s1, String s2) {
        // Code here
        int m = s1.length();
        
        int n = s2.length();
        
        t = new int[m + 1][n + 1];
        
        for(int[] row : t)
        
        Arrays.fill(row,-1);
        
        return solve(s1,s2,m,n);
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐
