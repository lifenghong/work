## 问题：
```
Given a sorted array consisting of only integers where every element appears twice except for one element which appears once. Find this single element that appears only once.

Example 1:
Input: [1,1,2,3,3,4,4,8,8]
Output: 2
Example 2:
Input: [3,3,7,7,10,11,11]
Output: 10
Note: Your solution should run in O(log n) time and O(1) space.
```
## 问题分析：
###### 其实这道题就是奇次偶次的问题，我看好多优质答案用了异或的运算，我没看懂，自己试着做了一下，提交成功了，是我第一次在LeetCode上完完全全只提交一次就成功的代码。
```cpp
class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) {
        int l = 0;
        int r = nums.size()-1;
        int m = 0;
        if(r==l) return 0;
        while (l <= r) {
            m= (l+r)/2;
            if (m%2 == 0) {
                if (nums[m] == nums[m-1]) {
                    r = m2;
                }
                else if (nums[m] == nums[m +1]) {
                    l  = m +2;
                }
                else break;
            }
            else {
                if (nums[m ] == nums[m -1]) {
                    l  = m +1;
                }
                else if (nums[m ] == nums[m +1]) {
                    r  = m -1;
                }
            }
        }
        return nums[m ];
    }
};
```
