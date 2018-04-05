## 题目：
```
Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].

Note:
You must do this in-place without making a copy of the array.
Minimize the total number of operations.
```
## 分析：
###### 这道题因为不允许在构造一个数组来储存，只能在原地修改，那就只能去掉0，再在数组最后加上相同数量的0就可以啦，思路比较简单；
## 代码：
```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int count=0;
       for(int i=0;i<nums.size();i++)
             {
                 if(nums[i])
                 {
                     nums[count++]=nums[i];
                     
                 }
             }
              for(int i=count;i<nums.size();i++)
              {
                  nums[i]=0;
              }
       
    }
};
```
