**思路**

先排序后返回结果


**解法**


```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        nums_len = len(nums)
        self.quick_sort(nums,0,nums_len-1)
        return nums[-k]
    
    def quick_sort(self, nums, left, right):
        if left >= right:
            return
        low = left
        high = right
        guard = nums[low]
        
        while left < right:
            while left < right and nums[right] > guard:
                right -= 1
            nums[left] = nums[right]
            while left < right and nums[left] <= guard:
                left += 1
            nums[right] = nums[left]
        nums[right] = guard
        self.quick_sort(nums,low,left-1)
        self.quick_sort(nums,left+1,high)
```