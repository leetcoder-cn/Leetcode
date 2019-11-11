**思路**

字符串法: 将数字转换为字符串，然后反转，比较两个字符串是否相等

**解法**

Python

```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        return str(x) == str(x)[::-1]
```