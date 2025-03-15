---
Difficulty: Hard  
Source: 160 Days of Problem Solving  
Tags:
  - Strings
---


#  _Day 6. Min Chars to Add for Palindrome_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/string-gfg-160/problem/minimum-characters-to-be-added-at-front-to-make-string-palindrome)  




## 💡 **Problem Description:**

Given a string `s`, find the minimum number of characters to be added at the front of the string to make it a palindrome.  

A palindrome string is a sequence of characters that reads the same forward and backward.  



## 🔍 **Example Walkthrough:**

**Input:**  
`s = "abc"`  
**Output:**  
`2`  

**Explanation:**  
Add `b` and `c` to the front to make the string a palindrome: `"cbabc"`

**Input:**  
`s = "aacecaaaa"`  
**Output:**  
`2`  

**Explanation:**  
Add `aa` at the front to make the string a palindrome: `"aaaacecaaaa"`



### Constraints:
- `1 <= s.size() <= 10^6`



## 🎯 **My Approach:**

### Key Idea:
The solution relies on combining the given string with its reverse using a separator (e.g., `$`) and computing the **Longest Prefix Suffix (LPS)** array for this combined string.  

The last value in the LPS array gives the length of the longest palindromic suffix in the original string. Subtracting this value from the length of the original string provides the minimum number of characters to be added.  

### Steps:
1. **Compute the Reverse String**:  
   Reverse the input string to identify palindromic suffixes.  

2. **Combine Strings**:  
   Concatenate the input string, a separator (`$`), and the reversed string to form the combined string.  

3. **Build LPS Array**:  
   Use the **Knuth-Morris-Pratt (KMP)** algorithm to compute the LPS array for the combined string.  

4. **Calculate the Result**:  
   The minimum characters to be added is equal to `n - lps[m-1]`, where `lps[m-1]` is the last value in the LPS array, `n` is the length of the original string, and `m` is the length of the combined string.  



## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity**: O(n), where `n` is the length of the string. Calculating the LPS array takes linear time.
- **Expected Auxiliary Space Complexity**: O(n), as the LPS array and the combined string require space proportional to the input size.

## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    public static int minChar(String s) {
        int n = s.length();

        String revStr = new StringBuilder(s).reverse().toString();

        String combined = s + "$" + revStr;

        int[] lps = new int[combined.length()];
        for (int i = 1; i < combined.length(); i++) {
            int j = lps[i - 1];
            while (j > 0 && combined.charAt(i) != combined.charAt(j)) {
                j = lps[j - 1];
            }
            if (combined.charAt(i) == combined.charAt(j)) {
                j++;
            }
            lps[i] = j;
        }

        return n - lps[combined.length() - 1];
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007) Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
