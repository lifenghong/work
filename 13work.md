## 问题：
```
Given an integer, write a function to determine if it is a power of three.

Follow up:
Could you do it without using any loop / recursion?
```
## 分析：
若没有其他要求，这道题其实很简单，但这道目要求不用递归和循环，这就要求用到一种函数
## 我的代码：
```cpp
class Solution {  
public:  
    bool isPowerOfThree(int n) {  
        if(n <= 0) return false;  
        while(n != 1)  
        {  
            if(n%3 != 0)  
            {  
                cout <<n << " "<< n%3 << endl;  //常规算法，很简单
                return false;  
            }  
            n = n/3;  
        }  
        return true;  
    }  
};  
```
## 函数另一种算法：
```cpp
class Solution {  
public:  
    bool isPowerOfThree(int n) {  
        if(n <= 0) return false;  
        return ((int)pow(3, (int)(log(INT_MAX)/log(3))) % n) == 0;  
    }  
};  
## 总结：
##### pow是C语言库函数中的数学函数之一，其声明为double pow(double n, double r);声明与math.h。其功能为求n的r次幂，并作为返回值返回。log和write函数我还没有弄懂明天会继续做这类题
