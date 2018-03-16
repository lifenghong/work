## 问题：
```
Count the number of segments in a string, where a segment is defined to be a contiguous sequence of non-space characters.

Please note that the string does not contain any non-printable characters.

Example:

Input: "Hello, my name is John"
Output: 5
```
## 问题分析：
###### 这道题目，我刚开始以为比较简单，就是输入一个字符串数组，用指针遍历数组，从开始若遇到空格，则计数器加一。输出count，也可以用函数解决比较方便
###### 用string函数，比较方便，也可以用getline，最近一直在学习这两个函数的用法，
## 代码实现：
```cpp
class Solution {
public:
    int countSegments(string s) {
        int res = 0;
        s.push_back(' ');
        for(int i = 1; i < s.size(); ++i)
          if(s[i] == ' ' && s[i-1] != ' ') ++res;
        return res;
    }
};
```
## 我的代码：
```cpp
int countSegments（s）
{ 
   ss（s）; 
int counts = 0;

    while(getline(ss,temp,' '))//getline函数，直到以下情况发生会导致生成的此字符串结束。1)到文件结束，2)遇到函数的定界符，3)输入达到最大限度。


    {
        if(!temp.empty())
            count++;
    }
        
    return count;
}
