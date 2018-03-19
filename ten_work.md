## 问题：
> We are given two strings, A and B.

A shift on A consists of taking string A and moving the leftmost character to the rightmost position. For example, if A = 'abcde', then it will be 'bcdea' after one shift on A. Return True if and only if A can become B after some number of shifts on A.

Example 1:
Input: A = 'abcde', B = 'cdeab'
Output: true

Example 2:
Input: A = 'abcde', B = 'abced'
Output: false
## 分析：这道题用以前的方法的话也可以做，不是特别麻烦，定义数组移位就可以，最近一直在做string函数的题，就参考答案用了string函数，就很简单了，string：：append、
