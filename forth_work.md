## 问题：
```
给你一个代表学生出勤记录的字符串。该记录只包含以下三个字符：
'A'：缺席。
'L'：晚了。
'P'：现在。
如果他的出勤记录不包含多于一个“A”（缺席）或超过两个连续的“L”（晚），则可以奖励学生。

您需要根据他的出勤记录返回是否可以奖励学生。
```
## 问题分析：
###### 这道题目比较简单，因为今天一直在做一道指针的问题，就做了一个简单的放松一下；这道题只需以一个char型数组保存输入的字符串，遍历数组，纪律、录下数组中A和L的个数，在判断即可，用简单的if和else就能做出来，或者也可以用bool型直接定义
## 代码实现(自己的）：
```cpp
c++
#include<iostream>
#include<cstring>
using namespace std;
int main()
{
	char a[100];
	gets(a);
	int count1=0;
	int count2=0;
	for(int i=0;i<strlen(a);i++)
	{
		if(a[i]=='A')
		count1++;
		if(a[i]=='L')
		count2++;
	}
	if(count1>1||count2>2)
	cout<<"false"<<endl;
	else 
	cout<<"ture"<<endl;
	
	return 0;
 } 
 ```
 ## 优质代码：
 ```cpp
 bool checkRecord(string s) {
    int a=0, l=0;
    for(int i=0;i<s.size();i++) {
        if(s[i]=='A') a++;
        if(s[i]=='L') l++;
        else l=0;
        if(a>=2||l>2) return false;
    }
    return true;
}
```
## 分析
##### 其实优质代码和自己的思路差不多，只是在代码实现上比我的更简洁，在做问题的时候，很多情况下知道思路，却不明白用怎样的代码去实现，会继续练习。
