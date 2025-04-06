# 🟢 LeetCode 3019: Number of Changing Keys

## 📌 Problem Statement

You are given a 0-indexed string `s` typed by a user. Changing a key is defined as using a key **different** from the last used key. For example, `s = "ab"` has a change of a key, while `s = "bBBb"` does **not** have any.

### ⚠️ Note
Modifiers like **Shift** or **Caps Lock** are ignored. That means typing `'a'` and `'A'` is considered using the same key.

---

## 🧩 Examples

### 🔸 Example 1
**Input:** `s = "aAbBcC"`  
**Output:** `2`  
**Explanation:**
- `a` → `A`: No change
- `A` → `b`: 🔁 key changed
- `b` → `B`: No change
- `B` → `c`: 🔁 key changed
- `c` → `C`: No change

### 🔸 Example 2
**Input:** `s = "AaAaAaaA"`  
**Output:** `0`  
**Explanation:** Only the `'a'` key was used, regardless of case.

---

## ✅ Java Solution

```java
class Solution {
    public int countKeyChanges(String s) {
        int count = 0 ;
        for(int i = 0 ; i  < s.length() - 1; i++ ){
            char c = s.charAt(i);
            char d = s.charAt(i + 1);
            if (c == d || c == d + 32 || d == c + 32) {
                // Same key (ignoring case)
            } else {
                count++;
            }
        }
        return count;
    }
}
```

---

## 🐍 Python Solution

```python
class Solution:
    def countKeyChanges(self, s: str) -> int:
        count = 0
        for i in range(len(s) - 1):
            if s[i].lower() != s[i + 1].lower():
                count += 1
        return count
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    int countKeyChanges(string s) {
        int count = 0;
        for (int i = 0; i < s.size() - 1; ++i) {
            if (tolower(s[i]) != tolower(s[i + 1])) {
                ++count;
            }
        }
        return count;
    }
};
```

---

## 🏁 Summary

| Language | Code Type         | Notes                          |
|----------|-------------------|--------------------------------|
| Java     | Character Compare | ASCII offset for case check    |
| Python   | Simpler Logic     | Uses `lower()` for comparison  |
| C++      | Efficient Compare | Uses `tolower()`                |

🧠 **Key Insight:** Normalize the characters to lowercase and compare to detect key changes.

---

🚀 **Happy Coding!**  
💬 Got a better way? Let's optimize together!
