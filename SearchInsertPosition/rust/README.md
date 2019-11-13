
**思路**

二分查找

**解法**

```rust
impl Solution {
    pub fn search_insert(nums: Vec<i32>, target: i32) -> i32 {
        let mut left = 0;
        let mut right = nums.len();
        while left < right {
            let mid = left + (right - left)/2;
            let mid_number = nums.get(mid).unwrap();
            if mid_number == &target {
                return mid as i32;
            }
            if mid_number > &target {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left as i32;
    }
}
```