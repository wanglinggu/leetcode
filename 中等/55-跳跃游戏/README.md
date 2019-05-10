[[55 跳跃游戏]](https://leetcode-cn.com/problems/jump-game/submissions/)

问题：

> 给定一个非负整数数组，你最初位于数组的第一个位置。
>
> 数组中的每个元素代表你在该位置可以跳跃的最大长度。
>
> 判断你是否能够到达最后一个位置。
>
> **示例 1:**
>
> ```
> 输入: [2,3,1,1,4]
> 输出: true
> 解释: 从位置 0 到 1 跳 1 步, 然后跳 3 步到达最后一个位置。
> ```
>
> **示例 2:**
>
> ```
> 输入: [3,2,1,0,4]
> 输出: false
> 解释: 无论怎样，你总会到达索引为 3 的位置。但该位置的最大跳跃长度是 0 ， 所以你永远不可能到达最后一个位置。
> ```



解析：

> 1、查找到 0，然后去判断其前面的数字是否能够超过与零之间的距离，超不过则返回 False。
>
> 2、从后向前，如果遇到的元素可以到达最后一行，则截断后边的元素。否则继续往前。



解决方案：

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        tmp_num = 1
        for i in range(len(nums) - 2, -1, -1):
            if nums[i] >= tmp_num:
                tmp_num = 1
            else:
                tmp_num += 1
            if i == 0 and tmp_num > 1:
                return False
        return True
```

