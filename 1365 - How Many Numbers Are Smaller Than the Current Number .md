# 📊 LeetCode 1365 - How Many Numbers Are Smaller Than the Current Number

## 🧠 Problem Statement

Given the array `nums`, for each `nums[i]`, find out **how many numbers in the array are smaller than it**.

That is, for each `nums[i]`, you have to count the number of valid `j`'s such that `j != i` and `nums[j] < nums[i]`.

🔁 Return the result in an array.

---

## 🧪 Examples

### ✅ Example 1:
**Input:**  
`nums = [8,1,2,2,3]`  
**Output:**  
`[4,0,1,1,3]`  

### ✅ Example 2:
**Input:**  
`nums = [6,5,4,8]`  
**Output:**  
`[2,1,0,3]`  

### ✅ Example 3:
**Input:**  
`nums = [7,7,7,7]`  
**Output:**  
`[0,0,0,0]`  

---

## 📚 Constraints

- `2 <= nums.length <= 500`
- `0 <= nums[i] <= 100`

---

## 💻 Java Solution
```java
class Solution {
    public int[] smallerNumbersThanCurrent(int[] nums) {
        int[] ans = new int[nums.length];
        for(int i = 0; i < nums.length ; i++){
            int count = 0;
            for(int j = 0; j < nums.length ; j++){
                if(nums[j] < nums[i]){
                    count++;
                }
                ans[i] = count;
            }
        }
        return ans;
    }
}
```

---

## 🐍 Python Solution
```python
class Solution:
    def smallerNumbersThanCurrent(self, nums):
        return [sum(j < i for j in nums) for i in nums]
```

---

## 💻 C++ Solution
```cpp
class Solution {
public:
    vector<int> smallerNumbersThanCurrent(vector<int>& nums) {
        vector<int> ans;
        for (int i = 0; i < nums.size(); ++i) {
            int count = 0;
            for (int j = 0; j < nums.size(); ++j) {
                if (nums[j] < nums[i]) count++;
            }
            ans.push_back(count);
        }
        return ans;
    }
};
```

---

## ⏱️ Time & Space Complexity

| Approach | Time Complexity | Space Complexity |
|----------|------------------|------------------|
| Brute Force | O(n²) | O(n) |

---

## 🔥 Pro Tip

This is a **brute force approach** suitable for small input sizes. For large-scale applications, consider **prefix sums or sorting with hashing** to optimize performance.

---

> 📘 Add this problem to your GitHub LeetCode repo! Star ⭐ if helpful!
