---
Difficulty: Hard
Source: 160 Days of Problem Solving
Tags:
  - Graph
  - Strings
  - Sorting
---

#  _Day 15. Alien Dictionary_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/graph-gfg-160/problem/alien-dictionary)  



## 💡 **Problem Description:**

A new alien language uses the English alphabet, but the order of the letters is unknown. You are given a list of words from the alien language’s dictionary, where the words are said to be sorted lexicographically by the language's own letter order.

Your task is to **determine the correct order of letters** based on the given words.  
If multiple valid orderings are possible, return any one of them.  
If no valid ordering exists (i.e., the words are not consistent with any letter ordering), return an empty string (`""`).



## 🔍 **Example Walkthrough:**

### **Example 1:**  
**Input:**  
`words[] = ["cb", "cba", "a", "bc"]`  
**Output:**  
`true`  
**Explanation:**  
One valid letter order is: `"cab"`.

### **Example 2:**  
**Input:**  
`words[] = ["ab", "aa", "a"]`  
**Output:**  
`""`  
**Explanation:**  
The order is invalid because `"aa"` appears before `"a"`.

### **Example 3:**  
**Input:**  
`words[] = ["ab", "cd", "ef", "ad"]`  
**Output:**  
`""`  
**Explanation:**  
There is a contradiction in the letter ordering.



### **Constraints**
- $1 \leq \text{words.length} \leq 500$  
- $1 \leq \text{words}[i].\text{length} \leq 100$  
- $\text{words}[i]$ consists only of lowercase English letters.  



## 🎯 **My Approach:**

### **Topological Sort using Kahn’s Algorithm (BFS)**

We model the **characters as graph nodes**, and **directed edges represent the precedence** between letters.

### **Algorithm Steps**:
1. Create an adjacency list `graph` to store the directed relationships (edges) between characters.
2. Build the graph by comparing adjacent words in the list:
   - For two words `a` and `b`, find the first index `i` where `a[i] != b[i]`.
   - Add a directed edge from `a[i]` to `b[i]`.
   - If `b` is a prefix of `a` and shorter, the input is invalid.
3. Compute in-degrees for all characters.
4. Use a **queue to apply Kahn’s Algorithm** for topological sorting:
   - Initialize the queue with all characters having `0 in-degree`.
   - Repeatedly remove a character from the queue, append to result, and decrement the in-degree of its neighbors.
5. If the result length is less than the number of unique characters, a cycle exists — return `""`.


## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(N + K)`, where  
  - `N` is the total number of characters across all words, and  
  - `K` is the number of distinct precedence relationships (edges in the graph).  
  We traverse each word once and process each edge once during topological sort.

- **Expected Auxiliary Space Complexity:** `O(N + K)`,  
  for the graph representation, in-degree array, and the result string.

## 📝 **Solution Code**

  ## **Code (Java)**

```java
class Solution {
    public String findOrder(String[] w) {
        List<List<Integer>> g = new ArrayList<>();
        int[] in = new int[26];
        boolean[] seen = new boolean[26];
        for (int i = 0; i < 26; i++) g.add(new ArrayList<>());
        for (String s : w) for (char c : s.toCharArray()) seen[c - 'a'] = true;
        for (int i = 0; i < w.length - 1; i++) {
            String a = w[i], b = w[i + 1];
            int j = 0, n = Math.min(a.length(), b.length());
            while (j < n && a.charAt(j) == b.charAt(j)) j++;
            if (j == n && a.length() > b.length()) return "";
            if (j < n) {
                g.get(a.charAt(j) - 'a').add(b.charAt(j) - 'a');
                in[b.charAt(j) - 'a']++;
            }
        }
        Queue<Integer> q = new LinkedList<>();
        for (int i = 0; i < 26; i++) if (seen[i] && in[i] == 0) q.add(i);
        StringBuilder res = new StringBuilder();
        while (!q.isEmpty()) {
            int u = q.poll();
            res.append((char)(u + 'a'));
            for (int v : g.get(u)) if (--in[v] == 0) q.add(v);
        }
        for (int i = 0; i < 26; i++) if (seen[i] && in[i] > 0) return "";
        return res.toString();
    }
}
```


## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---


