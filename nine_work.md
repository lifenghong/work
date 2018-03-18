## 问题：
```
S并且T是由小写字母组成的字符串。在S，没有信件出现一次以上。

S先前是按一些自定义顺序排序的。我们想要排列字符，T以便它们与S排序的顺序相匹配。更具体地说，如果x发生在yin 之前S，那么x应该y在返回的字符串之前出现。

返回T满足此属性的任何排列（作为字符串）。

例如：
输入： 
S =“cba”
T =“abcd”
输出： “cbad”
 说明： 
在S中出现“a”，“b”，“c”，因此“a”，“b”，“c”的顺序应该是“c”，“b”和“a”。 
由于“d”不出现在S中，它可以在T中的任何位置。“dcba”，“cdba”，“cbda”也是有效的输出。
 ```
 ## 问题分析：
 ##### 这道题我主要练习了一下类的使用，还有string函数，vector函数用法，现在基本掌握vector函数，string函数有一些地方一直不太理解，会继续百度，这几天会一直做这一类的题目。
 
 ```cpp
 struct CustomLess{
public:
    CustomLess(const string& s)
        : m_vals(26, 0) {
        for (size_t i = 0; i < s.size(); ++i) {
            m_vals[s[i] - 'a'] = i + 1;
        }
    }
    
    bool operator() (const char x, const char y) const{
        return m_vals[x - 'a'] < m_vals[y - 'a'];
    }
private:
    vector<int> m_vals;
};

string customSortString(string S, string T) {
    sort(T.begin(), T.end(), CustomLess(S));
    return T;
}
}; 
