给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。  

示例 1:  
    输入: 123  
    输出: 321  

示例 2:  
    输入: -123  
    输出: -321  

示例 3:  
    输入: 120  
    输出: 21  

注意:  

假设我们的环境只能存储得下 32 位的有符号整数，则其数值范围为 [−2^31,  2^31 − 1]。请根据这个假设，如果反转后整数溢出那么就返回 0。  



解析：  

1、将数字转为字符串，通过字符串反转，后将字符串转为 int ，这种方式需要对数据进行判断，因为只能存下32位数，所以反转后需要判断有无溢出。  



class Solution:  
    def reverse(self, x: int) -> int:  
        res = 0  
        if x >= 0:  
            res = int(str(x)[::-1])  
        elif x < 0:  
            res = -int(str(-x)[::-1])  

        if -2 ** 31 <= res <= 2 ** 31 - 1:  
            return res  
        else:  
            return 0  


python3中int类型位长整形，所以从 str 转为 int 时不会造成溢出异常  

C/C++中可以采取 try-catch 来捕获异常，如果报异常返回 0 。