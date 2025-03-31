---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Dynamic Programming
  - Strings
  - palindrome
---

#  _Day 5. Longest Palindrome in a String_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/longest-palindrome-in-a-string3411)  

## 💡 **Problem Description:**

Given a string `s`, your task is to find the **longest palindromic substring** within `s`.  

- A **substring** is a contiguous sequence of characters within the string (i.e., `s[i...j]` for `0 ≤ i ≤ j < len(s)`).
- A **palindrome** reads the same forwards and backwards, i.e., `reverse(s) == s`.
- If there are multiple palindromic substrings of the same maximum length, **return the first occurrence** from left to right.

## 🔍 **Example Walkthrough:**

### **Example 1:**  

#### **Input:**  
```
s = "forgeeksskeegfor"
```

#### **Output:**  
```
"geeksskeeg"
```

#### **Explanation:**  
Possible palindromic substrings include `"kssk"`, `"ss"`, `"eeksskee"`, etc. However, **"geeksskeeg"** is the **longest** among them.


### **Example 2:**  

#### **Input:**  
```
s = "Geeks"
```

#### **Output:**  
```
"ee"
```

#### **Explanation:**  
The substring **"ee"** is the longest palindrome in `"Geeks"`.


### **Example 3:**  

#### **Input:**  
```
s = "abc"
```

#### **Output:**  
```
"a"
```

#### **Explanation:**  
All substrings `"a"`, `"b"`, and `"c"` have length 1, which is the maximum. Returning the first occurrence results in `"a"`.


### **Constraints:**  
- $\(1 \leq s.\text{size()} \leq 10^3\)$  
- `s` consists of only **lowercase English letters**.


## 🎯 **My Approach:**
- First Initialize:
-   n = length of s
- t[n][n] → DP table to track palindromes.
-  maxL = 1, start = 0.
- Base Case:
- All substrings of length 1 are palindromes → set t[i][i] = true.
- Check Substrings of Length 2 and More:
- For substring length L = 2 to n:
- For each i, calculate j = i + L - 1.
- If s[i] == s[j] and (L == 2 or t[i+1][j-1] is true):
- Mark t[i][j] = true.
- Update maxL and start if L > maxL.
- Return: The substring s.substring(start, start + maxL).

  ## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** **O(N²)**
- **Expected Auxiliary Space Complexity:** **O(N²)**

  ## 📝 **Solution Code**

  ## **Code (Java)**  

```java
class Solution {
    static String longestPalindrome(String s) {
        // code here
        int n = s.length();
        
        boolean [][] t = new boolean[n][n];
        
        int maxL = 1;
        
        int start = 0;
        
        for(int i = 0; i < n; i++) {
            
            t[i][i] = true;
            
        }
        
        for(int L = 2; L <= n; L++) {
            
            for(int i = 0; i < n - L + 1; i++) {
                
                int j = i + L - 1;
                
                if(s.charAt(i) == s.charAt(j) && (t[i + 1][j - 1] || L == 2)) {
                    
                    t[i][j] = true;
                    
                    if(L > maxL) {
                        
                        maxL = L;
                        
                        start = i;
                    }
                }
            }
        }
        
        return s.substring(start, start + maxL);
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
