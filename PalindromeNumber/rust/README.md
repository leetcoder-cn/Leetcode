**思路**

1. 字符串法: 将数字转换为字符串，然后反转，比较两个字符串是否相等
2. 数字法:如果是负数,直接返回 false 如果是 0 则返回 true,如果是正数,则通过 ```余数 = x % 10; x = x/10; y = y*10 + 余数```, 然后判断```x 是否 = y ```


**解法**

解法一

```rust
impl Solution {
    pub fn is_palindrome(x: i32) -> bool {
        let str_x = x.to_string();
        return str_x == str_x.chars().rev().collect::<String>();
    }
}
```

解法二

```rust
impl Solution {
    pub fn is_palindrome(x: i32) -> bool {
        if x < 0 {
            return false;
        }
        
        if x == 0 {
            return true;
        }
        
        let mut a = x;
        let mut y = 0;
        
        while a / 10 > 0 {
            let z = a % 10;
            a = a / 10;
            y = y * 10 + z;
        }
        y = y* 10 + a;
        return x == y;
    }
}
```