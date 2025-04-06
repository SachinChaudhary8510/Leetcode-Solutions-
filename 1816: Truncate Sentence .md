# 🟢 LeetCode 1816: Truncate Sentence

## 📌 Problem Statement

A sentence is a list of words that are separated by a single space with no leading or trailing spaces. Each of the words consists of only uppercase and lowercase English letters (no punctuation).

You are given a sentence `s` and an integer `k`. You want to truncate `s` such that it contains only the **first `k` words**. Return `s` after truncating it.

---

## 🧩 Examples

### Example 1:
**Input:**  
`s = "Hello how are you Contestant"`, `k = 4`  
**Output:** `"Hello how are you"`

### Example 2:
**Input:**  
`s = "What is the solution to this problem"`, `k = 4`  
**Output:** `"What is the solution"`

### Example 3:
**Input:**  
`s = "chopper is not a tanuki"`, `k = 5`  
**Output:** `"chopper is not a tanuki"`

---

## 🔒 Constraints

- `1 <= s.length <= 500`
- `k` is in the range `[1, the number of words in s]`
- `s` consists only of lowercase and uppercase English letters and spaces
- The words in `s` are separated by a single space

---

## ✅ Java Solution

```java
class Solution {
    public String truncateSentence(String s, int k) {
        int count = 1;
        String str = "";
        for(int i = 0 ; i < s.length() ; i++){
            char c = s.charAt(i);
            if(c != ' ')
                str += c;
            else if(c == ' ' && count != k){
                str += c;
                count++;
            }
            else
                break;
        }
        return str;
    }
}
```

**📝 Explanation:**  
- Traverse the string character by character.
- Count spaces encountered until `k` words are included.
- Concatenate characters accordingly and return the truncated sentence.

---

## 🏁 Summary

| Language     | Logic                        | Notes                       |
|--------------|------------------------------|-----------------------------|
| Java         | Character iteration & count  | Manual space counting logic |

🧠 **Key Insight:** Stop parsing after encountering the `k`-th word.

---

🚀 **Happy Coding!**
