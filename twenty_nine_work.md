## 问题：
```
Find the minimum length word from a given dictionary words, which has all the letters from the string licensePlate. Such a word is said to complete the given string licensePlate

Here, for letters we ignore case. For example, "P" on the licensePlate still matches "p" on the word.

It is guaranteed an answer exists. If there are multiple answers, return the one that occurs first in the array.

The license plate might have the same letter occurring multiple times. For example, given a licensePlate of "PP", the word "pair" does not complete the licensePlate, but the word "supper" does.

Example 1:
Input: licensePlate = "1s3 PSt", words = ["step", "steps", "stripe", "stepple"]
Output: "steps"
Explanation: The smallest length word that contains the letters "S", "P", "S", and "T".
Note that the answer is not "step", because the letter "s" must occur in the word twice.
Also note that we ignored case for the purposes of comparing whether a letter exists in the word.
Example 2:
Input: licensePlate = "1s3 456", words = ["looks", "pest", "stew", "show"]
Output: "pest"
Explanation: There are 3 smallest length words that contains the letters "s".
We return the one that occurred first.
Note:
licensePlate will be a string with length in range [1, 7].
licensePlate will contain digits, spaces, or letters (uppercase or lowercase).
words will have a length in the range [10, 1000].
Every words[i] will consist of lowercase letters, and have length in range [1, 15].

```
## 分析：先分析所給字符串有多少g个字母，全部化成小写来计数。然后再在向量找出符合要求的长度最短的一个输出：
## 代码：
```cpp
class Solution {
public:
    string shortestCompletingWord(string licensePlate, vector<string>& words) {
        int array[26], ans = -1, copy[26];
        
        
        for (int i = 0; i < 26; i++) {
            array[i] = 0;
        }
        
        for (int i = 0; i < licensePlate.length(); i++) {
            if ('a' <= licensePlate[i] && licensePlate[i] <= 'z') {
                array[licensePlate[i] - 'a'] += 1;
            }
            if ('A' <= licensePlate[i] && licensePlate[i] <= 'Z') {
                array[licensePlate[i] - 'A'] += 1;
            }
        }
        
        for (int i = 0; i < words.size(); i++) {
            
            for (int j = 0; j < 26; j++) {
                copy[j] = array[j];
            }
            
            int j;
            
            for (j = 0; j < 26; j++) {
                for (int k = 0; k < words[i].length(); k++) {
                    if (copy[j] == 0) {
                        break;
                    }
                    
                    if (words[i][k] - 'a'== j) {
                        copy[j]--;
                    }
                }
                
                if (copy[j] != 0) {
                    break;
                }
            }
            
            if (j == 26) {
                if (ans == -1) {
                    ans = i;
                }
                else if (words[i].length() < words[ans].length()) {
                    ans = i;
                }
            }
        }
        
        return words[ans];
    }
};
```


