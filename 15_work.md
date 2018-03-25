## 问题：
```
  Given two strings s1 and s2, write a function to return true if s2 contains the permutation of s1. In other words, one of the first string's permutations is the substring of the second string.
Example 1:
Input:s1 = "ab" s2 = "eidbaooo"
Output:True
Explanation: s2 contains one permutation of s1 ("ba").
Example 2:
Input:s1= "ab" s2 = "eidboaoo"
Output: False
```
## 问题分析：
##### 其实这道题我没懂，刚开始我把题目理解成循环移位了，结果提交错误才发现自己理解错了，后来想了半天，参考了别人的代码才知道具体的实现过程
## 我的错误代码：
```cpp
#include <iostream>  
#include <string>  
using namespace std;  
  
bool yiwei(string src,string des)  
{  
    int len1 = src.size();  
    int len2 = des.size();  
    int i,j = 0;  
    for(i = 0;i < len1 + len2;i++)  
    {  
        if(src[i%len1] == des[j])  
        {  
            j++;  
            if(j == len2)  
            {  
               return ture;
				 break; 
				
                 
            } 
        } 
      else
       return false;
    }  
    if(j < len2)  
        cout << "not match!" << endl;  
}  
  ```
  ## 正确代码：
  ```cpp
  class Solution {
public:
    bool checkInclusion(string s1, string s2) { 
    vector<int> v1(256,0),v2(256,0);
        int n = s1.size();
        if(n>s2.size()) return false;
        for(int i = 0; i < n; ++i)
        {
            ++v1[s1[i]];
            ++v2[s2[i]];
        }
        if(v1==v2) return true;
        for(int i = n; i < s2.size(); ++i)
        {
            ++v2[s2[i]];
            --v2[s2[i-n]];
            if(v1 == v2) return true;
        }
        return false;
    }
};
