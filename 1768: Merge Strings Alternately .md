# 🔀 LeetCode Problem 1768: Merge Strings Alternately

## 📘 Problem Statement

You are given two strings `word1` and `word2`.

**Task:** Merge the strings by alternating characters from each, starting with `word1`.  
If one string is longer than the other, **append the remaining characters** of the longer string at the end.

---

## 🧪 Examples

### Example 1:
**Input:**  
`word1 = "abc"`  
`word2 = "pqr"`  
**Output:** `"apbqcr"`

### Example 2:
**Input:**  
`word1 = "ab"`  
`word2 = "pqrs"`  
**Output:** `"apbqrs"`

### Example 3:
**Input:**  
`word1 = "abcd"`  
`word2 = "pq"`  
**Output:** `"apbqcd"`

---

## 📚 Constraints

- `1 <= word1.length, word2.length <= 100`
- Both `word1` and `word2` contain only **lowercase English letters**

---

## ✅ Java Solution

```java
class Solution {
    public String mergeAlternately(String word1, String word2) {
        StringBuilder result = new StringBuilder();
        int i = 0;

        // Merge alternating characters
        while (i < word1.length() && i < word2.length()) {
            result.append(word1.charAt(i));
            result.append(word2.charAt(i));
            i++;
        }

        // Append the remaining part of the longer string
        while (i < word1.length()) {
            result.append(word1.charAt(i++));
        }

        while (i < word2.length()) {
            result.append(word2.charAt(i++));
        }

        return result.toString();
    }
}
```

- **Time Complexity:** O(n + m)  
- **Space Complexity:** O(n + m) (result string)

---

## 🐍 Python Solution

```python
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        result = []

        i = 0
        while i < len(word1) or i < len(word2):
            if i < len(word1):
                result.append(word1[i])
            if i < len(word2):
                result.append(word2[i])
            i += 1

        return ''.join(result)
```

- Uses a list as a buffer for string construction (efficient in Python)

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    string mergeAlternately(string word1, string word2) {
        string result;
        int i = 0;

        while (i < word1.size() || i < word2.size()) {
            if (i < word1.size()) result += word1[i];
            if (i < word2.size()) result += word2[i];
            i++;
        }

        return result;
    }
};
```

- Directly manipulates the `string` object for performance and simplicity

---

## 🔍 Complexity Analysis

| Metric           | Value       |
|------------------|-------------|
| Time Complexity  | O(n + m)    |
| Space Complexity | O(n + m)    |
| Stability        | ✅ Safe      |
| In-place         | ❌ Uses buffer (acceptable) |

---

## 📌 Key Observations

- **Character-wise merge** is trivial — use two pointers.
- No need for sorting or queue/stack operations.
- Excellent candidate for interview rounds on string manipulation and boundary condition awareness.

---

## 🧠 Pro Tip

In production scenarios, prefer using `StringBuilder`/`StringBuffer` in Java or list buffering in Python to avoid costly immutable string concatenations.

---

## 🔎 Test Cases to Validate

| Input                | Output         |
|---------------------|----------------|
| `"a"`, `"b"`         | `"ab"`         |
| `"abc"`, `"defgh"`   | `"adbcefgh"`   |
| `"longer"`, `"short"`| `"lsohnogrter"`|
| `"a" * 100`, `"b"`   | `"abababab...a"` (101 chars) |

---

## ✅ Final Verdict

| Area             | Verdict        |
|------------------|----------------|
| Time Efficiency  | ✅ Optimal      |
| Space Usage      | ✅ Acceptable   |
| Clarity          | ✅ Clean logic  |
| Constraint Fit   | ✅ Robust       |

> A must-know pattern for alternating merges or zipping sequences.
