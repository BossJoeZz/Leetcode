Leetcode目录
Easy:
* 20 Valid Parentheses

## 20 Valid Parentheses (Easy)
[https://leetcode-cn.com/problems/valid-parentheses/](https://leetcode-cn.com/problems/valid-parentheses/)
```python
class Solution:
    def isValid(self, s: str) -> bool:
        if len(s) % 2 == 1:
            return False
        
        pairs = {
            ")": "(",
            "]": "[",
            "}": "{",
        }
        
        stack = list()
        
        for ch in s:
            if ch in pairs:
                if stack is None or stack[-1] != pairs[ch]: # if not 就是 is None的意思
                    return False
                stack.pop()
            else:
                stack.append(ch)
        
        return not stack
