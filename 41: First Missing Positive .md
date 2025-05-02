# 🚨 LeetCode Problem 41: First Missing Positive

## 📘 Problem Statement

Given an unsorted integer array `nums`, return the smallest **positive** integer that **does not appear** in the array.

You must implement an algorithm that runs in **O(n)** time and uses **O(1)** auxiliary space.

---

## 🧪 Examples

### Example 1:
**Input:** `nums = [1,2,0]`  
**Output:** `3`  
**Explanation:** The numbers [1, 2] are present. Smallest missing = 3.

---

### Example 2:
**Input:** `nums = [3,4,-1,1]`  
**Output:** `2`  
**Explanation:** 1 is present, 2 is not.

---

### Example 3:
**Input:** `nums = [7,8,9,11,12]`  
**Output:** `1`  
**Explanation:** 1 is the smallest positive missing.

---

## 📚 Constraints

- `1 <= nums.length <= 10⁵`
- `-2³¹ <= nums[i] <= 2³¹ - 1`

---

## ⚠️ Requirements

- Time Complexity: **O(n)**
- Space Complexity: **O(1)** (ignore input/output space)

---

## ✅ Java (Optimal) Solution

```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        int n = nums.length;

        // Step 1: Place each number in its correct position
        for (int i = 0; i < n; i++) {
            while (
                nums[i] > 0 &&
                nums[i] <= n &&
                nums[nums[i] - 1] != nums[i]
            ) {
                int correctIndex = nums[i] - 1;
                int temp = nums[i];
                nums[i] = nums[correctIndex];
                nums[correctIndex] = temp;
            }
        }

        // Step 2: Identify first missing index
        for (int i = 0; i < n; i++) {
            if (nums[i] != i + 1)
                return i + 1;
        }

        return n + 1;
    }
}
```

---

## 🐍 Python Solution

```python
class Solution:
    def firstMissingPositive(self, nums):
        n = len(nums)

        for i in range(n):
            while 1 <= nums[i] <= n and nums[nums[i] - 1] != nums[i]:
                correct_idx = nums[i] - 1
                nums[i], nums[correct_idx] = nums[correct_idx], nums[i]

        for i in range(n):
            if nums[i] != i + 1:
                return i + 1

        return n + 1
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        int n = nums.size();

        for (int i = 0; i < n; i++) {
            while (
                nums[i] > 0 &&
                nums[i] <= n &&
                nums[nums[i] - 1] != nums[i]
            ) {
                swap(nums[i], nums[nums[i] - 1]);
            }
        }

        for (int i = 0; i < n; i++) {
            if (nums[i] != i + 1)
                return i + 1;
        }

        return n + 1;
    }
};
```

---

## ⏱ Complexity Analysis

| Metric           | Value       |
|------------------|-------------|
| Time Complexity  | O(n)        |
| Space Complexity | O(1)        |
| Sorting-Based    | ❌ Not allowed per constraints |

---

## 🔍 Common Mistakes

| Mistake                                      | Why It Fails                                      |
|---------------------------------------------|---------------------------------------------------|
| Using `Arrays.sort()` or built-in sort      | Violates **O(n)** constraint                      |
| Using extra hashsets or arrays              | Violates **O(1)** space constraint                |
| Ignoring values out of `[1, n]` range       | Needed to maintain constant time and space       |

---

## 📌 Final Verdict

| Area             | Verdict       |
|------------------|---------------|
| Performance      | ✅ Optimal     |
| Memory Usage     | ✅ Constant    |
| Production Ready | ✅ Yes         |
| Edge Cases       | ✅ Fully covered |

> ✅ Recommended approach for real-time systems and memory-constrained environments.

---

### 📦 Bonus

Your original Java solution:

```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        int num = 1;
        Arrays.sort(nums);
        for(int i = 0; i < nums.length; i++){
            if(nums[i] < num)
                continue;
            else if(nums[i] == num)
                num++;
            else
                break;
        }
        return num;
    }
}
```

🔴 **Status: Fails constraint**  
- **Time Complexity**: O(n log n) — due to sorting  
- **Space Complexity**: O(1) — acceptable  
✅ Valid if constraint on time is ignored.

