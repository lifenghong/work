## 问题：
```
Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

For example:
Given the below binary tree and sum = 22,

              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1
return true, as there exist a root-to-leaf path 5->4->11->2 which sum is 22.
```
## 分析：
##### 这道题我还是用来专门练习一下递归，现在基本可以熟练用运递归做类似的题目了。
## 代码实现：
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool hasPathSum(TreeNode* root, int sum) {
        if(root==NULL)
            return 0;
        else if(root->left==NULL&&root->right==NULL&&root->val==sum)
        {
            return 1;
        }
        else 
        {
            return hasPathSum(root->left,sum-root->val)||hasPathSum(root->right,sum-root->val);
        }
    }
};
```
