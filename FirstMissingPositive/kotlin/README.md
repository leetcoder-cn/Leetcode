**思路**

主要问题在于如何达到 O(1) 的空间复杂度. 

将出现的正数 n 放到原数组的下标 n - 1. 第二次遍历数组时, 找到第一个满足 nums[i] != i + 1 的 i , i + 1 就是答案(如果能找到的话).

**解法**

Runtime: 156 ms, faster than 100.00%
Memory Usage: 33.8 MB, less than 50.00%

```kotlin
class Solution {
    fun firstMissingPositive(nums: IntArray): Int {
        var i = 0
        while (i < nums.size) {
            var num = nums[i++]
            var nextI = num - 1
            while (num > 0 && nextI < nums.size && nums[nextI] != num) {
                val num1 = nums[nextI]
                nums[nextI] = num
                num = num1
                nextI = num - 1
            }
        }

        i = 0
        while (i < nums.size) {
            if (nums[i] != i + 1) {
                return i + 1
            }
            i++
        }
        return nums.size + 1
    }
}
```