## 问题：
```given a non-negative integer num, repeatedly add all its digits until the result has only one digit.

For example:

Given num = 38, the process is like: 3 + 8 = 11, 1 + 1 = 2. Since 2 has only one digit, return it.

Follow up:
Could you do it without any loop/recursion in O(1) runtime?
```
## 分析：
###### 其实这道题如果没有题目要求的话，就很简单，循环递归都可以，然题目要求不用循环递归，然后就不知道怎么做了，总觉得应该是有规律可遵，找啦好半天。才找到规律，这种题如果找不到规律
###### 就很费时间了，
## 代码：||递归：
```cpp
int addDigits(int num) {
	if (num < 10) return num;
	int sum = 0;
	while (num > 0) {
		sum += num % 10;
		num /= 10;
	}
	return addDigits(sum);

}

int main()
{
	int num;
	cin >> num;
	cout << addDigits(num) << endl;
	system("pause");
    return 0;
}
```
## 非递归||这个规律找到滞后，我试了一下，就Ac了；
```
num	     num的数位和	num - num的数位和
m(0≤m≤9)	   m	                0
16           7                 	9
38	         2	                36
86	         5	                81
94	         4	                90
113	         5	                108
```
##### 我试了几个后发现，与num-num的位数和都是9的整数倍，而num与num的位数和之间有位数和=1+（num-1）%9的规律；
## 代码：
```cpp
class Solution {
public:
    int addDigits(int num) {
         return ((num - 1) % 9) + 1;
    }
};
```
