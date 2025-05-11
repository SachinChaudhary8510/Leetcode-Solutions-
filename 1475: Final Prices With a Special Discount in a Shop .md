# 🛍️ LeetCode Problem 1475: Final Prices With a Special Discount in a Shop

## 📘 Problem Statement

You are given an integer array `prices` where `prices[i]` represents the price of the **i-th** item in a shop.

There is a special **discount rule**:  
For the i-th item, find the **first item j > i** such that `prices[j] <= prices[i]`.  
You will receive a **discount** equal to `prices[j]`. If no such `j` exists, no discount is applied.

Return an array `answer` where `answer[i]` is the **final price** you will pay for the i-th item, after applying the discount.

---

### 🧠 Examples

#### Example 1:
**Input:**  
`prices = [8,4,6,2,3]`  
**Output:** `[4,2,4,2,3]`  
**Explanation:**  
- `8` → next lower price is `4` → 8 - 4 = 4  
- `4` → next lower is `2` → 4 - 2 = 2  
- `6` → next lower is `2` → 6 - 2 = 4  
- `2` → no lower value → 2  
- `3` → no lower value → 3  

---

### 📚 Constraints

- `1 <= prices.length <= 500`
- `1 <= prices[i] <= 10,000`

---

## ✅ Java Solution – Brute Force

```java
class Solution {
    public int[] finalPrices(int[] prices) {
        int[] result = new int[prices.length];
        for (int i = 0; i < prices.length; i++) {
            result[i] = prices[i];
            for (int j = i + 1; j < prices.length; j++) {
                if (prices[j] <= prices[i]) {
                    result[i] -= prices[j];
                    break;
                }
            }
        }
        return result;
    }
}
```

---

## 🚀 Java Solution – Optimized (Monotonic Stack, O(n))

```java
import java.util.Stack;

class Solution {
    public int[] finalPrices(int[] prices) {
        Stack<Integer> stack = new Stack<>();
        for (int i = prices.length - 1; i >= 0; i--) {
            while (!stack.isEmpty() && stack.peek() > prices[i]) {
                stack.pop();
            }
            int discount = stack.isEmpty() ? 0 : stack.peek();
            prices[i] -= discount;
            stack.push(prices[i] + discount); // push original price
        }
        return prices;
    }
}
```

---

## 🐍 Python Solution – Optimized (Monotonic Stack, O(n))

```python
from typing import List

class Solution:
    def finalPrices(self, prices: List[int]) -> List[int]:
        stack = []
        for i in range(len(prices) - 1, -1, -1):
            while stack and stack[-1] > prices[i]:
                stack.pop()
            discount = stack[-1] if stack else 0
            prices[i] -= discount
            stack.append(prices[i] + discount)  # push original price
        return prices
```

---

## 💻 C++ Solution – Optimized (Monotonic Stack, O(n))

```cpp
#include <vector>
#include <stack>
using namespace std;

class Solution {
public:
    vector<int> finalPrices(vector<int>& prices) {
        stack<int> st;
        for (int i = prices.size() - 1; i >= 0; --i) {
            while (!st.empty() && st.top() > prices[i])
                st.pop();
            int discount = st.empty() ? 0 : st.top();
            prices[i] -= discount;
            st.push(prices[i] + discount); // push original price
        }
        return prices;
    }
};
```

---

## 🧾 Analysis

| Metric               | Brute Force | Stack Optimized |
|----------------------|-------------|-----------------|
| **Time Complexity**  | O(n²)       | O(n)            |
| **Space Complexity** | O(n)        | O(n)            |
| **Approach**         | Naive       | Monotonic Stack |

---

## 🧪 Test Cases

| prices             | Output       | Description                        |
|--------------------|--------------|------------------------------------|
| `[8,4,6,2,3]`       | `[4,2,4,2,3]` | Discount applied at first lower    |
| `[1,2,3,4,5]`       | `[1,2,3,4,5]` | No discounts available             |
| `[10,1,1,6]`        | `[9,0,1,6]`   | Discount applied to first match    |
| `[5,4,3,2,1]`       | `[1,1,1,1,1]` | Always find lower on immediate right |

---

## 📌 Conclusion

This problem is a classic candidate for **monotonic stack optimization**. While the brute force solution suffices for small input sizes, the optimized version is essential in professional environments with higher complexity requirements.

> 💡 **Pro Tip:** When asked to find the "next smaller/larger element" in linear time, your reflex should be: **Monotonic Stack.**
