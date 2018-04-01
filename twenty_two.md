## 问题：
```给定不同数字的集合，返回所有可能的排列。

例如，
[1,2,3]有以下排列：
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```
## 分析：
###### 这道题我没有做出来。刚开始我的代码能通过示例，但提交错误，数据一大就不行了，参考网上上的答案，还有·permute函数用法，也不是太明白，大概思路是懂了的，
###### 而这道题主要考察了它的用法，就很无奈。
## 代码：
```cpp
class Solution {
public:
    vector<vector<int>> permute(vector<int>& n) {
        vector<vector<int>>s;
        permuteRecursive(n,0,s);
        return s;
    }
    void permuteRecursive(vector<int>&n,int begin,vector<vector<int>>&s){
        if(begin>=n.size())
        {
            s.push_back(n);
            return ;
            
        }
        for(int i=begin;i<n.size();i++)
        {
            swap(n[begin],n[i]);
            permuteRecursive(n,begin+1,s);
            swap(n[begin],n[i]);
        }
    }
};
```
