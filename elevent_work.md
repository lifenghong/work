## 问题：
```
以k个步骤向右旋转n个元素的数组。

例如，当n = 7和k = 3时，数组[1,2,3,4,5,6,7]被旋转到[5,6,7,1,2,3,4]。

注意：
尽可能多地提出解决方案，至少有3种不同的方法来解决这个问题。
```
## 分析：
##### 这道题目刚开始我以为其实比较简单，用vector函数和·remove函数解决·或者反转字符串用数组也可以。但提交后是错误的，后来发现我只考虑了按顺序并且忽视了n的大小，
```cpp
class Solution 
{
public:
    void rotate(int nums[], int n, int k) 
    {
        if ((n == 0) || (k <= 0) || (k%n == 0))
        {
            return;
        }
        
        k = k%n;
        int start = 0;
        int tmp = 0;
        while (k > 0)
        {
            if (n - k >= k)
            {
                for (int i = 0; i < k; i++)
                {
                    tmp = nums[start + n - 2*k + i];
                    nums[start + n - 2*k + i] = nums[start + n - k + i];
                    nums[start + n - k + i] = tmp;
                }
                
                n = n - k;
                k = k%n;
            }
            else
            {
                for (int i = 0; i < n - k; i++)
                {
                    tmp = nums[start + i];
                    nums[start + i] = nums[start + n - k + i];
                    nums[start + n - k + i] = tmp;
                }
          
                tmp = n - k;
                n = k;
                k -= tmp;
                start += tmp;
            }
        }
    }
};

