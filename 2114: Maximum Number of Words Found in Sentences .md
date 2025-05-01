# 📝 LeetCode Problem 2114: Maximum Number of Words Found in Sentences

## 📘 Problem Statement

You're given an array of strings `sentences`, where each element represents a valid sentence. Each sentence consists of words separated by single spaces, with no leading or trailing spaces. Your task is to return the **maximum number of words** in any single sentence.

---

## 🧪 Examples

### Example 1:
**Input:**  
`sentences = ["alice and bob love leetcode", "i think so too", "this is great thanks very much"]`  
**Output:** `6`  
**Explanation:**  
- Sentence 1: 5 words  
- Sentence 2: 4 words  
- Sentence 3: 6 words ← ✅ max

---

### Example 2:
**Input:**  
`sentences = ["please wait", "continue to fight", "continue to win"]`  
**Output:** `3`  
**Explanation:**  
- Each of the last two sentences has 3 words  
- So the maximum is 3

---

## 📚 Constraints

- `1 <= sentences.length <= 100`
- `1 <= sentences[i].length <= 100`
- Only lowercase English letters and single spaces are used
- Sentences are well-formed — no extra whitespace, no punctuation

---

## 💻 Java Solution

```java
class Solution {
    public int mostWordsFound(String[] s) {
        int count = 1;
        for (int i = 0; i < s.length; i++) {
            int words = 1;
            for (int j = 0; j < s[i].length(); j++) {
                if (s[i].charAt(j) == ' ') {
                    words++;
                }
            }
            if (words > count)
                count = words;
        }
        return count;
    }
}
```

---

## 🐍 Python Solution

```python
class Solution:
    def mostWordsFound(self, sentences: List[str]) -> int:
        max_words = 0
        for sentence in sentences:
            word_count = sentence.count(' ') + 1
            max_words = max(max_words, word_count)
        return max_words
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    int mostWordsFound(vector<string>& sentences) {
        int maxWords = 0;
        for (const string& s : sentences) {
            int words = 1;
            for (char ch : s) {
                if (ch == ' ') words++;
            }
            maxWords = max(maxWords, words);
        }
        return maxWords;
    }
};
```

---

## ✅ Code Review

| Metric                | Verdict                                                   |
|------------------------|------------------------------------------------------------|
| **Correctness**         | ✅ Passes all test cases, both minimal and maximal         |
| **Logic**               | ✅ Each solution counts spaces to infer word count         |
| **Naming Convention**   | ⚠️ Java: consider renaming `count` → `maxWords` for clarity |
| **Optimization**        | ✅ Efficient with linear scans only                        |
| **Cross-Language**      | ✅ Solutions are consistent across Java, Python, C++       |

---

## ⏱ Time and Space Complexity

| Metric           | Value                 |
|------------------|------------------------|
| Time Complexity  | O(n · m)               |
| Space Complexity | O(1) (in-place counting) |

---

## 🧾 Final Verdict

| Category         | Verdict                         |
|------------------|----------------------------------|
| Code Quality     | ✅ Simple and efficient          |
| Production-Ready | ✅ Yes                           |
| Optimization     | ✅ Meets problem constraints     |
| Refactor Needed  | ❌ Minor naming tweak suggested  |

> 📌 Excellent cross-language problem. Easily extendable and safe for real-time string processing environments.

