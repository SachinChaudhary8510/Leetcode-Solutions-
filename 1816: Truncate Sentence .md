
# 🟢 LeetCode 1816: Truncate Sentence

## 📌 Problem Statement

A **sentence** is a string of words separated by single spaces, with no leading or trailing spaces.
You are given a sentence `s` and an integer `k`. Truncate `s` to contain only the first `k` words.

---

## 🧩 Examples

### Example 1
**Input:**  
`s = "Hello how are you Contestant", k = 4`  
**Output:** `"Hello how are you"`

### Example 2
**Input:**  
`s = "What is the solution to this problem", k = 4`  
**Output:** `"What is the solution"`

### Example 3
**Input:**  
`s = "chopper is not a tanuki", k = 5`  
**Output:** `"chopper is not a tanuki"`

---

## ✅ Constraints

- `1 <= s.length <= 500`
- `k` is in the range `[1, the number of words in s]`
- `s` contains only uppercase/lowercase English letters and spaces
- Words are separated by **a single space**

---

## 💻 Java Solution

```java
class Solution {
    public String truncateSentence(String s, int k) {
        int count = 1;
        String str = "";
        for(int i = 0 ; i < s.length() ; i++){
            char c = s.charAt(i);
            if(c != ' ')
                str += c;
            else if(c == ' ' && count != k){
                str += c;
                count++;
            } else
                break;
        }
        return str;
    }
}
```

---

## 🐍 Python Solution

```python
class Solution:
    def truncateSentence(self, s: str, k: int) -> str:
        return " ".join(s.split()[:k])
```

**📝 Explanation:**  
- Split the sentence into words
- Join the first `k` words with a space

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    string truncateSentence(string s, int k) {
        int count = 0;
        string result = "";
        for (char c : s) {
            if (c == ' ') {
                count++;
                if (count == k) break;
            }
            result += c;
        }
        return result;
    }
};
```

**📝 Explanation:**  
- Iterate over each character
- Count spaces until `k` words are collected

---

## 🏆 Summary

| Language | Logic | Performance |
|----------|-------|-------------|
| Java     | Manual char iteration | Good for learning character-level parsing |
| Python   | Use of built-in split & join | Most concise and pythonic |
| C++      | Efficient space-counting loop | Fast and memory-efficient |

🔑 **Key Insight:** Break the sentence using space as a delimiter and limit the result to `k` segments.

---

🚀 Happy Coding! 🔥  
💬 _Contributions & suggestions are welcome!_
