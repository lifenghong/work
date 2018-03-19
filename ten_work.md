## 问题：
```
We are given two strings, A and B.

A shift on A consists of taking string A and moving the leftmost character to the rightmost position. For example, if A = 'abcde', then it will be 'bcdea' after one shift on A. Return True if and only if A can become B after some number of shifts on A.

Example 1:
Input: A = 'abcde', B = 'cdeab'
Output: true

Example 2:
Input: A = 'abcde', B = 'abced'
Output: false
```
## 分析：
###### 这道题用以前的方法的话也可以做，不是特别麻烦，定义数组移位就可以，最近一直在做string函数的题，就参考答案用了string函数，就很简单了string：：Append()在string后加元素，string。remove移除数组中元素，比较简单。两个函数就可以，初级阶段，还是一练习为主，
## 代码：
```cpp

class Solution {
public:
    bool rotateString(string A, string B) {
        if(A.length()!=B.length())
            return false;
        if(A.length()==0)
            return true;
       char temp = new StringBuilder();
        temp.Append(A);
        for (int s = 0; s < A.Length; s++)
        {
            temp.Remove(0, 1);
            temp.Append(A[s]);
            if (temp.ToString() == B)
                return true;
        }

        return false;
}

};
```


