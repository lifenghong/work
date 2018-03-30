## 问题：. Binary Tree Inorder Traversal
```
Given a binary tree, return the inorder traversal of its nodes' values.

For example:
Given binary tree [1,null,2,3],
   1
    \
     2
    /
   3
return [1,3,2].
```
## 分析：
###### 这道题题目要求用迭代，然而我不会用迭代，就用了递归的方法，用递归的话就比较简单，以前没用过递归的方法，最近偶尔看到，觉得好用，就用来试试
###### 理解了具体的用法，就比较简单了。
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
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int>tree;
        if(!root)
            return tree;
        vector<int>tree1;
        tree1=inorderTraversal(root->left);
        if(!tree1.empty())
        {
             for(int i=0;i<tree1.size();i++)
             {
                 tree.push_back(tree1[i]);
             }
        }
         tree.push_back(root->val);
        vector<int>tree2;
        tree2=inorderTraversal(root->right);
            if(!tree2.empty())
            {
                for(int i=0;i<tree2.size();i++)
                {
                    tree.push_back(tree2[i]);
                }
            }
           return tree;
        
        
    }
};
```
