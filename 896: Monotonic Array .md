# LeetCode 896: Monotonic Array

## Problem Statement

An array is **monotonic** if it is either monotone increasing or monotone decreasing.

- An array `nums` is **monotone increasing** if for all `i <= j`, `nums[i] <= nums[j]`.
- An array `nums` is **monotone decreasing** if for all `i <= j`, `nums[i] >= nums[j]`.

### Task

Given an integer array `nums`, return `true` if the given array is monotonic, or `false` otherwise.

## Examples

### Example 1

**Input:** `nums = [1,2,2,3]`  
**Output:** `true`

### Example 2

**Input:** `nums = [6,5,4,4]`  
**Output:** `true`

### Example 3

**Input:** `nums = [1,3,2]`  
**Output:** `false`

## Constraints

- `1 <= nums.length <= 10^5`
- `-10^5 <= nums[i] <= 10^5`

---

## Java Solution

```java
class Solution {
    public boolean isMonotonic(int[] nums) {
        if (nums[0] < nums[nums.length - 1]) {
            for (int i = 0; i < nums.length - 1; i++) {
                if (nums[i] <= nums[i + 1]) {

                } else
                    return false;
            }
            return true;
        } else {
            for (int i = 0; i < nums.length - 1; i++) {
                if (nums[i] >= nums[i + 1]) {

                } else
                    return false;
            }
            return true;
        }
    }
}
```

### Time Complexity

- **O(n)** – Traverses the list once.
- **Space Complexity:** O(1) – Constant space.

---

## Python Solution

```python
class Solution:
    def isMonotonic(self, nums: list[int]) -> bool:
        increasing = decreasing = True
        for i in range(1, len(nums)):
            if nums[i] > nums[i - 1]:
                decreasing = False
            elif nums[i] < nums[i - 1]:
                increasing = False
        return increasing or decreasing
```

### Time Complexity

- **O(n)** – Single pass.
- **Space Complexity:** O(1)

---

## C++ Solution

```cpp
class Solution {
public:
    bool isMonotonic(vector<int>& nums) {
        bool increasing = true, decreasing = true;
        for (int i = 1; i < nums.size(); ++i) {
            if (nums[i] > nums[i - 1]) decreasing = false;
            if (nums[i] < nums[i - 1]) increasing = false;
        }
        return increasing || decreasing;
    }
};
```

### Time Complexity

- **O(n)** – Linear traversal.
- **Space Complexity:** O(1)

---

## Summary

This problem is a classic array traversal challenge, often used to assess understanding of array properties, control flow, and edge case handling. The optimal solutions in Java, Python, and C++ all maintain linear time and constant space complexity. A must-have problem in your GitHub LeetCode arsenal.
