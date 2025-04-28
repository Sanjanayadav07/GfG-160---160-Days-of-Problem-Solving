---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Trie
  - Design-Pattern
  - Advanced Data Structure
---

#  _Day 1. Implement Trie_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/tries-gfg-160/problem/trie-insert-and-search0651)  

## 💡 **Problem Description:**

Implement the Trie data structure. You are given queries of the following three types:
- **Type 1**: Insert a word into the Trie.
- **Type 2**: Search whether a word exists in the Trie.
- **Type 3**: Check whether a word is a prefix of any word stored in the Trie.

> 📅 Note: Sorry for uploading late, my Final Sem exam is going on.


## 🔍 **Example Walkthrough:**

### **Example 1:**  
#### **Input:**  
`[[1, "abcd"], [1, "abc"], [1, "bcd"], [2, "bc"], [3, "bc"], [2, "abc"]]`  
#### **Output:**  
`[false, true, true]`  
#### **Explanation:**  
- "bc" does not exist as a word  
- "bc" exists as prefix of "bcd"  
- "abc" exists  


### **Example 2:**  
#### **Input:**  
`[[1, "gfg"], [1, "geeks"], [3, "fg"], [3, "geek"], [2, "for"]]`  
#### **Output:**  
`[false, true, false]`  
#### **Explanation:**  
- "fg" is not a prefix  
- "geek" is a prefix of "geeks"  
- "for" not in Trie  


### **Constraints:**  
- $1 \leq \text{query.size()} \leq 10^4$  
- $1 \leq \text{word.size()} \leq 10^3$  


## 🎯 **My Approach:**

### **Fixed-Size Trie Using 26 Pointers**  

### **Algorithm Steps:**

We create a class Trie, with a nested structure (Node) that stores a boolean flag for end of word and a fixed array of 26 pointers (one for each lowercase letter).  
- **Insert:** Walk through characters, initialize child if needed.  
- **Search:** Check for existence and end-of-word.  
- **Prefix:** Just ensure prefix exists in Trie.


## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(L), where L = length of the word  
- **Expected Auxiliary Space Complexity:** O(1), as each function uses constant extra space aside from Trie structure itself  

## 📝 **Solution Code**
## **Code (Java)**

```java
class Trie {
    class N { N[] c = new N[26]; boolean e; }
    N r = new N();
    public void insert(String w) {
        N n = r;
        for (char ch : w.toCharArray())
            n = n.c[ch - 'a'] != null ? n.c[ch - 'a'] : (n.c[ch - 'a'] = new N());
        n.e = true;
    }
    public boolean search(String w) {
        N n = r;
        for (char ch : w.toCharArray())
            if ((n = n.c[ch - 'a']) == null) return false;
        return n.e;
    }
    public boolean isPrefix(String w) {
        N n = r;
        for (char ch : w.toCharArray())
            if ((n = n.c[ch - 'a']) == null) return false;
        return true;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---
