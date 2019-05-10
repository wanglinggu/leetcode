[[766 托普利茨矩阵]](https://leetcode-cn.com/problems/toeplitz-matrix/)

问题：

> 如果一个矩阵的每一方向由左上到右下的对角线上具有相同元素，那么这个矩阵是*托普利茨矩阵*。
>
> 给定一个 `M x N` 的矩阵，当且仅当它是*托普利茨矩阵*时返回 `True`。
>
> **示例 1:**
>
> ```
> 输入: 
> matrix = [
>   [1,2,3,4],
>   [5,1,2,3],
>   [9,5,1,2]
> ]
> 输出: True
> 解释:
> 在上述矩阵中, 其对角线为:
> "[9]", "[5, 5]", "[1, 1, 1]", "[2, 2, 2]", "[3, 3]", "[4]"。
> 各条对角线上的所有元素均相同, 因此答案是True。
> ```
>
> **示例 2:**
>
> ```
> 输入:
> matrix = [
>   [1,2],
>   [2,2]
> ]
> 输出: False
> 解释: 
> 对角线"[1, 2]"上的元素不同。
> ```
>
> **说明:**
>
> 1.  `matrix` 是一个包含整数的二维数组。
> 2. `matrix` 的行数和列数均在 `[1, 20]`范围内。
> 3. `matrix[i][j]` 包含的整数在 `[0, 99]`范围内。
>
> **进阶:**
>
> 1. 如果矩阵存储在磁盘上，并且磁盘内存是有限的，因此一次最多只能将一行矩阵加载到内存中，该怎么办？
> 2. 如果矩阵太大以至于只能一次将部分行加载到内存中，该怎么办？



解析：

> 1、每一行除了最后一个和下一行除了第一个相同，就返回 True。
>
> 2、在不考虑时间空间的情况下，可以采用其他方法。
>
> 3、进阶版本没做出来。



解决方案：

```python
class Solution:
    def isToeplitzMatrix(self, matrix: List[List[int]]) -> bool:
        '''
        if len(matrix) <= 1:
            return True
        for i in range(0, len(matrix) - 1):
            if matrix[i][:-1] != matrix[i+1][1:]:
                return False
        return True
        '''
        length = len(matrix)
        width = len(matrix[0])
        a,b=0,0
        while b<length-1:
            while a < width-1 :
                if matrix[b][a] == matrix[b+1][a+1]:
                    a += 1
                else:
                    return False
            b+=1
            a=0
        return True
```

