**思路**

通过一个变量统计符合添加的值的个数，并替换

**解法**

Rust

```rust

impl Solution {
    pub fn remove_element(nums: &mut Vec<i32>, val: i32) -> i32 {
       let mut k : usize = 0;
       for i in 0..nums.len() {
           if nums[i] != val {
               nums[k] = nums[i];
               k += 1;
           }
       }
       return k as i32;
    }
}
```