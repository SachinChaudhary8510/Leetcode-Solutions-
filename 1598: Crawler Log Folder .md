# 📁 LeetCode Problem 1598: Crawler Log Folder

## 📘 Problem Statement

The LeetCode file system keeps a log of every change folder operation performed by a user.

The operations can be:
- `"../"` : Move to the parent folder (unless already at the main/root folder).
- `"./"` : Stay in the current folder.
- `"x/"` : Move to a subfolder named `x`.

Given a list of strings `logs`, where `logs[i]` represents the `i-th` operation, return the **minimum number of operations** needed to go back to the main folder.

---

## 🔍 Examples

### Example 1:

**Input:**  
logs = ["d1/","d2/","../","d21/","./"]  
**Output:** 2  
**Explanation:**  
Current path is: `/d1/d21`  
Need to perform `"../"` twice to return to `/`.

---

### Example 2:

**Input:**  
logs = ["d1/","d2/","./","d3/","../","d31/"]  
**Output:** 3

---

### Example 3:

**Input:**  
logs = ["d1/","../","../","../"]  
**Output:** 0  
**Explanation:**  
Already at root, can't go higher.

---

## 🔒 Constraints

- `1 <= logs.length <= 10^3`
- `2 <= logs[i].length <= 10`
- `logs[i]` consists of lowercase English letters, digits, '.', and '/'
- All operations are valid

---

## 💻 Java Solution

```java
class Solution {
    public int minOperations(String[] logs) {
        int count = 0;
        for (int i = 0; i < logs.length; i++) {
            if (logs[i].charAt(0) != '.') {
                count++;
            } else {
                if (logs[i].charAt(0) == '.' && logs[i].charAt(1) == '.') {
                    count--;
                }
            }
            if (count <= 0)
                count = 0;
        }
        return count;
    }
}
```
## 🐍 Python Solution
```python
class Solution:
    def minOperations(self, logs: List[str]) -> int:
        depth = 0
        for log in logs:
            if log == "../":
                if depth > 0:
                    depth -= 1
            elif log != "./":
                depth += 1
        return depth
```
## 💠 C++ Solution
```cpp
class Solution {
public:
    int minOperations(vector<string>& logs) {
        int depth = 0;
        for (const auto& log : logs) {
            if (log == "../" && depth > 0) depth--;
            else if (log != "../" && log != "./") depth++;
        }
        return depth;
    }
};
```
## ⏱️ Time and Space Complexity
Time Complexity: `O(n)`, where `n` is the number of log operations

Space Complexity: `O(1)`

## 🌟 Summary
This problem checks how well you simulate simple stack-like behavior without actually using a stack. Track the folder depth directly and avoid unnecessary structure overhead when simple conditionals are sufficient.
