# 📝 LeetCode Problem 242: Valid Anagram

## 📘 Problem Statement

Given two strings `s` and `t`, determine if `t` is an anagram of `s`.

An anagram is a word formed by rearranging the letters of another word using **all** the original letters **exactly once**.

---

## 🧪 Examples

### Example 1:
**Input:**  
`s = "anagram"`  
`t = "nagaram"`  
**Output:** `true`  
**Explanation:** `t` is an anagram of `s`

---

### Example 2:
**Input:**  
`s = "rat"`  
`t = "car"`  
**Output:** `false`  
**Explanation:** They do not contain the same letters

---

## 📚 Constraints

- `1 <= s.length, t.length <= 5 × 10⁴`
- `s` and `t` consist of lowercase English letters only

---

## ⚠️ Follow-up

Can you solve it in **O(n)** time **without sorting**?

---

## 💻 Java Solution

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length() != t.length())
            return false;

        int[] a = new int[26];
        int[] b = new int[26];

        for(int i = 0; i < s.length(); i++){
            a[s.charAt(i) - 'a']++;
            b[t.charAt(i) - 'a']++;
        }

        for(int i = 0; i < 26; i++){
            if(a[i] != b[i])
                return false;
        }

        return true;
    }
}
```

---

## 🐍 Python Solution

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        count = [0] * 26

        for i in range(len(s)):
            count[ord(s[i]) - ord('a')] += 1
            count[ord(t[i]) - ord('a')] -= 1

        for c in count:
            if c != 0:
                return False

        return True
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        if (s.length() != t.length())
            return false;

        int count[26] = {0};

        for (int i = 0; i < s.length(); i++) {
            count[s[i] - 'a']++;
            count[t[i] - 'a']--;
        }

        for (int i = 0; i < 26; i++) {
            if (count[i] != 0)
                return false;
        }

        return true;
    }
};
```

---

## ⏱ Complexity Analysis

| Metric           | Value          |
|------------------|----------------|
| Time Complexity  | O(n)           |
| Space Complexity | O(1) – fixed array |

---

## ✅ Code Review

| Aspect              | Verdict                                        |
|---------------------|------------------------------------------------|
| Efficiency          | ✅ Linear time with fixed memory                |
| Correctness         | ✅ Matches spec in all edge cases              |
| Optimization        | ✅ Uses array counters instead of sorting      |
| Naming Conventions  | ⚠️ Consider `charCount` instead of `a` / `b`  |
| Readability         | ✅ Clear and concise                            |

---

## 🧾 Final Verdict

| Area           | Verdict                  |
|----------------|---------------------------|
| Production Use | ✅ Yes                    |
| Refactor Need  | ❌ Minor (variable naming) |
| Cross-Language | ✅ Identical logic         |

> 📌 Strong foundational problem. Efficient, scalable, and extensible for larger character sets (e.g., Unicode) with minimal tweaks.
