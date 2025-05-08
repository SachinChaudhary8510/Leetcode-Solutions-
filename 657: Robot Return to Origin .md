# 🤖 LeetCode Problem 657: Robot Return to Origin

## 📘 Problem Statement

There is a robot starting at the origin point (0, 0) on a 2D plane.  
Given a string `moves`, where each character represents a step (`'U'`, `'D'`, `'L'`, `'R'`), determine whether the robot returns to the origin after completing all moves.

- `'U'` = move one unit up (y + 1)
- `'D'` = move one unit down (y - 1)
- `'L'` = move one unit left (x - 1)
- `'R'` = move one unit right (x + 1)

---

### 🧠 Examples

#### Example 1:
**Input:** `moves = "UD"`  
**Output:** `true`  
**Explanation:** The robot moves up and down, ending up at (0,0).

#### Example 2:
**Input:** `moves = "LL"`  
**Output:** `false`  
**Explanation:** The robot ends at (-2,0), not the origin.

---

### 📚 Constraints

- `1 <= moves.length <= 2 * 10⁴`
- `moves` only contains characters `'U'`, `'D'`, `'L'`, `'R'`

---

## ✅ Java Solution – Coordinate Count Approach

```java
class Solution {
    public boolean judgeCircle(String moves) {
        int x_axis = 0;
        int y_axis = 0;
        for (int i = 0; i < moves.length(); i++) {
            if (moves.charAt(i) == 'U') y_axis++;
            else if (moves.charAt(i) == 'D') y_axis--;
            else if (moves.charAt(i) == 'L') x_axis--;
            else x_axis++;
        }
        return x_axis == 0 && y_axis == 0;
    }
}
```

---

### 🧾 Analysis

- **Time Complexity:** O(n), where n = length of `moves`
- **Space Complexity:** O(1), only two counters for x and y axes

---

## 🧠 Alternative Java Solution – Frequency Count (using HashMap)

```java
class Solution {
    public boolean judgeCircle(String moves) {
        int[] freq = new int[128]; // ASCII characters
        for (char c : moves.toCharArray()) {
            freq[c]++;
        }
        return freq['U'] == freq['D'] && freq['L'] == freq['R'];
    }
}
```

### ✅ Benefit:
- Shorter, more concise, especially if used with ASCII assumption.

---

## 🧪 Test Cases

| Input     | Output | Explanation                     |
|-----------|--------|---------------------------------|
| "UD"      | true   | Returns to origin               |
| "LL"      | false  | Ends at (-2, 0)                 |
| "UDLR"    | true   | Balanced movements              |
| "RRDDLU"  | false  | Unbalanced move on Y-axis       |
| "UDUDLR"  | true   | Full cycle returns to origin    |

---

## 📌 Final Notes

- This is a classic simulation problem.
- Clean integer tracking avoids overengineering.
- For high-performance systems, prefer array-based tracking over maps.

> A solid foundational problem to assess direction tracking, state modeling, and simple iteration logic.

