##  问题：814. Binary Tree Pruning
```
We are given the head node root of a binary tree, where additionally every node's value is either a 0 or a 1.

Return the same tree where every subtree (of the given tree) not containing a 1 has been removed.

(Recall that the subtree of a node X is X, plus every node that is a descendant of X.)

Example 1:
Input: [1,null,0,0,1]
Output: [1,null,0,null,1]
 
Explanation: 
Only the red nodes satisfy the property "every subtree not containing a 1".
The diagram on the right represents the answer.


Example 2:
Input: [1,0,1,0,0,0,1]
Output: [1,null,1,null,1]



Example 3:
Input: [1,1,0,1,1,0,1,0]
Output: [1,1,0,1,1,null,1]
```
## 分析：
###### 我发现好多二叉树的题都可以用递归做，简单方便。这道题大体的思路就是删除左右子树都为0的节点，为我们的判断就是当这个节点为0而且他的左右子树都为0时，（考虑到左右子树中有空的现象）
###### 删除这个节点，函数实现就是直接delete掉，然后返回空，再依次循环，找到下一个节点继续执行。
## 代码：
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
    TreeNode* pruneTree(TreeNode* root) {  
        if (root == NULL) {  
            return NULL;  
        }  
        TreeNode *left = pruneTree(root->left);  
        TreeNode *right = pruneTree(root->right);  
        if (left == NULL && right == NULL && root->val == 0) {  
            delete root;  
            return NULL;  
        }  
        root->left = left;  
        root->right = right;  
        return root;  
    }  
};  
```
