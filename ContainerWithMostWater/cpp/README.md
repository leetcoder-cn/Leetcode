**思路**

两个下标确定的容器大小即是，下标之差（容器底边长）与下标中较小的那个边（短板）的高度的乘积。

可以采用双下标的方式，从两侧开始遍历，每次循环记录当前两个下标所代表的容器的容量大小。记录下最大的容器容量。

步进方法，将边长较小的那条边的下标向中间走一步，直到两个下标重合为止，最大的容量值，即为返回值。

因为每次循环总会让容器的边缩小一下，因此这个程序总能结束，所有元素都要被访问依次，因此时间复杂度为`O(n)`，所需空间为常数，空间复杂度为`O(1)`

**Runtime Result**

Runtime: 20 ms, faster than 98.58% of C++ online submissions for Container With Most Water.
Memory Usage: 9.9 MB, less than 88.32% of C++ online submissions for Container With Most Water.

**解法**
```
class Solution {
public:
    int maxArea(vector<int>& height) {
        int i = 0, j = height.size() - 1;
        int area = 0;
        while(i < j)
        {
            int a = (j - i) * min(height[i], height[j]);
            if(area < a)
            {
                area = a;
            }
            if(height[i] < height[j]) i++;
            else j--;
        }
        return area;
    }
};
```