
# 📊 LeetCode Problem 2176: Count Equal and Divisible Pairs in an Array

## 📘 Problem Statement

Given a **0-indexed** integer array `nums` of length `n` and an integer `k`, return the number of pairs `(i, j)` where `0 <= i < j < n`, such that `nums[i] == nums[j]` and `(i * j)` is divisible by `k`.

---

## 🔍 Examples

### Example 1:

**Input:**  
nums = [3,1,2,2,2,1,3], k = 2  
**Output:** 4  
**Explanation:**  
There are 4 pairs that meet all the requirements:
- nums[0] == nums[6], and 0 * 6 == 0, which is divisible by 2.
- nums[2] == nums[3], and 2 * 3 == 6, which is divisible by 2.
- nums[2] == nums[4], and 2 * 4 == 8, which is divisible by 2.
- nums[3] == nums[4], and 3 * 4 == 12, which is divisible by 2.

---

### Example 2:

**Input:**  
nums = [1,2,3,4], k = 1  
**Output:** 0  
**Explanation:**  
Since no value in `nums` is repeated, there are no pairs `(i,j)` that meet all the requirements.

---

## 🔒 Constraints

- 1 <= nums.length <= 100  
- 1 <= nums[i], k <= 100

---

## 💻 Java Solution

```java
class Solution {
    public int countPairs(int[] nums, int k) {
        int count = 0;
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] == nums[j] && (i * j) % k == 0) {
                    count++;
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
    def countPairs(self, nums: List[int], k: int) -> int:
        count = 0
        for i in range(len(nums)):
            for j in range(i + 1, len(nums)):
                if nums[i] == nums[j] and (i * j) % k == 0:
                    count += 1
        return count
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    int countPairs(vector<int>& nums, int k) {
        int count = 0;
        for (int i = 0; i < nums.size(); ++i) {
            for (int j = i + 1; j < nums.size(); ++j) {
                if (nums[i] == nums[j] && (i * j) % k == 0) {
                    count++;
                }
            }
        }
        return count;
    }
};
```

---

## ⏱️ Time and Space Complexity

- **Time Complexity:** O(n²) — brute-force pairwise comparison.
- **Space Complexity:** O(1)

---

## 🌟 Summary

This problem focuses on **pair counting**, **value equality**, and **index-based arithmetic** checks. A brute-force solution is acceptable within the given constraints.
