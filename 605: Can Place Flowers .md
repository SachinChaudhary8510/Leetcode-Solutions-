# 🌼 LeetCode Problem 605: Can Place Flowers

## 📘 Problem Statement
You are given:
- An integer array `flowerbed` consisting of 0s (empty plots) and 1s (already planted plots).
- An integer `n` representing the number of flowers you need to plant.

**Rules:**
- You **cannot** plant flowers in adjacent plots.
- Return `true` if you can plant `n` flowers without violating the rule, else return `false`.

---

## 🔍 Examples

### Example 1:
**Input:**  
`flowerbed = [1,0,0,0,1]`, `n = 1`  

**Output:**  
`true`

**Explanation:**  
You can plant one flower at index 2.

---

### Example 2:
**Input:**  
`flowerbed = [1,0,0,0,1]`, `n = 2`  

**Output:**  
`false`

**Explanation:**  
You cannot plant two flowers without breaking the no-adjacent rule.

---

## 🔒 Constraints
- `1 <= flowerbed.length <= 2 × 10^4`
- `flowerbed[i]` is either `0` or `1`
- No two adjacent plots are initially planted.
- `0 <= n <= flowerbed.length`

---

## 💻 Java Solution
```java
class Solution {
    public boolean canPlaceFlowers(int[] flowerBed, int n) {
        if (flowerBed[0] == 0 && flowerBed.length == 1)
            return 1 >= n;
        int count = 0;
        if (flowerBed[0] == 0 && flowerBed[1] == 0) {
            flowerBed[0] = 1;
            count++;
        }
        if (flowerBed[flowerBed.length - 1] == 0 && flowerBed[flowerBed.length - 2] == 0) {
            flowerBed[flowerBed.length - 1] = 1;
            count++;
        }
        for (int i = 1; i < flowerBed.length - 1; i++) {
            if (flowerBed[i - 1] == 0 && flowerBed[i] == 0 && flowerBed[i + 1] == 0) {
                flowerBed[i] = 1;
                count++;
            }
        }
        return count >= n;
    }
}
```

---

## 🐍 Python Solution
```python
class Solution:
    def canPlaceFlowers(self, flowerbed: List[int], n: int) -> bool:
        flowerbed = [0] + flowerbed + [0]
        count = 0
        for i in range(1, len(flowerbed) - 1):
            if flowerbed[i - 1] == flowerbed[i] == flowerbed[i + 1] == 0:
                flowerbed[i] = 1
                count += 1
        return count >= n
```

---

## 💠 C++ Solution
```cpp
class Solution {
public:
    bool canPlaceFlowers(vector<int>& flowerbed, int n) {
        flowerbed.insert(flowerbed.begin(), 0);
        flowerbed.push_back(0);
        int count = 0;
        for (int i = 1; i < flowerbed.size() - 1; ++i) {
            if (flowerbed[i-1] == 0 && flowerbed[i] == 0 && flowerbed[i+1] == 0) {
                flowerbed[i] = 1;
                count++;
            }
        }
        return count >= n;
    }
};
```

---

## ⏱️ Time and Space Complexity
- **Time Complexity:** O(flowerbed.length)
- **Space Complexity:** 
  - Java: O(1) (modifying in place)
  - Python/C++: O(flowerbed.length) (due to padding with extra zeroes)

---

## 🌟 Critical Review
Now, let’s talk brass tacks:

- **Positive:**  
  Your approach works. It checks edge plots separately (first and last) — a necessary evil because the array is not padded. Good in-place update strategy — minimal overhead, very lean.

- **Skeptical View:**  
  Frankly, updating the input array (`flowerbed`) directly is **not ideal** in a real-world system where input immutability is expected. If this was a critical system (think banking software, embedded systems), **mutating inputs** would trigger a code review rejection.  
  Padding with dummy zeroes would have saved you from writing special cases for the first and last elements — cleaner and logically symmetrical.

- **Maintainability Risk:**  
  This method is prone to off-by-one errors — if any constraint changes (e.g., multiple plants allowed per slot in a future version), your code would **collapse** under maintenance.

---

## 📢 Final Verdict
- **Working?** ✅
- **Corporate Production-ready?** ⚠️ (Input mutation, special casing is not future-proof)
- **Recruiter Impression?** *"Solid understanding of greedy logic, but could improve robustness and defensive coding skills."*

---

> ✅ **Recommendation:** Prefer padding the array or create a clone of the array if input mutation is not allowed. Clean separation between logic and input data improves reliability in long-term codebases.
