
**思路**

遍历列表,通过哈希表记录元素位置,如果 target - 元素 值存在于哈希表中,则直接返回两个元素的索引


**解法**

```python
class Solution:
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        hash_dict = {}
        for key,value in enumerate(nums):
            hash_dict[value] = key
        
        for key,value in enumerate(nums):
            if (target - value) in hash_dict and key != hash_dict[target - value]:
                return [key,hash_dict[target - value]]
        
```
