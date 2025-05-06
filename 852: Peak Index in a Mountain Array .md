# ⛰️ LeetCode Problem 852: Peak Index in a Mountain Array

## 📘 Problem Statement

You're given an array `arr` that is a **mountain array**:
- Elements first strictly **increase**, then strictly **decrease**.
- You must find and return the **index of the peak** (maximum element).
- The solution **must run in O(log n)** time.

---

### 🧠 Examples

#### Example 1:
**Input:** `arr = [0,1,0]`  
**Output:** `1`

#### Example 2:
**Input:** `arr = [0,2,1,0]`  
**Output:** `1`

#### Example 3:
**Input:** `arr = [0,10,5,2]`  
**Output:** `1`

---

### 📚 Constraints

- `3 <= arr.length <= 10⁵`
- `0 <= arr[i] <= 10⁶`
- `arr` is **guaranteed** to be a mountain array.

---

## 🚫 Java Brute Force Solution (Linear Search)

```java
class Solution {
    public int peakIndexInMountainArray(int[] arr) {
        for (int i = 1; i < arr.length - 1; i++) {
            if (arr[i] >= arr[i + 1])
                return i;
        }
        return -1;
    }
}
```

- ❌ **Time Complexity:** O(n) – not acceptable per problem constraints
- ✅ **Space Complexity:** O(1)
- 🚫 **Fails performance requirements for large inputs**

---

## ✅ Optimal Java Solution – Binary Search (O(log n))

```java
class Solution {
    public int peakIndexInMountainArray(int[] arr) {
        int low = 0, high = arr.length - 1;

        while (low < high) {
            int mid = (low + high) / 2;

            if (arr[mid] < arr[mid + 1]) {
                // Peak is to the right
                low = mid + 1;
            } else {
                // Peak is at mid or to the left
                high = mid;
            }
        }

        return low; // or high – both will be equal
    }
}
```

---

## 🐍 Python Solution

```python
class Solution:
    def peakIndexInMountainArray(self, arr: List[int]) -> int:
        low, high = 0, len(arr) - 1

        while low < high:
            mid = (low + high) // 2
            if arr[mid] < arr[mid + 1]:
                low = mid + 1
            else:
                high = mid

        return low
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    int peakIndexInMountainArray(vector<int>& arr) {
        int low = 0, high = arr.size() - 1;

        while (low < high) {
            int mid = (low + high) / 2;
            if (arr[mid] < arr[mid + 1])
                low = mid + 1;
            else
                high = mid;
        }

        return low;
    }
};
```

---

## 🔍 Complexity Analysis

| Metric           | Value       |
|------------------|-------------|
| Time Complexity  | O(log n)    |
| Space Complexity | O(1)        |

---

## ✅ Test Cases

| arr                | Output |
|--------------------|--------|
| [0,1,0]            | 1      |
| [0,2,1,0]          | 1      |
| [0,10,5,2]         | 1      |
| [3,5,7,9,11,8,4,1] | 4      |
| [1,2,3,4,5,3,1]    | 4      |

---

## 📌 Final Notes

- ❗ The brute force approach is **not compliant** with the required `O(log n)` constraint.
- ✅ Binary search exploits the "valley-peak-valley" structure of a mountain array to converge to the peak efficiently.
- 🧠 Remember: `arr[mid] < arr[mid + 1]` means the peak lies **right**, otherwise **left**.

> In a production codebase, this is a textbook application of binary search over a unimodal array. Linear solutions are a red flag.
