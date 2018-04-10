## 问题：
```
Suppose you have N integers from 1 to N. We define a beautiful arrangement as an array that is constructed by these N numbers successfully if one of the following is true for the ith position (1 <= i <= N) in this array:

The number at the ith position is divisible by i.
i is divisible by the number at the ith position.
Now given N, how many beautiful arrangements can you construct?

Example 1:
Input: 2
Output: 2
Explanation: 

The first beautiful arrangement is [1, 2]:

Number at the 1st position (i=1) is 1, and 1 is divisible by i (i=1).

Number at the 2nd position (i=2) is 2, and 2 is divisible by i (i=2).

The second beautiful arrangement is [2, 1]:

Number at the 1st position (i=1) is 2, and 2 is divisible by i (i=1).

Number at the 2nd position (i=2) is 1, and i (i=2) is divisible by 1.
```
## 思路：
###### 这道题做了好久，刚开始准备找规律，发现毫无规律可言，只能穷举，但又超时，就只能尝试着用递归和回溯，将数先按自然数顺序输入数组，
###### 然后判断，如果符合题目要求，count++，在将元素位置调换，再次判断，一直递归下去，直到所有的元素位置都已经掉换过，而没有重复；
```cpp
class Solution {
public:
    int countArrangement(int N) {
        vector<int> num;
        for (int i=0; i<N; ++i) num.push_back(i+1);
        return counts(N, num);
    }
    int counts(int n, vector<int>& num) {
        if (n ==1) return 1;
        int count = 0;
        for (int i=0; i<n; ++i) {
            if (num[i]%n==0 || n%num[i]==0) {
                swap(num[i],num[n-1]);
                count += counts(n-1, num);
                swap(num[i], num[n-1]);
            }
        }
        return count;
    }
};
```
