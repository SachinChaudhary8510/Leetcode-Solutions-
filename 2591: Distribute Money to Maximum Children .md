# 💰 LeetCode Problem 2591: Distribute Money to Maximum Children

## 📘 Problem Statement

You are given:
- An integer `money` representing the **total amount of dollars** you must distribute.
- An integer `children` representing the **number of children** you must distribute money to.

You must follow **three strict rules**:
1. **All money must be distributed**.
2. **Each child must receive at least 1 dollar**.
3. **No child can receive exactly 4 dollars**.

Your task:  
➡️ Return the **maximum number of children** who can receive **exactly 8 dollars** under these constraints.  
➡️ If it's **impossible** to distribute the money, return `-1`.

---

## 🧠 Examples

### Example 1:
**Input:**  
`money = 20`, `children = 3`  
**Output:** `1`  
**Explanation:**  
- Distribute 8 to child 1, 9 to child 2, 3 to child 3 → all constraints satisfied.  
- No valid distribution allows more than **1 child** to get exactly 8 dollars.

### Example 2:
**Input:**  
`money = 16`, `children = 2`  
**Output:** `2`  
**Explanation:**  
- Both children can receive 8 dollars.  
- Total = 8 + 8 = 16 → all money distributed, no one gets 4.

---

## 📚 Constraints

- `1 <= money <= 200`
- `2 <= children <= 30`

---

## ✅ Java Solution

```java
class Solution {
    public int distMoney(int m, int c) {
        if (m < c) return -1;

        m -= c;  // give 1 dollar to each child
        int count = m / 7;

        if (m % 7 == 3 && count > 0 && c - count == 1) {
            count--;
        }

        if (count == c && m % 7 != 0) {
            count--;
        }

        return Math.min(count, c - 1);
    }
}
```

---

## 🐍 Python Solution

```python
class Solution:
    def distMoney(self, money: int, children: int) -> int:
        if money < children:
            return -1
        
        money -= children  # 1 dollar per child
        count = money // 7

        if money % 7 == 3 and count > 0 and children - count == 1:
            count -= 1

        if count == children and money % 7 != 0:
            count -= 1

        return min(count, children - 1)
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    int distMoney(int money, int children) {
        if (money < children) return -1;

        money -= children;  // give 1 dollar to each child
        int count = money / 7;

        if (money % 7 == 3 && count > 0 && children - count == 1) {
            count--;
        }

        if (count == children && money % 7 != 0) {
            count--;
        }

        return std::min(count, children - 1);
    }
};
```

---

## 🧾 Analysis

| Metric               | Value              |
|----------------------|-------------------|
| **Time Complexity**  | O(1) (constant)   |
| **Space Complexity** | O(1)             |
| **Approach**         | Greedy math logic with edge case validation |

---

### 🔍 Key Observations

- Always subtract `children` first to allocate the mandatory $1 to each child.
- Each 8-dollar child needs 7 additional dollars.
- Check special case:
  - Remainder is 3, only 1 child left → would force a 4-dollar allocation → invalid.
- Avoid giving 4 inadvertently in other edge cases.
- Cap `count` of 8-dollar kids to `children - 1` to ensure compliance.

---

## 🧪 Test Cases

| money | children | Output | Explanation |
|-------|----------|--------|-------------|
| 20    | 3        | 1      | Valid config: [8,9,3] |
| 16    | 2        | 2      | [8,8] |
| 2     | 3        | -1     | Not enough money |
| 7     | 2        | 0      | No child gets 8 |
| 23    | 4        | 2      | [8,8,5,2] or similar |

---

## 📌 Conclusion

This problem is deceptively simple until the edge cases hit:
- It's a pure **greedy** problem.
- Avoiding the forbidden value (4 dollars) requires **thoughtful constraint handling**.
- Efficiently solvable in **constant time**, making it suitable for interviews.

> ⚠️ Don’t be fooled by the "Easy" label — edge conditions make this a mini-puzzle in disguise.
