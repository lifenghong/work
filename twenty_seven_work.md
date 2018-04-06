## 问题：
```
Given a list of sorted characters letters containing only lowercase letters, and given a target letter target, find the smallest element in the list that is larger than the given target.

Letters also wrap around. For example, if the target is target = 'z' and letters = ['a', 'b'], the answer is 'a'.
```
## 分析：
##### 这道题就是用了二分法：说了数组至少有两个元素，那么我们首先用数组的尾元素来跟target比较，如果target大于等于尾元素的话，直接返回数组的首元素即可。否则就利用二分法来做，这里是查找第一个大于目标值的数组
### 代码：
```cpp
class Solution {
public:
    char nextGreatestLetter(vector<char>& letters, char target) {
        if (target >= letters.back()) return letters[0];
        int n = letters.size(), left = 0, right = n;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (letters[mid] <= target) left = mid + 1;
            else right = mid;
        }
        return letters[right];
    }
};

```
