# 🌟 LeetCode Problem 2390: Removing Stars From a String

## 📘 Problem Statement

You are given a string `s` containing lowercase letters and stars `*`.

In one operation, you:

- Remove the **closest non-star character to the left** of a `*`
- Remove the `*` itself

You must perform **all such operations** and return the resulting string.

> ✅ It is guaranteed that every `*` will have a non-star character before it.  
> ✅ The result will always be **uniquely** determined.

---

## 🧪 Examples

### Example 1:

**Input:** `s = "leet**cod*e"`  
**Output:** `"lecoe"`

**Explanation:**

- `"leet**cod*e"` → remove 't' and `*` → `"lee*cod*e"`
- → remove 'e' and `*` → `"lecod*e"`
- → remove 'd' and `*` → `"lecoe"`

---

### Example 2:

**Input:** `s = "erase*****"`  
**Output:** `""`  

All characters are removed step-by-step.

---

## 📚 Constraints

- `1 <= s.length <= 10⁵`
- `s` contains lowercase letters and `*`
- Each `*` has a valid non-star character before it

---

## ✅ Java Solution

```java
public class Solution {
    public String removeStars(String s) {
        StringBuilder result = new StringBuilder();

        for (char c : s.toCharArray()) {
            if (c == '*') {
                result.deleteCharAt(result.length() - 1); // Simulate pop
            } else {
                result.append(c); // Simulate push
            }
        }

        return result.toString();
    }
}
```

- Time Complexity: O(n)
- Space Complexity: O(n) (due to stack simulation using `StringBuilder`)

---

## 🐍 Python Solution

```python
class Solution:
    def removeStars(self, s: str) -> str:
        result = []

        for ch in s:
            if ch == '*':
                result.pop()
            else:
                result.append(ch)

        return ''.join(result)
```

- Uses a Python list to simulate stack operations.
- Efficient due to constant time `append()` and `pop()` operations.

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    string removeStars(string s) {
        string result;

        for (char ch : s) {
            if (ch == '*') {
                result.pop_back(); // Remove last character
            } else {
                result.push_back(ch); // Add to result
            }
        }

        return result;
    }
};
```

- Leverages C++ STL's `string` operations: `push_back()` and `pop_back()`

---

## ⏱ Complexity Analysis

| Metric           | Value       |
|------------------|-------------|
| Time Complexity  | O(n)        |
| Space Complexity | O(n)        |
| In-Place Modify  | ❌ No, due to use of auxiliary structure |

---

## ⚙️ Stack Simulation Logic

This problem mimics a **stack behavior**, where:
- Letters are **pushed**
- Stars act as **pops**

Using a `StringBuilder` or `List` (Java/Python) or a simple `string` (C++) suffices due to linear time mutation.

---

## 🧠 Pro Tip

Avoid using `replace()` or `regex` tricks. They fail to meet the **O(n)** and **linear processing** requirement due to repeated scans.

---

## 🔍 Edge Cases to Validate

- Only letters: `"abcde"` → output: `"abcde"`
- Only stars with letters: `"a*"` → output: `""`
- Interleaved characters: `"a*b*c*"` → output: `""`
- Long repeated pattern: `"a*b*c*d*e*f*g*h*i*j*k*"` → output: `""`

---

## 📌 Final Verdict

| Area             | Verdict       |
|------------------|---------------|
| Time Efficiency  | ✅ Optimal     |
| Space Usage      | ✅ Acceptable  |
| Clarity          | ✅ Clear logic |
| Constraint Fit   | ✅ Passes all  |

> Recommended approach in production systems involving editor-like or undo-style operations.

