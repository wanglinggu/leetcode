[[19 删除链表的倒数第N各节点]](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/)

问题：

> 给定一个链表，删除链表的倒数第 *n* 个节点，并且返回链表的头结点。
>
> **示例：**
>
> ```
> 给定一个链表: 1->2->3->4->5, 和 n = 2.
> 
> 当删除了倒数第二个节点后，链表变为 1->2->3->5.
> ```
>
> **说明：**
>
> 给定的 *n* 保证是有效的。
>
> **进阶：**
>
> 你能尝试使用一趟扫描实现吗？



解析：

> 1、题不难，难的是进阶。
>
> 2、如何保证一趟遍历能够定位到倒数第N各节点或其前一个节点。
>
> 3、如何保证链表为空。



解决方案：

```python
# Definition for singly-linked list.
# class ListNode:
# def __init__(self, x):
# self.val = x
# self.next = None

class Solution:
    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        tmp_head = ListNode(0)
        tmp_head.next = head
        fast_head = tmp_head
        res = tmp_head
        for i in range(n):
            fast_head = fast_head.next
        while fast_head.next != None:
            fast_head = fast_head.next
            tmp_head = tmp_head.next
        tmp_head.next = tmp_head.next.next
        return res.next
```

