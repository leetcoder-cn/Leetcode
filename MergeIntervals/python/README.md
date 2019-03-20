**思路**

先排序然后遍历，排序按照 start 值大小排序，排序完后，遍历排序后的列表 sorted_list，假设当前元素位置 i, 判断 sorted_list[i-1].end >= sorted_list[i]，说明两个区间有重合，将  sorted_list[i].start = sorted_list[i-1].end，**注意判断 sorted_list[i-i].end 是否大于 sorted_list[i].end，如果大于，则 sorted_list[i].end = sorted_list[i-1].end** 

**解法**

```python
# Definition for an interval.
# class Interval:
#     def __init__(self, s=0, e=0):
#         self.start = s
#         self.end = e

class Solution:
    def merge(self, intervals: List[Interval]) -> List[Interval]:
        sorted_start_list = sorted(intervals,key=lambda x:x.start)
        list_len = len(sorted_start_list)
        res_list = []
        count = 0
        i = 1
        while i < list_len - count:
            if sorted_start_list[i-1].end >= sorted_start_list[i].start:
                if sorted_start_list[i-1].end > sorted_start_list[i].end:
                    sorted_start_list[i].end = sorted_start_list[i-1].end
                sorted_start_list[i].start = sorted_start_list[i-1].start
                sorted_start_list.remove(sorted_start_list[i-1])
                count += 1
                i -= 1
            i += 1
        return sorted_start_list
```