# 🚀 LeetCode Problem 1684: Count the Number of Consistent Strings

## 📘 Problem Statement
You are given:
- A string `allowed` consisting of distinct characters.
- An array of strings `words`.

A **string is consistent** if **every character** in the string appears in `allowed`.

Return the **number of consistent strings** in the array `words`.

---

## 🔍 Examples

### Example 1:
**Input:**  
`allowed = "ab"`  
`words = ["ad","bd","aaab","baa","badab"]`  

**Output:**  
`2`  

**Explanation:**  
Only `"aaab"` and `"baa"` consist entirely of `'a'` and `'b'`, which are in `allowed`.

---

### Example 2:
**Input:**  
`allowed = "abc"`  
`words = ["a","b","c","ab","ac","bc","abc"]`  

**Output:**  
`7`  

**Explanation:**  
All words consist only of `'a'`, `'b'`, and `'c'`. All are consistent.

---

### Example 3:
**Input:**  
`allowed = "cad"`  
`words = ["cc","acd","b","ba","bac","bad","ac","d"]`  

**Output:**  
`4`  

**Explanation:**  
Words `"cc"`, `"acd"`, `"ac"`, and `"d"` are consistent.

---

## 🔒 Constraints
- `1 <= words.length <= 10^4`
- `1 <= allowed.length <= 26`
- `1 <= words[i].length <= 10`
- `allowed` contains only distinct lowercase English letters.
- `words[i]` and `allowed` consist of only lowercase English letters.

---

## 💻 Java Solution
```java
class Solution {
    public int countConsistentStrings(String allowed, String[] words) {
        int count = 0;
        for (String i : words) {
            for (int j = 0; j < i.length(); j++) {
                int length1 = 0;
                for (int k = 0; k < allowed.length(); k++) {
                    if (i.charAt(j) == allowed.charAt(k)) {
                        length1++;
                        break;
                    }
                }
                if (length1 == 0) {
                    count--;
                    break;
                }
            }
        }
        return words.length + count;
    }
}
```

---

## 🐍 Python Solution
```python
class Solution:
    def countConsistentStrings(self, allowed: str, words: List[str]) -> int:
        allowed_set = set(allowed)
        return sum(all(char in allowed_set for char in word) for word in words)
```

---

## 💠 C++ Solution
```cpp
class Solution {
public:
    int countConsistentStrings(string allowed, vector<string>& words) {
        unordered_set<char> allowedSet(allowed.begin(), allowed.end());
        int count = 0;
        for (string word : words) {
            bool consistent = true;
            for (char c : word) {
                if (allowedSet.find(c) == allowedSet.end()) {
                    consistent = false;
                    break;
                }
            }
            if (consistent) count++;
        }
        return count;
    }
};
```

---

## ⏱️ Time and Space Complexity
- **Time Complexity:** O(N × M)  
  where N = number of words and M = average word length (at most 10).
- **Space Complexity:** 
  - O(1) for Java (using only counters).
  - O(26) for Python/C++ solutions with `set` or `unordered_set` (constant space).

---

## 🌟 Summary
Despite looking trivial at first glance, this problem tests for **basic nested iteration efficiency** and **early exits** in loops.  
In interviews, choosing the most optimal data structure (like a `HashSet`) **screams competency** — don't brute-force your way into performance bottlenecks. 🚨
