
**思路**

遍历列表,通过哈希表记录元素位置,如果 target - 元素 值存在于哈希表中,则直接返回两个元素的索引


**解法**

```rust
use std::collections::HashMap;
impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
        let mut index_hash_map = HashMap::new();
        let mut key = 0;
        for value in nums.iter() {
            let index = target - value;
            if index_hash_map.contains_key(&index) {
                 return vec![index_hash_map[&index], key];
            }
            index_hash_map.insert(value,key);
            key += 1;
        }
        return vec![];
    }
}
```

```rust
use std::collections::HashMap;
impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {

        let mut sum_dict = HashMap::new();

        for (i,num) in nums.iter().enumerate() {
            let ref key = target - num;
            if sum_dict.contains_key(key) {
                return vec![sum_dict[key],i as i32];
            }
            sum_dict.insert(num,i as i32);
        }
        return vec![]
    }
}
```