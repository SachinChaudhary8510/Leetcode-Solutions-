
# 🧮 LeetCode Problem 2535 - Difference Between Element Sum and Digit Sum of an Array

**Difficulty**: 🟢 Easy  
**Tags**: Math, Array  
**Problem Source**: [LeetCode #2535](https://leetcode.com/problems/difference-between-element-sum-and-digit-sum-of-an-array/)

---

## 📘 Problem Statement

You are given a **positive integer array** `nums`.

- The **element sum** is the sum of all the elements in `nums`.
- The **digit sum** is the sum of all the digits (not necessarily distinct) that appear in `nums`.

Return the **absolute difference** between the element sum and digit sum of `nums`.

🔔 Note: The absolute difference between two integers `x` and `y` is defined as `|x - y|`.

---

## 🔍 Examples

### Example 1:
```
Input: nums = [1,15,6,3]
Output: 9
Explanation: 
Element sum = 1 + 15 + 6 + 3 = 25
Digit sum = 1 + 1 + 5 + 6 + 3 = 16
|25 - 16| = 9
```

### Example 2:
```
Input: nums = [1,2,3,4]
Output: 0
Explanation:
Element sum = 10, Digit sum = 10
|10 - 10| = 0
```

---

## ✅ Constraints

- `1 <= nums.length <= 2000`
- `1 <= nums[i] <= 2000`

---

## 💡 Java Solution
```java
class Solution {
    public int differenceOfSum(int[] nums) {
        int sum = 0, sumd = 0;
        for (int i : nums) {
            sum += i;
        }
        for (int i : nums) {
            while (i > 0) {
                sumd += i % 10;
                i /= 10;
            }
        }
        return Math.abs(sum - sumd);
    }
}
```

---

## 🐍 Python Solution
```python
class Solution:
    def differenceOfSum(self, nums):
        total = sum(nums)
        digit_total = sum(int(d) for num in nums for d in str(num))
        return abs(total - digit_total)
```

---

## 💻 C++ Solution
```cpp
class Solution {
public:
    int differenceOfSum(vector<int>& nums) {
        int total = 0, digitSum = 0;
        for (int num : nums) {
            total += num;
            while (num > 0) {
                digitSum += num % 10;
                num /= 10;
            }
        }
        return abs(total - digitSum);
    }
};
```

---

## 📁 Project Structure
```
📁 DifferenceElementDigitSum
├── Solution.java
├── solution.py
├── solution.cpp
└── README.md ✅
```

---

## 📬 Contribute

Found a better approach or optimization? Feel free to fork and contribute! 🚀

---

## 🧠 Think Deep. Code Smart. 💻
