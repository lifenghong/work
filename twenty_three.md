## 问题：
```
Given a string representing an expression of fraction addition and subtraction, you need to return the calculation result in string format. The final result should be irreducible fraction. If your final result is an integer, say 2, you need to change it to the format of fraction that has denominator 1. So in this case, 2 should be converted to 2/1.

Example 1:
Input:"-1/2+1/2"
Output: "0/1"
Example 2:
Input:"-1/2+1/2+1/3"
Output: "1/3"
Example 3:
Input:"1/3-1/2"
Output: "-1/6"
Example 4:
Input:"5/3+1/3"
Output: "2/1"
```
## 分析：
###### 这道题目不用函数也可以做，就是用最普通的方法做，记得以前做过一道类似的题目，在这儿用了gcd函数，但有的测试器不支持gcd函数，就很悲剧
###### 这道题的题意很简单，就是针对分式做计算，最后返回最简分式作为结果，本题的关键件就是使用C++的stringstream来分割字符串，然后求最大公约数
###### 最大公约数则用gcd函数实现。
## 代码：
```cpp
class Solution 
{
public:
    string fractionAddition(string expression)
    {
        stringstream str(expression);
        int fenzi = 0, fenmu = 1, s, m;
        char n;
        while (str >> s >> n >> m)
        {
            fenzi = fenzi*m + fenmu*s;
            fenmu = fenmu*m;
            int dev = gcd(abs(fenzi), abs(fenmu));
            fenzi /= dev;
            fenmu /= dev;
        }
        return to_string(fenzi) + "/" + to_string(fenmu);
    }

    int gcd(int i, int j)
    {
        if(j==0)
        {
            return i;
        }
        else
            return  gcd(j,i%j);
    }
};
```
