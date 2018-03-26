## 问题：
```
Given a binary tree, find the length of the longest path where each node in the path has the same value. This path may or may not pass through the root.

Note: The length of path between two nodes is represented by the number of edges between them.

## 分析：
##### 开始搞错了，原来要求的是最长的路径，所以就不可以往回走，只能是两个节点的路径，那这个路径就可以表示为一个根结点到左边的最长路径+到右边最长路径，简单的对每一个根结点往左往右递归求解就好。 
对每一个结点，以其作为根结点，对左右分别dfs求得从当前节点出发左边最长和右边最长的值，然后加起来和max对比，如果大于max则替换max。然后返回上一层，返回上一层的数要为左边或右边的最大值，而不是相加值，因为对于父节点为根结点的话只能往左或者往右寻找最长路径，而不能先去左边然后去右边然后返回。
## 代码：
```cpp
class Solution {
public:
    int longestUnivaluePath(TreeNode* root) {
        if (!root) return 0;
        int max = 0;
        dfs(root, max);
        return max;
    }

    int dfs(TreeNode* root, int & max) {
        int l = 0, r = 0;

        if (root->left && root->left->val == root->val)
            l = 1 + dfs(root->left, max);
        else if (root->left)
            dfs(root->left, max);

        if (root->right && root->right->val == root->val)
            r = 1 + dfs(root->right, max);
        else if (root->right)
            dfs(root->right, max);

        if (l+r > max)
            max = l+r;

        return (l > r) ? l : r;
    }
};
## 分析：
###### 其实这道题我是想练习一下递归，然后dfs函数的使用，get新的知识点
