---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Dynamic Programming
---

#  _Day 2. Longest String Chain_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/longest-string-chain)  


## 💡 **Problem Description:**

You are given an array of words where each word consists of lowercase English letters.

A **wordA** is a **predecessor** of **wordB** if and only if we can insert exactly **one letter** anywhere in wordA without changing the order of the other characters to make it equal to wordB.  
For example, **"abc"** is a predecessor of **"abac"**, but **"cba"** is not a predecessor of **"bcad"**.

A **word chain** is a sequence of words [word1, word2, ..., wordk] with k >= 1, where **word1** is a predecessor of **word2**, **word2** is a predecessor of **word3**, and so on.  
A single word is trivially a word chain with k = 1.

You need to **return the length of the longest possible word chain** with words chosen from the given list in any order.


## 🔍 **Example Walkthrough:**

### **Example 1:**  

#### **Input:**  
```
words[] = ["ba", "b", "a", "bca", "bda", "bdca"]
```

#### **Output:**  
```
4
```

#### **Explanation:**  
One of the longest word chains is ["a", "ba", "bda", "bdca"].  


### **Example 2:**  

#### **Input:**  
```
words[] = ["abc", "a", "ab"]
```

#### **Output:**  
```
3
```

#### **Explanation:**  
The longest chain is ["a", "ab", "abc"].  


### **Example 3:**  

#### **Input:**  
```
words[] = ["abcd", "dbqca"]
```

#### **Output:**  
```
1
```

#### **Explanation:**  
The trivial word chain ["abcd"] is one of the longest word chains.  


### **Constraints:**  

- $1 \leq \text{words.length} \leq 10^4$  
- $1 \leq \text{words}[i].\text{length} \leq 10$  
- words[i] only consists of lowercase English letters.  


## 🎯 **My Approach:**

### **Dynamic Programming with Predecessor Check**

### **Algorithm Steps:**  
1. **Sort words by length**. This ensures that whenever we process a word, all possible predecessors (shorter words) are already processed.
2. Use a **HashMap (dp)** where `dp[word]` stores the length of the longest chain ending at `word`.
3. For each word, **try removing every character one by one** to form all possible predecessors.
4. If a predecessor exists in the map, **update the chain length** for the current word.
5. Keep track of the **maximum chain length** found.


## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** O(N * L²), where N is the number of words and L is the maximum length of a word.
- **Expected Auxiliary Space Complexity:** O(N), where N is the number of words stored in the DP table.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public int longestStringChain(String[] words) {
        Arrays.sort(words, Comparator.comparingInt(String::length));
        Map<String, Integer> dp = new HashMap<>();
        int res = 1;
        for (String w : words) {
            dp.put(w, 1);
            for (int i = 0; i < w.length(); i++) {
                String pred = w.substring(0, i) + w.substring(i + 1);
                dp.put(w, Math.max(dp.get(w), dp.getOrDefault(pred, 0) + 1));
            }
            res = Math.max(res, dp.get(w));
        }
        return res;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!  

⭐ **If you find this helpful, please give this repository a star!** ⭐  

--- 
