# 🚀 LeetCode Problem 3289: The Two Sneaky Numbers of Digitville

## 📘 Problem Statement
In the town of Digitville:
- You are given an array `nums` containing integers from `0` to `n - 1`.
- **Each number should appear exactly once**, but two numbers have appeared **twice**.
- As the town detective, your mission is to find these two sneaky numbers.

Return an array of size **two** containing the two repeated numbers **in any order**.

---

## 🔍 Examples

### Example 1:
**Input:**  
`nums = [0,1,1,0]`  

**Output:**  
`[0,1]`  

**Explanation:**  
The numbers `0` and `1` both appear twice.

---

### Example 2:
**Input:**  
`nums = [0,3,2,1,3,2]`  

**Output:**  
`[2,3]`  

**Explanation:**  
The numbers `2` and `3` both appear twice.

---

### Example 3:
**Input:**  
`nums = [7,1,5,4,3,4,6,0,9,5,8,2]`  

**Output:**  
`[4,5]`  

**Explanation:**  
The numbers `4` and `5` both appear twice.

---

## 🔒 Constraints
- `2 <= n <= 100`
- `nums.length == n + 2`
- `0 <= nums[i] < n`
- The input is **guaranteed** to contain exactly two repeated numbers.

---

## 💻 Java Solution
```java
class Solution {
    public int[] getSneakyNumbers(int[] nums) {
        int[] result = new int[2];
        int k = 0;
        for(int i = 0; i < nums.length; i++) {
            int count = 0;
            for(int j = i + 1; j < nums.length; j++) {
                if(nums[i] == nums[j]) {
                    count++;
                    break;
                }
            }
            if(count == 1) {
                result[k] = nums[i];
                k++;
                if(k == 2)
                    break;
            }
        }
        return result;
    }
}
```

---

## 🐍 Python Solution
```python
class Solution:
    def getSneakyNumbers(self, nums: List[int]) -> List[int]:
        seen = set()
        result = []
        for num in nums:
            if num in seen:
                result.append(num)
                if len(result) == 2:
                    break
            else:
                seen.add(num)
        return result
```

---

## 💠 C++ Solution
```cpp
class Solution {
public:
    vector<int> getSneakyNumbers(vector<int>& nums) {
        unordered_set<int> seen;
        vector<int> result;
        for (int num : nums) {
            if (seen.count(num)) {
                result.push_back(num);
                if (result.size() == 2) break;
            } else {
                seen.insert(num);
            }
        }
        return result;
    }
};
```

---

## ⏱️ Time and Space Complexity
- **Time Complexity:** O(N²) in the Java solution (brute-force nested loops).
- **Optimized Solutions (Python/C++):** O(N) using `HashSet`.
- **Space Complexity:** 
  - O(1) for Java solution (no extra structures except result array).
  - O(N) for optimized solutions (because of `HashSet`).

---

## 🌟 Summary
Let's be blunt — **nested loops are inefficient and outdated** for problems like this.  
Savvy interviewers expect you to **leverage hashing** for O(N) performance.  
In real-world systems, inefficiencies scale like wildfire — **brute force is simply not scalable.**

If you want to *actually* impress your technical panel, **always think: "HashMap? HashSet? Bit Manipulation?"** when duplicate detection comes up. 🧠💥
