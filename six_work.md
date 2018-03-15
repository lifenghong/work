## 问题:
```
给定一个非负整数num。对于范围0≤i≤num中的每个数字i，计算其二进制表示中的1的数目并将它们作为数组返回。

例如：
对于num = 5您应该返回[0,1,1,2,1,2]。

跟进：

用运行时O（n * sizeof（integer））提出解决方案非常容易。但是你可以在线性时间O（n） /可能在一次传递中做到吗？
空间复杂度应该是O（n）。
你能像老板一样做吗？ 在c ++或任何其他语言中不使用__builtin_popcount等内建函数
```
## 分析：
##### 这道题我的思路是先设立一个循环，在循环中将整数转化为二进制，并用动态数组储存，然后遍历数组，计算元素为1的个数，然后输出，但我看别人的代码，用了两个函数，巧妙的解决了，用时少：
## 代码实现：
```cpp
class Solution {  
public:  
    vector<int> countBits(int num) //countBits 对 num
    {  的设置位进行计数 并返回设置为的数目
        vector<int> answer; //定义大小未知的数组 
        int count;  
        int j;  
        for(int i=0;i<=num;i++)  
        {  
            j=i;  
            count=0;  
            while(j>0)  
            {  
               int right=j>>1;  
               int left=right<<1;  //位运算
               if(j>left) count++;  
               j=right;  
            }  
            answer.push_back(count);  
        }  
        return answer;  
    }  
};  

