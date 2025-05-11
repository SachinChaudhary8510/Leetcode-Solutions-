# 🔍 LeetCode Problem 3146: Permutation Difference Between Two Strings

## 📘 Problem Statement

You are given two strings `s` and `t` such that:
- Each character appears **at most once** in `s`.
- `t` is a **permutation** of `s`.

The **permutation difference** between `s` and `t` is defined as the **sum of the absolute differences** between the index of each character in `s` and its corresponding index in `t`.

Return the **permutation difference** between `s` and `t`.

---

### 🧠 Examples

#### Example 1:
**Input:**  
`s = "abc"`  
`t = "bac"`  
**Output:** `2`  
**Explanation:**  
- |index('a' in s) - index('a' in t)| = |0 - 1| = 1  
- |index('b' in s) - index('b' in t)| = |1 - 0| = 1  
- |index('c' in s) - index('c' in t)| = |2 - 2| = 0  
- Total = 1 + 1 + 0 = **2**

#### Example 2:
**Input:**  
`s = "abcde"`  
`t = "edbac"`  
**Output:** `12`  
**Explanation:**  
- |0 - 3| + |1 - 2| + |2 - 4| + |3 - 1| + |4 - 0| = **12**

---

### 📚 Constraints

- `1 <= s.length <= 26`
- Each character occurs **at most once** in `s`
- `t` is a **permutation** of `s`
- Both strings consist of lowercase English letters

---

## ✅ Java Solution – Index Mapping via ASCII

```java
class Solution {
    public int findPermutationDifference(String s, String t) {
        int[] s1 = new int[26];
        int[] s2 = new int[26];
        
        for (int i = 0; i < s.length(); i++) {
            s1[s.charAt(i) - 97] = i;
            s2[t.charAt(i) - 97] = i;
        }
        
        int result = 0;
        for (int i = 0; i < 26; i++) {
            result += Math.abs(s1[i] - s2[i]);
        }
        
        return result;
    }
}
```

---

### 🧾 Analysis

| Metric               | Value        |
|----------------------|-------------|
| **Time Complexity**  | O(n)        |
| **Space Complexity** | O(1) (fixed 26-size arrays) |
| **Approach**         | Indexed difference summation via ASCII mapping |

---

### ✅ Key Observations

- Since `s.length <= 26` and has unique characters, we can use **fixed-size arrays** for character-to-index mapping.
- ASCII math (`char - 'a'`) allows constant-time index lookups.
- Efficiently handles the comparison in **linear time** with **constant space overhead**.

---

## 🧪 Test Cases

| s       | t       | Output | Reason                                                |
|---------|---------|--------|-------------------------------------------------------|
| "abc"   | "bac"   | 2      | 1 + 1 + 0                                              |
| "abcde" | "edbac" | 12     | 0↔3, 1↔2, 2↔4, 3↔1, 4↔0                                |
| "a"     | "a"     | 0      | Same index                                            |
| "ab"    | "ba"    | 2      | 0↔1, 1↔0 => 1 + 1                                     |
| "xyz"   | "zyx"   | 4      | |0-2| + |1-1| + |2-0| = 2 + 0 + 2                      |

---

## 📌 Conclusion

This problem is a textbook case of character-index mapping using fixed-size structures for optimal performance. The crux lies in recognizing the one-to-one character-to-index correspondence, then leveraging that to compute a direct and efficient diff.

> The solution is tight, performant, and scale-safe due to the character bounds. No need for over-engineered data structures—just raw, indexed logic.

