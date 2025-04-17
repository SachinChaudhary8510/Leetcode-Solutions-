# 🚀 LeetCode Problem 1528: Shuffle String

## 📘 Problem Statement
You are given a string `s` and an integer array `indices` of the same length. The string `s` will be shuffled such that the character at the `i-th` position moves to `indices[i]` in the shuffled string.

Return the shuffled string.

---

## 🔍 Examples

### Example 1:
**Input:**  
`s = "codeleet"`  
`indices = [4,5,6,7,0,2,1,3]`  
**Output:**  
`"leetcode"`  
**Explanation:**  
"codeleet" becomes "leetcode" after rearranging characters to the given indices.

---

### Example 2:
**Input:**  
`s = "abc"`  
`indices = [0,1,2]`  
**Output:**  
`"abc"`  
**Explanation:**  
All characters remain in their original position.

---

## 🔒 Constraints
- `s.length == indices.length == n`
- `1 <= n <= 100`
- `s` consists of only lowercase English letters.
- `0 <= indices[i] < n`
- All values of `indices` are unique.

---

## 💻 Java Solution
```java
class Solution {
    public String restoreString(String s, int[] indices) {
        int n = s.length();
        char[] ans = new char[n];
        for (int i = 0; i < n; ++i) {
            ans[indices[i]] = s.charAt(i);
        }
        return String.valueOf(ans);
    }
}
```

---

## 🐍 Python Solution
```python
class Solution:
    def restoreString(self, s: str, indices: List[int]) -> str:
        n = len(s)
        result = [''] * n
        for i in range(n):
            result[indices[i]] = s[i]
        return ''.join(result)
```

---

## 💠 C++ Solution
```cpp
class Solution {
public:
    string restoreString(string s, vector<int>& indices) {
        string result = s;
        for (int i = 0; i < s.length(); ++i) {
            result[indices[i]] = s[i];
        }
        return result;
    }
};
```

---

## ⏱️ Time and Space Complexity
- **Time Complexity:** O(n)  
- **Space Complexity:** O(n)

---

## 🌟 Summary
This is a classic index-mapping problem that requires building a new structure based on reordering rules. It checks for correct use of auxiliary data structures and index-based assignments—a core skill for string manipulation problems.
