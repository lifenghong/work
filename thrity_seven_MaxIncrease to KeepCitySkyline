## 问题：Max Increase to Keep City Skyline
```
In a 2 dimensional array grid, each value grid[i][j] represents the height of a building located there. We are allowed to increase the height of any number of buildings, by any amount (the amounts can be different for different buildings). Height 0 is considered to be a building as well. 

At the end, the "skyline" when viewed from all four directions of the grid, i.e. top, bottom, left, and right, must be the same as the skyline of the original grid. A city's skyline is the outer contour of the rectangles formed by all the buildings when viewed from a distance. See the following example.

What is the maximum total sum that the height of the buildings can be increased?

Example:
Input: grid = [[3,0,8,4],[2,4,5,7],[9,2,6,3],[0,3,1,0]]
Output: 35
Explanation: 
The grid is:
[ [3, 0, 8, 4], 
  [2, 4, 5, 7],
  [9, 2, 6, 3],
  [0, 3, 1, 0] ]

The skyline viewed from top or bottom is: [9, 4, 8, 7]
The skyline viewed from left or right is: [8, 7, 9, 3]

The grid after increasing the height of buildings without affecting skylines is:

gridNew = [ [8, 4, 8, 7],
            [7, 4, 7, 7],
            [9, 4, 8, 7],
            [3, 3, 3, 3] ]
```
## 分析：
##### 这道题的实际要求给一位二维数组的元素增加它的值，结果不能使其每行每列的最大的数还是原来的数字，我的做法是遍历每行每列找到最大的数，储存在一个数组中a
##### 然后要求数组中其他元素增加过后的值任然小于数组a中的最小值，计算总共增加的值就可以啦
## 代码：
```cpp
class Solution {
public:
    int maxIncreaseKeepingSkyline(vector<vector<int>>&grid ) {
        int r = grid.size(), c= grid[0].size(); 
        int count=0;
       /* for(int j=0;j<c;j++)
        {
            ;
            for(int i=0;i<r;i++)
          {
           if(grid.[i]>ans)
           {
               ans=grid[i];
           }
          }
        }
        for(int i=0;i<r;i++)
        {
            for(int j=0j<c;j++)
            {
                if(grid[i][j]>anss)
                {
                    anss=grid[i][j];
                }

             }
        }
        for(int i=0;i<c;i++)
        {
            for(int j=0;j<c;j++)
            {
                if(grid[i][j]<ans||grid[i][j]<anss)
                {
                   (grid[i][j])++;
                    count++;
                    
                }
            }
        }*/
        vector<int>row(r,0);
        vector<int>col(c,0);
        for(int i=0;i<r;i++)
        {
            
            for(int j=0;j<c;j++)
            {
                row[i]=max(row[i],grid[i][j]);
                col[j]=max(col[j],grid[i][j]);
            }
        }
        for(int i=0;i<r;i++)
        {
            for(int j=0;j<c;j++)
            {
                int minnum=min(row[i],col[j]);
                if(grid[i][j]<minnum)
                {
                    count+=minnum-grid[i][j];
                }
            }
        }
        return count;
    }
};
```
