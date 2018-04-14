## 问题：
```
Description:

Count the number of prime numbers less than a non-negative number, n.
```
## 题目分析：
###### 这是比较简单的题，我主要是被标题吸引了，先将小于n的所有数都标记为true，从0开始，对接下来见到的每一个素数（true），使所有有这个素数因子的数都标记为false（本身不标记） 
###### 最后查找数组中为true的个数就是答案，这样可以减少一定的运算次数
```cpp
class Solution {
public:
    int countPrimes(int n) {
    vector<bool> prime(n,true);
    prime[0]=false,prime[1]=false;
    for(int i=0;i<sqrt(n);++i){
        if(prime[i]){
            for(int j=i*i;j<n;j+=i){
                prime[j]=false;
            }
        }
    }
    return count(prime.begin(),prime.end(),true);
}
};
```
