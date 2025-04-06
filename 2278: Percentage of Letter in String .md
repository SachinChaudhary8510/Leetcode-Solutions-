
# 🟢 LeetCode 2278: Percentage of Letter in String

## 📌 Problem Statement

Given a string `s` and a character `letter`, return the percentage of characters in `s` that equal `letter`, **rounded down** to the nearest whole percent.

---

## 🧩 Examples

### Example 1:
**Input:**
```text
s = "foobar", letter = "o"
```
**Output:**
```text
33
```
**Explanation:**  
2 out of 6 characters in `"foobar"` are `'o'` → (2 / 6) * 100 = **33.33%**, rounded down to **33%**

---

### Example 2:
**Input:**
```text
s = "jjjj", letter = "k"
```
**Output:**
```text
0
```
**Explanation:**  
No `'k'` in `"jjjj"` → 0 / 4 = 0%

---

## ✅ Constraints

- `1 <= s.length <= 100`
- `s` consists of **lowercase English letters**
- `letter` is a lowercase English letter

---

## ✅ Java Solution

```java
class Solution {
    public int percentageLetter(String s, char letter) {
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == letter)
                count++;
        }
        return (count * 100) / s.length();
    }
}
```

---

## 🐍 Python Solution

```python
class Solution:
    def percentageLetter(self, s: str, letter: str) -> int:
        count = s.count(letter)
        return (count * 100) // len(s)
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    int percentageLetter(string s, char letter) {
        int count = 0;
        for(char c : s){
            if(c == letter)
                count++;
        }
        return (count * 100) / s.length();
    }
};
```

---

## 🧠 Key Takeaway

- Efficient solutions across all languages just use basic counting and integer division.
- Integer division automatically handles rounding down as required.

---

🚀 **Simple logic. Accurate math. Reliable output.**  
💡 **Perfect warm-up problem for basic string and math ops.**
