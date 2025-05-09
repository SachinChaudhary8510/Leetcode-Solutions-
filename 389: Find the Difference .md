# 🔍 LeetCode Problem 389: Find the Difference

## 📘 Problem Statement

You are given two strings `s` and `t`, where:
- `t` is generated by **shuffling** `s` and adding **one extra character** at a random position.

Return the **character that was added**.

---

### 🧠 Examples

#### Example 1:
**Input:**  
`s = "abcd"`, `t = "abcde"`  
**Output:** `"e"`

#### Example 2:
**Input:**  
`s = ""`, `t = "y"`  
**Output:** `"y"`

---

### 📚 Constraints

- `0 <= s.length <= 1000`
- `t.length == s.length + 1`
- `s` and `t` consist of only lowercase English letters.

---

## ✅ Java Solution – Frequency Count

```java
class Solution {
    public char findTheDifference(String s, String t) {
        int[] a = new int[26];
        int[] b = new int[26];

        for (int i = 0; i < s.length(); i++) {
            a[s.charAt(i) - 'a']++;
        }
        for (int i = 0; i < t.length(); i++) {
            b[t.charAt(i) - 'a']++;
        }

        for (int i = 0; i < 26; i++) {
            if (a[i] != b[i])
                return (char) (i + 'a');
        }

        return '0'; // Should never reach here if constraints are followed
    }
}
```

### 🧾 Analysis:
- **Time Complexity:** O(n), where n = length of `t`
- **Space Complexity:** O(1), constant auxiliary space (two fixed-size arrays)

---

## 🧠 Optimal Java Solution – Bitwise XOR (O(n), O(1))

```java
class Solution {
    public char findTheDifference(String s, String t) {
        char result = 0;

        for (char c : s.toCharArray()) {
            result ^= c;
        }
        for (char c : t.toCharArray()) {
            result ^= c;
        }

        return result;
    }
}
```

### 💡 Why It Works:
- XOR of a character with itself is 0.
- XOR with 0 returns the character itself.
- All characters cancel out except the one that was added.

---

## 🐍 Python Equivalent (XOR-based)

```python
class Solution:
    def findTheDifference(self, s: str, t: str) -> str:
        res = 0
        for c in s + t:
            res ^= ord(c)
        return chr(res)
```

---

## 🔍 Test Cases

| s       | t        | Output |
|---------|----------|--------|
| "abcd"  | "abcde"  | "e"    |
| ""      | "y"      | "y"    |
| "a"     | "aa"     | "a"    |
| "aeiou" | "uaeioo" | "o"    |

---

## 📌 Final Notes

- ✅ Frequency map approach is readable and intuitive for beginners.
- ✅ XOR-based solution is elegant, optimal, and leverages bit manipulation—a classic technique for interviews.
- ❗ Avoid sorting-based solutions which unnecessarily add O(n log n) overhead.

> This problem is a great example of how clever use of XOR can reduce auxiliary space and increase efficiency.

