## 问题：
```
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:

Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
## 分析：
###### 这道题算是比较简单的啦，但我做的第一次还是超时了，就很想不通。思路大致是循环，双指针遍历数组，找到数组中两个相加等于目标的数就好啦。
## 代码：
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int temp=0;
        vector<int>sum;
        int k;
        for(int i=0;i<nums.size();i++)
        {
            for(k=i+1;k<nums.size();k++)
            {

            temp= nums[k]+nums[i];
            if(temp==target)
            {
               sum.push_back(i);
                    sum.push_back(k);
               break;
            }
                if(!sum.empty())
                    break;
            }
           
            
        }
        
        return sum;
    }
};
```
