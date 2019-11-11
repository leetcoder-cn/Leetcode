判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。

**示例 1:**

```
输入: 121
输出: true
```

**示例 2:**

```
输入: -121
输出: false
解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。
```

**示例 3:**

```
输入: 10
输出: false
解释: 从右向左读, 为 01 。因此它不是一个回文数。
```

**进阶:**

你能不将整数转为字符串来解决这个问题吗？


**思路**

1. 字符串法: 将数字转换为字符串，然后反转，比较两个字符串是否相等
2. 数字法:如果是负数,直接返回 false 如果是 0 则返回 true,如果是正数,则通过 ```余数 = x % 10; x = x/10; y = y*10 + 余数```, 然后判断```x 是否 = y ```