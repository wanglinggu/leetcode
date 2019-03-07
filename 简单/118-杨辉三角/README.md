[[118 杨辉三角]](https://leetcode-cn.com/problems/pascals-triangle/)

问题：

> 给定一个非负整数 *numRows，*生成杨辉三角的前 *numRows* 行。
>
> ![img](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)
>
> 在杨辉三角中，每个数是它左上方和右上方的数的和。
>
> 示例:
>
> ```
> 输入: 5
> 输出:
> [
>      [1],
>     [1,1],
>    [1,2,1],
>   [1,3,3,1],
>  [1,4,6,4,1]
> ]
> ```

解析：

> 1、根据行数初始化一个 list，然后根据上一个 list 中的内容两两相加将结果填入 list，最后将 list 添加进一个大的 list 中作为结果返回。

解决方案：

```python
class Solution(object):
    def generate(self, numRows):
        """
        :type numRows: int
        :rtype: List[List[int]]
        """
        res = []
        for i in range(numRows):
            now = [1]*(i+1)
            if i >= 2:
                for n in range(1,i):
                    now[n] = pre[n-1]+pre[n]
            res += [now]
            pre = now
        return res
```

