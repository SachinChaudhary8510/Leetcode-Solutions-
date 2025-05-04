# 📝 LeetCode Problem 1832: Check if the Sentence Is Pangram

## 📘 Problem Statement

A **pangram** is a sentence where every letter of the English alphabet appears **at least once**.

Given a string `sentence` containing only **lowercase English letters**, return `true` if the sentence is a pangram, or `false` otherwise.

---

## 🧪 Examples

### Example 1:
**Input:**  
`sentence = "thequickbrownfoxjumpsoverthelazydog"`  
**Output:** `true`  
**Explanation:** The sentence includes every character from 'a' to 'z'.

---

### Example 2:
**Input:**  
`sentence = "leetcode"`  
**Output:** `false`  
**Explanation:** Several letters are missing.

---

## 📚 Constraints

- `1 <= sentence.length <= 1000`
- `sentence` consists of **lowercase English letters only**.

---

## ✅ Java Solution

```java
class Solution {
    public boolean checkIfPangram(String sentence) {
        int[] a = new int[26];
        for (int i = 0; i < sentence.length(); i++) {
            a[sentence.charAt(i) - 'a']++;
        }
        for (int i = 0; i < 26; i++) {
            if (a[i] == 0)
                return false;
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
    def checkIfPangram(self, sentence: str) -> bool:
        seen = [0] * 26
        for ch in sentence:
            seen[ord(ch) - ord('a')] += 1
        return all(x > 0 for x in seen)
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    bool checkIfPangram(string sentence) {
        int count[26] = {0};
        for (char c : sentence) {
            count[c - 'a']++;
        }
        for (int i = 0; i < 26; i++) {
            if (count[i] == 0)
                return false;
        }
        return true;
    }
};
```

---

## 🧠 Key Insights

- The solution leverages a **fixed-size array of 26** elements to track character occurrence.
- Optimal for lowercase-only constraints.
- `Set`-based alternatives exist, but they are more memory-expensive and less performant.

---

## 🔍 Complexity Analysis

| Metric           | Value         |
|------------------|---------------|
| Time Complexity  | O(n)          |
| Space Complexity | O(1)          |

- Space is constant due to the fixed 26-length array.

---

## 🔬 Test Cases

| Input                                | Output |
|-------------------------------------|--------|
| `"thequickbrownfoxjumpsoverthelazydog"` | `true` |
| `"leetcode"`                        | `false` |
| `"abcdefghijklmnopqrstuvwxyz"`      | `true` |
| `"abcde"`                           | `false` |

---

## ✅ Final Assessment

| Criteria         | Verdict    |
|------------------|------------|
| Efficiency       | ✅ Optimal |
| Simplicity       | ✅ Clean   |
| Scalability      | ✅ High    |
| Correctness      | ✅ Verified|

> This is a direct application of frequency counting with a 26-length array. Anything more is wasted abstraction.

