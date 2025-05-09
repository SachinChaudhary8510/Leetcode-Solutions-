# 🔤 LeetCode Problem 2053: Kth Distinct String in an Array

## 📘 Problem Statement

A **distinct string** is one that appears exactly once in a given string array.

Given:
- an array of strings `arr`
- an integer `k`

Return the **kth distinct string** in the order of appearance.  
If fewer than `k` distinct strings exist, return an empty string `""`.

---

### 🧠 Examples

#### Example 1:
**Input:** `arr = ["d","b","c","b","c","a"], k = 2`  
**Output:** `"a"`  
**Explanation:** The distinct strings are `"d"` and `"a"`, in order. `"a"` is the 2nd.

#### Example 2:
**Input:** `arr = ["aaa","aa","a"], k = 1`  
**Output:** `"aaa"`  
**Explanation:** All strings are distinct, return the 1st.

#### Example 3:
**Input:** `arr = ["a","b","a"], k = 3`  
**Output:** `""`  
**Explanation:** Only one distinct string `"b"` exists. Return empty string since k=3.

---

### 📚 Constraints

- `1 <= k <= arr.length <= 1000`
- `1 <= arr[i].length <= 5`
- `arr[i]` contains only lowercase English letters

---

## ✅ Java Solution – Brute-force Counting (Nested Loops)

```java
class Solution {
    public String kthDistinct(String[] arr, int k) {
        for (String a : arr) {
            int count = 0;
            for (String b : arr) {
                if (a.equals(b)) {
                    count++;
                    if (count == 2) break; // optimization to skip unnecessary checks
                }
            }
            if (count == 1) {
                k--;
                if (k == 0)
                    return a;
            }
        }
        return "";
    }
}
```

---

### 🧾 Analysis

- **Time Complexity:** O(n²), due to nested traversal to count occurrences.
- **Space Complexity:** O(1), no additional data structures used.

---

## 🚀 Optimized Java Approach (Using HashMap)

```java
class Solution {
    public String kthDistinct(String[] arr, int k) {
        Map<String, Integer> freq = new HashMap<>();
        for (String str : arr) {
            freq.put(str, freq.getOrDefault(str, 0) + 1);
        }
        for (String str : arr) {
            if (freq.get(str) == 1) {
                k--;
                if (k == 0)
                    return str;
            }
        }
        return "";
    }
}
```

### ✅ Benefits:
- **Time Complexity:** O(n)
- **Space Complexity:** O(n)
- Much more efficient for large input sizes.

---

## 🧪 Test Cases

| Input                             | k  | Output | Explanation                                  |
|----------------------------------|----|--------|----------------------------------------------|
| `["d","b","c","b","c","a"]`       | 2  | `"a"`  | `"d"` is 1st, `"a"` is 2nd distinct           |
| `["aaa","aa","a"]`                | 1  | `"aaa"`| All strings are distinct, return first       |
| `["a","b","a"]`                   | 3  | `""`   | Only `"b"` is distinct; k=3 is invalid        |
| `["a","b","c","d","a","b","e"]`   | 3  | `"e"`  | `"c"`, `"d"`, and `"e"` are distinct          |

---

## 📌 Conclusion

- The brute-force approach is readable and intuitive for interviews.
- For production or large datasets, favor the HashMap-based solution for better performance.
- Key insight: Track frequency first, then maintain **input order** for selection.

> This problem emphasizes the balance between **accuracy of frequency count** and **preservation of order**, a common theme in interview-style questions.

