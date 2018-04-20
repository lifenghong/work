## 问题：
```
S and T are strings composed of lowercase letters. In S, no letter occurs more than once.

S was sorted in some custom order previously. We want to permute the characters of T so that they match the order that S was sorted. More specifically, if x occurs before y in S, then x should occur before y in the returned string.

Return any permutation of T (as a string) that satisfies this property.
```
## 分析：
##### 给定两个字符串S和T，然后返回S字符串和T中和S不同的元素，S中的元素保持原来的顺序，T中的元素可以查在S的任意位置。思路就是先找到T中与S不同的元素，储存在另一个字符数组中，最后相连S和该字符数组，返回相加后的字符串
## 代码：
class Solution {
public:
    string customSortString(string S, string T) {
        map<char, int> num;
        for (int i=0; i<S.size(); i++) {
            num[S[i]] = 0;
        }
        string s;
        for (int i=0; i<T.size(); i++) {
            if (num.count(T[i]) > 0) {
                num[T[i]]++;
            } else {
                s.push_back(T[i]);
            }
        }
        for (int i=0; i<S.size(); i++) {
            for (int j=0; j<num[S[i]]; j++) {
                s += S[i];   
            }
        }
        return s;
    }
};
