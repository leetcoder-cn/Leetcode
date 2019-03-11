**思路：**

与普通二分法类似，每次循环，比较中间元素与target的大小，进一步缩小比较范围。
循环排序数组中，每次缩小搜索范围需要根据两个条件，一是确定当前中间坐标mid的左边还是右边是有序的，第二确定target是否刚好在有序的序列内，两者都是，则控制搜素边界向该范围移动，否则，向mid的另外一边移动。比如在数组`[4,5,6,7,8,1,2,3]`中搜索`8`，首先比较中间元素`7`，并且`7`的左侧是有序数列，但是`8`不在该序列内，因此，下一个搜索范围在`7`的右侧，依次类推，最终得到`8`的下标。

需要注意的边界情况：有两个元素并且倒序时，搜索目标为后一个元素。

Runtime Result
--------
Runtime: 8 ms, faster than 99.52% of C++ online submissions for Search in Rotated Sorted Array.
Memory Usage: 9.9 MB, less than 25.89% of C++ online submissions for Search in Rotated Sorted Array.
