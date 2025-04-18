---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Dynamic Programming
---

#  _Day 23. Word Break_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/dynamic-programming-gfg-160/problem/word-break1352)

## 💡 **Problem Description:**

You are given a string `s` and a list `dictionary[]` of words. Your task is to determine whether the string `s` can be formed by concatenating one or more words from the `dictionary[]`.

**Note:** From `dictionary[]`, any word can be taken any number of times and in any order.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```plaintext
s = "ilike"
dictionary[] = ["i", "like", "gfg"]
```

#### **Output:**

```plaintext
true
```

#### **Explanation:**

The given string `s` can be broken down as `"i like"` using words from the dictionary.

### **Example 2:**

#### **Input:**

```plaintext
s = "ilikegfg"
dictionary[] = ["i", "like", "man", "india", "gfg"]
```

#### **Output:**

```plaintext
true
```

#### **Explanation:**

The given string `s` can be broken down as `"i like gfg"` using words from the dictionary.

### **Example 3:**

#### **Input:**

```plaintext
s = "ilikemangoes"
dictionary[] = ["i", "like", "man", "india", "gfg"]
```

#### **Output:**

```plaintext
false
```

#### **Explanation:**

The given string `s` **cannot** be formed using the dictionary words.

### **Constraints:**

- $\( 1 \leq |s| \leq 3000 \)$
- $\( 1 \leq |dictionary| \leq 1000 \)$
- $\( 1 \leq |dictionary[i]| \leq 100 \)$

## 🎯 **My Approach:**

### **Dynamic Programming**

#### **Algorithm Steps:**

1. Use a boolean DP vector `dp` of size _n+1_ where `dp[i]` indicates if the substring `s[0...i-1]` can be segmented.
2. Insert dictionary words into an unordered set for O(1) lookups.
3. Iterate through the string and check all possible substrings using the dictionary.
4. If a valid word is found and its prefix was segmentable, mark `dp[i+j]` as true.
5. Return `dp[n]`.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** $\( O(n \times m) \)$, as each substring is checked in the dictionary.
- **Expected Auxiliary Space Complexity:** $\( O(n) \)$, as we use a DP array of size `n+1`.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public boolean wordBreak(String s, String[] d) {
        Set<String> set = new HashSet<>(Arrays.asList(d));
        int n = s.length(), m = 0;
        for (String w : d) m = Math.max(m, w.length());
        boolean[] dp = new boolean[n + 1];
        dp[0] = true;
        for (int i = 0; i < n; i++) {
            if (!dp[i]) continue;
            for (int j = 1; j <= m && i + j <= n; j++)
                if (set.contains(s.substring(i, i + j))) dp[i + j] = true;
        }
        return dp[n];
    }
}
```


## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐
