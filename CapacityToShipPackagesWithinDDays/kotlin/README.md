**思路**

先遍历一遍数组, 确定下可能的最小容量, 然后从这个容量开始向后枚举, 找到第一个符合条件的.

**解法**

Runtime: 344 ms.
Memory Usage: 41.5 MB.

```kotlin
class Solution {
    fun shipWithinDays(weights: IntArray, D: Int): Int {
        var need = Int.MIN_VALUE
        var weight = 0
        
        // 找到最大的重量
        for (i in 0..weights.lastIndex) {
            need = kotlin.math.max(need, weights[i])
            weight += weights[i]
        }

        // 计算平均每天需要搬运重量, 如果容量小于这个肯定是不行的
        // 选取平均重量和最大重量中较大的那个
        need = kotlin.math.max(need, kotlin.math.ceil( weight.toFloat() / D).toInt())

        // 寻找最小的容量
        do {
            var day = 1
            var sum = 0
            var nextNeed = Int.MAX_VALUE
            for (i in 0..weights.lastIndex) {
                val nextSum = sum + weights[i]
                sum = if (nextSum > need) {
                    day++
                    // 此时的 nextSum 可能就是下一个候选的最小容量
                    nextNeed = kotlin.math.min(nextNeed, nextSum)
                    weights[i]
                } else {
                    nextSum
                }
            }
            if (day > D) need = nextNeed
        } while (day > D)

        return need
    }
}
```