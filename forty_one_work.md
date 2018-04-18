## 题目：507. Perfect Number
```
We define the Perfect Number is a positive integer that is equal to the sum of all its positive divisors except itself.

Now, given an integer n, write a function that returns true when it is a perfect number and false when it is not.
Example:
Input: 28
Output: True
Explanation: 28 = 1 + 2 + 4 + 7 + 14
```
## 分析：
###### （从这道题感受到了LeetCode怼我满满的恶意，换了好几种格式，明明编译通过了，提交不是超时就是wr，写了20分钟代码，找了一小时错误还是没找到）这道题就是
###### 找到给定正整数的因子，并计算出来自己本身以外的因子的和。如果等于它本身则返回true，

## 代码：(AC的代码）
```cpp
class Solution {
public:
    bool checkPerfectNumber(int num) {
        vector<int>res(1,1);
        int upper=num;
        for(int i=2;i<upper;i++) 
        {
            if(num%i==0) 
            {res.push_back(i);
                res.push_back(num/i);
            }
            upper=num/i;
        }
        int sum=0;
        for(int i=1;i<res.size();i++) sum+=i;
        return sum==num && num!=1;
    }
};
```
## 我的代码（真的没找出错）
```cpp
class Solution {
public:
    bool checkPerfectNumber(int num) {
        vector<int>n(1,1);
        int a=num;
        for(int i=1;i<a;i++)
        {
            for(int j=i+1;j<a;j++)
            {
                if(i*j==a)
                {
                    n.push_back(i);
                    n.push_back(j);
                }
            }
        }
        int sum=0;
        for(auto i:n)
            sum+=i;
            return sum==num && num!=1;
    }
};
```
