## 问题:
```
给定两个表示两个复数的字符串。

您需要返回一个表示其乘法的字符串。注意i 2 = -1根据定义。

示例1： 
输入： “1 + 1i”，“1 + 1i” 
输出： “0 + 2i” 
说明：（1 + i）（1 + i）= 1 + i 2 + 2 i = 2i，以0 + 2i的形式。 
示例2： 
输入： “1 + -1i”，“1 + -1i” 
输出： “0 + -2i” 
说明：（1 - i）（1 - i）= 1 + i 2 - 2 i =您需要将其转换为0 + -2i的形式。
```
## 分析：
##### 这道题其实理解·起来不难，，就是根据+进行分割，然后进行转成数字进行计算，，用传统的方法也可以做出来，但这里我主要用来练习了一下stoi和substr的用法，这里主要是注意返回任然是a+bi的形式，我第一次就错了


### 代码实现：

```cpp
 string complexNumberMultiply(string c1, string c2) {
        if(c1.length() == 0|| c2.length() == 0)
            return "";
        string result = "";
        int a,b,c,d;
        string::size_type sz;
        sz = 0;
        a = stoi(c1,&sz);
        
        b = stoi(c1.substr(sz+1),NULL);
        sz =0;
        
        c = stoi(c2,&sz);
        d = stoi(c2.substr(sz+1),NULL);
        int A = a*c - b*d;
        int B = a*d + c*b;
        result += to_string(A);
         result+="+";
        result += to_string(B);  
        result+="i";
      return result;  
    }
    ```
