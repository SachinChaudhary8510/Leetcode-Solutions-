# 🔍 LeetCode Problem 2108: Find First Palindromic String in the Array

## 📘 Problem Statement

Given an array of strings `words`, return **the first palindromic string** in the array.  
If there is **no palindromic string**, return an empty string `""`.

> A **palindromic string** is one that reads the same forward and backward.

---

## 🧪 Examples

### Example 1:
**Input:**  
`words = ["abc","car","ada","racecar","cool"]`  
**Output:** `"ada"`  
**Explanation:**  
"ada" is the first palindrome found. "racecar" is also a palindrome but not the first.

---

### Example 2:
**Input:**  
`words = ["notapalindrome","racecar"]`  
**Output:** `"racecar"`

---

### Example 3:
**Input:**  
`words = ["def","ghi"]`  
**Output:** `""`

---

## 📚 Constraints

- `1 <= words.length <= 100`
- `1 <= words[i].length <= 100`
- Each `words[i]` consists of **only lowercase English letters**

---

## ✅ Java Solution

```java
class Solution {
    public static boolean palindrome(String s) {
        for (int i = 0; i < (s.length() + 1) / 2; i++) {
            if (s.charAt(i) != s.charAt(s.length() - 1 - i))
                return false;
        }
        return true;
    }

    public String firstPalindrome(String[] words) {
        for (int i = 0; i < words.length; i++) {
            if (palindrome(words[i]))
                return words[i];
        }
        return "";
    }
}
```

- **Time Complexity:** O(n × m), where n = number of words and m = average word length
- **Space Complexity:** O(1)

---

## 🐍 Python Solution

```python
class Solution:
    def firstPalindrome(self, words: List[str]) -> str:
        for word in words:
            if word == word[::-1]:  # Checks for palindrome
                return word
        return ""
```

- Uses Python string slicing for concise palindrome checking.

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    bool isPalindrome(const string& s) {
        int left = 0, right = s.size() - 1;
        while (left < right) {
            if (s[left++] != s[right--]) return false;
        }
        return true;
    }

    string firstPalindrome(vector<string>& words) {
        for (const string& word : words) {
            if (isPalindrome(word))
                return word;
        }
        return "";
    }
};
```

- Efficient pointer-based comparison with constant space.

---

## 🔍 Complexity Analysis

| Metric           | Value         |
|------------------|---------------|
| Time Complexity  | O(n × m)      |
| Space Complexity | O(1)          |
| Stability        | ✅ Safe        |
| In-place         | ✅ Yes         |

---

## 🧠 Key Insights

- This is a classic **scan-and-check** problem.
- Minimal overhead: no use of extra data structures.
- Slicing (Python) and pointer checks (C++) offer efficient palindrome testing.

---

## 🧪 Recommended Test Cases

| Input                                       | Output     |
|--------------------------------------------|------------|
| `["abc", "cdc", "ada"]`                     | `"cdc"`    |
| `["a"]`                                     | `"a"`      |
| `["abc", "def", "ghi"]`                     | `""`       |
| `["racecar", "madam", "step"]`              | `"racecar"`|

---

## ✅ Final Verdict

| Area             | Verdict         |
|------------------|-----------------|
| Time Efficiency  | ✅ Optimal       |
| Space Usage      | ✅ Constant      |
| Logic Clarity    | ✅ Transparent   |
| Code Structure   | ✅ Maintainable  |

> Quick string-based linear scan. Excellent for warm-up or basic string manipulation rounds.
