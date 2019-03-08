**思路**

1. 新建链表
2. 同时遍历 l1 和 l2 链表,求和,计算进位,直至其中有一个链表到底底部
3. 因为无法得知 l1 和 l2 长度,因此重新遍历两个链表,**注意:首次求和需要加上步骤 2 最后一次的进位 carry**
4. 遍历完成后,检查是否存在进位 carry,返回结果

**解法**

```python
# author : leetao<leetao94cn@gmail.com>
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution:
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        sum_node = ListNode(-1)
        head = sum_node
        carry = 0
        while l1 and l2:
            sum_val = l1.val + l2.val + carry
            val = sum_val % 10
            carry = sum_val // 10
            sum_node.next = ListNode(val)
            sum_node = sum_node.next
            l1 = l1.next
            l2 = l2.next
        
        while l1:
            sum_val = l1.val + carry
            val = sum_val % 10
            carry = sum_val // 10
            sum_node.next = ListNode(val)
            l1 = l1.next
            sum_node = sum_node.next
        
        while l2:
            sum_val = l2.val + carry
            val = sum_val % 10
            carry = sum_val // 10
            sum_node.next = ListNode(val)
            l2 = l2.next
            sum_node = sum_node.next
        
        if l1 is None and l2 is None and carry > 0:
            sum_node.next = ListNode(carry)
            
        return head.next
```