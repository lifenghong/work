## 问题：
```
Implement strStr().

Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

Example 1:

Input: haystack = "hello", needle = "ll"
Output: 2
Example 2:

Input: haystack = "aaaaa", needle = "bba"
Output: -1
```
## 分析：
###### 轮寻第一个字符串s1，比较s1的字符和s2的第一个字符，如果相等，则strncmp(s1, s2, len(s2)) == 0 ?。不相等则s1++。

```cpp
class Solution {
public:
    int strStr(string haystack, string needle) {
        int len = needle.length();
        if(len == 0){
            return 0;
        }
        if(haystack.length() == 0){
            return -1;
        }
        for(int i = 0; i < haystack.length(); ++i){
            if(haystack[i] == needle[0] && haystack.substr(i, len) == needle){
                return i;
            }
        }
        return -1;
    }
};
```
## 总结
##### strncmp函数用于比较特定长度的字符串。

##### 头文件：string.h。

##### 语法  int strncmp(const char *string1, const char *string2, size_t count);
 
