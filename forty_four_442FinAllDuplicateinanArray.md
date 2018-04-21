## 问题：
```Given an array of integers, 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.

Find all the elements that appear twice in this array.

Could you do it without extra space and in O(n) runtime?

Example:
Input:
[4,3,2,7,8,2,3,1]

Output:
[2,3]
```
## 分析：
###### 这道题思路，一：从左到右遍历数组，判断元素是否相同，相同的元素储存在另一个数组中，最后输出就好
###### 思路二：先给数组中的元素归位，使得数组中元素与下标相对应，如果元素与下标数加一不相等，则该元素为重复元素。储存输出；
## 代码一：
```cpp
class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
        vector<int>vs;
        for(int i=0;i<nums.size()-1;i++)
        {
            for(int j=i+1;j<nums.size();j++)
            {
                if(nums[i]==nums[j])
                {
                    vs.push_back(nums[j]);
                }
            }
            
        }
        return vs;
        }
   ```
   ## 代码二：
   ```cpp
  class Solution {
    public:
    vector<int> findDuplicates(vector<int>& nums) {
        vector<int>vs;
        for(int i=0;i<nums.size();)
        {
            if(nums[nums[i]-1]!=nums[i])
                swap(nums[nums[i]-1],nums[i]);
            else
                i++;
            
        }
        for(int i=0;i<nums.size();i++)
        {
            if(nums[i]!=i+1)
                vs.push_back(nums[i]);
                
        }
        return vs;
    }
};
