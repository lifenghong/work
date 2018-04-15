## 问题：
```
Given a 32-bit signed integer, reverse digits of an integer.

Example 1:

Input: 123
Output: 321
Example 2:

Input: -123
Output: -321
Example 3:

Input: 120
Output: 21
```
## 分析：
####### 其实就是一到很简单的反转问题，可以转换成字符串解决，也可以直接解决，但最注意的是对于超时的判断，以前做的代码没有注意这一点，LeetCode上过不去。
## 代码：
```cpp
class Solution {
public:
    int reverse(int x) {
        int a= 0x7fffffff,b=0x80000000;
       int flag;
       long long num=0;
        if(x>0)
           flag=1;
        if(x<0)
            flag=-1;
        while(x)
        {
            num=num*10+x%10;
            if(num>a||num<b)
            {
                num=0;
                break;
            }
           x/=10;
        }
        return num;
    }
};
```
