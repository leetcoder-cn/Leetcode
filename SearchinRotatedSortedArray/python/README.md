
**思路**

从 O(log n) 的时间复杂度很容易想到是**二分查找**, 二分查找的核心就是分治算法,将一个问题拆分为两个问题,针对拆分后的小问题,也重复上述步骤,直到无法再拆分. 这里需要注意,由于存在旋转,需要判断遍历的区间,假设数组为 arr, 左边索引为 left, 右边索引为 right, 目标值为 target, 存在以下几种情况:

1. arr[mid] > target:
    1. arr[mid] > arr[right]: 由于原本数组是升序排列, 那么 right 右侧有可能存在值等于 target
    2. 其他情况正常递归二分
2. arr[mid] <  target:
    1. arr[mid] > arr[right]: 由于原本数组是升序排列, 那么 right 右侧同样可能存在值等于 target
    2. 其他情况正常递归二分
3. arr[mid] == target: 返回索引


**解法**

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left = 0
        right = len(nums) - 1
        return self.binary_search(nums,left,right,target)
    
    def binary_search(self, arr, left, right, target):
        if left > right:
            return -1
        mid = (left + right) // 2
        res = -1 
        if arr[mid] > target:
            if arr[mid] > arr[right]:
                tmp_res = self.binary_search(arr,mid+1,right,target)
                res = tmp_res if tmp_res != -1 else res
            tmp_res = self.binary_search(arr,left,mid-1,target)
            res = tmp_res if tmp_res != -1 else res
        if arr[mid] < target:
            tmp_res = self.binary_search(arr,mid+1,right,target)
            res = tmp_res if tmp_res != -1 else res
            if arr[mid] < arr[left]:
                tmp_res = self.binary_search(arr,left,mid-1,target)
                res = tmp_res if tmp_res != -1 else res
        if arr[mid] == target:
            res = mid
        return res
```

优化版

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left = 0
        right = len(nums) - 1
        return self.binary_search(nums,left,right,target)
    
    def binary_search(self, arr, left, right, target):
        if left > right:
            return -1
        mid = (left + right) // 2
        res = -1 
        if arr[mid] != target:
            tmp_res = self.binary_search(arr,mid+1,right,target)
            if tmp_res != -1:
                return tmp_res
            tmp_res = self.binary_search(arr,left,mid-1,target)
            if tmp_res != -1:
                return tmp_res
        if arr[mid] == target:
            return mid
        return res
```