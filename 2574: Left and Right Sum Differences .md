# ➗ **LeetCode 2574: Left and Right Sum Differences**
> **Difficulty:** Easy  
> **Topic:** Prefix Sum, Arrays  
> **Tag:** Absolute Difference, Array Manipulation  

---

## 📘 Problem Statement

You are given a `0-indexed` integer array `nums` of size `n`.

Define two arrays:

- `leftSum[i]` is the **sum of elements to the left** of index `i` in the array `nums`. If no such element, `leftSum[i] = 0`.
- `rightSum[i]` is the **sum of elements to the right** of index `i` in the array `nums`. If no such element, `rightSum[i] = 0`.

Your task is to **return an integer array `answer` of size `n`** where:  
`answer[i] = |leftSum[i] - rightSum[i]|`

---

## 💡 Examples

### ✅ Example 1
**Input:** `nums = [10,4,8,3]`  
**Output:** `[15,1,11,22]`

**Explanation:**  
- `leftSum = [0, 10, 14, 22]`  
- `rightSum = [15, 11, 3, 0]`  
- `answer = [|0-15|, |10-11|, |14-3|, |22-0|] = [15,1,11,22]`

---

### ✅ Example 2
**Input:** `nums = [1]`  
**Output:** `[0]`  
**Explanation:** No elements to left or right → Both sums are `0` → `|0 - 0| = 0`

---

## 📏 Constraints

- `1 <= nums.length <= 1000`  
- `1 <= nums[i] <= 10^5`  

---

## ☕ Java Solution

```java
class Solution {
    public int[] leftRightDifference(int[] nums) {
        int[] a = new int[nums.length];
        int[] b = new int[nums.length];
        int leftsum = 0, rightsum = 0;
        for (int i = 0; i < nums.length - 1; i++) {
            leftsum += nums[i];
            a[i + 1] = leftsum;
            rightsum += nums[nums.length - i - 1];
            b[nums.length - 2 - i] = rightsum;
        }
        int[] ans = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            ans[i] = Math.abs(a[i] - b[i]);
        }
        return ans;
    }
}
```

**🕒 Time Complexity:** `O(n)`  
**📦 Space Complexity:** `O(n)`  

---

## 🐍 Python Solution

```python
class Solution:
    def leftRightDifference(self, nums: list[int]) -> list[int]:
        n = len(nums)
        left_sum = [0] * n
        right_sum = [0] * n

        for i in range(1, n):
            left_sum[i] = left_sum[i - 1] + nums[i - 1]

        for i in range(n - 2, -1, -1):
            right_sum[i] = right_sum[i + 1] + nums[i + 1]

        return [abs(left_sum[i] - right_sum[i]) for i in range(n)]
```

**🕒 Time Complexity:** `O(n)`  
**📦 Space Complexity:** `O(n)`

---

## 💻 C++ Solution

```cpp
class Solution {
public:
    vector<int> leftRightDifference(vector<int>& nums) {
        int n = nums.size();
        vector<int> left(n, 0), right(n, 0), answer(n);
        
        for (int i = 1; i < n; i++) {
            left[i] = left[i - 1] + nums[i - 1];
        }
        for (int i = n - 2; i >= 0; i--) {
            right[i] = right[i + 1] + nums[i + 1];
        }
        for (int i = 0; i < n; i++) {
            answer[i] = abs(left[i] - right[i]);
        }
        return answer;
    }
};
```

**🕒 Time Complexity:** `O(n)`  
**📦 Space Complexity:** `O(n)`

---

## 🚀 Takeaway

- 📚 Useful for mastering prefix and suffix sum patterns.
- 🔍 Teaches space optimization and how to keep track of sub-array totals.
- 💪 Foundation for more advanced dynamic programming problems.

---

✅ Ideal for coding portfolios to demonstrate algorithmic thinking & clean logic!
