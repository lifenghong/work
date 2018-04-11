## 问题：
```
Given two integers n and k, you need to construct a list which contains n different positive integers ranging from 1 to n and obeys the following requirement: 
Suppose this list is [a1, a2, a3, ... , an], then the list [|a1 - a2|, |a2 - a3|, |a3 - a4|, ... , |an-1 - an|] has exactly k distinct integers.

If there are multiple answers, print any of them.

Example 1:
Input: n = 3, k = 1
Output: [1, 2, 3]
Explanation: The [1, 2, 3] has three different positive integers ranging from 1 to 3, and the [1, 1] has exactly 1 distinct integer: 1.
Example 2:
Input: n = 3, k = 2
Output: [1, 3, 2]
Explanation: The [1, 3, 2] has three different positive integers ranging from 1 to 3, and the [2, 1] has exactly 2 distinct integers: 1 and 2.
```
## 分析：
##### 这道题就是给了两个数，n k，使得1到n组成的数组中相邻两个数的差的绝对值正好有k种。给了k和n的关系为k<n;
##### 所以我们知道k最大为n-1，所以这样的排列一定会存在。我们的策略是，先按照这种最小最大数相邻的方法排列，
##### 没排一个，k自减1，当k减到1的时候，后面的排列方法只要按照生序的方法排列，就不会产生不同的差的绝对值我们使用两个指针，初始时分别指向1和n，
##### 然后分别从i和j取数加入结果res，每取一个数字k自减1，直到k减到1的时候，开始按升序取后面的数字
##### 然而我再一次超时了，这是修改后的；
## 代码：
```cpp
vector<int> s;
        int i = 1, j = n;
        while (i <= j)
        {
            if (k == 1)
            {
               s.push_back(i);
                i++;
            }
            else if (k > 1)
            {
                if (k % 2 == 1)
                {
                    s.push_back(i);
                    i++;
                }
                else
                {
                   s.push_back(j);
                    j--;
                }
                k--;
            }
        }
        return res;
