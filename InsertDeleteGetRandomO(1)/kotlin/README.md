**思路**

很容易想到 ArrayList + HashMap 的组合. ArrayList 的 remove 可能会产生元素移动, 但是移除最后一个元素不会造成其他元素的移动.
参考了 [Java, concise & fast (beats 100%)](https://leetcode.com/problems/insert-delete-getrandom-o1/discuss/249013/Java-concise-and-fast-(beats-100)) 来简化 remove 方法的代码.

**解法**

Runtime: 268 ms, faster than 100.00% of Kotlin online submissions.
Memory Usage: 45.3 MB, less than 100.00% of Kotlin online submissions.

```kotlin
class RandomizedSet() {

   /** Initialize your data structure here. */
    private val map = hashMapOf<Int, Int>()
    private val list = arrayListOf<Int>()

    /** Inserts a value to the set. Returns true if the set did not already contain the specified element. */
    fun insert(`val`: Int): Boolean {
        if (map[`val`] != null) {
            return false
        }
        map[`val`] = map.size
        list.add(`val`)
        return true
    }

    /** Removes a value from the set. Returns true if the set contained the specified element. */
    fun remove(`val`: Int): Boolean {
        val index = map[`val`] ?: return false
        list[index] = list.last()
        map[list.removeAt(list.lastIndex)] = map[`val`]!!
        map.remove(`val`)
        return true
    }

    /** Get a random element from the set. */
    fun getRandom(): Int {
        return list[(Math.random() * list.size).toInt()]
    }

}
```