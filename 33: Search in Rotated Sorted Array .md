# 🔍 LeetCode Problem 33: Search in Rotated Sorted Array

## 📘 Problem Statement

You are given a **sorted** array `nums` of **distinct integers**, which has been **rotated** at some unknown pivot. Your task is to find an element `target` in the array and return its **index**, or `-1` if not found.

The solution **must run in O(log n)** time.

---

### 🧠 Example

#### Example 1:
**Input:**  
`nums = [4,5,6,7,0,1,2]`, `target = 0`  
**Output:** `4`

#### Example 2:
**Input:**  
`nums = [4,5,6,7,0,1,2]`, `target = 3`  
**Output:** `-1`

#### Example 3:
**Input:**  
`nums = [1]`, `target = 0`  
**Output:** `-1`

---

### 📚 Constraints

- `1 <= nums.length <= 5000`
- `-10⁴ <= nums[i], target <= 10⁴`
- All values in `nums` are **distinct**
- `nums` is sorted and **possibly rotated**

---

## 🚫 Java Brute Force Solution (Not O(log n))

```java
class Solution {
    public int search(int[] nums, int target) {
        if (target < nums[0]) {
            for (int i = 0; i < nums.length; i++) {
                if (nums[nums.length - 1 - i] == target)
                    return nums.length - 1 - i;
            }
        } else {
            for (int i = 0; i < nums.length; i++) {
                if (nums[i] == target)
                    return i;
            }
        }
        return -1;
    }
}
```

- ❌ **Time Complexity:** O(n) – violates the problem's constraint
- ❌ **Space Complexity:** O(1)

---

## ✅ Optimal Java Solution – Binary Search (O(log n))

```java
class Solution {
    public int search(int[] nums, int target) {
        int low = 0, high = nums.length - 1;

        while (low <= high) {
            int mid = (low + high) / 2;

            if (nums[mid] == target) return mid;

            // Left half is sorted
            if (nums[low] <= nums[mid]) {
                if (nums[low] <= target && target < nums[mid]) {
                    high = mid - 1;
                } else {
                    low = mid + 1;
                }
            }
            // Right half is sorted
            else {
                if (nums[mid] < target && target <= nums[high]) {
                    low = mid + 1;
                } else {
                    high = mid - 1;
                }
            }
        }

        return -1;
    }
}
```

---

## 🐍 Python Solution

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        low, high = 0, len(nums) - 1

        while low <= high:
            mid = (low + high) // 2

            if nums[mid] == target:
                return mid

            # Left half is sorted
            if nums[low] <= nums[mid]:
                if nums[low] <= target < nums[mid]:
                    high = mid - 1
                else:
                    low = mid + 1
            # Right half is sorted
            else:
                if nums[mid] < target <= nums[high]:
                    low = mid + 1
                else:
                    high = mid - 1

        return -1
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int low = 0, high = nums.size() - 1;

        while (low <= high) {
            int mid = (low + high) / 2;

            if (nums[mid] == target) return mid;

            // Left half sorted
            if (nums[low] <= nums[mid]) {
                if (nums[low] <= target && target < nums[mid])
                    high = mid - 1;
                else
                    low = mid + 1;
            }
            // Right half sorted
            else {
                if (nums[mid] < target && target <= nums[high])
                    low = mid + 1;
                else
                    high = mid - 1;
            }
        }

        return -1;
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

## 🧪 Test Cases

| nums                          | target | Output |
|-------------------------------|--------|--------|
| [4,5,6,7,0,1,2]               | 0      | 4      |
| [4,5,6,7,0,1,2]               | 3      | -1     |
| [1]                           | 0      | -1     |
| [1,3]                         | 3      | 1      |
| [5,1,3]                       | 5      | 0      |

---

## ✅ Final Assessment

| Criteria         | Verdict         |
|------------------|-----------------|
| Runtime          | ✅ O(log n)     |
| Edge Case Proof  | ✅ Covered      |
| Code Quality     | ✅ Clean        |
| Implementation   | ✅ Optimal      |

> Binary search in rotated arrays is an essential interview pattern. Ignore anything O(n); this is strictly logarithmic territory.
