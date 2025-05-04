# 🔍 LeetCode Problem 387: First Unique Character in a String

## 📘 Problem Statement

Given a string `s`, find the **first non-repeating character** and return **its index**. If no such character exists, return `-1`.

---

## 🧪 Examples

### Example 1:
**Input:**  
`s = "leetcode"`  
**Output:** `0`  
**Explanation:** `'l'` appears only once and is the first such character.

---

### Example 2:
**Input:**  
`s = "loveleetcode"`  
**Output:** `2`  
**Explanation:** `'v'` is the first character that occurs only once.

---

### Example 3:
**Input:**  
`s = "aabb"`  
**Output:** `-1`  
**Explanation:** No characters are unique.

---

## 📚 Constraints

- `1 <= s.length <= 10⁵`
- `s` consists of only **lowercase English letters**.

---

## ✅ Java Solution

```java
class Solution {
    public int firstUniqChar(String s) {
        int[] a = new int[26];
        for (int i = 0; i < s.length(); i++) {
            a[s.charAt(i) - 'a']++;
        }
        for (int i = 0; i < s.length(); i++) {
            if (a[s.charAt(i) - 'a'] == 1)
                return i;
        }
        return -1;
    }
}
```

- **Time Complexity:** O(n)
- **Space Complexity:** O(1) — fixed 26-length array

---

## 🐍 Python Solution

```python
class Solution:
    def firstUniqChar(self, s: str) -> int:
        freq = [0] * 26
        for c in s:
            freq[ord(c) - ord('a')] += 1
        for i, c in enumerate(s):
            if freq[ord(c) - ord('a')] == 1:
                return i
        return -1
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    int firstUniqChar(string s) {
        int count[26] = {0};
        for (char c : s) {
            count[c - 'a']++;
        }
        for (int i = 0; i < s.size(); i++) {
            if (count[s[i] - 'a'] == 1)
                return i;
        }
        return -1;
    }
};
```

---

## 🔍 Complexity Analysis

| Metric           | Value         |
|------------------|---------------|
| Time Complexity  | O(n)          |
| Space Complexity | O(1)          |

- Uses only a constant array of size 26, independent of input size.

---

## 🧠 Key Insights

- Frequency arrays are more efficient than hash maps for lowercase-only problems.
- Two-pass linear scan ensures performance is optimal and avoids early false positives.

---

## 🧪 Edge Case Testing

| Input         | Output |
|---------------|--------|
| `"a"`         | `0`    |
| `"aa"`        | `-1`   |
| `"aabbcc"`    | `-1`   |
| `"zxyxzyz"`   | `2`    |

---

## ✅ Final Verdict

| Area             | Verdict       |
|------------------|---------------|
| Performance      | ✅ Optimal     |
| Readability      | ✅ Clean       |
| Edge Handling    | ✅ Robust      |
| Space Usage      | ✅ Constant    |

> This is a textbook frequency-array problem. Any attempt to over-engineer (e.g., HashMap) for this case is unnecessary and inefficient in high-volume inputs.

