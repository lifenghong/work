
## 问题：
```
Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.

If the last word does not exist, return 0.

Note: A word is defined as a character sequence consists of non-space characters only.

Example:

Input: "Hello World"
Output: 5
```
## 分析：
###### 这道题比较简单，还是练习了一下string函数的用法，定义string的对象，用string函数就可以解决，刚开始我用了遍历整个个字符串的方法，从头到尾遍历，找到最后一个字符串，然后用begin-end，做出来了，但比较麻烦，后来用另一种，比较容易理解。

## 方法一：
```cpp
class Solution {
public:
   int lengthOfLastWord(string s) {
   
        int i=s.size()-1,j;
       
        while(i>=0&&s[i]==' ') i--;
        j=i;
        while(i>=0&&s[i]!=' ') i--;
        return j-i;
    }
};
```
## 方法二:
```cpp
int lengthOfLastWord（string s）{ 
int count = 0;

    int i = s.size() - 1;
     while(i >= 0 && s[i] == ' ' ) --i;
    if(i == -1) return 0;
   
    while(i >= 0 && s[i--] != ' ' ) ++count;
    
    return count;
}
```
