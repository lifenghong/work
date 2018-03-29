## 问题：
```
Given a list of non negative integers, arrange them such that they form the largest number.

For example, given [3, 30, 34, 5, 9], the largest formed number is 9534330.

Note: The result may be very large, so you need to return a string instead of an integer.

Credits:
Special thanks to @ts for adding this problem and creating all test cases.
```
## 分析：
##### 刚开始想的是这个比较简单，直接排序就好啦，结果做的时候发现，这样子就要一个个的转换成整数然后排序，没办法做到，后来想了一下其实很简单只要将整数转化成字符串就好，但最大额问题是怎样转换，所以就用单一个函数sprintf
##### 最重要的是sprintf函数的用法
```cpp
class Solution {
public:
    string largestNumber(vector<int>& nums) {   
        int len = nums.size();
        vector<string> str;
        for (int i = 0; i < len; ++i) {
            char m[20];
            sprintf(m, "%d", nums[i]);
            str.push_back(m); 
        }
        sort(str.begin(), str.end(), c);
        string ret;
        for (int i = 0; i < len; ++i) ret += str[i];
        if (ret == "" || ret[0] == '0') ret = "0";

        return ret;
    }
    static bool c(string a, string b) { return a + b > b + a; }
};
```
