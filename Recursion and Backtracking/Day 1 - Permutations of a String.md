---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Strings
  - Recursion
  - Backtracking
---

#  _Day 1. Permutations of a String_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/recursion-and-backtracking-gfg-160/problem/permutations-of-a-given-string2041)

## 💡 **Problem Description:**

You are given a string `s`, which may contain duplicate characters. Your task is to generate and return an array of all unique permutations of the string. You can return the permutations in any order.

## 🔍 **Example Walkthrough:**

### **Example 1**

**Input:**  
`s = "ABC"`  
**Output:**  
`["ABC", "ACB", "BAC", "BCA", "CAB", "CBA"]`  
**Explanation:**  
Given string `ABC` has 6 unique permutations.

### **Example 2**

**Input:**  
`s = "ABSG"`  
**Output:**  
`["ABGS", "ABSG", "AGBS", "AGSB", "ASBG", "ASGB", "BAGS", "BASG", "BGAS", "BGSA", "BSAG", "BSGA", "GABS", "GASB", "GBAS", "GBSA", "GSAB", "GSBA", "SABG", "SAGB", "SBAG", "SBGA", "SGAB", "SGBA"]`  
**Explanation:**  
Given string `ABSG` has 24 unique permutations.

### **Example 3**

**Input:**  
`s = "AAA"`  
**Output:**  
`["AAA"]`  
**Explanation:**  
No other unique permutations can be formed as all the characters are the same.

### **Constraints**

- `1 <= s.size() <= 9`
- `s` contains only uppercase English alphabets.

## 🎯 **My Approach:**

1. **Lexicographical Permutation Method:**

   - Sort the characters of the string to generate permutations in lexicographical order.
   - Use a loop to find the **next lexicographical permutation** until all permutations are found.

2. **DFS with Backtracking:**

   - Use backtracking to generate all permutations.
   - Avoid duplicates by skipping over elements that are the same and ensuring a sorted order before starting.

3. **Key Steps:**
   - Sort the string or array of characters to start with the smallest permutation.
   - Generate all permutations using a **DFS approach** or iterate through lexicographical order using the `next_permutation()` function.
   - Ensure uniqueness by checking and avoiding duplicate entries in the result.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(N! \* N), where N is the length of the string. Generating all permutations takes **O(N!)**, and sorting or creating permutations takes **O(N)**.
- **Expected Auxiliary Space Complexity:** O(N), for storing intermediate permutations in recursion or iteration.

## 📝 **Solution Code**

## **Approach : Using STL `next_permutation()`**

## Code (Java)

## Code (Java)

```java
class Solution {
    public ArrayList<String> findPermutation(String s) {
        ArrayList<String> res = new ArrayList<>();
        char[] chars = s.toCharArray();
        Arrays.sort(chars);
        do res.add(new String(chars));
        while (next(chars));
        return res;
    }

    private boolean next(char[] c) {
        int i = c.length - 2, j = c.length - 1;
        while (i >= 0 && c[i] >= c[i + 1]) i--;
        if (i < 0) return false;
        while (c[j] <= c[i]) j--;
        char t = c[i]; c[i] = c[j]; c[j] = t;
        for (int l = i + 1, r = c.length - 1; l < r; l++, r--) {
            t = c[l]; c[l] = c[r]; c[r] = t;
        }
        return true;
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
