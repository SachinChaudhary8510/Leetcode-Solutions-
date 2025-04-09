# 🟢 LeetCode 1480: Running Sum of 1D Array

## 📌 Problem Statement
Given an array `nums`, we define a running sum of an array as `runningSum[i] = sum(nums[0]…nums[i])`. 

Return the running sum of `nums`.

### 🔹 Example 1:
**Input:**  
`nums = [1, 2, 3, 4]`  
**Output:**  
`[1, 3, 6, 10]`  
**Explanation:**  
Running sum is obtained as follows: `[1, 1+2, 1+2+3, 1+2+3+4]`

### 🔹 Example 2:
**Input:**  
`nums = [1, 1, 1, 1, 1]`  
**Output:**  
`[1, 2, 3, 4, 5]`  
**Explanation:**  
Running sum is obtained as follows: `[1, 1+1, 1+1+1, 1+1+1+1, 1+1+1+1+1]`

### 🔹 Example 3:
**Input:**  
`nums = [3, 1, 2, 10, 1]`  
**Output:**  
`[3, 4, 6, 16, 17]`

---

## 🚀 Constraints:
- `1 <= nums.length <= 1000`  
- `-10^6 <= nums[i] <= 10^6`

---

## ✅ Java Solution
```java
class Solution {
    public int[] runningSum(int[] nums) {
        int sum = 0;
        int[] a = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            sum += nums[i];
            a[i] = sum;
        }
        return a;
    }
}
```
**📝 Explanation:**  
- Use a loop to maintain a running sum and store each step in the result array.
- **Time Complexity:** `O(n)` where `n` is the length of the input array.
- **Space Complexity:** `O(n)` due to the extra array used for the result.

---

## ✅ Python Solution
```python
class Solution:
    def runningSum(self, nums: list[int]) -> list[int]:
        sum = 0
        result = []
        for num in nums:
            sum += num
            result.append(sum)
        return result
```
**📝 Explanation:**  
- A simple loop adds each number to a running total and appends it to the result list.
- **Time Complexity:** `O(n)` where `n` is the length of the input list.
- **Space Complexity:** `O(n)` for the result list.

---

## ✅ C++ Solution
```cpp
class Solution {
public:
    vector<int> runningSum(vector<int>& nums) {
        int sum = 0;
        vector<int> result;
        for (int num : nums) {
            sum += num;
            result.push_back(sum);
        }
        return result;
    }
};
```
**📝 Explanation:**  
- Uses a vector to accumulate the sum and return the result.
- **Time Complexity:** `O(n)` where `n` is the length of the input vector.
- **Space Complexity:** `O(n)` for the result vector.

---

## 🏆 Summary

| Language     | Time Complexity | Space Complexity | Approach |
|--------------|-----------------|------------------|----------|
| Java         | O(n)            | O(n)             | Iterative, accumulating sum |
| Python       | O(n)            | O(n)             | Iterative, accumulating sum |
| C++          | O(n)            | O(n)             | Iterative, accumulating sum |

🧠 **Key Insight:** Simple iterative accumulation of sum and storage of results is an optimal solution.

---

🚀 **Happy Coding!**  
📝 **Contributions Welcome!** Feel free to submit improvements or alternatives.
