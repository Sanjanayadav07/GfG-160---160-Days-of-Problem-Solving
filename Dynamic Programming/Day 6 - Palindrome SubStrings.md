---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Dynamic Programming
  - Strings
  - palindrome
---

#  _Day 6. Palindrome SubStrings_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/count-palindrome-sub-strings-of-a-string0652/1)

## 💡 **Problem Description:**

Given a string **s**, count all **palindromic substrings** present in the string where the **length of each palindromic substring** is **greater than or equal to 2**.

## 🔍 **Example Walkthrough:**

### **Example 1**  
**Input:**  
```
s = "abaab"
```
**Output:**  
```
3
```
**Explanation:**  
All palindromic substrings are: `"aba"`, `"aa"`, and `"baab"`.

### **Example 2**  
**Input:**  
```
s = "aaa"
```
**Output:**  
```
3
```
**Explanation:**  
All palindromic substrings are: `"aa"`, `"aa"`, and `"aaa"`.

### **Example 3**  
**Input:**  
```
s = "abbaeae"
```
**Output:**  
```
4
```
**Explanation:**  
All palindromic substrings are: `"bb"`, `"abba"`, `"aea"`, and `"eae"`.

## **Constraints**
- $\( 2 \leq \text{length}(s) \leq 10^3 \)$
- String contains only **lowercase English characters**.


## 🎯 **My Approach:**

- Create a 2D array dp[n][n], initialized to false, where n is the length of s.
- Traverse the string in reverse order for the starting index i (from n-1 down to 0).
- Set dp[i][i] = true for all i (single-character palindromes, though not counted, are needed to build multi-character palindromes).
- For each i, iterate j from i+1 to n-1:
- If s[i] == s[j] and the substring in-between is a palindrome (or j - i == 1 for adjacent chars), set dp[i][j] = true.
- If dp[i][j] is true, increment the count.
- The result is the total count of palindromic substrings of length ≥ 2.

  ## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** **O(N²)**
- **Expected Auxiliary Space Complexity:** **O(N²)**

  ## 📝 **Solution Code**

  ## **Code (Java)**  

```java
class Solution {
    public int countPS(String s) {
        // code here
        int n = s.length();
        
        int count = 0;
        
        boolean[][] t = new boolean [n][n];
        
        for(int i = n - 1; i >= 0; i--) {
            
            t[i][i] = true;
            
            for(int j = i+1; j < n; j++) {
                
                if(s.charAt(i) == s.charAt(j) &&(j - i == 1 || t[i + 1][j - 1])) {
                    
                    t[i][j] = true;
                    
                    count++;
                }
                
            }
        }
        return count;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐
