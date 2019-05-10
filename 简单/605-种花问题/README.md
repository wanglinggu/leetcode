[[605 种花问题]](https://leetcode-cn.com/problems/can-place-flowers/)

问题：

> 假设你有一个很长的花坛，一部分地块种植了花，另一部分却没有。可是，花卉不能种植在相邻的地块上，它们会争夺水源，两者都会死去。
>
> 给定一个花坛（表示为一个数组包含0和1，其中0表示没种植花，1表示种植了花），和一个数 **n** 。能否在不打破种植规则的情况下种入 **n** 朵花？能则返回True，不能则返回False。
>
> **示例 1:**
>
> ```
> 输入: flowerbed = [1,0,0,0,1], n = 1
> 输出: True
> ```
>
> **示例 2:**
>
> ```
> 输入: flowerbed = [1,0,0,0,1], n = 2
> 输出: False
> ```
>
> **注意:**
>
> 1. 数组内已种好的花不会违反种植规则。
> 2. 输入的数组长度范围为 [1, 20000]。
> 3. **n** 是非负整数，且不会超过输入数组的大小。



解析：

> 1、想要种花，只有三个空才能种。
>
> 2、查找三个空能有几个，就可以种几个花。
>
> 3、为了保证头尾两部分也能进行判断，在头尾各添加一个 0。
>
> 4、例如 0，0，1，0，1，0 变为了 0，0，0，1，0，1，0，0，可以看出在头可以种一个花。



解决方案：

```python
class Solution:
    def canPlaceFlowers(self, flowerbed: List[int], n: int) -> bool:
        flowerbed = [0] + flowerbed + [0]
        mid = 1
        tmp_num = 0
        while mid + 1 < len(flowerbed):
            if flowerbed[mid - 1:mid + 2] == [0, 0, 0]:
                flowerbed[mid] = 1
                tmp_num += 1
            mid += 1
        if tmp_num >= n:
            return True
        else:
            return False
```

