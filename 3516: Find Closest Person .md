# 🚀 LeetCode Problem 3516: Find Closest Person

## 📘 Problem Statement
You are given three integers `x`, `y`, and `z`, representing the positions of three people on a number line:

- `x` is the position of Person 1.
- `y` is the position of Person 2.
- `z` is the position of Person 3, who does not move.

Both Person 1 and Person 2 move toward Person 3 at the same speed.

Determine which person reaches Person 3 first:

- Return `1` if Person 1 arrives first.
- Return `2` if Person 2 arrives first.
- Return `0` if both arrive at the same time.

---

## 🔍 Examples

### Example 1:
**Input:**  
`x = 2, y = 7, z = 4`  
**Output:**  
`1`  
**Explanation:**  
Person 1 is at position 2 and reaches position 4 in 2 steps.  
Person 2 is at position 7 and reaches position 4 in 3 steps.  
Person 1 arrives first.

---

### Example 2:
**Input:**  
`x = 2, y = 5, z = 6`  
**Output:**  
`2`  
**Explanation:**  
Person 1 takes 4 steps to reach position 6.  
Person 2 takes only 1 step.  
Person 2 arrives first.

---

### Example 3:
**Input:**  
`x = 1, y = 5, z = 3`  
**Output:**  
`0`  
**Explanation:**  
Both persons reach the position 3 in exactly 2 steps.

---

## 🔒 Constraints
- `1 <= x, y, z <= 100`

---

## 💻 Java Solution
```java
class Solution {
    public int findClosest(int x, int y, int z) {
        if (Math.abs(z - y) > Math.abs(z - x))
            return 1;
        else if (Math.abs(z - y) < Math.abs(z - x))
            return 2;
        else
            return 0;
    }
}
```

---

## 🐍 Python Solution
```python
class Solution:
    def findClosest(self, x: int, y: int, z: int) -> int:
        dist1 = abs(z - x)
        dist2 = abs(z - y)
        if dist1 < dist2:
            return 1
        elif dist2 < dist1:
            return 2
        else:
            return 0
```

---

## 💠 C++ Solution
```cpp
class Solution {
public:
    int findClosest(int x, int y, int z) {
        int dist1 = abs(z - x);
        int dist2 = abs(z - y);
        if (dist1 < dist2) return 1;
        else if (dist2 < dist1) return 2;
        else return 0;
    }
};
```

---

## ⏱️ Time and Space Complexity
- **Time Complexity:** O(1)
- **Space Complexity:** O(1)

---

## 🌟 Summary
This is a direct math-based problem involving absolute difference. It’s a typical comparison problem designed to test clarity in conditional handling and edge symmetry between two variables.
