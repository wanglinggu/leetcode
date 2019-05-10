[[42 接雨水]](https://leetcode-cn.com/problems/trapping-rain-water/)

问题：

> 给定 *n* 个非负整数表示每个宽度为 1 的柱子的高度图，计算按此排列的柱子，下雨之后能接多少雨水。
>
> ![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/22/rainwatertrap.png)
>
> 上面是由数组 [0,1,0,2,1,0,1,3,2,1,2,1] 表示的高度图，在这种情况下，可以接 6 个单位的雨水（蓝色部分表示雨水）。 **感谢 Marcos** 贡献此图。
>
> **示例:**
>
> ```
> 输入: [0,1,0,2,1,0,1,3,2,1,2,1]
> 输出: 6
> ```



解析：

> 1、要先理解题目说的内容。
>
> 2、根据理解画出图。
>
> 3、每两个高的柱子之间可以存雨水。
>
> 4、寻找最高的柱子，从两个开始循环，当两侧的柱子比两侧前一个柱子高的时候，就可以存水。



解决方案：

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        if len(height) <= 2:
            return 0
        index = 0
        tmp_max = 0
        for i in range(len(height)):
            if height[i] > tmp_max:
                tmp_max = height[i]
                index = i
        res = 0
        tmp_height = height[0]
        for i in range(1, index):
            if tmp_height > height[i]:
                res += tmp_height - height[i]
            else:
                tmp_height = height[i]
        tmp_height = height[-1]
        for j in range(-2, -(len(height)-index), -1):
            if tmp_height > height[j]:
                res += tmp_height - height[j]
            else:
                tmp_height = height[j]
        return res
```

