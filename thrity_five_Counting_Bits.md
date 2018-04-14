## 问题：
```
Given a non negative integer number num. For every numbers i in the range 0 ≤ i ≤ num calculate the number of 1's in their binary representation and return them as an array.

Example:
For num = 5 you should return [0,1,1,2,1,2].

Follow up:

It is very easy to come up with a solution with run time O(n*sizeof(integer)). But can you do it in linear time O(n) /possibly in a single pass?
Space complexity should be O(n).
Can you do it like a boss? Do it without using any builtin function like __builtin_popcount in c++ or in any other language.
```
## 分析：
##### 这道题用暴力解法可以说是非常简单的了，但是题干要求，不能用暴力解法，要让时间复杂度和空间复杂度都是O（n），这就需要想一种更为高效的算法。
##### 其实我的解法有点像“找规律”，通过列出0-16的二进制数的“1”的个数{0，1，1，2，1，2，2，3，1，2，2，3，2，3，3，4}，我们可以发现以下规律：
##### 其实大于等于2的k次方、小于2的k+1次方之间的二进制数的“1”的个数，正好是大于等于0、小于2的k次方的数每个数对应加一得来，比如：当k等于1时，
##### 2的k次方等于2，2的k+1次方等于4，那么[2, 4)中（即2和3）的二进制数的“1”的个数是{1，2}，[0, 2）中（即0和1）的二进制数的“1”的个数是{0，1}，
##### 也就是{0，1}的中的两项各加1即可得{1，2}。
## 代码：
```cpp
class Solution {
public:
    vector<int> countBits(int num) {
        vector<int> ans;
        int index = 0;
        for (int i = 0; i <= num; i++) {
            if (i == 0) {
                ans.push_back(0);
                continue;
            }
            if (i == pow(2, index)) {
                index++;
            }
            ans.push_back(1 + ans[i - pow(2, index - 1)]);
        }
        return ans;
    }
};
```
