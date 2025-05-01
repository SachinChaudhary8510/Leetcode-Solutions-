# 📏 LeetCode Problem 806: Number of Lines To Write String

## 📘 Problem Statement

You are given a string `s` consisting of lowercase English letters, and an integer array `widths` where `widths[0]` is the pixel width of `'a'`, `widths[1]` is the width of `'b'`, ..., and so on up to `'z'`. You are to simulate writing the characters of `s` on multiple lines, each with a maximum width of 100 pixels. Characters are added sequentially, and once a line exceeds 100 pixels, a new line begins.

### Return:
An integer array `result` where:
- `result[0]` is the number of lines used.
- `result[1]` is the width in pixels of the final line.

---

## 🧪 Examples

### Example 1:
**Input:**  
`widths = [10,10,10,...,10], s = "abcdefghijklmnopqrstuvwxyz"`  
**Output:** `[3, 60]`  
**Explanation:**  
- Line 1: 10 characters (100 pixels)  
- Line 2: 10 characters (100 pixels)  
- Line 3: 6 characters (60 pixels)

---

### Example 2:
**Input:**  
`widths = [4,10,10,...], s = "bbbcccdddaaa"`  
**Output:** `[2, 4]`  
**Explanation:**  
- Line 1: fills up to 98 pixels  
- Line 2: contains just `'a'` (4 pixels)

---

## 📚 Constraints

- `widths.length == 26`
- `2 <= widths[i] <= 10`
- `1 <= s.length <= 1000`
- `s` contains only lowercase English letters

---

## 💻 Java Solution

```java
class Solution {
    public int[] numberOfLines(int[] widths, String s) {
        int[] result = new int[2];
        int sum = 0;

        for (int i = 0; i < s.length(); i++) {
            sum += widths[s.charAt(i) - 97];

            if (sum > 100) {
                result[0]++;
                sum = widths[s.charAt(i) - 97];
            }
        }

        result[1] = sum;
        result[0]++;
        return result;
    }
}
```

---

## ✅ Evaluation of the Submitted Solution

| Metric               | Evaluation                                          |
|----------------------|-----------------------------------------------------|
| **Correctness**       | ✅ Fully accurate with consistent output             |
| **Edge Case Handling**| ✅ Handles near-boundary widths and edge lengths     |
| **Code Clarity**      | ✅ Readable, logically sequenced, and minimal        |
| **Performance**       | ✅ O(n) — optimal for `n <= 1000`                    |
| **Use of Primitives** | ✅ Efficient indexing with `charAt(i) - 'a'`        |

---

## 🧠 Suggested Enhancements (Optional)

- Rename `sum` to `lineWidth` or `currentLineWidth` for improved clarity.
- Add comments to improve code legibility for junior developers.
- Consider using `'a'` instead of hard-coded `97` for better semantic understanding:
  ```java
  sum += widths[s.charAt(i) - 'a'];
  ```

---

## ⏱ Time and Space Complexity

| Metric           | Value  |
|------------------|--------|
| Time Complexity  | O(n)   |
| Space Complexity | O(1)   |

---

## 🧾 Final Verdict

| Category         | Verdict                           |
|------------------|------------------------------------|
| Code Quality      | ✅ Clean, concise, and correct     |
| Algorithm Choice  | ✅ Optimal for constraints         |
| Refactor Needed   | ❌ No refactoring needed           |
| Ready for Prod    | ✅ Yes, production-ready           |

> 📌 Your implementation is optimal and maintainable. It effectively handles edge cases and adheres to time complexity expectations. Solid execution.
