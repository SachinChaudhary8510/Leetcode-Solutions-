# 📝 LeetCode Problem 1941: Check if All Characters Have Equal Number of Occurrences

## 📘 Problem Statement

Given a string `s`, return `true` if **all the characters** that appear in `s` occur the **same number of times**, and `false` otherwise.

A string is considered **"good"** if the frequency of all distinct characters is the same.

---

## 🧪 Examples

### Example 1:
**Input:**  
`s = "abacbc"`  
**Output:** `true`  
**Explanation:** The characters 'a', 'b', and 'c' each appear twice.

---

### Example 2:
**Input:**  
`s = "aaabb"`  
**Output:** `false`  
**Explanation:** 'a' appears 3 times, 'b' appears 2 times — unequal frequencies.

---

## 📚 Constraints

- `1 <= s.length <= 1000`
- `s` consists of **lowercase English letters only**

---

## ✅ Java Solution

```java
class Solution {
    public boolean areOccurrencesEqual(String s) {
        int[] a = new int[26];
        for (int i = 0; i < s.length(); i++) {
            a[s.charAt(i) - 'a']++;
        }
        int count = 0;
        for (int i = 0; i < 26; i++) {
            if (a[i] == 0) continue;
            if (count == 0) count = a[i];
            else if (a[i] != count) return false;
        }
        return true;
    }
}
```

- **Time Complexity:** O(n)
- **Space Complexity:** O(1)

---

## 🐍 Python Solution

```python
class Solution:
    def areOccurrencesEqual(self, s: str) -> bool:
        from collections import Counter
        freq = Counter(s)
        return len(set(freq.values())) == 1
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    bool areOccurrencesEqual(string s) {
        int freq[26] = {0};
        for (char c : s) {
            freq[c - 'a']++;
        }
        int target = 0;
        for (int i = 0; i < 26; i++) {
            if (freq[i] == 0) continue;
            if (target == 0) target = freq[i];
            else if (freq[i] != target) return false;
        }
        return true;
    }
};
```

---

## 🔍 Complexity Analysis

| Metric           | Value         |
|------------------|---------------|
| Time Complexity  | O(n)          |
| Space Complexity | O(1)          |

> Fixed-size array for lowercase letters yields constant space usage regardless of input size.

---

## 🔬 Test Cases

| Input       | Output |
|-------------|--------|
| `"abacbc"`  | `true` |
| `"aaabb"`   | `false` |
| `"zzzz"`    | `true` |
| `"abcabc"`  | `true` |
| `"a"`       | `true` |

---

## ✅ Final Assessment

| Criteria         | Verdict    |
|------------------|------------|
| Efficiency       | ✅ Optimal |
| Simplicity       | ✅ Concise |
| Edge Case Ready  | ✅ Covered |
| Implementation   | ✅ Clean   |

> This is a textbook frequency analysis problem. Straightforward and efficient — ideal for interviews and code screens.

