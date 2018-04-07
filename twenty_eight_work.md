## 问题：
```
Given two non-empty binary trees s and t, check whether tree t has exactly the same structure and node values with a subtree of s. 
A subtree of s is a tree consists of a node in s and all of this node's descendants. 
@ The tree s could also be considered as a subtree of itself.
```
## 分析：
###### 这道题树s和树t均非空，判断s是不是整体与t相同，相同返回TRUE，不同的话判断s的左子树和右子树是否与t相同，依次递归下去
###### 关键是写出一个函数，给定两个二叉树根节点，判断两个二叉树是否相等，做过很多类似的题目了，还算可以啦
## 代码
```cpp
**
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
    bool isSubtree(TreeNode* s, TreeNode* t) {
        if(s==NULL)
            return false;
       if(same(s,t))
           return true;
        return isSubtree(s->left,t)||isSubtree(s->right,t);
    }
    bool same(TreeNode* p,TreeNode *q)
        {
            if(p==NULL&&q==NULL){
                return true;
                
            }
            if(p==NULL||q==NULL)
                return false;
            if(p->val!=q->val)
                return false;
            return  same(p->left,q->left)&&same(p->right,q->right);
            
        }
        
    
};
