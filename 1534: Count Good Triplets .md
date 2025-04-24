# 🚀 LeetCode Problem 1534: Count Good Triplets

## 📘 Problem Statement
Given an array of integers `arr`, and three integers `a`, `b`, and `c`, return the number of **good triplets**.

A triplet `(arr[i], arr[j], arr[k])` is **good** if the following conditions are true:

- `0 <= i < j < k < arr.length`
- `|arr[i] - arr[j]| <= a`
- `|arr[j] - arr[k]| <= b`
- `|arr[i] - arr[k]| <= c`

Where `|x|` denotes the absolute value of `x`.

---

## 🔍 Examples

### Example 1:
**Input:**  
`arr = [3,0,1,1,9,7], a = 7, b = 2, c = 3`  
**Output:**  
`4`  
**Explanation:**  
There are 4 good triplets: `(3,0,1)`, `(3,0,1)`, `(3,1,1)`, `(0,1,1)`.

---

### Example 2:
**Input:**  
`arr = [1,1,2,2,3], a = 0, b = 0, c = 1`  
**Output:**  
`0`  
**Explanation:**  
No triplet satisfies all conditions.

---

## 🔒 Constraints
- `3 <= arr.length <= 100`
- `0 <= arr[i] <= 1000`
- `0 <= a, b, c <= 1000`

---

## 💻 Java Solution
```java
class Solution {
    public int countGoodTriplets(int[] arr, int a, int b, int c) {
        int count = 0;
        for (int i = 0; i < arr.length; i++) {
            for (int j = i + 1; j < arr.length; j++) {
                for (int k = j + 1; k < arr.length; k++) {
                    if (Math.abs(arr[i] - arr[j]) <= a &&
                        Math.abs(arr[j] - arr[k]) <= b &&
                        Math.abs(arr[i] - arr[k]) <= c) {
                        count++;
                    }
                }
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
    def countGoodTriplets(self, arr: List[int], a: int, b: int, c: int) -> int:
        count = 0
        n = len(arr)
        for i in range(n):
            for j in range(i + 1, n):
                for k in range(j + 1, n):
                    if abs(arr[i] - arr[j]) <= a and \
                       abs(arr[j] - arr[k]) <= b and \
                       abs(arr[i] - arr[k]) <= c:
                        count += 1
        return count
```

---

## 💠 C++ Solution
```cpp
class Solution {
public:
    int countGoodTriplets(vector<int>& arr, int a, int b, int c) {
        int count = 0;
        int n = arr.size();
        for (int i = 0; i < n; ++i) {
            for (int j = i + 1; j < n; ++j) {
                for (int k = j + 1; k < n; ++k) {
                    if (abs(arr[i] - arr[j]) <= a &&
                        abs(arr[j] - arr[k]) <= b &&
                        abs(arr[i] - arr[k]) <= c) {
                        count++;
                    }
                }
            }
        }
        return count;
    }
};
```

---

## ⏱️ Time and Space Complexity
- **Time Complexity:** O(n³)
- **Space Complexity:** O(1)

---

## 🌟 Summary
This problem is a brute-force search exercise. Given the small constraint on array length, a triple-nested loop is acceptable. However, it's an excellent opportunity to recognize early exits or avoid redundant checks in performance-critical applications.
